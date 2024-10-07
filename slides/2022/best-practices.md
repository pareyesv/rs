---
title: 'Best Practices'
subtitle: "A talk for Barcelona Supercomputing Center's Ph.D. students"
author: Andrés Aravena, PhD
company: Istanbul University
date: "October 7, 2022"
lang: en
bibliography: "../ref/recommended.bib"
nocite: |
  @Noble2009, @Wilson2014, @PeterJ.Feibelman165, @AlisonB.Miller171, @RyderCarroll3260, @DavidAllen1374, @Silva2007, @Annesley2010c, @Derish2010, @Annesley2010b, @Annesley2010, @Annesley2010f, @Annesley2010e, @Annesley2010a, @Annesley2010g, @Annesley2010h, @Annesley2010d, @Annesley2011, @Derish2011, @Annesley2011b, @Annesley2011a
...

## **Welcome to Ph.D. student's life** {.center .Large}

<!-- cSpell:ignore Supercomputing Feibelman Annesley Derish nocite INRIA -->

Congratulations, by the way

## Doing a Ph.D. is an amazing experience {.center}

But it can also be stressful

## We want to present some ideas on how to survive (and succeed) your Ph.D

::: large
Some of them are personal opinions

(informed by shared experiences)

Some of them are endorsed by research
:::

## I am Andres Aravena

+ Assistant Professor at Molecular Biology and Genomics Department, Istanbul University
+ Mathematical Engineer, U. of Chile
+ PhD Informatics, INRIA–U Rennes 1, France
+ PhD Mathematical Modeling, U. of Chile
+ Research in machine learning for metagenomics, and in gene expression analysis for systems biology

## Focus on Philosophy, not Tools

Tools will change in time. There will be new tools

You probably use tools that did not exist 10 years ago

And they often are a matter of _personal taste_

So we will focus on the _philosophy_ of the tools

(i.e. the part that will not change)

## **A Ph.D. goal is to produce and communicate new knowledge** {.center .black background="yellow" .Large}

(we call it "Doing Science")

## **The key word here is _communicate_** {.center}

What is the value of a result that is not made public?

<!-- # Communication while doing research {.center .good} -->

## We communicate with our _collaborators_

Most of research is done in teams

Good practices help teamwork, by:

+ Keep track of what was (or was not) done
+ Coordinate next steps
+ Avoid work duplication

## …but I work alone…

Even if we work alone, we are still communicating

+ with your **supervisor** or **advisor**
+ with the **referees** of your paper
+ with other **scientists** that read (and cite) you
  + including the next Ph.D. student in your lab
+ with the **general public**
+ with our **future self**

Each one of these interactions can improve following a good practice

## Communicate with **your supervisor**

Research results are not enough

You must convince your boss (and the jury) that you deserve to be called "Doctor"

Make your work easy to _understand_

Make clear what is your original contribution

## …with the **referees** of your paper

Give them all they need to _replicate_ and _validate_ your work

Referees are busy people and are not paid

Being _clear and transparent_ helps them to decide fast

You will get published faster, or at least get good feedback

## …with **other scientists** in your field…

…that will read your paper (and hopefully cite it)

The game does not end when you publish

50% of papers are read only by the referee

Make your work easy to _understand_ and _replicate_

::: source
I forgot where I read it
:::

## …with the **general public**

Eventually, your work will have an impact outside academia

(the end goal is to make a better world, no?)

We need to be aware of the _ethical_ implications

+ Licensing
+ Privacy
+ Truth

<!-- > This is reflected in the _Reproducibility Crisis_ -->

## …with your **future self**

Nothing is more frustrating that reading your old work

As they say: "The past is a foreign country"

Undocumented code/protocols are hard to understand…

and you can only blame yourself

# Why we need <br/> good practices {.center .good}

## We need good practices, because {.large .center .black background="yellow"}

[our mind fools us]{.Huge}

## We think we will never forget, but we do

> "I remember it now, therefore I will remember it forever"

When we see something or learn something, this fact is present in our short-term memory and we feel like we will always remember it

**Solution:** Use a journal (or lab notebook, or blog)

## We think our memories correspond to facts, but often they do not

> "Things were exactly as I remember"

Research shows that our memory is not at all a "recorder"

We misremember a lot

**Solution:** Use a journal

## We are bad at estimating projects' complexity

We think that we can finish a project in less time that it will really take

**Solution:** Write in your journal how much time you worked every day.  
Reflect on how did you use your time

## We think that everybody knows what we know, so they do not need explanations

> "I understand it, so everybody understands it"

This is the _curse of knowledge_

It is **the main reason** why our text is hard to read

**Solution:** This one I'm still trying to figure out. Practice.

## We think that everything we do is easy

> "I'm not really that good, and one day they will realize I don't know anything"

We learn a little every day, so it never feels hard

But we accumulated learning in a large period,  
and it is hard to see how much we have learned

This leads to _Impostor Syndrome_

**Solution:** Look at your journal and _reflect_ on how much have you learned in the last year

## We don't know that we don't know

> "Incompetent, and unaware of it"

This is the Dunning-Kruger effect

It is hard to improve if we don't know we are bad

Be open to criticism of your work

**You are not your work**

# Folder structure {.center .good}

## What is a "project"

<!-- cSpell:ignore cookiecutter tiago schuster -->

We can distinguish four categories

+ _Projects_ with well-defined goals and deadlines, e.g. a thesis
+ _Areas_ that are permanently active, like "health" or "family"
+ _Resources_ that can be useful for several projects, like code libraries, or general interest papers
+ _Archives_, anything that is no longer active. Can be copied to external media and stored out of the computer

:::source  
Tiago Forte
_Building a Second Brain_,
Simon and Schuster, 2022  
:::

## Prepare your files for the next user

> Someone unfamiliar with your project should be able to look at your computer files and understand in detail what you did and why

&nbsp;

> Everything you do, you will probably have to do over again

::: source  
The ideas of this section are mostly based on  
William Stafford Noble. _“A Quick Guide to Organizing Computational Biology Projects.”_ PLoS Computational Biology 5, no. 7 (2009): 1–5. <https://doi.org/10.1371/journal.pcbi.1000424>.  
:::

## This “someone” could be

+ someone who wants to try to reproduce your work,
+ a collaborator who wants to understand your experiments,
+ a future student in your lab extending your work
  + after you have moved on to a new job,
+ your research advisor evaluating your research skills.

Most commonly, however, that “someone” is you.

::: source  
William Stafford Noble. _“A Quick Guide to Organizing Computational Biology Projects.”_ PLoS Computational Biology 5, no. 7 (2009): 1–5. <https://doi.org/10.1371/journal.pcbi.1000424>.  
:::

## Folder structure for data projects {.center-h}

![](images/folder-struct.svg)

:::small

+ `docs` is where you write your paper/talk/thesis
+ `refs` is to store reference documents, like citations
+ `data` is anything that you get from outside the computer
+ `results` is what your code produces
+ `scripts` and `src` is where you write your code
+ `bin` is for the compiled code
:::

## Use a script to build the structure {.fl-r}

![](https://4.bp.blogspot.com/-cfoxP3_DFiE/Tqy52Df5YJI/AAAAAAAA_OI/a7_hRs8QmSE/s1600/3.jpg)

Cookiecutter is a python tool to create new projects

You can find search for recipes in GitHub with a query like [`topic:cookiecutter` `topic:r`](https://github.com/search?q=topic%3Acookiecutter+topic%3Ar)

## Where to store it

+ In the server only

+ Cloud drive like Dropbox, Google Drive
  + Good to share large data and non-text files
  + Bad if two people changes the same file
  + Works better with permanent internet access

+ Version control system like GitHub, GitLab, Bitbucket
  + Good for text and code, bad for big files
  + Keeps history
  + works well without internet access

## Never use Git in a shared folder  {.center .black background="yellow" .Large}

It can easily become corrupt

## Sharing

+ Hybrid, using symbolic links
  + create a local Git repo, for `docs` and `scripts`
  + Put `data` and `results` in the cloud
  + `data` and `results` in the repo are symbolic links
  + `data/` and `results/` are ignored (`.gitignore`)

+ Or use an online editor
  + Google Docs
  + HackMD.io
  + Overleaf

## Raw Data is Sacred

Producing data is expensive and time consuming

You don't want to lose it.
**Mark it _read only_ immediately**  
(and make backups)

Never modify raw data. Use a script to make a clean version

Use folders `raw` and `clean` inside `data/YYYY-MM-DD`  
Code for that in `scripts`

## Be coherent when choosing filenames

Decide when to use `.`, `-`, and `_`. Avoid spaces in filenames

Either `John-Smith.txt` or `John_Smith.txt`

Usually `.` separates filetypes, like `.csv` or `.yml`

## Define a standard with your collaborators

Check periodically that you are following your standard  
(maybe with a script)

## Examples

### Bad Example

```
1-Introduction.docx
2_Methods.docx
3.Results.docx
4 discussion.docx
10-conclusions.docx
results-01-03-09.txt
```

### Good Example

```
01-Introduction.docx
02-Methods.docx
03-Results.docx
04-Discussion.docx
10-conclusions.docx
2009-01-03-results.txt
```

## Another Good Example

```
01_Introduction.docx
02_Methods.docx
03_Results.docx
04_Discussion.docx
10_conclusions.docx
20090103results.txt
```

Both are good, but use only one

## Write dates as YYYY-MM-DD

+ When was 8/3/1965? August or March?

+ Is today 7/10/2022 or 10/7/2022?

It is better to write YYYY-MM-DD. This is an ISO standard

There is no ambiguity of meaning

Sorting alphabetically, numerically, and chronologically give the same result

## Keep a logbook or Lab Notebook

Experimental scientists use a notebook to record every experiment

+ What is the purpose of the experiment
+ What is the expected output
+ What was the result, positive or negative
+ What were the lessons learned

Lab Notebooks are legal documents in case you want to patent something

You should at least carry a lab notebook in digital

## Each folder needs a README file

Good filenames help a lot to understand the project

But they are usually not enough

A `README` file in each folder can explain the purpose of each file

It takes time to write them, but it saves time in the long run

How to write the README?

# Structured Documents {.good .center}

## Structured documents

You probably know that using a good _data structure_ can dramatically improve an algorithm

And you use _structured programs_

The same applies to structuring our documents

Maybe you have used LaTeX, or Markdown

Maybe you know HTML

## Separation of concerns

<!-- cSpell:ignore Lamport Entscheidungsproblem beamer -->

The key idea is to describe _what things are_, not _how they look_

Describe the role of text, not the "looks"

Separate style from structure

::: source
This part is based on the ideas discussed in "LaTeX: A Document Preparation System" by Leslie Lamport (1986).
:::

## It is like a house {.large}

Structure makes the house solid and comfortable

If you only do decoration, the house looks nice but it is not solid

Structure of the walls come first

Painting the walls in a nice color is secondary

## Structural elements

+ Sections, subsections, paragraphs
+ Figures and Tables
+ Lists
+ References
+ Equations
+ Metadata
  + Title
  + Authors
  + Affiliations
  + Dates: submission, acceptance
  + Media/format

## Example: writing in LaTeX

A LaTeX document looks like this

```latex
\documentclass[a4paper]{article}
\title{On computable numbers, with an application to the Entscheidungsproblem}
\author{Alan M. Turing}
\date{28 May, 1936}
\begin{document}
\section{Introduction}
The ``computable'' numbers may be described as the real numbers whose
expression as a decimal are calculable by finite means.
\end{document}
```

LaTeX files are text files. They will never be obsolete.

Changing the `documentclass` will change the document _look_

## LaTeX {.fl-r}

![](https://upload.wikimedia.org/wikipedia/commons/5/50/Leslie_Lamport.jpg)

In the 80's Leslie Lamport created LaTeX as an extension of TeX

Leslie Lamport won the Turing Award in 2013

## TeX {.fl-r}

![](https://1.bp.blogspot.com/-W25qRh3dArI/Tw1nW9AlaWI/AAAAAAAAGsg/UaOEHyv3jdA/s1600/Knuth_b.jpg){height="500px"}

Invented in tht 70's by Donald Knuth, who is probably the most important computer scientist of the last 70 years

Donald Knuth won the Turing Award in 1974

## Advantages of LaTeX

+ It is free

+ Write first, compile later

+ Do not waste time playing with fonts

+ Good journals accept LaTeX submissions  
(they also accept Microsoft Word format)

## LaTeX files are _text files_

+ Independent of any provider

+ Use your favorite text editor (VScode?)

+ Version control friendly (GitHub?)

+ Can probably be read 20 years from now

We cannot say the same about Microsoft Word

## The real advantage: it looks real {.center .full-v}

![](images/latex.png)

## According to the author of LaTeX

> "[LaTeX] It's easy to use---if you're one of the 2% of the population who thinks logically and can read an instruction
manual. The other 98 % of the population would find
it very hard or impossible to use.

So maybe the main advantage is that it _forces_ you to think logically and organize your ideas

::: source
"How (La)TeX changed the face of Mathematics". An E-interview with Leslie Lamport. <http://lamport.azurewebsites.net/pubs/lamport-latex-interview.pdf>
:::

## 3 mistakes that people should stop making

According to Leslie Lamport

1. Worrying too much about formatting and not enough about content.

2. Worrying too much about formatting and not enough about content.

3. Worrying too much about formatting and not enough about content.

::: source
"How (La)TeX changed the face of Mathematics". An E-interview with Leslie Lamport. <http://lamport.azurewebsites.net/pubs/lamport-latex-interview.pdf>
:::

## Bonus: Slides for presentations

After writing your paper, you will probably present it  
(or maybe before finishing it)

Using structured document makes it easy to _recycle_ your material to presentation slides

In LaTeX you can do that using the `beamer` document class

## Writing Math Expressions

LaTeX is favored by people who writes mathematical formulas

```latex
$$(a+b)^n=\sum_{k=0}^n \frac{n!}{k!(n-k)!} a^k b^{n-k}$$
```

$$(a+b)^n=\sum_{k=0}^n \frac{n!}{k!(n-k)!} a^k b^{n-k}$$

You can use this syntax in Microsoft Word's Equation Editor, and in web pages (using KaTeX or MathJax)

Learning how to write math is a good investment

## Bibliographic References

There are _hundreds_ of citation styles

Life is too short to sort references _manually_

LaTeX also provides a convenient way to handle references

References are stored in a separate text file, in BiBTeX format

Many tools can create BiBTeX files for you

+ Zotero
+ Mendeley

## Collaborating with other people

Since LaTeX files are _text files_, it can be put under _version control_

In practice this means `git`, and maybe _GitHub_ or _GitLab_  
(or something in your server)

Several people can edit the same file at the same time  
Git will do the right thing when merging

It does not need permanent Internet access  
(i.e. you can write while traveling)

## Real time collaboration

> Overleaf is an online collaborative writing and publishing tool
>
> Overleaf provides … an easy-to-use LaTeX editor with real-time collaboration and the compiled output produced automatically … as you type

You do not need to install anything in your computer

[https://www.overleaf.com/](https://www.overleaf.com/){target="_blank"}

## LaTeX disadvantages

+ LaTeX is hard to learn
  + This discourages many people
  + Your collaborators may not use it
  + You need to have the Reference Manual at hand
+ It is oriented to producing printed material
  + It produces PDF files or equivalents
  + Not suitable for Web or eBook
+ Writing tables is hard

## Alternative: Markdown

It is a light markup system that can be easily converted into nice presentations

```md
---
title: On computable numbers, with an application to the Entscheidungsproblem
author: Alan M. Turing
date: 28 May, 1936
...

# Introduction
The "computable" numbers may be described as the real numbers whose
expression as a decimal are calculable by finite means.
```

You probably have seen it in GitHub or Jupyter Notebooks

Same philosophy as LaTeX, but simpler

## Markdown's author says

<!-- cSpell:ignore Gruber swiss Powerpoint -->

> "The overriding design goal for Markdown’s formatting syntax is to make it as readable as possible.
>
> "The idea is that a Markdown-formatted document should be publishable as-is, as plain text, without looking like it’s been marked up with tags or formatting instructions."

::: source
John Gruber
<https://daringfireball.net/projects/markdown/>
:::

## Using Markdown in practice

There are dozens (maybe hundreds) of Markdown editors and compilers

They offer many extensions

They are not always compatible

There is not yet an official standard

**Recommendation**: pandoc

## Pandoc

> If you need to convert files from one markup format into another, pandoc is your swiss-army knife

Pandoc can convert between _many_ formats, including

+ Markdown
+ Microsoft Word/Powerpoint
+ LaTeX
+ Jupyter notebook

## Practical pandoc

+ You can write your main text in Markdown, and convert it into LaTeX

+ Pandoc understands LaTeX math expression, and can convert them to HTML or Microsoft Word

+ You can mix Markdown and LaTeX, and pandoc will keep the LaTeX part

## Pandoc advantages

+ Text files

+ It is easy to write tables in Markdown

+ It is easy to write lists

+ Can be used for slides
  + Several web platforms (like this document)
  + Microsoft Powerpoint

+ Handles BiBTeX references

::: notes
See examples in the source code
:::

## Collaborating using Markdown

Markdown files are text files

Thus, _git_ is the way to go

But if you want _real time_ collaboration, try [https://hackmd.io/](https://hackmd.io/){target="_blank"}

## RMarkdown and Quarto

+ Developed for R language, but supports Python and other languages
+ Syntax is Markdown + code
  + The code for each table and figure is included in the document
  + This is a big step towards _replicability_
+ R replaces each _code chunk_ with its result, and gives a plain Markdown file
+ It uses _pandoc_ to make Word/PDF/HTML
+ Can be shared using _git_

## RMarkdown v/s Jupyter Notebooks

Both are similar in spirit

+ Jupyter is like Excel. It is good to explore ideas
  + It is code with a lot of comments
+ RMarkdown is like Word. It is good to write a paper
  + It is text with just enough code

## Alternative: Microsoft Word

Depending on your _boundary conditions_, you may choose to use a WYSIWYG word processor

You can still follow the same philosophy:

+ Separate style from structure
+ Focus on content

## Style is not Structure {.large}

In word processors like Word®,  
_What You See Is What You Get_

This is sometimes called **WYSIWYG**

It is easy to change fonts, sizes, colors and other visual attributes, without paying attention to _structure_

## Structured Word documents {.no-gap .center-h .full-v .shadow}

![](images/word-styles.png)

## Now the document has structure {.no-gap .center-h .full-v .shadow}

![](images/word-outline.png)

## Collaborating {.center-h}

Sharing Word documents by email is a **VERY BAD IDEA**  
It leads to _chaos and confusion_

![](images/sharing-word.svg)

## Use an Online service

You can share your document via Dropbox or Google Drive

You can edit online using Microsoft Office 365 or Google Docs

Several people can work in the same document at the same time

**Advantage:** better spelling and grammar correction

But they require a permanent internet connection

## How I work with my students

When I collaborate with non-markdown people, we use Google Docs

+ We avoid using **bold** and _italics_
  + Exception: scientific names of species (e.g. _Homo sapiens_)
+ Instead we use _Styles_ to define the structure
+ I follow _pandoc_ rules for citations
+ Once finished, I export a Word file, and I convert it to Markdown using _pandoc_
+ We share the _code_ to produce every figure and table

# Collaborating {.center .good}

## Choosing roles and protocols

Define who are the authors early

Recommended reading:

“What Makes an Author.” Nature Methods 18, no. 9 (September 3, 2022): 983–983. <https://doi.org/10.1038/s41592-021-01271-8>.

Gewin, Virginia. “Steer Clear of Conflict.” Nature 594, no. 7863 (2022): 462–63.

## More recommendations

<!-- cSpell:ignore Weinberger Stefano Allesina Lortie Frassl Gewin Pomodoro Marieke -->

::: small
Weinberger, Cody J., James A. Evans, and Stefano Allesina. “Ten Simple (Empirical) Rules for Writing Science.” PLoS Computational Biology 11, no. 4 (2015): 11–13.

Lortie, Christopher J. “Ten Simple Rules for Writing Statistical Book Reviews.” PLoS Computational Biology 15, no. 1 (2019): 1–5.

Frassl, Marieke A., David P. Hamilton, et al. “Ten Simple Rules for Collaboratively Writing a Multi-Authored Paper.” PLoS Computational Biology 14, no. 11 (2018): 6–13.

Erren, T, P Cullen, M Erren, and P Bourne. “Ten Simple Rules for Doing Your Best Research, According to Hamming.” PLoS Computational Biology 3, no. 10 (January 1, 2007): e213.
:::

# Final comments {.center .good}

## Take care of yourself

+ Drink a lot of water
  + Especially when you drink alcohol
+ Get enough sleep
  + Don't fry your brain, you only have one
+ Try to make a routine. Minimize trivial decisions
  + Save your energy for important things
+ Go for a walk every day

## Become a writer

+ Write every day. No exceptions.
  + Start with 150 or 200 daily words
  + Ideal is 750 daily words

+ Once you see yourself as "someone who writes every day", it will be easy to write papers, projects, thesis, etc.

+ Get addicted to write, as you are addicted to social media

+ Try the _Pomodoro technique_

<!-- - define and agree on communication methods
    - Slack, -->

<!-- ## Practice
- avoid WYSIWYG (until the last minute)
- markdown/latex/pandoc/(Google docs+rules)

- When we have coauthors
    - Define who are the authors early
    - define and agree on communication methods
        - slack
    - Do not send attached word documents!
        - `doc-v1-real-final2.docx`
        - leads to a cacophony of version
    - Tools to collaborate
        - Shared folders
        - Github 
        - Docker
    - Online conversation -->

## References

[(please scroll to see more entries)]{.small}

::: {#refs .scroll}
:::

<!-- https://pandoc.org/try/
https://stackedit.io/
https://www.tablesgenerator.com/markdown_tables -->

<style>
.reveal blockquote {
    width: 90%;
    border: solid thin darkslategrey;
    box-shadow: 10px 10px 5px #aaaaaa;
    padding: 0 15px;
}
</style>
