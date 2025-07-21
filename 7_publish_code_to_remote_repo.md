# Publish Code to Remote Repository

- After the setup of your `ssh key` and added it to your github account, you can start pushing your code to the remote repository.

Create a new Repo on your system first, add some code and commit it.

* `git init`
* `git add <files>`
* `git commit -m "commit message"`
* `git branch -M main`, (optional)


## Do follow these below commands, and for understanding their meaning, scroll down: 👇👇

1) `git remote -v`

2) `git remote add origin <remote-url>`
> e.g: `git remote add origin https://github.com/username/my-repo.git`

3) `git remote -v`

4) `git push origin main`


> After that, if you again create commit, then do follow:
> Or, even you can skip `git push origin main`. Just start with below command: 

* `git push -u origin main`

> After that, if you again create commit and then just do:

* `git push`

---

### If you switches to another branch, if exits and want to push that branch also, then do follow:

* `git checkout <branch-name>`
> e.g: `git checkout bug-fix`

* `git push origin bug-fix`


> After that, if you again create commit to the same branch then do follow:
> Or, even you can skip `git push origin main`. Just start with below command: 

* `git push -u origin bug-fix`

> After that, if you again create commit to the same branch and then just do:

* `git push`




---
## Understanding above command meaning:


* ### `git remote -v`
> is used to list the remote repositories connected to your local Git repository, along with their URLs.

**🔍 Explanation:**
- `remote`: Refers to the remote repositories (typically hosted on GitHub, GitLab, etc.).

- `-v`: Stands for verbose, which means it shows the URLs as well as the names.

🧾 Output Example:
_______________________________________________________
origin  https://github.com/username/my-repo.git (fetch)
origin  https://github.com/username/my-repo.git (push)
_______________________________________________________
**📌 What This Tells You:**
- You have a remote named origin.

- The URL points to your GitHub repository.

- This URL is used for both fetching and pushing data.


📚 Common Remote Names:

|Remote Name| Purpose                                    |
|-----------|--------------------------------------------|
|origin	    | Default name for your main remote repo     |
|upstream	|Often used when you fork someone else’s repo|


✅ Use Cases:
- Check which GitHub repo your local project is connected to.

- Confirm whether you’ve added a remote.

- Ensure correct URLs before pushing or pulling.




* ### `git remote add origin <remote-url>`

> e.g: `git remote add origin https://github.com/username/my-repo.git`

> is used to connect your local Git repository to a remote GitHub repository.

**🔍 Breakdown:**
- `git remote add`: Tells Git you want to add a new remote connection.

- `origin`: The name you’re giving to the remote. origin is the default and most commonly used name.

- `https://github.com/username/my-repo.git`: This is the URL of the remote repository (on GitHub, in this case).

**💡 What it does:**
- It tells Git:
> “From now on, treat https://github.com/username/my-repo.git as the remote repo named origin.”






* ### `git push origin main`
> is used to upload your local commits on the main branch to the remote repository named origin (usually GitHub).

**🔍 Breakdown:**
|Part	   |  Meaning                              |  
|----------|---------------------------------------|
|`git push`|	Pushes (uploads) your local changes|  
|`origin`  |  The name of the remote repository    |  
|`main`    |The name of the branch you're pushing (usually main)|


**💡 What it Does:**

> “Take all my commits on the local main branch and upload them to the main branch on GitHub (origin).”


**📌 Requirements:**
- You must have already committed changes locally.

- The remote (usually GitHub) should be added (via git remote add origin ...).

- The branch you’re pushing (main) must exist locally.






* ### `git push -u origin main`

> Pushes your local main branch to origin/main. Same as `git push origin main`.
> Just difference in this command is that `-u`:

🔹 The `-u` in `git push -u origin main` sets origin/main as the upstream, so in the future you can just type:

* `git push`

