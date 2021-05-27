# git helper

### ADDING GIT GLOBAL ITEMS
```
git config --global user.name "Vishal Gupta"
git config --global user.email "EMAIL_ADDRESS"
```
### PUSHING EXISTING FOLDER TO GITHUB OR GITLAB
```
cd existing_folder
git init
git remote add origin REMOTE_URL
git add .
git commit -m "Initial commit"
git push -u origin master
```

### PUSHING EXISTING GIT REPO TO NEW GIT REPO
```
cd existing_repo
git remote rename origin my_old_origin
git remote add origin REMOTE_URL
git push -u origin --all
git push -u origin --tags

```
### Revert back Modified File
```git
git restore <Filename>
```

### if you have added `git add .` from terminal by mistake and want them to move them back to uncommited state..

```
git rm --cached -r .

or 

git reset HEAD^ -- path/to/file

```
### ADD LONG MESSAGES IN COMMIT 
it will open default editor to type
```
git commit 

```

### CREATE A BRANCH
```
git branch branch_name

```
### SWITCH TO TO OTHER BRANCH
```
git checkout branch_name
```

### CREATE A NEW BRANCH AND SWITCH TO OTHER BRANCH AT SAME TIME
```
git checkout -b branch_name
```

### MERGE SOME BRANCH TO MASTER BRANCH 
```
git checkout master
git merge branch_name

```
### The “fatal: refusing to merge unrelated histories” Git error
```
git pull origin master --allow-unrelated-histories
```

### USEFULL GITIGNORE TEMPLATES
`url` : <https://github.com/github/gitignore>

#### ` Git Merge. You are in the middle of a merge. Cannot Amend.` or `You cannot merge there are conflicts`
```
      
        /o-----o---o--o-----o--------- branch
--o-o--A--o---o---o---o----o--o-o-o--- master
When you rebase you can move it like this:

                                   /o-----o---o--o-----o------ branch
--o-o--A--o---o---o---o----o--o-o-o master
```
.
```
git rebase <branch_name>
```
First, rewinding head to replay your work on top of it...

Applying: change name

Using index info to reconstruct a base tree...

resolve conflicts

```
git rebase --continue

```
now you will see your branch is on top and problem is resolved.




### REMOVE LOCAL UNTRACKED FILES FROM THE CURRENT GIT BRANCH
see which files will be deleted 
```
git clean -n
```
then remove files
To remove directories, run `git clean -f -d` or `git clean -fd`
To remove ignored files, run `git clean -f -X` or `git clean -fX`
To remove ignored and non-ignored files, run `git clean -f -x` or `git clean -fx`



### CREATE AND APPLY PATCH
```
git diff > my.patch
or 
git diff {branch_name} > my.patch

```
apply patch
```
git apply --whitespace=warn my.patch
```

### STASH CHANGES
it will stash untracked files also

```git
git stash save -u "change name"
```
stash list
```
git stash list
```
apply stash

```
git stash apply stash@{number}
```

### Merge Commits into single commit
Lets assume we have two commits.. we need to merge them to one on branch "abc"
commit 1 : intiall commit
commit 2 : for review put commit

We need to merge both into single
```git
git rebase -i HEAD~2
```
Now it will ask for pick and squash commit
```git
pick 01d1124 Initall commit message
pick 6340aaa For Review put commit commit message

# Rebase 60709da..30e0ccb onto 60709da
#
# Commands:
#  p, pick = use commit
#  r, reword = use commit, but edit the commit message
#  e, edit = use commit, but stop for amending
#  s, squash = use commit, but meld into previous commit
#  f, fixup = like "squash", but discard this commit's log message
#  x, exec = run command (the rest of the line) using shell
#
# If you remove a line here THAT COMMIT WILL BE LOST.
# However, if you remove everything, the rebase will be aborted.
#
```
now we have to put squash which needs to merge 

```git
pick 01d1124 Initall commit message
squash 6340aaa For Review put commit commit message

```
Now it will merge into single commit


### Alias in git
you have to add this in .gitconfig file.
there are two options to add these
1) command line 
- windows: `git config --global alias.ci "commit -v"`
- Mac : `git config --global alias.ci 'commit -v'`

2) opening file
- windows : `C:\Users\ABC\.gitconfig`
- mac : `~/.gitconfig`

```

[mergetool "vsdiffmerge"]
	cmd = \"C:\\Program Files ......."
[alias]
	rdev = reset --hard origin/dev
	pd = pull origin dev
	ca = commit --amend
	com = commit
      	cb = checkout -b
      	co = checkout
      	ui = !gitk --all
```
Use: `git pd` or `git ui`
