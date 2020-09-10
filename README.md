# githelper

#### if you have added `git add .` from terminal by mistake and want them to move them back to uncommited state..

```
git rm --cached -r .

```
#### want to add long message in commit type only below command

```
git commit 

```

#### create a new branch
```
git branch branch_name

```
#### switch to to other branch
```
git checkout branch_name
```

#### create a new branch and switch to other branch at same time 
```
git checkout -b branch_name
```

#### merge some branch to master branch 
```
git checkout master
git merge branch_name

```

#### Usefull gitignore templates
`url` : <https://github.com/github/gitignore>

#### ` Git Merge. You are in the middle of a merge. Cannot Amend.` or `You cannot merge there are conflicts`
```
      
        /o-----o---o--o-----o--------- branch
--o-o--A--o---o---o---o----o--o-o-o--- master
When you rebase you can move it like this:

                                   /o-----o---o--o-----o------ branch
--o-o--A--o---o---o---o----o--o-o-o master
```
> ..
```
git rebase
```
> First, rewinding head to replay your work on top of it...

> Applying: change name

> Using index info to reconstruct a base tree...

resolve conflicts

```
git rebase --continue

```
now you will see your branch is on top and problem is resolved.

