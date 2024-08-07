# git helper

Content :
- <a href="#adding-git-global-items">ADDING GIT GLOBAL ITEMS</a>
- <a href="#pushing-existing-folder-to-github-or-gitlab">PUSHING EXISTING FOLDER TO GITHUB OR GITLAB</a>
- <a href="#pushing-existing-folder-to-github-or-gitlab">PUSHING EXISTING GIT REPO TO NEW GIT REPO</a>
- <a href="#revert-back-modified-file">Revert back Modified File</a>
- <a href="#if-you-have-added-git-add--from-terminal-by-mistake-and-want-them-to-move-them-back-to-uncommited-state">if you have added `git add .` from terminal by mistake and want them to move them back to uncommited state</a>
- <a href="#usefull-gitignore-templates">USEFULL GITIGNORE TEMPLATES </a>
- <a href="#remove-local-untracked-files-from-the-current-git-branch">REMOVE LOCAL UNTRACKED FILES FROM THE CURRENT GIT BRANCH</a>
- <a href="#alias-in-git">Alias in git</a>


### ADDING GIT GLOBAL ITEMS
```
git config --global user.name "Vishal Gupta"
git config --global user.email "EMAIL_ADDRESS"
git config --global commit.template /Users/vishal.gupta/Documents/code/.gitmessage
git config --global core.editor "/Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl -n -w" // for mac
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

#### revert back single file to source

```
 git restore --source origin/dev <filename>
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

### change  Author for the Very Last Commit
```
git commit --amend --author="John Doe <john@doe.org>"
```

### Pick any commit from commit id
check your commit id for ex. asgsdfsdfsdfsd
```
git cherry-pick asgsdfsdfsdfsd

```


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




<details>
<summary><strong>Graphs</strong> examples </summary>

## Graph Examples 
```mermaid
   stateDiagram-v2
        State1 : plain text message
        block1 : plain text block 1
        block2 : plain text block 2
        block3 : plain text block 3

        State1 --> block1
        State1 --> block2
        State1 --> block3
    
        enkey1: Encyption Key
        enkey2: Encyption Key
        enkey3: Encyption Key

        encyptionAlgo : Encyption Algorithim
        encyptionAlgo2 : Encyption Algorithim
        encyptionAlgo3 : Encyption Algorithim


        state block1 {
            plaintext1 --> encyptionAlgo
            enkey1 --> encyptionAlgo 
            encyptionAlgo --> cipherBlock1
        }

        state block2 {
            plaintext2 --> encyptionAlgo2
            enkey2 --> encyptionAlgo2
            encyptionAlgo2 --> cipherBlock2
        }

        state block3 {
            plaintext3 --> encyptionAlgo3
            enkey3 --> encyptionAlgo3
            encyptionAlgo3 --> cipherBlock3
        }

        State2 : cipher message
        block1 --> State2
        block2 --> State2
        block3 --> State2

```

```mermaid
        stateDiagram-v2
        State1 : plain text message
        block1 : plain text block 1
        block2 : plain text block 2
        block3 : plain text block 3

        State1 --> block1
        State1 --> block2
        State1 --> block3
    
        enkey1: Encyption Key
        enkey2: Encyption Key
        enkey3: Encyption Key

        encyptionAlgo : Encyption Algorithim
        encyptionAlgo2 : Encyption Algorithim
        encyptionAlgo3 : Encyption Algorithim


        state block1 {
            plaintext1 --> xor
            iv --> xor
            xor --> encyptionAlgo
            enkey1 --> encyptionAlgo 
            encyptionAlgo --> cipherBlock1
        }

        state block2 {
            plaintext2 --> xor1
            block1 --> xor1
            xor1 --> encyptionAlgo2
            enkey2 --> encyptionAlgo2
            encyptionAlgo2 --> cipherBlock2
        }

        state block3 {
            plaintext3 --> xor2
            block2 --> xor2
            xor2 --> encyptionAlgo3
            enkey3 --> encyptionAlgo3
            encyptionAlgo3 --> cipherBlock3
        }

        State2 : cipher message
     
        block1 --> block2
        block2 --> block3
        block3 --> State2


        
```
---
</details>


### GITK
if in mac os , `gitk --all` is not working then use ` brew install git-gui`


