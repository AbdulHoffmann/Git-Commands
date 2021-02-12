ALIASES & USEFUL COMMANDS
===

h3. Prune local branches against remote:
+ alias git-prune='git branch --merged | grep -v "\*" | grep -v "master" | grep -v "develop" | grep -v "staging" | xargs -n 1 git branch -d'
  
h3. Cleaning up old remote git branch references (The remote upstream/reference/tracking is still there while the branch itself has been deleted on the remote):
+ git fetch [remote_name] --prune [--dry-run]
+ git remote prune [remote_name]

> remote_name being usually `origin`
