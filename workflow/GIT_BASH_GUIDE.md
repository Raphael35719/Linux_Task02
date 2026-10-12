# Publish with Git Bash

Run these commands in Git Bash on Windows from the extracted project directory. They publish the repository; they do not run the Linux practical.

## 1. Enter the project folder
```bash
cd /c/path/to/linux-task-02-command-line-practical
```
Replace the example path with the actual folder path.

## 2. Initialize and commit
```bash
git init
git status
git add README.md what-to-do evidence workflow outputs submission-notes
git status
git commit -m "Add Linux Task 02 practical workflow"
```

## 3. Create a GitHub repository
Create an empty repository named `linux-task-02-command-line-practical` on GitHub.

## 4. Connect and push
Replace `YOUR-USERNAME` with your GitHub username:
```bash
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/linux-task-02-command-line-practical.git
git push -u origin main
```
If `origin` already exists, check `git remote -v`; correct it with `git remote set-url origin <repository-url>` if needed.

## 5. Publish future updates
```bash
git status
git add .
git commit -m "Add task evidence and actual outputs"
git push
```
Before pushing, ensure no passwords, tokens, private keys, or unrelated private data are included. Choose public/private repository visibility intentionally.