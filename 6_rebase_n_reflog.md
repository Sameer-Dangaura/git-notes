# Rebase and Reflog


## Rebase in git

- Git **rebase** is a powerful Git feature used to change the base of a branch. It effectively allows you to move a branch to a new starting point, usually a different commit, by “replaying” the commits from the original base onto the new base. This can be useful for keeping a cleaner, linear project history.

- Some people like to use rebase over the merge command because it allows you to keep the commit history cleaner and easier to understand. It also allows you to make changes to the code without affecting the original branch.

> Tip: Do not pierce the base of main(master) branch.

> Rebase is done 99.99% to the sub-branches of main(master) branch. i.e. We do pierce the base of the sub-branches as per needed. 


> Small recap of merge...
## Merge commits

- A merge commit is a commit that combines two or more commits into one. It is created when you merge two or more branches into a single branch. The merge commit contains all the changes from the original branches, and it is used to keep the project history clean and easy to understand.
> Since, merge create commits where some people don't really like those unwanted commits for merge. So, those types of people refer to rebase, which do re-allocate the base without having commit.




## Rebase                                                
<!-- (For this, you can visit "6.i)and6.ii)_rebase_concept.mp4" and do not play video in vs-code, it can't handle the videos) -->

- Rebase is a powerful tool in Git that allows you to move a branch to a new starting point. It effectively replays the commits from the original base onto the new base. This can be useful for keeping a cleaner, linear project history.

- Here’s a flow example of using git rebase with all the commands involved:

- Suppose you have a feature branch called feature-branch that you want to rebase onto the main branch.

> Ensure you are on the branch you want to rebase ( ! do not alter the base of main(master) branch ):

* `git checkout feature-branch`
> This command switches to feature-branch whose base you want to re-allocate or re-base on main(master). 
After that do: 

* `git rebase master`
> This command re-allocate or re-bases of feature-branch(since, you were switched to feature-branch in above command) on main(master).


---
### Tip for rebase:
> Don't use rebase to change the base of main(master) branch.                                                   
> Use rebase to change the base of the sub-branches on the main(master) branch instead of merge from main(master) branch to sub-branches, if you don't want extra commits for merge. 
---





## Git reflog

- Git reflog is a command that shows you the history of your commits. It allows you to see the changes that you have made to your repository over time. This can be useful for debugging and understanding the history of your project.

### View the reflog

* `git reflog`
> This command shows a list of recent changes to HEAD, including commits, checkouts, and resets.



### Find specific commit

- You can find a specific commit using the following command:

* `git reflog | grep "<commit-hash>"`
> This command not gonna work in vs-code's powershell. You have to use in git bash.

> **Explanation:** `git reflog | grep "<commit-hash>"`
>
>* `git reflog`: Shows the history of changes to the tip of branches (like HEAD, master, etc.) — including commits, rebase, merge, reset, checkout, etc.
>
>* `|`: Pipes the output of git reflog into another command.
>
>* `grep "<commit-hash>"`: Filters the reflog to show only lines that contain the given <commit-hash>.

**What it does:**
- This command searches the reflog for a specific commit hash to find when and how that commit was referenced or used.




### Check a Commit's Details

* `git show <commit-hash>`



### Move HEAD to a commit (without modifying working files)

* `git checkout <commit-hash>`
> This command is used to switch to a specific commit in a Git repository. This command is like a time traveller which can use to go past commits.
### Note: 
>If you do pierce to past commits, then it can affect to the future and present commits.
>  After done checkout that commit and wanna come back then you can do: 
  * `git checkout <recent-new-commit-hash>`
  or,
  * `git checkout master`
  > This command will switch to the recent new commit of that master(main) branch.



### Recover lost commits or changes

- If you accidentally deleted a branch or made changes that are no longer visible in the commit history, you can often recover them using the reflog. First, find the reference to the commit where the branch or changes existed, and then reset your branch to that reference.

* `git reflog` 
or,
* `git log` 

and then:

* `git reset --hard <commit-hash>`
> This command forcefully moves the current branch to a specific commit and deletes all changes after it.

### Note: 
> Commits removed by git reset --hard cannot be recovered unless they exist in the reflog.
