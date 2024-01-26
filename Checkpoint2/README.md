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

- [Git Status Untracked](git_status_untracked.txt)
- [Git Status Uncommitted](git_status_uncommitted.txt)
- [Git Status Committed](git_status_committed.txt)

## Part B: Inspecting Local Repo with `git status` and `git log`

**Q) How do these two commands differ - `git status` vs `git log`? Elaborate with an example.**

`git status` shows the status of your local working directory since the last commit, covering untracked, uncommitted, and committed changes. It also provides details about the current local branch in relation to the remote repository. On the other hand, `git log` is used to examine the commit history details. 

```bash
# git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   Checkpoint2/README.md

no changes added to commit (use "git add" and/or "git commit -a")
```
```bash
# git log -n 2 
commit 4fa44b8d45a36520d49018611dab48222afcc079
Author: Sanah <shedavalath-vayalil@myseneca.ca>
Date:   Thu Jan 25 23:34:55 2024 -0500

    add finishing touches to README.md

commit 58642e615d84692614f2fe823cd1992376c6c6bc
Author: Sanah <shedavalath-vayalil@myseneca.ca>
Date:   Thu Jan 25 23:33:40 2024 -0500

    added Part D - README.md
```
In short, `git status` deals with the current state of your working directory (in the above case, the untracked files) and `git log` focuses on the historical record of commits in the repository (in the above case, the latest 2 commits).

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
## Part D: Git Branching Strategy Review Question

**Q1) What are the differences between `develop` branch and `main` branch?**

The `main` branch houses our production-ready code, clearly marked with version number tags, and only hotfix branches stem from it for critical updates. In contrast, the `develop` branch contains the code that are in active development. Its code is in-progress and moves to the main branch through a release process after thorough testing. Branches for new features and bugfixes are created from it.

**Q2) What are the three supporting branches? Briefly describe the function of each of these supporting branches.**

- **Feature/Bugfix Branches** : 
Feature and bugfix branches, with naming convention `feat-issue-<id>` and `bug-issue-<id>`, respectively, are employed for adding new features or fixing bugs. These branches consistently branch off from and merge back into the `develop` branch after resolving any conflicts with its HEAD. Importantly, feature branches can be merged back into the `develop` branch at any stage of the deployment cycle, depending on the time it takes to complete the feature. On the other hand, bugfix branches typically have a short-lived existence, not lasting longer than one deployment cycle.

- **Hotfix Branches** : 
Hotfix branches, with naming convention `hotfix-issue-<id>`, are designed for immediate fixes to our live production code. They branch directly from `main` to swiftly address urgent issues without waiting for scheduled deployments. After resolving the problems, they merge back into both `main` and `develop` to ensure consistency.

- **Release Branches** : 
Release branches, with naming convention `release-<semver>`, are short-lived branches used to finalize preparations for a new release. After incorporating all scheduled features and bug fixes into the `develop` branch, a release branch is created. It handles final touches like versioning and last-minute fixes. When ready, it merges into `main` for the release and back into `develop` to maintain synchronization.

**Q3) What are the best practices in working with release branches?**

In adhering to best practices with `release` branches, it is essential to follow a naming convention such as `release-<semver>`. These branches should originate from the `develop` branch but merge both into `main` for the actual release and back into `develop` to maintain synchronization for future development. `release` branches should only be created when all planned features and bug fixes for a scheduled release are fully integrated and tested in the `develop` branch. These branches are primarily reserved for last-minute minor adjustments and should be tagged with an updated version number. When merging, using the `--no-ff` flag is recommended to create a merge commit that preserves historical information. Effective communication and team lead approvals at each stage are crucial for a smooth release.
