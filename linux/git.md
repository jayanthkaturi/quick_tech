```bash
git add folder_name/ file_name

git commit
git commit --amend ## amend to previous commit

git push
git push origin branch
git push origin +branch ## force update branch, in case of amended commits

## Git History
git reflog ## history of git commands
git reset [ref_number] ## go to a particular point in future

## Git upstream
git branch --set-upstream <remote-branch>
git branch --unset-upstream

## Update index
git update-index --assume-unchanged <path_to_file>
git update-index --no-assume-unchanged <path_to_file>

## Cherry pick sequence of commits
git cherry-pick A...B (cherry pick commits from A (excluded) to B)
git cherry-pick A^...B (cherry pick commits from A (included) to B)

## Git stashing
git stash
git stash clear | pop
git stash push <path_to_file>
git stash show <stash_number | stash{@1}>
```
