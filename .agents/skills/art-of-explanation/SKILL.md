---
name: Art of Explanation
description: Verify an explanation draft or plan against Step Four ("Organise the information") of Ros Atkins' The Art of Explanation. Checks the strand list, the two extra strands, strand ordering, element placement, within-strand ordering, leftovers handling, and the chapter's Quick Check. Use when the user asks to review, audit, or check their explanation against the book's Step Four process.
---

# Art of Explanation — Step Four Review

Audit a user's work against **Step Four** of *The Art of Explanation* (Ros Atkins),
and report exactly which steps are satisfied, which are missing, and what to do
next. You verify; you do not rewrite or reorganise the explanation unless the
user separately asks for that.

## Inputs

- The user's Step Four artifact: a text/markdown file containing their **strand
  list** and their **distilled elements placed into strands**. They may keep the
  distilled information and the strand document separate — read both.
- If no path is given, ask for it before reviewing.
- Read `references/source.md` for the exact chapter wording, and
  `references/checklist.md` for the checks (C1–C15) and how to apply them.

## Workflow

1. **Confirm scope.** State up front that this review covers *Step Four only*.
   It does not assess the distillation step that came before, nor wording,
   factual accuracy, or the final write-up. Do not mark those as failures.
2. **Read the artifact(s) completely** before judging anything.
3. **Run checks C1–C15** from `references/checklist.md`.
4. **Assign a status** to each check (legend below) and ground it in evidence:
   quote the text or cite `file:line`. Never assert compliance you cannot point to.
5. **Separate author-only questions** (Quick Check reflections the agent cannot
   answer) from the verifiable checks. List them as questions for the user.
6. **Report** in the format below, shortest useful form.

## Status legend

| Status | Meaning |
| --- | --- |
| ✅ Done | The step is clearly satisfied in the artifact. |
| ⚠️ Partial | Present but incomplete or ambiguous; say what is missing. |
| ❌ Missing | Not found in the artifact. |
| ➖ N/A | Legitimately not applicable at this stage (e.g. no leftovers). |
| ❓ Needs author | Only the author can answer (self-reflection / intent). |

## Report format

```
## Step Four review — <artifact path>

Scope: Step Four only (strand organisation). Not checked: distillation, wording, final delivery.

| ID | Check | Status | Evidence / gap |
| -- | ----- | ------ | -------------- |
| C1 | ... | ✅ | `<file:line>` ... |
| ... |

### Must fix before moving on
- ...

### Partial / ambiguous
- ...

### Questions only you can answer
- ...
```

Order the table by check ID. Keep evidence concrete. If the artifact is absent
or unreadable, say so and stop rather than guessing.

## Boundaries

- The chapter explicitly allows the strand list and the ordering to change later.
  Do **not** treat a provisional list or ordering as a failure; only check that a
  first pass exists.
- The **high-impact** and **not-sure** strands must be *deferred* from
  within-strand organising at this stage. Their elements being un-ordered is
  correct, not a gap.
- Do not judge the quality of the subject matter, the choice of strands, or the
  writing. Verify process and structure only.
- This skill reflects one chapter. If the source at `references/source.md` is
  updated, re-check the checklist against it before relying on the result.
