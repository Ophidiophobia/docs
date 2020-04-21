# Github

Github is one possible way to host git repositories. Lots of projects use it and so you will likely have to use it too.

Assumptions:
 - upstream: source of the project without write/commit access
 - origin: copy/fork of the project with write/commit access

# Fork a project

Use Github's website to fork the project and then use the following script:
* 'git clone --depth=1' only downloads the recent revision.
  - \+ saves bandwith
  - \- no local changelog history before that revision
  - \- will not fetch branches ( solved )
* if you need to look up older history then look up about `git fetch`

```
GH_USER="Ophidiophobia"
GH_EMAIL="sandstrahl700@gmx.de"
GH_PROJECT="https://github.com/void-linux/void-packages.git"
GH_PROJECTNAME=`basename $GH_PROJECT`

git clone --depth=1 git@github.com:$GH_USER/$GH_PROJECTNAME
# restore working with remote branches
git config --local remote.origin.fetch "+refs/heads/*:refs/remotes/origin/*"

git config --local user.name $GH_USER
git config --local user.email $GH_EMAIL
git remote add upstream $GH_PROJECT
```

# Fetch upstream changes (the nice way)
```
git fetch upstream
git checkout master
git pull upstream master
git push origin master
```

# Create a new branch
```
git branch $BRANCH
git checkout $BRANCH
```

# Switch branch
```
git checkout $BRANCH
```

# Push a change to a branch on origin
```
git push origin $BRANCH
```

# Delete a branch
```
# delete the branch on origin
git push -d origin $BRANCH
# delete the local branch
git branch -d $BRANCH
```

# Fetch upstream changes (the hard way)
**This may delete any local changes in the local git dir.** If you have any important changes then back up them now!

```
git fetch upstream
git checkout master
git rebase upstream/master
git push -f origin master
```

