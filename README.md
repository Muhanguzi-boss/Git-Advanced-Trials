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

```