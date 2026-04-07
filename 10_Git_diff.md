# Git diff usage

**how to see what have been changes in working directory compared to pushed code**

- To see what has changed in your working directory compared to the pushed code (remote repository), you’ll use a few Git commands depending on what exactly you want to compare.

## 1. 🔍 Check current status
```bash
git status
```
Shows:
- Modified files
- Staged files
- Untracked files

👉 This compares working directory vs staging area (index)


## 2. 📝 See actual changes (not staged)
```bash
git diff
```
- Shows line-by-line differences
- Compares:
  - Working directory vs last commit (HEAD)


## 3. 📦 See staged changes
```bash
git diff --staged
```
- Compares:
  - Staging area vs last commit


## 4. 🌐 Compare with pushed code (remote)

- First, fetch latest remote state:
```bash
git fetch
```
Then compare:

👉 See difference with remote branch
```bash
git diff origin/main
```
(or replace main with your branch)

- Compares:
  - Your local branch vs remote (pushed code)


## 5. 📊 See commits difference
```bash
git log origin/main..HEAD
```
- Shows commits you have locally but not pushed yet


## 6. 🔁 See everything (simple overview)
```bash
git status
git diff
git diff origin/main
```
🧠 Simple understanding
- git diff → what you changed locally
- git diff origin/main → what is different from pushed code
- git status → quick summary

⚠️ Common mistake

If you don’t run:
```bash
git fetch
```
- You might compare with old remote data


If you want, I can show you how to do this visually inside VS Code Git panel, which might be easier for you 👍