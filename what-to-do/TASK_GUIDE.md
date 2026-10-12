# Task Guide — Linux Command Line Practical

This guide follows the supplied PDF's steps and terminology. Run these Linux commands in Kali Linux, not in Windows Git Bash.

## Step 1 — Create and switch to `student01`
From an account with authorized administrative privileges:
```bash
sudo useradd -m -s /bin/bash student01
sudo passwd student01
sudo usermod -aG sudo student01
su - student01
whoami
```
The PDF says add the user to `sudo` “if required”; use `usermod` if needed. If the account already exists, inspect it with `id student01` and `getent passwd student01` instead of rerunning `useradd`. Expected `whoami` result: `student01`.

## Step 2 — Directories and files
As `student01`:
```bash
mkdir -p ~/project/docs ~/project/scripts ~/project/bin
cd ~/project/docs
echo "This is the initial report by student01." > report.txt
ls -la
echo "Top Secret" > .secret.txt
ls -la
```

## Step 3 — Edit and move files
```bash
nano report.txt
```
Add this second line, then save with `Ctrl+O`, Enter, and exit with `Ctrl+X`:
```text
Appended line using nano.
```
Verify with `cat report.txt`. Then:
```bash
cp report.txt ~/project/scripts/
mv .secret.txt ~/project/bin/classified.txt
cat > ~/project/scripts/install.sh <<'EOF'
#!/bin/bash
echo "Installing project dependencies..."
EOF
cat ~/project/scripts/install.sh
```

## Step 4 — Permissions with chmod
Make the script executable by all users:
```bash
chmod a+x ~/project/scripts/install.sh
ls -l ~/project/scripts/install.sh
```
Remove read permission for others from `classified.txt`:
```bash
chmod o-r ~/project/bin/classified.txt
ls -l ~/project/bin/classified.txt
```
Create owner-read/write-only notes:
```bash
touch ~/project/docs/admin_notes.txt
chmod 600 ~/project/docs/admin_notes.txt
ls -l ~/project/docs/admin_notes.txt
```
Mode `600` appears as `-rw-------`.

## Step 5 — Clean-up and final touches
```bash
rm ~/project/docs/admin_notes.txt
mkdir -p ~/project/backup
cp -r ~/project/docs ~/project/scripts ~/project/backup/
```
This creates `backup/docs/` and `backup/scripts/` containing copies of those directories.

## Final checks
```bash
cd ~
tree project
ls -la ~/project/docs ~/project/scripts ~/project/bin ~/project/backup
```
If `tree` is missing, the PDF suggests `sudo apt install tree` (requires admin privileges). Alternatively, inspect with `find ~/project -maxdepth 4 -print`.

## Optional bonus — history
```bash
history
history > ~/commands_used.txt
```
Review this file before sharing; command history can contain sensitive or irrelevant information.