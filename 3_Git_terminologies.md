# Checking git version:
* `git -- version`  



# Repository

- Repository is a folders name.

- A repository is a collection of files and directories that are stored together. It is a way to store and manage your code.  

- A repository is like a folder on your computer, but it is more than just a folder. It can contain other files, folders, and even other repositories.


# To check folders status, type:
* `git status` 

<!-- this command donot support everywhere, there are some cases/criteria to use this command. -->



# Your config setting

- Github has a lot of settings that you can change. You can change your username, email, and other settings. 

- Whenever you checkpoint your changes, git will add some information about your such as your username and email to the commit. 

- There is a git config file that stores all the settings that you have changed. You can make settings like what editor you would like to use etc. 

There are :
 - some global settings and
 - some repository specific settings.



* `git config --global user.email "your-email@example.com"`
> **config --global**: This makes git, in our system configuration file at global settings and git knows where the file it is.
>
> **--global user.email**: This means, we are setting our email at global label.
>
> * `git config --global user.email "your-email@example.com"`: means this will set your account's default identity globally, meaning that it will be used for all repositories on your computer.



* `git config --global user.name "Your Name"` 

<!--  
# What we did :
----------------------------------------------------
PS D:\user\code\Git> git config --global user.email "johndoe@gmail.com"
PS D:\user\code\Git> git config --global user.name "John-Doe"

// for checking, just type:

PS D:\user\code\Git> git config --global user.name
John-Doe
PS D:\user\code\Git> git config --global user.email
johndoe@gmail.com
----------------------------------------------------
-->
- Again we can change by over-writing if needed.


* `git config --list`: This will show you all the settings that you have changed.




# Creating a repository

- Creating a repository is a process of creating a new folder on your system and initializing it as a git repository. 

- It’s just regular folder to code your project, you are just asking git to track it.

## While creating repository do follow:

At 1st:
* `git status`
>  `git status` command shows the current state of your working directory and staging area in Git. It helps you track changes and understand what files are: 
1. Untracked (new files not yet added to Git)
2. Modified (existing files that have changed but are not staged)
3. Staged (files that are ready to be committed)
4. Committed (no changes detected, everything is up to date)

---

## 🤔 Is it necessary to do always first check: git status, Before creating repo ?
> Ans: Yes, it necessary to do always 1st check: git status , Before creating repo, NOT syntatically but sementically. 
> Because if already existing repository is there then it could overwrite the already existing repository and your progresses and checkpoints could be lose, by the chances of 1%.

---


And 2ndly:
* `git init` 
>  `git init` command will create a new folder on your system and initialize it as a git repository.  This adds a hidden .git folder to your project. This directory contains all Git-related files, such as commit history, branches, and configurations.
>
> The directory becomes a Git repository, ready to track changes.
> i.e. Our current working folder/directory(i.e. temp_folder1) will turn into git repository and will start tracking.

---

## After git init, you can see a hidden folder (i.e. .git folder)   by using  Git Bash command:

* `ls -la`
> for this explaination do visit "2)_Git_bash.md"

---




# Entering Staging Area
 
- After   `git init`   to the selected working directory the next step is to entering the staging area.

- **staging area**:  means Ready to work but not working OR,
- everyone are reached to stage but the performance is not started ).

# Stage
>  Stage is a way to tell git to track a particular file or folder. 
You can use the following command to stage a file:

* `git add <file> <file2> <file3>`: stages specific files/folders
OR,
* `git add .`: stages all files/folders


After that, do check status of the current directory as you checked before git init :

* `git status`
>  will show the current status of your working directory.
> (For more about this, do scroll up in creating repository part).

---

- Here, we are initializing the repository and adding a file to the repository. Then we can see that the file is now being tracked by git. Currently our files are in staging area, this means that we have not yet committed the changes but are ready to be committed.
>  (At this point of time, I took screen shot you can visit "3.i) and 3.ii)_e.g._git_add.png")





# Commit:  (is a check point like in game.)

- After the  git add   the next step is to    commit .

- commit is a way to save your changes to your repository. It is a way to record your changes and make them permanent. You can think of a commit as a snapshot of your code at a particular point in time. When you commit your changes, you are telling git to save them in a permanent way. This way, you can always go back to that point in time and see what you changed.

You can use following command to comit:
* `git commit -m "commit message"`
> - Here we are committing the changes to the repository. We can see that the changes are now committed to the repository. 
>
> - The   -m     flag is used to add a message to the commit. This message is a short description of the changes that were made. You can use this message to remember what the changes were. Missing the -m flag will result in an action that opens your default settings editor, which is usually VIM. We will change this to vscode in the next section.


After that, do check again status of the current directory as you checked before git init :
* `git status`




## Suppose after the commit , later again we make changes to some file (let we make change to "temp_folder1/.git/temp_file2.txt") , 
> then you have to again check status:
* `git status`: to know the current status of working directory.

---

Since, you have changes to file, So you will see:

> On branch master
> Changes not staged for commit:
>  (use "git add <file>..." to update what will be committed)
>  (use "git restore <file>..." to discard changes in working directory)
>        modified:   temp_file2.txt
>
> no changes added to commit (use "git add" and/or "git commit -a")

---

So, you have to do again:
* `git add <file>`
and then 
* `git commit -m "commit message"`



And then, do check again status of the current directory:
* `git status` 
and will show:

---

> On branch master
> nothing to commit, working tree clean
 
---







# Logs

* `git log`
>  This command will show you the history of your repository. It will show you all the commits that were made to the repository. 

* `git log --oneline`
> - You gonna use this mostly.
> - You can use the   `--oneline`     flag to show only the commit message. This will make the output more compact and easier to read.




# .gitignore file

- Sometimes, we just don't need to add some files/folders to repository and github.
- For that, we have to create a  '.gitignore' file    to the repository and we have to write that files/folders name to    '.gitignore' file . 
- And then:
- we have to add, and commit that  '.gitignore' file     to the repository.




# .gitkeep file

- Since, empty folder do not get tracked. 
- So, to keep tracked empty folder we have to just add the `.gitkeep` file    to that empty folder.

