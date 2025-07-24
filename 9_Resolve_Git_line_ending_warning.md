# Understanding and Resolving Git Line Ending Warnings


## Sometimes you will get warning when you add file in git like as below:👇

> warning: in the working copy of 'file-name', LF will be replaced by CRLF the next time Git touches it

**🔍 Explanation in Simple Terms:** 

Git is telling you that:

- The file 'file-name' currently uses LF (Line Feed) line endings — typical on Linux/macOS.

- But on your system (likely Windows), Git is configured to convert those to CRLF (Carriage Return + Line Feed).

- The phrase "next time Git touches it" means during future actions like checkout, commit, or merge, Git will change the line endings from LF → CRLF in your working directory (not the actual Git history).


### So, what to do or, what is the solution.

There are two solution:

### 1) 👉Solution: **Set your configuration file**.

- set your configuration file as (on windows):
 `git config --global core.autocrlf true`

✅ On Windows:
- `git config --global core.autocrlf true`

- Converts CRLF → LF when committing.
- Converts LF → CRLF when checking out (so files open nicely in Notepad, etc.).
- Git stores files with LF, but working copy uses CRLF (invisible to the user).


✅ On Linux/macOS:
- `git config --global core.autocrlf input`

- Converts CRLF → LF on commit.
- Does not convert LF → CRLF on checkout.
- Ideal for Unix systems.


**🧠 How This Solves Your Problem:**
- Keeps LF in the repository, no matter where users are working.
- Ensures platform-native line endings in their editors.
- Avoids .gitattributes .
- Requires each contributor to set Git config properly.


**📌Pros:**
- Once set and will not occur again this type of warning over any repo.

### Guide to set in your computer using this above method:

> If you're on Windows and want consistent behavior for yourself and others (but without a .gitattributes file), here’s exactly what to do.

✅ Goal:
- Let Git auto-handle line endings the correct way on Windows.
- Keep LF endings in the repo (for compatibility with Linux/macOS contributors).
- Use CRLF locally, so Windows tools (e.g., Notepad, VS Code) behave nicely.
- Avoid line-ending warnings without needing .gitattributes.


🔧 Step-by-Step Git Setup for Windows (One Time):

1. Set `core.autocrlf` to `true`:
Open Git Bash or Command Prompt and run:

- `git config --global core.autocrlf true`

**🔍 What it does:**

- Converts CRLF → LF when you commit (keeps repo clean).
- Converts LF → CRLF when you checkout (matches Windows tools).

2. (Optional) Confirm the setting
Run this command to make sure it’s set:

- `git config --global core.autocrlf`

It should return:
- `true`


3. (Optional but recommended) Re-check out your files
This step refreshes your working directory using the new config:

- `git rm --cached -r .`
- `git reset --hard`

**📌 Explanation:**

- `git rm --cached -r .` unstages all files (doesn't delete them)

- `git reset --hard` re-checks out all files with CRLF line endings, ready to go


**🎯 You’re Done!**

From now on:
- Files you edit will use CRLF on Windows.
- When committed, Git will store LF in the repo.
- You’ll avoid "CRLF will be replaced by LF" warnings.

<!--
🧠 Tip: Share with Teammates
In your README.md or CONTRIBUTING.md, add:
___________________________________________________
## Recommended Git Settings (Windows)

If you're using Windows, run this command to avoid line-ending issues:

`git config --global core.autocrlf true`

- This ensures CRLF locally and LF in the repository.
 
____________________________________________________
-->



### 2) 👉Solution: **Add `.gitattributes` file**. 

- Add `.gitattributes` file in your root directory of your repo. 
- When you commit and force`.gitattributes` to your repository it can overwrites the core.autocrlf setting for all repository contributors. 
- Be sure that, you have commited to changes.
<!-- 
> (This below `.gitattributes` content could not be suitable for collaboration - by chatgpt. Since, there is not set as: *.c text eol=lf and *.h text eol=lf ) 
____________________________________
`.gitattributes` file will contain: |   
_________________________________________________________
# Set the default behavior, in case people don't have core.autocrlf set.
* text=auto

# Explicitly declare text files you want to always be normalized and converted
# to native line endings on checkout.
*.c text
*.h text

# Declare files that will always have CRLF line endings on checkout.
*.sln text eol=crlf

# Denote all files that are truly binary and should not be modified.
*.png binary
*.jpg binary
_________________________________________________________ 
-->

after that, do:
- `git add .gitattributes`
- `git commit -m "Add .gitattributes to normalize line endings"`
- `git checkout-index --force --all`
And now, try again to add file.



