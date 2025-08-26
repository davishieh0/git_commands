# git_commands

### Git Manual
- The Git manual

---

## Switching Branches
`git switch`  
`git switch -c`  
- Creates a branch if it doesn't exist  

---

### View My Git Configurations
`cat ~/.gitconfig`

---

## Reset
The `git reset` command can be used to undo the last commit(s) or any changes in the index (staged changes, but not committed) and in the working tree (unstaged changes, not committed).

`git reset --soft COMMITHASH`  
- Preserves changes in the staging area

`git reset --hard COMMITHASH`  
- Discards all changes and returns to the commit  
- Works to delete staged changes that haven't been committed  
- **DANGEROUS COMMAND!**

---

### Remote
`git remote add <name> <uri>`  
- Adds a remote repository  

`git fetch`  
- Downloads objects and refs from another repository  
- Doesn't bring all files to the working directory, only updates the history  

`git log remote/branch`  
- Views commits from the remote branch  

`git merge remote/branch`  
- Merges the remote into the local branch, creating a clean *fast-forward*  
- **Note:** in practice, pure `git merge` is rarely used to update the branch; it's more common to use `git rebase` to maintain linear history

---

### Github 
`curl -sS https://webi.sh/gh | sh`  
- Installs GitHub CLI which facilitates authentication  

`gh auth login`  
- Performs authentication  

`git push <remote> <local_branch>`  
- Sends from a local branch to a remote branch
  
`gh auth setup-git`

---

## Rebase
`git rebase`  
- Reapplies your local commits on top of another branch, creating linear history without unnecessary merge commits  
- Frequently used instead of `git merge` when updating branches

---

## Interactive Rebase
`git rebase -i <base>`  
- Allows editing local history before sending to remote  
- Possibilities:
  - Reorder commits
  - Combine commits (`squash`)
  - Edit messages
  - Delete commits  
- Very useful for cleaning up history and organizing commits

---

## Configure Pull with Rebase
`git config --global pull.rebase true`  
- Sets every `git pull` to rebase instead of merge by default  
- This avoids automatic merge commits when updating from remote and maintains linear history  
- It's very rare to use pure `git merge` in this workflow

---

## I Made a Mistake
### Change Branch Name
`git branch -m <new-name>`

See commands to revert branch in **#Reset**  

`git commit --amend -m "<message>"`  
- Rewrites the commit message

---

## Custom Log
`git log --oneline --decorate --graph --parents -5`  
- **`--oneline`** → shows each commit in a single line (abbreviated hash + message).  
- **`--decorate`** → displays references associated with the commit (tags, branches).  
- **`--graph`** → draws ASCII graph representing the structure of commits and merges.  
- **`--parents`** → shows the parent commit(s) of each commit, useful for analyzing merges and forks.  

**Example:**  
```bash
git log --oneline --decorate --graph --parents
```

## My Solo Workflow
When I'm working by myself, I usually stick to a single branch, main. I mostly use Git on solo projects to keep a backup remotely and to keep a history of my changes. I only rarely use separate branches.

Make changes to files  
`git add .` (or `git add <files>` if I only want to add specific files)  
`git commit -m "a message describing the changes"`  
`git push origin main`  

It really is that simple for most solo work. git log, git reset, and some others are, of course, useful from time to time, but the above is the core of what I do day-to-day.

<img width="930" height="436" alt="image" src="https://github.com/user-attachments/assets/179784e0-8831-49d5-9381-cc867c0fa682" />

### My Aliases
```bash
nano ~/.bashrc       # Bash
nano ~/.zshrc        # Zsh
nano ~/.config/fish/config.fish  # Fish

gl = git log --oneline --decorate --graph --parents
grs = git reset --soft
grh = git reset --hard
gs = git switch
gb = git branch
gr = git rebase
```