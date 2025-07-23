# Git Commands for Undoing and Fixing Mistakes


## Undo git init command
>  Just do: `rm -rf .git`

**🔥What it does ?**

> rm = remove
>
> -r = recursively (delete folders and their contents)
>
> -f = force (don’t ask for confirmation)
>
> .git = the entire Git repository metadata folder

- So this command permanently deletes the entire .git directory, which is what makes your project a Git repository.





## Modify the most recent commit

Enter: 
- `git commit --amend` and press Enter. 
Or,
- `git commit --amend -m "an updated commit message"` if you want to pass in a new message from the command line without being prompted to open an editor.





## Want to permanently delete a pushed Git commit from the server (remote repo), you must perform a hard reset and then push back to the server with force:
- `git reset --hard <commit-hash>`
- `git push --force origin`
> However, pushing back to the server with force is a destructive move, as it rewrites history to permanently delete the pushed commit.

**Understanding above command:**
* `git push --force origin`
> The `git push --force -u origin` command overrides this restriction in Git, meaning it allows you to forcefully overwrite the commit history of your local branch to the remote repository branch.
> 
> It overwrites the remote repository with your local version.
> 
> Even if your local commit history is different, it says:
> 
> “Make the remote match me, no matter what’s on it!”

**✅ Good if:** You intentionally rewrote history (like after `git reset --hard <commit-hash>`)
**❌ Bad if:** Others are working on the same branch — it can break their clones!

* `git reset --hard <commit-hash>` is already covered in [Reflog topic](6_rebase_n_reflog.md).

> `git reset --hard <commit-hash>` and `git reset --hard` works different.


* `git reset --hard`: (⚠️ Be careful while doing `git reset --hard` and `git reset --hard <commit-hash>`. It cannot be recovered. Uncommited changes will be removed 😱 . Because of this command, I lost c my programming files at that time I didn't know.)
> - It removes all uncommitted changes (both staged and unstaged).
>
> - It resets your working directory and staging area to the last committed state.
>
> - It’s like saying:
> “Forget everything I changed — go back to how it was at the last commit.”

**✅ Good if:** You made a mess and want to throw away all changes.

**❌ Bad if:** You haven't saved your work — because it's gone!






## Forcefully discard local changes 

- `git checkout -f` 

> This command forces Git to check out the current branch again, discarding any uncommitted changes in tracked files (like `git reset --hard`, but without changing history or commits).

**🔍 Breakdown:**
`git checkout`: Used to switch branches or restore files.

`-f` or `--force`: Forces the checkout, overwriting local changes to tracked files.

**✅ What it does:**
- Resets all tracked files to the state of the last commit.

- Uncommitted changes (in files tracked by Git) are lost.

- It doesn't affect:

> - Untracked files
> - Commit history
> - Staging area (it clears it, though)

**❗ Be Careful:**
- `git checkout -f` cannot be undone unless you’ve stashed or committed changes before.

🔁 Example Use Case:
- Imagine you're halfway through some changes and realize everything is a mess. You just want to throw away all edits:

> `git checkout -f`

All tracked files go back to the last committed state.



