# diff, stash, and Tags


## Git diff

- The    git diff     is an informative command that shows the differences between two commits. It is used to compare the changes made in one commit with the changes made in another commit. Git consider the changed versions of same file as two different files. Then it gives names to these two files and shows the differences between them.


### How to read the diff:
* `a/`: the original file (before changes)  or, file A
* `b/`: the updated file (after changes)  or, file B
* `---`:  marks the beginning of the original file
* `+++`: marks the beginning of the updated file
* `@@`: shows the line numbers and position of changes

Here the file A and file B are the same file but different versions.

Git will show you the changes made in the file A and file B. It will also show you the line number where the change occurred along with little preview of the change.


### Comparing Working Directory and Staging Area

* `git diff`
> This command shows the unstaged changes in your working directory compared to the staging area. This command alone will not show you the changes made in the file A and file B, you need to provide options to show the changes.



### Comparing Staging Area with Repository

* `git diff --staged`
> This command shows the changes between your last commit and the staging area (i.e., changes that are staged and ready to be committed).



### Comparing between branches

* `git diff <branch-name-one> <branch-name-two>`
> - This command compares the difference between two branches.
> - Another way to compare the difference between two branches is to use the following command:

* `git diff branch-name-one..branch-name-two`
> e.g: git diff master..bug-fix 



### Comparing Specific Commits:

* `git diff <commit-hash-one> <commit-hash-two>`
> This command compares the difference between two commits.





## Git Stash

- **Stash** is a way to save your changes in a temporary location. It is useful when you want to make changes to a file but don’t want to commit them yet. You can then come back to the file later and apply the changes.

- Conflicting changes will not allow you to switch branches without committing the changes. Another alternative is to use the     `git stash`     command to save your changes in a temporary location.


* `git stash`
> This command saves your changes in a temporary location. It is like a stack of changes that you can access later.



### Naming the stash

- You can also name the stash (instead of using: `git stash`   , only ) by using the following command:

* `git stash save "work in progress on X feature"`
> This command saves your changes in a temporary location having your given statement"work in progess on X feature".



### View the stash list
> You can view the list of stashes by using the following command:
* `git stash list`



### Apply the stash

- You can apply the stash by using the following command:

* `git stash apply`
> is used to reapply the most recently saved changes from the stash without removing them from the stash list.
>
> This command helps to bring those changes back into your working directory, which have been recently stashed. 



### Apply the specific stash

- You can apply the specific stash by using the following command:

* `git stash apply stash@{0}`
> Here stash@{0} is the name of the stash. You can use the git stash list command to get the name of the stash.



### Applying and dropping the stash

- You can apply and drop the stash by using the following command:

* `git stash pop`
> This command applies the stash and drops it from the stash list.



### Drop the stash

- You can drop the stash from the stash list by using the following command:

* `git stash drop`



### Applying stash to a specific branch

- You can apply the stash to a specific branch by using the following command:

* `git stash apply stash@{0} <branch-name>`
> ! Be careful while using this command, this command apply a stash to a specific branch and can cause the conflict.



### Clearing the stash

- You can clear the stash by using the following command:

* `git stash clear`
> This command deletes all stashes.





## Git Tags

- Tags are a way to mark a specific point in your repository. They are useful when you want to remember a specific version of your code or when you want to refer to a specific commit. Tags are like sticky notes that you can attach to your commits.


### Creating a tag

- You can create a tag using the following command:

* `git tag <tag-name>`
> This command creates a new tag with the specified name. The tag will be attached to the current commit.


> - Tag's are not used by developer's in organizations. Instead of developer's, product managers uses them. So, I'm skipping this section...
