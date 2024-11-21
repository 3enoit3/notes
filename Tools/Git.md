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
git merge --ff-only my_branch
git push

# Delete
git branch -d my_branch # local
git push origin --delete my_branch # remote
```
## Configuration
```bash
git config --global push.default simple # default 'matching' may push other branches, particularly dangerous in case of forced push
```
## Tips
```bash
# Nice log graph, with age and author
git log --pretty=format:'%C(auto)%h%d%C(reset) \"%s\" %C(yellow)%ar by %an' --graph --all -30

# Get the changes of a commit in local
git cherry-pick --no-commit <changeset_id>

# Get a file of a commit in local
git show <changeset_id_or_branch>:<path_to_the_file> > <local_file_name>

# See only changed files of a commit
git show --name-only <changeset_id>

# Tell Git how to rebase
git rebase --onto <changeset_id_to_replay_on> <changeset_id_to_replay_from_not_included>
# this is useful when the parent branch has been squashed: git rebase --onto <new_squashed_changeset> <forking_changeset>

# See where is a commit
git branch --contains <changeset_id>

# See new files on branch
git diff --name-only --diff-filter=A develop.. -- .

# See diff ignoring identation and context
git diff -w -U0 --word-diff-regex='[^[:space:]]' -- .

# Find even a deleted file
git log --all --full-history -- <path-to-file>
```
## Tags
```bash
# Create tag
git tag <tagname>

# Push
git push origin <tagname>
```
## Remote
```bash
# See remotes
git remote -v

# Change remote for ssh
git remote set-url origin git@github.com:USERNAME/REPOSITORY.git
````
