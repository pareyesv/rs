% Git Merge & Its Pitfalls
% Navigating the Danger Zones
% [Your Name/Date]

# The Roadmap

We will categorize merge problems into three stages:

1.  **Before**: Preparation failures (The "Dirty" Directory).
2.  **During**: The act of merging (Conflicts, Wrong Direction).
3.  **After**: History and Logic (Fast-forwards, Logic bugs, Reverts).

# 1. The "Dirty" Working Directory

## The Scenario

You are fixing a bug in `styles.css`. You haven't committed yet.
You try to run `git merge main` to get updates.

## The Error

```text
error: Your local changes to the following files
would be overwritten by merge:
    styles.css
Please commit your changes or stash them before you merge.
```

## The Solution

Git protects your unsaved work. You must clear the table before serving new food.

1. **Stash (Hide):** `git stash` -> Merge -> `git stash pop`
2. **Commit (Save):** `git commit -m "WIP"` -> Merge

---

## 2. The Textual Conflict

## The Scenario

Alice changes the Title to "Alpha".
Bob changes the Title to "Beta".
Git cannot decide which is correct.

## The Scary Output

```bash
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit.
```

## The Fix

Open the file. Look for the markers:

```text
<<<<<<< HEAD
Title: Beta
=======
Title: Alpha
>>>>>>> main
```

**Action:** Delete the markers, choose the text you want, save, `git add`, and `git commit`.

---

# 3. The "Stuck" State (Panic Mode)

## The Scenario

You hit a conflict. You panic. You try to switch branches to check something else.

```bash
$ git checkout main
error: you need to resolve your current index first
```

You are trapped in `(MERGING)` limbo.

## The Eject Button

If you want to give up and go back to exactly how things were before you typed merge:

```bash
$ git merge --abort
```

---

# 4. Fast-Forward vs. Merge Commits

## The Scenario

You merge a feature branch. Git simply moves the pointer forward.

* **Result:** Your history is a straight line. You can't tell where the feature started or ended.

## The Fix: `--no-ff`

Force Git to create a "Merge Bubble" (a commit object).

```bash
$ git merge --no-ff feature-login
```

**Why?** It preserves the historical context that a specific feature existed and was merged at a specific time.


# 5. Logical Conflicts (The Silent Killer)

## The Scenario

* **Branch A:** Renames `calculateTax()` to `getTax()`.
* **Branch B:** Writes new code calling `calculateTax()`.

## The Merge

Git merges successfully! (Different lines/files).

## The Crash

The app fails at runtime:

```text
Uncaught TypeError: calculateTax is not a function.
```

## The Lesson

**Git merges text, not logic.**
A clean merge does not mean working code.
*Always run automated tests after merging.*

# 6. The Wrong Direction

## The Scenario

You want to bring `feature` into `main`.
**Mistake:** You are sitting on `feature` and run `git merge main`.

## The Result

* `feature` gets polluted with `main` code.
* `main` stays outdated.

## The Analogy

"Get on the bus you want to bring passengers onto."

## The Fix

Check your branch *before* merging.

```bash
$ git checkout main
$ git merge feature-branch
```

---

# 7. Binary File Conflicts

## The Scenario

Two people edited `hero.png` (an image).

## The Error

```text
warning: Cannot merge binary files: hero.png
CONFLICT (content): Merge conflict in hero.png
```

## The Fix

You cannot edit "pixels" inside a text editor. You must pick a winner.

```bash
# Keep MY version
$ git checkout --ours hero.png

# Keep THEIR version
$ git checkout --theirs hero.png

$ git add hero.png
$ git commit
```

# 8. Reverting a Merge (Advanced)

## The Scenario

You merged `dev` into `main`. It broke production. You run `git revert <merge-hash>`.

## The Error

```text
error: commit is a merge but no -m option was given.
```

## The Explanation

A merge has **two parents**. Git doesn't know which side to revert to.

## The Fix

Specify the "Mainline" parent (usually 1).

```bash
$ git revert -m 1 <merge-commit-hash>
```

## Summary: The Merge Checklist

1. **Status:** Is my working directory clean? (`git status`)
2. **Location:** Am I on the correct target branch? (`git checkout target`)
3. **Command:** Do I need `--no-ff` to preserve history?
4. **Conflict:**
    * Text? Edit markers.
    * Binary? Choose `--ours` or `--theirs`.
    * Panic? `git merge --abort`.
5. **Verify:** Run tests (Git checks text, you check logic).

---

## Exercise

1. Create a repo with a file `story.txt`.
2. Create branch `A`, change line 1, commit.
3. Go back to main.
4. Create branch `B`, change line 1 (differently), commit.
5. Merge `A` into `main`.
6. **Task:** Merge `B` into `main` and resolve the conflict.

