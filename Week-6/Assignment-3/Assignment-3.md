# Assignment 3 - Branching and Merging

## Branching

**1. Create a new branch “GitNewBranch”**
```bash
git branch GitNewBranch
```

**2. List all the local and remote branches available in the current trunk**
*(Observe the “*” mark which denote the current pointing branch)*
```bash
git branch -a
```

**3. Switch to the newly created branch. Add some files to it with some contents.**
```bash
git checkout GitNewBranch
echo "This is a new feature" > feature.txt
git add feature.txt
```
*(Note: If you are using Git version 2.23 or newer, you can also use `git switch GitNewBranch` instead of `checkout`)*

**4. Commit the changes to the branch.**
```bash
git commit -m "Add feature.txt in GitNewBranch"
```

**5. Check the status with “git status” command.**
```bash
git status
```

---

## Merging

**1. Switch to the master**
```bash
git checkout master
```
*(Note: Depending on your default branch name, it might be `main` instead of `master`. Use `git checkout main` if that's the case).*

**2. List out all the differences between trunk and branch.**
```bash
git diff master..GitNewBranch
```

**3. List out all the visual differences between master and branch using P4Merge tool.**
*(Note: Ensure P4Merge is installed and configured as your Git difftool beforehand)*
```bash
git difftool master..GitNewBranch
```

**4. Merge the source branch to the trunk.**
```bash
git merge GitNewBranch
```

**5. Observe the logging after merging using “git log –oneline –graph –decorate”**
```bash
git log --oneline --graph --decorate
```

**6. Delete the branch after merging with the trunk and observe the git status.**
```bash
git branch -d GitNewBranch
git status
```
