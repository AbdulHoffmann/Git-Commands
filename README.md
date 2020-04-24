Git Commands
============

## Translated Versions
- [Versão em português](READMEpt.md)

___

_A list of my commonly used Git commands_

*If you are interested in my Git aliases, have a look at my `.bash_profile`, found here: https://github.com/joshnh/bash_profile/blob/master/.bash_profile*

--

### Info
+ `HEAD` is the most recent commit on the branch I'm in currently.
+ There are three local stages: The **working directory** (or working tree) where the modified files go. When you stage them, they go to the **staging index**. When you commit staged changes they get promoted to the **commit history**.

### Getting & Creating Projects

| Command | Description |
| ------- | ----------- |
| `git init` | Initialize a local Git repository |
| `git clone ssh://git@github.com/[username]/[repository-name].git` | Create a local copy of a remote repository |

### Basic Snapshotting

| Command | Description |
| ------- | ----------- |
| `git status` | Check status |
| `git add [file-name.txt]` | Add a file to the staging area |
| `git add -A` | Add all new and changed files to the staging area |
| `git commit -m "[commit message]"` | Commit changes |
| `git rm -r [file-name.txt]` | Remove a file (or folder) |

### Branching & Merging

| Command | Description |
| ------- | ----------- |
| `git branch` | List branches (the asterisk denotes the current branch) |
| `git branch -a` | List all branches (local and remote) |
| `git branch [branch name]` | Create a new branch |
| `git branch -d [branch name]` | Delete a branch |
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git checkout -b [branch name]` | Create a new branch and switch to it |
| `git checkout -b [branch name] origin/[branch name]` | Clone a remote branch and switch to it |
| `git branch -m [old branch name] [new branch name]` | Rename a local branch |
| `git checkout [branch name]` | Switch to a branch |
| `git checkout -` | Switch to the branch last checked out |
| `git checkout -- [file-name.txt]` | Discard changes to a file |
| `git merge [branch name]` | Merge a branch into the active branch |
| `git merge [source branch] [target branch]` | Merge a branch into a target branch |
| `git cherry-pick [--no-commit] <commit>` | Used for picking a single commit from another branch. `--no-commit` will execute the cherry pick but instead of making a new commit it will move the contents of the target commit into the working directory of the current branch.[REFERENCE](https://www.atlassian.com/git/tutorials/cherry-pick) |

### Stash
| `git stash` | Stash changes in a dirty working directory. Same as `git stash push`. |
| `git stash apply <stash_id>` | Retrieves modifications from the stash without removing it from the stash |
| `git stash pop <stash_id>` | Retrieves modifications from the stash and removes it from the stash |
| `git stash list` | Lists all stashed entries |
| `git stash show [-p]` | Show the changes recorded in the stash entry as a diff between the stashed contents and the commit back when the stash entry was first created. `-p` shows the diff content. Optionally you can pass the stash id, e.g. stash@{2}, if the you are interested in an entry other than stash@{0}. |
| `git stash drop <stash_id>` | Drops a single entry from the stash |
| `git stash clear` | Remove all stashed entries |

### Sharing & Updating Projects

| Command | Description |
| ------- | ----------- |
| `git push origin [branch name]` | Push a branch to your remote repository |
| `git push -u origin [branch name]` | Push changes to remote repository (and remember the branch) |
| `git push` | Push changes to remote repository (remembered branch) |
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git pull` | Update local repository to the newest commit |
| `git pull origin [branch name]` | Pull changes from remote repository |
| `git remote add origin ssh://git@github.com/[username]/[repository-name].git` | Add a remote repository |
| `git remote set-url origin ssh://git@github.com/[username]/[repository-name].git` | Set a repository's origin branch to SSH |

### Inspection & Comparison

| Command | Description |
| ------- | ----------- |
| `git log` | View changes |
| `git log --summary` | View changes (detailed) |
| `git log --oneline` | View changes (briefly) |
| `git diff [source branch] [target branch]` | Preview changes before merging |

### Managing commit history (undoing)

| Command | Description |
| ------- | ----------- |
| `git reset [--soft\|mixed\|hard] <commit>` | `hard`: changes will be removed from the working directory and from the index, you will lose all modifications. `mixed`: keeps changes in the working directory but NOT in the index (i.e. files with discarded changes will show up as *untracked* ). `soft`: Git is instructed not to modify the files in the working directory or in the index at all (i.e. files with affected changes will show up as staged.) [REFERENCE1](https://www.atlassian.com/git/tutorials/undoing-changes/git-reset) [REFERENCE2](https://devconnected.com/how-to-undo-last-git-commit/) |
| `git revert <commit>` | The `git revert` command is slightly different from the `git reset` command because it will record a new commit with the changes introducted by reverting the last commit. Note also that with `git reset` you would specify 'HEAD~1' to undo the last commit because the reset command sets a new HEAD position while reverting actually reverts the commit specified. As a consequence, you will have to commit the changes again for the files to be reverted and for the commit to be undone. |
| `git revert [--no-commit] <commit>..<other_commit>` | Reverts a range of commits. The `--no-commit` flag lets git revert all the commits at once - otherwise you'll be prompted for a message for each commit in the range, littering your history with unnecessary new commits. |
| `git rebase [-i] <commit>` | Git rebase in standard mode will automatically take the commits in your current working branch and apply them to the head of the passed branch. Running git rebase with the -i flag begins an interactive rebasing session. Instead of blindly moving all of the commits to the new base, interactive rebasing gives you the opportunity to alter individual commits in the process. This lets you clean up history by removing, splitting, and altering an existing series of commits. `git rebase --abort` to cancel the rebase operation. [REFERENCE](https://www.atlassian.com/git/tutorials/rewriting-history/git-rebase) |

+ HEAD is the most recent commit in the current branch
+ HEAD~1 (or HEAD^): one commit before HEAD in the index
+ HEAD~2 (or HEAD^^): two commits before HEAD in the index
+ master~1 (or master^): notation can also be used aiming at branches names.

### Managing Stages

| Command | Description |
| ------- | ----------- |
| `git clean [-f] [-i] [-n] [-d] <filename>` | Remove untracked files and dirs (with -d flag) |
| `git checkout -- <filename>` | Remove unstaged modified file |
| `git checkout .` | Remove all unstaged modified files |
| `git restore [--source=<commit>] [--staged] [--worktree] <filename>` |  Restores files in the working tree from either the index or another commit. This command does not update your branch. The command can also be used to restore files in the index from another commit. [REFERENCE](https://stackoverflow.com/questions/58003030/what-is-git-restore-command-what-is-the-different-between-git-restore-and-git)|
| `git reset [--soft\|mixed\|hard] <commit_hash>` | Reset the state of the branch to the referenced commit hash. For managing stage purposes the commit is gonna always be HEAD. `hard` removes the modifications permanentely, `mixed` unstage them to the working tree, and `soft` resets everything to the stage index (more useful when used to commits other than HEAD)  [REFERENCE](https://www.atlassian.com/git/tutorials/undoing-changes/git-reset) |

+ HARD: The Commit History ref pointers are updated to the specified commit. Then, the Staging Index and Working Directory are reset to match that of the specified commit. Any previously pending changes to the Staging Index and the Working Directory gets reset to match the state of the Commit Tree. This means any pending work that was hanging out in the Staging Index and Working Directory will be lost.
+ MIXED: This is the default operating mode. The ref pointers are updated. The Staging Index is reset to the state of the specified commit. Any changes that have been undone from the Staging Index are moved to the Working Directory.

### Stages
![stages](./figures/stages.png)
![stages_2nd_view](./figures/remote_local.png)
