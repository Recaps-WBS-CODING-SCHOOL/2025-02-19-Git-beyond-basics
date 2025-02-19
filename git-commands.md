### Amending previous commit

The `git commit --amend` command allows you to modify the most recent commit. It is useful for making changes or corrections to your last commit without creating a new commit. Here’s how it works:

**What It Does**

- **Edit Commit Message**: If you realize there’s a typo or want to improve the commit message, `git commit --amend` lets you edit the commit message of the latest commit.
- **Include New Changes**: If you’ve forgotten to add some files or need to make changes to the files you just committed, you can stage those changes and then use `git commit --amend` to include them in the last commit.

**How It Works**

1. Modify Files (Optional): Make any necessary changes to your files or stage any additional files.
2. Run the Command: Execute `git commit --amend`.
3. Edit Commit Message (Optional): An editor will open, allowing you to modify the commit message. Save and close the editor to finalize the amended commit. You can exit the editor in the terminal by pressing the `esc` key, then typing `:wq` and pressing `enter`
4. You can alternately use `git commit --amend --no-edit` if you only want to add some changes to the previous commit but keep the commit message the same. `--no-edit` saves you the step of re-entering the message.

**Important Note**

- Rewriting History: `git commit --amend` rewrites the commit history, so avoid using it on commits that have already been pushed to a shared repository, as it may cause issues for others working on the same branch.

---

### Git reflog

`git reflog` is a powerful Git tool that records every move your HEAD makes, allowing you to recover lost commits, reset actions, or other operations that change your commit history. It is like a safety net, providing a record of your Git actions and allowing you to recover from mistakes or explore your history in detail.

#### Recovering a Lost Branch Using Reflog

If you accidentally delete a branch or lose track of it, you can use `git reflog` to recover it. Here’s how you can do it:

1. **View Reflog**: Run `git reflog` to see a list of all recent actions, including branch checkouts, commits, and resets.

2. **Identify the Commit**: Look through the reflog entries to find the commit where the branch was last present. Note the commit hash associated with that entry.

3. **Create a New Branch**: Once you have identified the commit hash, you can create a new branch pointing to that commit. Use `git checkout -b <new-branch-name> <commit-hash>` (This is the same as doing `git checkout <commit-hash>` and then doing `git checkout -b <new-branch-name>`)

   Replace `<new-branch-name>` with the desired name for your recovered branch and `<commit-hash>` with the hash you noted from the reflog.

By following these steps, you can effectively recover a lost branch using the reflog.

---

### Resets

1. `git reset --soft`

   - **Effect on Commit History**: Moves the HEAD (the current branch) to the specified commit without changing the working directory or the staging area.
   - **Staging Area**: All changes between the current commit and the target commit remain staged.
   - **Working Directory**: Files in your working directory remain unchanged.
   - **Use Case**: Use this when you want to undo a commit but keep the changes staged for a new commit.

2. `git reset --mixed` (Default)

   - **Effect on Commit History**: Moves the HEAD to the specified commit, just like --soft.
   - **Staging Area**: All changes between the current commit and the target commit are unstaged.
   - **Working Directory**: Files in your working directory remain unchanged.
   - **Use Case**: Use this when you want to undo a commit and unstage the changes, but keep the changes in the working directory.

3. `git reset --hard`

   - **Effect on Commit History**: Moves the HEAD to the specified commit, discarding all changes.
   - **Staging Area**: The staging area is reset to match the specified commit.
   - **Working Directory**: The working directory is also reset to match the specified commit, meaning any uncommitted changes are lost.
   - **Use Case**: Use this when you want to completely discard all changes after a certain commit and reset everything to a clean state.
