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

### if you have added `git add .` from terminal by mistake and want them to move them back to uncommited state..

```
git rm --cached -r .

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
git rebase
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

