# Questions on Git and GitHub:
============================

## Core Concepts & Terminology:

1.  **What is Git, and why is it used?** (Define Git and explain its purpose as a version control system.)
2.  **What is the difference between Git and GitHub?** (Distinguish between the local version control system and the web-based hosting service.)
3.  **Explain the concept of a "repository" in Git.** (What does it contain, and what's its role?)
4.  **What is a "commit" in Git, and what information does it typically contain?** (Explain its purpose as a snapshot and its components.)
5.  **Describe the three states of files in Git: Working Directory, Staging Area (or Index), and Repository.** (Explain what each state represents.)
6.  **What is "branching" in Git, and why is it important?** (Explain the concept of parallel development.)
7.  **What is "HEAD" in Git?** (How does it relate to the current branch and commits?)
8.  **What is the purpose of the `.gitignore` file?** (How do you use it?)

**Basic Commands & Workflow:**

9.  **How do you initialize a new Git repository?** (Which command do you use?)
10. **What does the `git status` command do?** (What information does it provide?)
11. **Explain the `git add` command and its purpose.** (How do you stage changes?)
12. **How do you create a commit in Git?** (What is the basic command and how do you add a message?)
13. **What is `git clone`, and why do you use it?** (How do you get a copy of a remote repository?)
14. **Explain the difference between `git pull` and `git fetch`.** (When would you use each?)
15. **How do you push your local changes to a remote repository on GitHub?** (Which command?)
16. **How do you create a new branch and switch to it in one command?**
17. **What is a "merge conflict," and how do you typically resolve one?** (Describe the process.)
18. **How would you view the commit history of a repository?** (Which command provides this?)
19. **What is a "Pull Request" on GitHub, and what is its purpose in a team workflow?** (Explain its role in collaboration and code review.)
20. **How do you undo the last commit while keeping the changes in your working directory?** (Hint: `git reset` with a specific option.)

## 5 Hands-On Exercises

These exercises are designed to be performed on a local machine with Git installed, and optionally, a GitHub account for the remote aspects.

**Exercise 1: Basic Repository Setup and Committing**

* **Task:**
    1.  Create a new directory named `my_project`.
    2.  Initialize a Git repository inside `my_project`.
    3.  Create a file named `README.md` and add some content (e.g., "My first Git project.").
    4.  Add `README.md` to the staging area.
    5.  Commit the changes with a meaningful message like "Initial commit: Added README file."
    6.  Verify the commit history.
* **Commands to expect:** `mkdir my_project`, `cd my_project`, `git init`, `echo "My first Git project." > README.md`, `git add README.md`, `git commit -m "Initial commit: Added README file."`, `git log`

**Exercise 2: Branching and Merging**

* **Task:**
    1.  From your `main` (or `master`) branch in `my_project`, create a new branch named `feature/add-contact`.
    2.  Switch to the `feature/add-contact` branch.
    3.  Create a new file named `contact.txt` and add some contact information (e.g., "Email: test@example.com").
    4.  Add and commit `contact.txt` on this branch with a message like "Added contact information."
    5.  Switch back to the `main` branch.
    6.  Merge the `feature/add-contact` branch into `main`.
    7.  Verify that `contact.txt` is now present in the `main` branch.
* **Commands to expect:** `git branch feature/add-contact`, `git checkout feature/add-contact`, `echo "Email: test@example.com" > contact.txt`, `git add contact.txt`, `git commit -m "Added contact information."`, `git checkout main`, `git merge feature/add-contact`

**Exercise 3: Handling Merge Conflicts**

* **Task:**
    1.  On your `main` branch, modify `README.md` to say "My first Git project with new features." and commit it.
    2.  Create a new branch named `bugfix/typo`.
    3.  Switch to `bugfix/typo`.
    4.  Modify `README.md` to fix a "typo" (e.g., change "first" to "1st") and commit it with a message like "Fixed typo in README."
    5.  Switch back to `main`.
    6.  Attempt to merge `bugfix/typo` into `main`. This should result in a merge conflict.
    7.  Resolve the merge conflict, ensuring both changes are present and the `README.md` looks like: "My 1st Git project with new features."
    8.  Add the resolved file and commit the merge.
* **Commands to expect:** `git checkout main`, (edit `README.md`), `git commit -m "Updated README for new features."`, `git branch bugfix/typo`, `git checkout bugfix/typo`, (edit `README.md`), `git commit -m "Fixed typo in README."`, `git checkout main`, `git merge bugfix/typo`, (manual conflict resolution in `README.md`), `git add README.md`, `git commit`

**Exercise 4: Remote Repository Interaction (GitHub)**

* **Task:**
    1.  Go to GitHub and create a new public repository (without a README or .gitignore).
    2.  From your local `my_project` directory, add this new GitHub repository as a remote named `origin`.
    3.  Push your `main` branch to `origin`.
    4.  Make a small change to `contact.txt` locally (e.g., add a phone number), commit it.
    5.  Push this new commit to `origin`.
    * **Commands to expect:** (GitHub website actions), `git remote add origin <your_github_repo_url>`, `git push -u origin main`, (edit `contact.txt`), `git commit -m "Added phone number."`, `git push origin main`, `git clone <another_github_repo_url>`

**Exercise 5: Reverting Changes**

* **Task:**
    1.  In your `my_project` repository, make a new commit on the `main` branch (e.g., create a file `notes.txt` with some content and commit it).
    2.  Realize this commit was a mistake and you want to undo *only that specific commit* but keep the changes in your working directory.
    3.  Verify that the `notes.txt` file is still present in your working directory but the commit is no longer in the history.
* **Commands to expect:** `echo "Some notes." > notes.txt`, `git add notes.txt`, `git commit -m "Added notes file (mistake)."`, `git log --oneline`, `git reset HEAD~1` (or `git reset --soft HEAD~1`), `git log --oneline`, `ls` (to check for `notes.txt`).
