# Void Linux Packages

## Prepare branch
```
BRANCH=good_name_for_branch

git fetch upstream
git checkout master
git pull upstream master
git push origin master

git branch $BRANCH
git checkout $BRANCH
```

## Commit the change for PR

Example message: `megatools: update to 1.10.3 fixes #20820`
```
# check what changed
git status
git add -A
git status

git fetch upstream
git pull upstream master
git commit -m "$MSG"
git push origin $BRANCH
```

## Apply corrections
```
# check what changed
git status
git add -A
git status

git commit --ammend
git push origin $BRANCH
```

## Cleanup after PR is accepted
```
# delete the branch on origin
git push -d origin $BRANCH
# delete the local branch
git branch -d $BRANCH
```
