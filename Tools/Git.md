# Git
## Branches
```bash
# Squash
git rebase -i HEAD~<number of commits on the branch, after the fork>
git commit --amend
git push --force-with-lease

# Rebase (from the branch)
git checkout my_branch
git rebase master
git push --force-with-lease

# Merge (from master)
git checkout master
git merge my_branch
git push
```
## Tips
```bash
# Nice log graph, with age and author
git log --pretty=format:'%C(auto)%h%d%C(reset) \"%s\" %C(yellow)%ar by %an' --graph --all -30
```
