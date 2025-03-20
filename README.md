# day_3
Notes and final exercise on day 3

## Head
Remember that a branch is not a container for your committed files. It is a pointer (or reference) to a specific commit. It represents the tip of a series of commits. The branch's history is extrapolated from the commit relationships.
A HEAD is reference to a commit object.
It points to a specific commit in the branch that we are currently viewing (and working on).
You can switch HEAD to point at another branch so that you can follow the progress (commits) to that branch.

## New branch
Create a new branch:
`git branch new_branch`
View details of current branch:
`git branch`
To work on a different branch, you have to switch to that branch.
Switch to a different branch:
`git switch new_branch`
Use `git log` to see where the head is pointing and what has been committed.
Rename a branch
1. Switch to the branch.
2. `git branch -m new_name`

Delete a branch:
1. Switch to a different branch. You cannot delete a branch while you are working in it. Note that you will be asked to stash or commit any existing changes in the branch, if relevant.
2. `git branch -d unwanted_branch` or `git branch -D unwanted_branch` -D won't prompt you to merge if it hasn't been merged.

## Merging
### Fast-forward merge
This is where the branch you branched from has not been changed.
1. `git switch master`
2. `git merge new_branch`

Where the branch you have branched from has had further commits:
1. `git switch master`
2. `git merge new_branch`
If no conflicts, this creates an automatic commit to update the target branch of the merge. You will be asked to name the commit - but a default name is provided.
**No conflicts** means that no information will be lost as a result of the changes.

## Conflicts
If line x in a file has different changes in each branch. What you see is this:

```
<<<<<<< HEAD
...some content from the file
=======
...different content from the other branch
>>>>>>> new branch
```

- The HEAD (usually master branch) comes first. **This is the branch you have switched to.**
- ======== is the divider
- then you get the content from the branch you are merging (new_branch in this case).

VSCode offers you:
- Accept 
current change - this is the change on the HEAD (master)
- Accept incoming change - this is the change from your branch
- Accept both changes (sepereate lines)
- Accept neither set of changes

### Differences
`git diff` enables you to check for unadded and uncommitted changes (by default). It shows the differences between the current state of a file and the state of the file at the last commit.
Important to understand the output:
- top line indicates you are comparing version a of a file with version b
- it tells you how it uses --- to refer to one version's content and +++ to refer to another version's content
- syntax: @@ -start_line_number, end_line_number + start_line_number , end_line_number @@
	example: @@ -1 + start_line_number @@
Full docs on diff at: https://git-scm.com/docs/git-diff
For example, to view the difference between files on master and on branch:
`git diff master branch`

# Exercise
This exercise was completely in a local repo
1. create new repo
2. create text file with one two three
3. add and commit on master
4. create new branch translation
5. switch to this branch
6. translate numbers to IT
7. add and commit to branch
8. View differences between master branch and translation branch
9. Merge - should work as a fast-forward merge (master has had no changes)
**Implemented this successfully.**

