# Git Commands Reference

Every command you actually use, with a plain-English description.

---

## ⚙️ Setup & Config

| Command | Description |
|---------|-------------|
| `git config --global user.name "Your Name"` | Set your name — shown on every commit |
| `git config --global user.email "you@email.com"` | Set your email — must match GitHub for contributions to count |
| `git config --global core.editor vim` | Set default editor for commit messages |
| `git config --global init.defaultBranch main` | Make all new repos start on `main` |
| `git config --list` | Show all current git configuration values |
| `git init` | Initialise a new local repo in the current folder |

---

## 📝 Basic Workflow

| Command | Description |
|---------|-------------|
| `git status` | Show which files are staged, unstaged, or untracked |
| `git add <file>` | Stage a specific file for the next commit |
| `git add .` | Stage every changed and new file in the current directory |
| `git commit -m "message"` | Save staged changes with a description message |
| `git commit --amend` | Edit the last commit message or add forgotten files |
| `git diff` | Show line-by-line changes not yet staged |
| `git diff --staged` | Show changes that are staged and ready to commit |
| `git rm <file>` | Delete a file and stage its removal in one step |

---

## 🌿 Branching & Merging

| Command | Description |
|---------|-------------|
| `git branch` | List all local branches — active one marked with * |
| `git branch <name>` | Create a new branch without switching to it |
| `git checkout -b <name>` | Create a new branch and switch to it immediately |
| `git switch <name>` | Switch to an existing branch (modern alternative to checkout) |
| `git merge <branch>` | Merge another branch into the current one |
| `git rebase <branch>` | Replay your commits on top of another branch for a clean history |
| `git branch -d <name>` | Delete a branch that has already been merged |
| `git branch -D <name>` | Force-delete a branch even if unmerged |

---

## 🌐 Remote / GitHub

| Command | Description |
|---------|-------------|
| `git clone <url>` | Download a repo and its full history to your machine |
| `git remote -v` | List all remote connections and their URLs |
| `git remote add origin <url>` | Connect your local repo to a remote for the first time |
| `git push origin <branch>` | Upload your local commits to the remote branch |
| `git push -u origin main` | Push and set upstream — future `git push` needs no arguments |
| `git pull` | Fetch remote changes and merge into your current branch |
| `git fetch` | Download remote changes without merging — safe to inspect first |
| `git push --delete origin <branch>` | Delete a branch on the remote |

---

## ↩️ Undo & Fix

| Command | Description |
|---------|-------------|
| `git restore <file>` | Discard unstaged changes — reverts to last commit |
| `git restore --staged <file>` | Unstage a file without losing your changes |
| `git reset HEAD~1 --mixed` | Undo last commit but keep changes in working directory |
| `git reset HEAD~1 --hard` | Completely delete the last commit and all its changes |
| `git revert <commit>` | Create a new commit that reverses a specific commit — safe for shared branches |
| `git clean -fd` | Delete all untracked files and directories |

---

## 📦 Stash

| Command | Description |
|---------|-------------|
| `git stash` | Temporarily save uncommitted changes to switch branches cleanly |
| `git stash pop` | Restore the most recently stashed changes |
| `git stash list` | Show all saved stashes with their index numbers |
| `git stash drop` | Delete the most recent stash without applying it |

---

## 🔍 Inspect & Log

| Command | Description |
|---------|-------------|
| `git log --oneline --graph` | Compact visual history showing branches and merges |
| `git log -p <file>` | Show the full change history of a specific file |
| `git show <commit>` | Display full details and diff of a specific commit |
| `git blame <file>` | Show who last changed each line and in which commit |
| `git shortlog -sn` | Show commit counts per contributor — ranked |
| `git tag <v1.0>` | Mark a specific commit as a release with a label |

---

## ⚡ Advanced

| Command | Description |
|---------|-------------|
| `git cherry-pick <commit>` | Apply a specific commit from another branch onto current |
| `git bisect start` | Begin binary search to find which commit introduced a bug |
| `git reflog` | Show every HEAD movement — recover lost commits after a bad reset |
| `git submodule add <url>` | Embed another git repo inside your repo as a tracked dependency |
| `git archive --format=zip HEAD > out.zip` | Export repo snapshot as zip without git history |
| `git gc` | Run garbage collection to compress and clean up the repo |

---

## 🚀 git push — Full Reference

| Command | Description |
|---------|-------------|
| `git push` | Push current branch to its tracked upstream |
| `git push origin main` | Push local `main` to remote `origin` |
| `git push -u origin main` | Push and set upstream — future pushes need no arguments |
| `git push origin <branch>` | Push a local feature branch to remote for the first time |
| `git push origin local:remote` | Push local branch to a differently-named remote branch |
| `git push --all origin` | Push every local branch to remote in one go |
| `git push origin --delete <branch>` | Delete a branch on the remote |
| `git push origin :<branch>` | Shorthand to delete a remote branch |
| `git push --set-upstream origin <branch>` | Link local branch to remote and set tracking |
| `git push origin HEAD` | Push current branch without typing its name |
| `git push origin v1.0.0` | Push a specific tag — tags are not pushed automatically |
| `git push --tags` | Push all local tags to remote at once |
| `git push --follow-tags` | Push commits and annotated tags pointing to those commits |
| `git push origin --delete v1.0.0` | Delete a tag from the remote |
| `git push --force` | ⚠️ Overwrite remote history — never use on shared branches |
| `git push --force-with-lease` | Safer force push — refuses if someone else pushed since your last fetch |
| `git push --force-with-lease --force-if-includes` | Safest force push — also checks remote-tracking refs |
| `git push --dry-run` | Simulate the push — nothing is actually sent |
| `git push --verbose` | Show detailed output of what is being pushed |
| `git push --no-verify` | Skip pre-push hooks |
| `git push --atomic` | All refs succeed or all fail — atomic operation |
| `git push --mirror` | Mirror all refs including deletions — used for full backups |
| `git push --prune` | Remove remote branches with no local counterpart |
| `git push origin HEAD --force-with-lease` | Safest way to force-push current branch after rebase |
| `git push -u origin HEAD` | Push current branch and set upstream in one command |
| `git push origin --all --follow-tags` | Push all branches and their tags in one command |
| `git push origin --delete feature && git branch -d feature` | Delete branch on remote and locally — full cleanup |

---

*79 commands total — updated 2026*

---

## 🔀 Rebase

| Command | Description |
|---------|-------------|
| `git rebase <branch>` | Replay your commits on top of another branch — clean linear history |
| `git rebase -i HEAD~3` | Interactive rebase — squash, reorder, reword or drop last 3 commits |
| `git rebase -i origin/main` | Interactively rebase all commits not yet on main — clean up before a PR |
| `git rebase --onto main old-base feature` | Move feature branch from old-base onto main — precise transplanting |
| `git rebase --continue` | Resume rebase after resolving a conflict |
| `git rebase --skip` | Skip the current conflicting commit and continue |
| `git rebase --abort` | Cancel the rebase — return to state before it started |
| `git rebase --autosquash -i origin/main` | Auto-arrange fixup! and squash! commits |
| `git rebase --autostash <branch>` | Auto-stash changes before rebase and restore after |
| `git commit --fixup=<commit>` | Create a fixup commit that auto-squashes into an earlier commit on rebase |
| `git pull --rebase` | Pull and rebase your commits on top instead of merging |
| `git config --global pull.rebase true` | Make rebase the default for all future pulls |

---

## 🗂️ Worktree

| Command | Description |
|---------|-------------|
| `git worktree add <path> <branch>` | Check out a branch into a separate folder — two branches at once |
| `git worktree list` | Show all linked worktrees and their branches |
| `git worktree remove <path>` | Remove a linked worktree |
| `git worktree prune` | Clean up stale worktree references |

---

## 🪝 Hooks & Automation

| Command | Description |
|---------|-------------|
| `ls .git/hooks/` | List all available hooks — rename `.sample` files to activate |
| `chmod +x .git/hooks/pre-commit` | Make a hook executable |
| `git commit --no-verify` | Skip pre-commit and commit-msg hooks |
| `git config --global core.hooksPath ~/.githooks` | Set a global hooks directory shared across all repos |

---

## ⚙️ Config & Aliases

| Command | Description |
|---------|-------------|
| `git config --global alias.st status` | Create alias — `git st` runs `git status` |
| `git config --global alias.lg "log --oneline --graph --decorate"` | Create alias for a complex command |
| `git config --global core.autocrlf input` | Convert CRLF to LF on commit — essential on Linux/macOS |
| `git config --global core.excludesfile ~/.gitignore_global` | Set a global gitignore for every repo |
| `git config --global merge.tool vimdiff` | Set preferred merge conflict tool |
| `git config --global diff.tool vscode` | Use VS Code as diff viewer |
| `git config --local user.email "work@company.com"` | Override config for a single repo only |
| `git config --global rerere.enabled true` | Remember conflict resolutions and auto-apply them next time |

---

*119 commands total — updated 2026*