ALIASES & USEFUL COMMANDS
===

h3. Prune local branches against remote:
+ alias git-prune='git branch --merged | grep -v "\*" | grep -v "master" | grep -v "develop" | grep -v "staging" | xargs -n 1 git branch -d'
  
h3. Cleaning up old remote git branches (The remote upstream is still there while the branch has been deleted on the remote):
+ git fetch [remote-name] --prune [--dry-run]
+ git remote prune [remote-name]

> remote-name being usually `origin`
