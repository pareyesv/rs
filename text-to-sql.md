---
title: Semantic SQL Generation & Prompt Translation
author: Gemini 3.0
date: November 21, 2025
---

This is a specialized area of AI engineering that combines **Database Theory** (Semantic Layers) with **Large Language Model (LLM)** mechanics (Prompt Engineering).

Here is an explanation of **Semantic SQL Generation** and **Prompt-Based Query Translation**, detailing how they differ and how they work together to build reliable "Talk-to-Data" systems.

---

## 1. The Core Concept: Why Do We Need This?

Standard "Text-to-SQL" (asking ChatGPT to write a query) often fails in production because LLMs do not understand your business context. They might write valid SQL code that calculates "Revenue" incorrectly because they don't know your company's specific logic (e.g., *Revenue = Sales - Returns*).

* **Semantic SQL Generation** solves the **"Context"** problem (defining what the data *means*).
* **Prompt-Based Query Translation** solves the **"Mechanics"** problem (converting English into code).

---

## 2. Semantic SQL Generation

This approach moves away from letting an LLM guess how to join your raw tables. Instead, you introduce a "Semantic Layer"—an intermediate translation layer that defines your business logic.

### How It Works

1. **The Semantic Layer:** You define a virtual view of your data (using tools like Cube, Looker, dbt, or a custom JSON schema). You tell the system: "A **Customer** has many **Orders**," and "Total **Revenue** is the sum of `order_value` where `status` is 'completed'."
2. **Generation Process:** When a user asks, "Show me revenue by customer," the system does not try to guess the join paths between 15 different raw tables. It looks at your Semantic definitions.
3. **The Output:** The generation target is often not raw SQL immediately, but a "Semantic Query" (like a specialized API call or a simplified logical SQL) which is then deterministically compiled into the complex, optimized physical SQL needed by the database.

### Why It Matters

* **Hallucination Prevention:** The LLM is restricted to choosing from a defined list of metrics (e.g., `Revenue`, `Churn_Rate`) rather than making up columns that don't exist.
* **Consistency:** If two users ask for "Sales," they get the exact same SQL calculation, guaranteed by the semantic layer.

---

## 3. Prompt-Based Query Translation

This refers to the specific techniques used to guide an LLM (like GPT-4, Claude 3.5, or Llama 3) to perform the translation from Natural Language (NL) to SQL. This is the "engine" of the system.

It is rarely as simple as "Here is my schema, write a query." Advanced architectures use the following translation strategies:

### A. The Translation Pipeline (RAG for SQL)

Instead of pasting your entire database schema into the prompt (which is too large and confusing), you use **Retrieval-Augmented Generation (RAG)**:

1. **User Question:** "Who are the top buyers in California?"
2. **Schema Retrieval:** The system searches your metadata to find only the relevant tables (e.g., `Users` and `Orders`) and ignores irrelevant ones (e.g., `Inventory`, `HR_Log`).
3. **Prompt Construction:** The system builds a dynamic prompt containing only those relevant tables + the user's question.

### B. Key Prompting Techniques

* **Zero-Shot Translation:** You provide the schema and the question, relying entirely on the model's training. (Lowest accuracy).
* **Few-Shot Translation (In-Context Learning):** You include 3-5 examples of "Question -> Correct SQL" pairs in the prompt. This massively increases accuracy because the model mimics the pattern of the examples.
* **Chain-of-Thought (CoT):** You instruct the model to "Think step-by-step" before writing the code.
  * *Example Output:* "First, I need to identify the user's table. Second, I need to filter by 'California'. Third, I will join the orders table to sum purchases. Finally, I will generate the SQL."

### C. Decomposition (Query Translation)

For complex questions, the system translates the user's intent into smaller steps before generating SQL.

* *User:* "Compare the sales of Q1 2023 vs Q1 2024."
* *Translation:* The system breaks this into two sub-queries (Get Q1 '23 Sales; Get Q1 '24 Sales) or translates it into a single query with a `CASE` statement, based on the prompt instructions.

---

## 4. Putting It Together: The Architecture

In a modern, enterprise-grade system, these two concepts merge into a workflow like this:

1. **User Input:** "How many red widgets did we sell last week?"
2. **Semantic Parsing:** The system identifies "red widgets" as a filter on the `Product` entity and "last week" as a time range.
3. **Prompt Engineering:** The system constructs a prompt.
    * *Context:* "You are a Postgres expert."
    * *Semantic Info:* "Note: 'Sold' means `order_status = 'closed'`."
    * *Schema:* (Only snippets of the `Products` and `Sales` tables).
4. **Generation & Self-Correction:** The LLM generates the SQL.
    * *Validation:* The system tries to run a "Dry Run" (EXPLAIN) of the query. If the database returns a syntax error, the error message is fed back into the LLM to "fix your code" (Self-Correction).
5. **Execution:** The final, valid SQL is run against the database.

## Summary Table

| Feature | Semantic SQL Generation | Prompt-Based Query Translation |
| :--- | :--- | :--- |
| **Focus** | **Business Logic** (What the data means) | **Syntax & Structure** (How to write the code) |
| **Primary Goal** | Consistency, Accuracy, preventing logic errors. | Syntactic correctness, handling complex joins/filters. |
| **Key Component** | Semantic Layer (Looker, Cube, dbt). | LLM Context Window, System Prompts. |
| **Analogy** | The "Dictionary" that defines terms. | The "Translator" that speaks the language. |

---

## Examples

Here are several concrete examples using Python to integrate OpenAI and Google Gemini APIs for SQL generation.

I have categorized these by **complexity**, starting from a simple translation to a robust "Self-Correcting" system that validates the SQL.

### Prerequisites

You will need the libraries:

```bash
pip install openai google-generativeai
```

---

### Example 1: Basic Schema-Aware Translation (OpenAI)

In this example, we provide the LLM with the database schema (context) so it doesn't hallucinate column names. We specifically instruct it to output *only* raw SQL.

```python
import os
from openai import OpenAI

client = OpenAI(api_key="YOUR_OPENAI_API_KEY")

# 1. Define the Schema (Context)
# This is crucial. The LLM needs to know what tables exist.
schema_context = """
CREATE TABLE users (
    id INT PRIMARY KEY,
    signup_date DATE,
    region VARCHAR(50)
);

CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    user_id INT,
    amount DECIMAL(10, 2),
    status VARCHAR(20) -- values: 'completed', 'pending', 'cancelled'
);
"""

def generate_sql_openai(natural_query):
    prompt = f"""
    Given the following SQL schema:
    {schema_context}

    Write a SQL query to answer this question: "{natural_query}"
    
    IMPORTANT: 
    - Return ONLY the SQL code. No markdown, no explanations.
    - Use standard PostgreSQL syntax.
    """

    response = client.chat.completions.create(
        model="gpt-4o", # or gpt-3.5-turbo
        messages=[
            {"role": "system", "content": "You are a SQL expert."},
            {"role": "user", "content": prompt}
        ],
        temperature=0 # Keep temperature low for deterministic code
    )
    
    return response.choices[0].message.content.strip()

# Usage
nl_query = "Find the total amount spent by users in the 'US' region who signed up in 2023."
sql_output = generate_sql_openai(nl_query)

print(f"Query: {nl_query}")
print(f"SQL: {sql_output}")
```

---

### Example 2: Google Gemini with "Chain of Thought" Prompting

Here we use Gemini. We also use a **Chain of Thought (CoT)** prompt approach. We ask the model to explain its logic *before* writing the SQL. This usually results in higher accuracy for complex joins.

```python
import google.generativeai as genai

genai.configure(api_key="YOUR_GOOGLE_API_KEY")

def generate_sql_gemini(natural_query):
    model = genai.GenerativeModel('gemini-1.5-flash')
    
    schema = """
    Table: Employees (id, name, dept_id, salary, hire_date)
    Table: Departments (id, name, location)
    """
    
    prompt = f"""
    You are a data analyst. 
    Schema: {schema}
    
    Question: {natural_query}
    
    Instructions:
    1. Think step-by-step about which tables to join.
    2. Identify necessary filters.
    3. Finally, output the SQL query inside a JSON block like this:
    {{ "thought_process": "...", "sql": "..." }}
    """
    
    response = model.generate_content(prompt)
    return response.text

# Usage
query = "List the top 3 departments with the highest average salary."
print(generate_sql_gemini(query))
```

---

### Example 3: The "Self-Correction" Loop (Validation)

**This is the most important architecture.** LLMs often make syntax errors. This script attempts to run the SQL on a local database (`sqlite3`). If it fails, it feeds the error message *back* into the LLM and asks it to fix the code.

```python
import sqlite3
from openai import OpenAI

client = OpenAI(api_key="YOUR_OPENAI_API_KEY")

# Setup a dummy in-memory database to test the SQL
conn = sqlite3.connect(":memory:")
cursor = conn.cursor()
cursor.executescript("""
    CREATE TABLE products (id INTEGER, name TEXT, price REAL, category TEXT);
    INSERT INTO products VALUES (1, 'Laptop', 1200.00, 'Electronics');
    INSERT INTO products VALUES (2, 'Mouse', 25.00, 'Electronics');
""")
conn.commit()

def run_query_safe(sql):
    try:
        cursor.execute(sql)
        return cursor.fetchall(), None
    except Exception as e:
        return None, str(e)

def translate_and_validate(question):
    # Initial Prompt
    messages = [
        {"role": "system", "content": "You are a SQL generator for SQLite."},
        {"role": "user", "content": f"Schema: Table products(id, name, price, category).\nQuestion: {question}\nReturn ONLY SQL."}
    ]

    # Allow up to 3 attempts to fix errors
    for attempt in range(3):
        print(f"--- Attempt {attempt + 1} ---")
        
        # call LLM
        response = client.chat.completions.create(model="gpt-4o", messages=messages)
        sql_candidate = response.choices[0].message.content.replace("```sql", "").replace("```", "").strip()
        
        print(f"Generated SQL: {sql_candidate}")

        # VALIDATION STEP: Try to run it
        results, error = run_query_safe(sql_candidate)
        
        if error:
            print(f"SQL Error found: {error}")
            # Feed the error back to the LLM context
            messages.append({"role": "assistant", "content": sql_candidate})
            messages.append({"role": "user", "content": f"That SQL query resulted in an error: {error}. Please fix the query and return only the corrected SQL."})
        else:
            print("Validation Successful!")
            return sql_candidate, results

    return None, "Failed to generate valid SQL after 3 attempts."

# Usage
# Let's ask a question. 
# (Note: The system handles the logic seamlessly, or fixes syntax if it messes up).
sql, data = translate_and_validate("What is the average price of Electronics?")
print(f"\nFinal Data: {data}")
```

---

### Example 4: Semantic Validation (Logic Checking)

Sometimes the SQL is valid (it runs), but the **logic** is wrong (it hallucinates a column).

You can use a "Validation Step" where you ask the LLM to critique its own work against a strict column list before returning the answer.

```python
def validate_semantics(generated_sql, valid_columns):
    """
    Uses a cheaper model to check if the generated SQL uses phantom columns.
    """
    prompt = f"""
    Review this SQL query:
    {generated_sql}
    
    The ONLY allowed columns in the database are: {valid_columns}
    
    Check if the query uses any columns NOT in that list.
    If valid, reply "VALID".
    If invalid, reply "INVALID: <explanation>"
    """
    
    # Call Gemini or OpenAI here
    # response = client.chat.completions.create(...)
    # return response
    pass
```

### Key Best Practices for Production

1. **Read-Only Permissions:** Never give the LLM a database connection with `DROP`, `INSERT`, or `UPDATE` permissions. Create a specific Read-Only user in your database.
2. **LIMIT Clause:** Inject a `LIMIT 100` into your prompt instructions to prevent the LLM from crashing your server by selecting 10 million rows.
3. **Vector Stores (RAG):** If you have 500 tables, do not put them all in the prompt. Use a Vector Database to search for the relevant 5 tables based on the user's question, and only inject those 5 into the prompt.
