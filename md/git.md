# git
```
# rename all commits with reset author
git rebase -r --root --exec "git commit --amend --no-edit --reset-author"

# rename commits up to certain commit 
git rebase -r <some commit before all of your bad commits> --exec 'git commit --amend --no-edit --reset-author'
```
