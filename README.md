# Git Advanced Exercises

## Part 1

### Missing File Fix
```bash

PS C:\Users\PC\Documents\Git-Advanced-Trials> git add test4.md; git commit -m "chore: Create the fourth file"  
[main 3f4a608] chore: Create the fourth file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test4.md
```

### Editing Commit History
```bash

PS C:\Users\PC\Documents\Git-Advanced-Trials> git log --oneline
3f4a608 (HEAD -> main) chore: Create the fourth file
1b35a5b chore: Create third and fourth files
3365e58 chore: Create another file
PS C:\Users\PC\Documents\Git-Advanced-Trials> git rebase -i HEAD~3
Successfully rebased and updated refs/heads/main.
PS C:\Users\PC\Documents\Git-Advanced-Trials> git log --oneline
3f4a608 (HEAD -> main) chore: Create the fourth file
1b35a5b chore: Create third and fourth files
3365e58 chore: Create another file
1509564 chore: Create initial file
PS C:\Users\PC\Documents\Git-Advanced-Trials> git rebase -i HEAD~3
[detached HEAD cfd7e1e] chore: Create second file
 Date: Tue Mar 4 21:22:42 2025 +0200
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.md
Successfully rebased and updated refs/heads/main.
PS C:\Users\PC\Documents\Git-Advanced-Trials> git log --oneline
9a94b7e (HEAD -> main) chore: Create the fourth file
3160bd8 chore: Create third and fourth files
cfd7e1e chore: Create second file
1509564 chore: Create initial file
PS C:\Users\PC\Documents\Git-Advanced-Trials> 
```

### Keeping History Tidy - Squashing Commits:
```bash 

PS C:\Users\PC\Documents\Git-Advanced-Trials> git rebase -i --root
[detached HEAD a44a62b] chore: Create initial file and second file
 Date: Tue Mar 4 21:22:03 2025 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test1.md
 create mode 100644 test2.md
Successfully rebased and updated refs/heads/main.
PS C:\Users\PC\Documents\Git-Advanced-Trials> git log --oneline
9e7d096 (HEAD -> main) chore: Create the fourth file
4f98214 chore: Create third and fourth files
a44a62b chore: Create initial file and second file
PS C:\Users\PC\Documents\Git-Advanced-Trials>

```

### Splitting a commit
```bash
PS C:\Users\PC\Documents\Git-Advanced-Trials> git log --oneline
314e756 (HEAD -> main) chore: Create fourth file
726e10a chore: Create third file
a44a62b chore: Create initial file and second file
PS C:\Users\PC\Documents\Git-Advanced-Trials> 

```

### Advanced Squashing
```bash
314e756 (HEAD -> main) chore: Create fourth file
726e10a chore: Create third file
a44a62b chore: Create initial file and second file
PS C:\Users\PC\Documents\Git-Advanced-Trials> git rebase -i HEAD~2
[detached HEAD 19d6bcb] chore: Create third and fourth files
 Date: Tue Mar 4 21:50:25 2025 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md
 create mode 100644 test4.md
Successfully rebased and updated refs/heads/main.
PS C:\Users\PC\Documents\Git-Advanced-Trials> git log --oneline
19d6bcb (HEAD -> main) chore: Create third and fourth files
a44a62b chore: Create initial file and second file
PS C:\Users\PC\Documents\Git-Advanced-Trials> 

```


### Dropping a commit
```bash
PS C:\Users\PC\Documents\Git-Advanced-Trials> git log --oneline
408ce30 (HEAD -> main) Unwanted commit
19d6bcb chore: Create third and fourth files
a44a62b chore: Create initial file and second file
PS C:\Users\PC\Documents\Git-Advanced-Trials> git rebase -i HEAD~2
Successfully rebased and updated refs/heads/main.
PS C:\Users\PC\Documents\Git-Advanced-Trials> git log --oneline
19d6bcb (HEAD -> main) chore: Create third and fourth files
a44a62b chore: Create initial file and second file
PS C:\Users\PC\Documents\Git-Advanced-Trials> 

```

### Reordering commit messages
```bash

PS C:\Users\PC\Documents\Git-Advanced-Trials> git log --oneline
19d6bcb (HEAD -> main) chore: Create third and fourth files
a44a62b chore: Create initial file and second file
PS C:\Users\PC\Documents\Git-Advanced-Trials> git rebase -i HEAD~2
fatal: invalid upstream 'HEAD~2'
PS C:\Users\PC\Documents\Git-Advanced-Trials> git rebase -i --root
Successfully rebased and updated refs/heads/main.
PS C:\Users\PC\Documents\Git-Advanced-Trials> git log --oneline
9589c96 (HEAD -> main) chore: Create initial file and second file
3f4d676 chore: Create third and fourth files
PS C:\Users\PC\Documents\Git-Advanced-Trials> 
```

### Cherry Picking Commits

```bash

PS C:\Users\PC\Documents\Git-Advanced-Trials> git add test5.md
PS C:\Users\PC\Documents\Git-Advanced-Trials> git commit -m "Implemented test5 file"
[ft/branch 5a67f73] Implemented test5 file
 1 file changed, 1 insertion(+)
PS C:\Users\PC\Documents\Git-Advanced-Trials> git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
PS C:\Users\PC\Documents\Git-Advanced-Trials> git log ft/branch --oneline
1ee4b46 (HEAD -> main, origin/main) first part of advanced git
9589c96 chore: Create initial file and second file
3f4d676 chore: Create third and fourth files
PS C:\Users\PC\Documents\Git-Advanced-Trials> git cherry-pick 5a67f73
[main bac799e] Implemented test5 file
 Date: Wed Mar 5 16:24:06 2025 +0200
 1 file changed, 1 insertion(+)
 create mode 100644 test5.md
PS C:\Users\PC\Documents\Git-Advanced-Trials> git log --oneline
bac799e (HEAD -> main) Implemented test5 file
1ee4b46 (origin/main) first part of advanced git
9589c96 chore: Create initial file and second file
3f4d676 chore: Create third and fourth files
PS C:\Users\PC\Documents\Git-Advanced-Trials> cat test5.md
This is test5.md file
PS C:\Users\PC\Documents\Git-Advanced-Trials>

```
### Visualizing commit history
```bash

PS C:\Users\PC\Documents\Git-Advanced-Trials> git log --graph
* commit bac799e54243ff8d6636deab433ca3a7a95c1989 (HEAD -> main)
| Author: Muhanguzi boss <bossmuhanguzi@gmail.com>
| Date:   Wed Mar 5 16:24:06 2025 +0200
|
|     Implemented test5 file
| 
* commit 1ee4b469bb34472282d7315b07c4f3235c4dc362 (origin/main)
| Author: Muhanguzi boss <bossmuhanguzi@gmail.com>
| Date:   Tue Mar 4 22:28:19 2025 +0200
|
|     first part of advanced git
|
* commit 9589c9614976b1c5b3888b91b873403f928c29d8
| Author: Muhanguzi boss <bossmuhanguzi@gmail.com>
```

### Understanding reflogs
```bash
PS C:\Users\PC\Documents\Git-Advanced-Trials> git reflog
bac799e (HEAD -> main) HEAD@{0}: cherry-pick: Implemented test5 file
1ee4b46 (origin/main) HEAD@{1}: checkout: moving from ft/branch to main
5a67f73 (ft/branch) HEAD@{2}: commit: Implemented test5 file
1ee4b46 (origin/main) HEAD@{3}: checkout: moving from main to ft/branch
1ee4b46 (origin/main) HEAD@{4}: commit: first part of advanced git
9589c96 HEAD@{5}: rebase (finish): returning to refs/heads/main
9589c96 HEAD@{6}: rebase (pick): chore: Create initial file and second file
3f4d676 HEAD@{7}: rebase (pick): chore: Create third and fourth files
25cf306 HEAD@{8}: rebase (start): checkout 25cf306fe6df345df5c0731fb6d6ce762d6f8ca4
19d6bcb HEAD@{9}: rebase (finish): returning to refs/heads/main
19d6bcb HEAD@{10}: rebase (start): checkout HEAD~2
408ce30 HEAD@{11}: commit: Unwanted commit
19d6bcb HEAD@{12}: rebase (finish): returning to refs/heads/main
19d6bcb HEAD@{13}: rebase (squash): chore: Create third and fourth files
```


## Part 2

### Feature Branch Creation:
```bash
PS C:\Users\PC\Documents\Git-Advanced-Trials> git checkout -b ft/new-feature
Switched to a new branch 'ft/new-feature'
PS C:\Users\PC\Documents\Git-Advanced-Trials> 
```

### Working on a feature branch
```bash
PS C:\Users\PC\Documents\Git-Advanced-Trials> New-Item feature.txt

    Directory: C:\Users\PC\Documents\Git-Advanced-Trials


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----          3/5/2025   5:07 PM              0 feature.txt


PS C:\Users\PC\Documents\Git-Advanced-Trials> git add feature.txt
PS C:\Users\PC\Documents\Git-Advanced-Trials> git commit -m "Implemented core functionality for new feature"
[ft/new-feature f35476c] Implemented core functionality for new feature
 1 file changed, 1 insertion(+)
 create mode 100644 feature.txt
PS C:\Users\PC\Documents\Git-Advanced-Trials> git log --oneline
f35476c (HEAD -> ft/new-feature) Implemented core functionality for new feature
d57d74d (origin/main, main) Last commits on part one
bac799e Implemented test5 file
1ee4b46 first part of advanced git
9589c96 chore: Create initial file and second file
3f4d676 chore: Create third and fourth files
PS C:\Users\PC\Documents\Git-Advanced-Trials> 
```
### Switching Back and Making More Changes:
```bash
PS C:\Users\PC\Documents\Git-Advanced-Trials> git checkout main
Your branch is up to date with 'origin/main'.
PS C:\Users\PC\Documents\Git-Advanced-Trials> New-Item readme.txt


    Directory: C:\Users\PC\Documents\Git-Advanced-Trials


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----          3/5/2025   5:15 PM              0 readme.txt


PS C:\Users\PC\Documents\Git-Advanced-Trials> git add readme.txt
PS C:\Users\PC\Documents\Git-Advanced-Trials> git commit -m "Updated project readme"
[main 367a108] Updated project readme
 1 file changed, 1 insertion(+)
 create mode 100644 readme.txt
PS C:\Users\PC\Documents\Git-Advanced-Trials> 
```

### Renaming Branches
```bash
PS C:\Users\PC\Documents\Git-Advanced-Trials> git branch -m ft/new-branch-from-commit ft/improved-branch-name  
PS C:\Users\PC\Documents\Git-Advanced-Trials> git branch
  ft/branch
  ft/improved-branch-name
* main
```
### Checking Out Detached HEAD:
```bash
PS C:\Users\PC\Documents\Git-Advanced-Trials> git checkout 0513171
M       README.md
M       readme.txt
Note: switching to '0513171'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 0513171 fifth and sixth sessions of part 2
PS C:\Users\PC\Documents\Git-Advanced-Trials> 
```
