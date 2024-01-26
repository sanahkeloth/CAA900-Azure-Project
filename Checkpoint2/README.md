### Checkpoint2 Submission

- **COURSE INFORMATION: CAA900 - Capstone Project**
- **STUDENT’S NAME: Sanah Hussain Edavalath Vayalil Keloth**
- **STUDENT'S NUMBER: 160683231**
- **GITHUB USER ID: 160683231-myseneca**
- **TEACHER’S NAME: Atoosa Nasiri**

### Table of Contents

1. [Part A: Adding Files - Local Repo Workflow](#part-a-adding-files---local-repo-workflow)
2. [Part B: Inspecting Local Repo with `git status` and `git log`](#part-b-inspecting-local-repo-with-git-status-and-git-log)
3. [Part C: Creating & Merging Branches](#part-c-creating--merging-branches)
4. [Part D: Git Branching Strategy Review Question](#part-d-git-branching-strategy-review-question)

## Part A: Adding Files - Local Repo Workflow

a. [Git Status Untracked](git_status_untracked.txt)
b. [Git Status Uncommitted](git_status_uncommitted.txt)
c. [Git Status Committed](git_status_committed.txt)

## Part B: Inspecting Local Repo with `git status` and `git log`

**Q) How do these two commands differ - `git status` vs `git log`? Elaborate with an example.**

`git status` shows the status of your local working directory since the last commit, covering untracked, uncommitted, and committed changes. It also provides details about the current local branch in relation to the remote repository. On the other hand, `git log` is used to examine the commit history details. In short, `git status` deals with the current state of your working directory and `git log` focuses on the historical record of commits in the repository.

## Part C: Creating & Merging Branches

**Output of `git log -n 5`**
```bash
commit 1be9174b1ba7b72e39def3d56dd6088988f8d3d5 (HEAD -> main, origin/feat-emojis, feat-emojis)
Author: Sanah <shedavalath-vayalil@myseneca.ca>
Date:   Thu Jan 25 20:07:01 2024 -0500

    adds emojis to feat-emojis branch

commit 398ee4774867a88ae60b28f5c89d52e102c2c6ae (origin/main, origin/HEAD)
Author: Sanah <shedavalath-vayalil@myseneca.ca>
Date:   Thu Jan 25 20:03:02 2024 -0500

    adds footnotes folder

commit 95a6c6a229bb29195a89736f926d1179f9a5aa1d
Author: Sanah <shedavalath-vayalil@myseneca.ca>
Date:   Thu Jan 25 19:49:35 2024 -0500

    adds git status upto date

commit bd8759ce6de81e5fa27f3bd3b9d844b8d4800367
Author: Sanah <shedavalath-vayalil@myseneca.ca>
Date:   Thu Jan 25 19:47:57 2024 -0500

    adds Checkpoint2/README.md

commit 4e6eb805eefc133902f921872343685ef0428aa5
Author: Sanah <shedavalath-vayalil@myseneca.ca>
Date:   Thu Jan 25 19:28:17 2024 -0500

    Created a new folder Checkpoint1 in the root dir and copied files to it
```
