# Essential Git Commands

This is a quick reference for some of the most commonly used Git commands.

## ⚙️ Setup & Initialization

*   `git init`
    *   Initializes a new Git repository in the current directory.
*   `git clone <repository_url>`
    *   Creates a local copy of a remote repository.
    *   Example: `git clone git@github.com:user/repo.git`
    *   or `git clone https://github.com/user/repo.git`

## 🔄 Daily Workflow: Staging & Committing

*   `git status`
    *   Shows the status of changes as untracked, modified, or staged.
*   `git add <file_name>`
    *   Adds a specific file's changes to the staging area.
    *   Example: `git add README.md`
*   `git add .` or `git add -A`
    *   Adds all new and modified files in the current directory and subdirectories to the staging area.
*   `git commit -m "Your descriptive commit message"`
    *   Records the staged changes to the repository's history.
    *   Example: `git commit -m "feat: Add user authentication"`
*   `git commit --amend`
    *   Modifies the last commit. Useful for fixing typos in commit messages or adding forgotten files.
*   `git diff`
    *   Shows changes between working directory and staging area (unstaged changes).
*   `git diff --staged`
    *   Shows changes between staging area and the last commit (staged but not committed).

## 🌿 Branching & Merging

*   `git branch`
    *   Lists all local branches. Current branch is marked with `*`.
*   `git branch <branch_name>`
    *   Creates a new branch.
    *   Example: `git branch new-feature`
*   `git checkout <branch_name>` or `git switch <branch_name>`
    *   Switches to an existing branch.
    *   Example: `git checkout new-feature`
*   `git checkout -b <branch_name>` or `git switch -c <branch_name>`
    *   Creates a new branch and switches to it.
    *   Example: `git checkout -b hotfix-123`
*   `git merge <branch_name>`
    *   Merges the specified branch's history into the current branch.
    *   Example (while on `main`): `git merge new-feature`
*   `git rebase <branch_name>`
    *   Re-applies commits from the current branch onto the tip of another branch. Helps maintain a linear history.
    *   Example (while on `new-feature`): `git rebase main`
*   `git branch -d <branch_name>`
    *   Deletes a local branch (if it has been merged).
*   `git branch -D <branch_name>`
    *   Force-deletes a local branch (even if unmerged).

## 🌐 Working with Remotes (e.g., GitHub)

*   `git remote -v`
    *   Lists all configured remote repositories with their URLs.
*   `git remote add <remote_name> <repository_url>`
    *   Adds a new remote repository.
    *   Example: `git remote add origin https://github.com/user/repo.git`
*   `git fetch <remote_name>`
    *   Downloads objects and refs from a remote repository without integrating them.
    *   Example: `git fetch origin`
*   `git pull <remote_name> <branch_name>`
    *   Fetches changes from the remote and merges them into the current local branch. (Equivalent to `git fetch` then `git merge`).
    *   Example: `git pull origin main`
*   `git push <remote_name> <branch_name>`
    *   Uploads local branch commits to the remote repository.
    *   Example: `git push origin new-feature`
*   `git push -u <remote_name> <branch_name>` or `git push --set-upstream <remote_name> <branch_name>`
    *   Pushes the current branch and sets up tracking for future pulls/pushes.
    *   Example: `git push -u origin feature-branch`
*   `git push <remote_name> --delete <branch_name>` or `git push <remote_name> :<branch_name>`
    *   Deletes a remote branch.
    *   Example: `git push origin --delete old-feature`

## 📜 Viewing History & Undoing Changes

*   `git log`
    *   Shows the commit history for the current branch.
*   `git log --oneline`
    *   Shows a condensed, one-line commit history.
*   `git log --graph --decorate --oneline --all`
    *   A more visual log showing branches and merges.
*   `git show <commit_hash>`
    *   Shows metadata and content changes of a specific commit.
*   `git reset <file_name>`
    *   Unstages a file, keeping the changes in the working directory.
*   `git checkout -- <file_name>`
    *   Discards changes in the working directory for a specific file, reverting it to the version in the last commit (or staging area).
*   `git reset HEAD~1`
    *   Uncommits the last commit, keeping changes in the staging area (soft reset).
*   `git reset --hard HEAD~1`
    *   **DANGEROUS:** Uncommits the last commit and discards all changes from it.
*   `git revert <commit_hash>`
    *   Creates a new commit that undoes the changes made in a previous commit. Safer for shared history than `reset`.

## ✨ Other Useful Commands

*   `git stash`
    *   Temporarily shelves changes you've made to your working copy.
*   `git stash pop`
    *   Re-applies the most recently stashed changes and removes them from the stash list.
*   `git stash apply <stash_id>`
    *   Re-applies a specific stash without removing it from the list.
    *   Example: `git stash apply stash@{1}`
*   `git stash list`
    *   Lists all stashed changes.
*   `git tag <tag_name>`
    *   Creates a lightweight tag pointing to the current commit (often for releases).
    *   Example: `git tag v1.0.0`
*   `git tag -a <tag_name> -m "Tag message"`
    *   Creates an annotated tag with a message.
*   `git push --tags`
    *   Pushes all local tags to the remote repository.

---

Remember to replace placeholders like `<repository_url>`, `<branch_name>`, `<file_name>`, and `<commit_hash>` with your actual values.
For more details on any command, use `git help <command>` or `git <command> --help`.
