## 🔍 Inspect Repository

| Command | Description |
|---------|-------------|
| `git status` | Check repository status |
| `git log --graph --oneline --all` | View branch history as a graph |
| `git show <commit-id>` | Show details of a commit |
| `git ls-files` | List tracked files |

---

## 📂 Staging

| Command | Description |
|---------|-------------|
| `git add .` | Stage all changes |
| `git add <file>` | Stage a specific file |
| `git add *.md` | Stage all Markdown files |
| `git restore --staged <file>` | Unstage a file |

---

## ✏️ Commit

| Command | Description |
|---------|-------------|
| `git commit -m "message"` | Commit staged changes |
| `git commit --amend` | Modify the last commit |

---

## 🔄 Reset

| Command | Description |
|---------|-------------|
| `git reset --soft HEAD~1` | Undo commit, keep staged changes |
| `git reset --mixed HEAD~1` | Undo commit, unstage changes (default) |
| `git reset --hard HEAD~1` | Undo commit and discard changes |

---

## 📦 Stash

| Command | Description |
|---------|-------------|
| `git stash` | Save uncommitted changes |
| `git stash list` | List all stashes |
| `git stash pop` | Apply and remove latest stash |
| `git stash apply` | Apply stash without removing it |
| `git stash drop` | Delete latest stash |

---

## 🌐 Remote

| Command | Description |
|---------|-------------|
| `git remote -v` | List remotes |
| `git remote add origin <url>` | Add remote repository |
| `git remote remove origin` | Remove remote |
| `git remote set-url origin <url>` | Change remote URL |
| `git fetch` | Download remote changes |
| `git pull origin main` | Pull latest changes |
| `git push origin main` | Push changes |
| `git push -u origin main` | Push and set upstream |

---

## 🌿 Branches

| Command | Description |
|---------|-------------|
| `git branch` | List local branches |
| `git branch -a` | List all branches |
| `git branch <branch-name>` | Create branch |
| `git checkout <branch-name>` | Switch branch |
| `git checkout -b <branch-name>` | Create and switch |
| `git switch <branch-name>` | Switch branch (new syntax) |
| `git switch -c <branch-name>` | Create and switch (new syntax) |
| `git merge <branch-name>` | Merge a branch |
| `git branch -d <branch-name>` | Delete branch |

---

## 🚫 Ignore Files

| Command | Description |
|---------|-------------|
| `touch .gitignore` | Create `.gitignore` file |
| `git rm --cached <file>` | Stop tracking a file |

---

## 🏷️ Tags

| Command | Description |
|---------|-------------|
| `git tag` | List tags |
| `git tag <tag-name>` | Create a tag |
| `git push origin <tag-name>` | Push a tag |

---

## 🧹 Cleanup

| Command | Description |
|---------|-------------|
| `git clean -fd` | Remove untracked files and directories |
| `git rm <file>` | Remove tracked file |
| `git mv <old> <new>` | Rename or move a file |

---

## 🚀 Daily Workflow

```bash
git pull origin main
git add .
git commit -m "Describe your changes"
git push origin main
```