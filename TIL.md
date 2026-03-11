# 📓 TIL — Today I Learned 

A running log of git tricks, discoveries, and "why didn't I know this sooner" moments.  
Updated regularly to document things I pick up while working on real projects.

---

## 2026-03-11

### `git rebase --autostash` is a game changer

Always used to get "cannot rebase: you have unstaged changes" and had to manually stash, rebase, pop.  
Turns out `--autostash` does all three automatically:

```bash
git rebase --autostash origin/main
```

Git stashes your working tree, applies the rebase, then restores your changes. Zero interruption.  
Set it permanently so you never think about it again:

```bash
git config --global rebase.autoStash true
```

---

### Interactive rebase with `--autosquash` cleans up messy commit history

When fixing a bug I already committed, instead of a vague "fix typo" commit I can now do:

```bash
git commit --fixup=abc1234   # where abc1234 is the original commit
```

Then on the next rebase:

```bash
git rebase -i --autosquash origin/main
```

Git automatically places the fixup right below the original commit and marks it for squashing.  
The PR history stays clean without manually editing the rebase todo list.

---

### `git worktree` lets you review a PR without touching your current work

Previously: stash → checkout → review → checkout back → pop stash.  
Now:

```bash
git worktree add ../review-pr-42 origin/feature/pr-42
cd ../review-pr-42
# review, run tests, etc.
cd ../main-repo
git worktree remove ../review-pr-42
```

Two branches, two folders, zero stashing. Both are fully live at the same time.

---

### `git rerere` remembers conflict resolutions

`rerere` = **Re**use **Re**corded **Re**solution.  
Enable it once:

```bash
git config --global rerere.enabled true
```

Next time you hit the same merge conflict (e.g., the same dependency version conflict after every rebase),  
git resolves it automatically. Huge time-saver on long-running feature branches.

---

### The difference between `git reset` modes — finally clear

| Mode | Index (staging) | Working tree | Use case |
|------|----------------|--------------|----------|
| `--soft` | ✅ keeps | ✅ keeps | Undo commit, keep staged changes |
| `--mixed` *(default)* | ❌ unstages | ✅ keeps | Undo commit + unstage, keep files |
| `--hard` | ❌ clears | ❌ clears | Nuclear — wipe everything |

`--soft` is the safe "oops, wrong commit message" reset.  
`--hard` is the "start over completely" reset. Always double-check before using it.

---

*Started: March 2026 · 
