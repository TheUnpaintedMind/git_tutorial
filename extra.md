<<[Previous Chapter(Setup Git)](visual.md) &emsp;[Next Chapter(GitHub)](github.md)>>

# Replicate Google Docs feature
*Suppose we checkout to an earlier commit, make changes to it and want our new commit to be on top of the master commit,
we can achieve this by using rebase and then calling master to point to where HEAD is pointing.*


**One can use the following command if they don't want to show their author and date/time of making a commit**

```powershell
git log --oneline --decorate --all
```

<br>

<img width="409" height="124" alt="image" src="https://github.com/user-attachments/assets/b546bf2a-63a0-4c6c-8a0e-1a6389d609cb" />

<br>

See that HEAD is behind the master branch pointer, now what if i make a commit here ?

<br>

<img width="440" height="161" alt="image" src="https://github.com/user-attachments/assets/2e96c8bf-b126-4956-b56f-f7b182787daa" />

<br>

Just adding --graph to the previous command shows us the branching, now in Google Docs such commit will be on top of the master branch, to do the same in git, we use the following command

<br>

```powershell
git rebase master
```
**Just replace master with your branch name**

<br>

<img width="465" height="141" alt="image" src="https://github.com/user-attachments/assets/01f10e09-b75f-4f12-a9c3-1ad10453b290" />

<br>

Now we see that master is behind the HEAD so to make master point to the same commit as HEAD, we use

```powershell
git branch -f master HEAD
```

<br>

<img width="498" height="136" alt="image" src="https://github.com/user-attachments/assets/ea770b15-8f7e-4d9e-9e66-aa4ef325c2fa" />

<br>

Now here HEAD and master both point to the same commit, but if we make a commit then master will move ahead of HEAD so to make HEAD always point to master we use the following command 

```powershell
git checkout master
```
<br>

<img width="492" height="143" alt="image" src="https://github.com/user-attachments/assets/4de04331-36ce-4d8f-9f70-85a1bc1f1d6b" />

<br>

Here we can see that HEAD is pointing to master branch.

### Extra Features of Git

* **Aliases** : Suppose we want to use a shorter version of a git command, such as using "git s" instead of "git status". This can be achieved using the following command

  ```powershell
  git config --global alias.s "status"
  ```
  
  <img width="551" height="68" alt="image" src="https://github.com/user-attachments/assets/7541b81c-9cdb-4c98-80fb-6750a18661e3" />
  
  <br>
  
  Now here git s can be used for git status, similarly we can use aliases for any other git command provided that the alias is not already used as a git command.

* **Adding git ignore file** : Suppose there are some files that shouldn't be added to our repository, so to make sure that these files are not tracked by git we can add a .gitignore file which contains the names of our files that we don't want to add

  <img width="926" height="134" alt="image" src="https://github.com/user-attachments/assets/df8c1334-13b9-40be-a26c-ba9cbddf46a6" />

<br>

  <img width="583" height="104" alt="image" src="https://github.com/user-attachments/assets/228adc81-8f69-44ad-964b-a264dc2dfc58" />

  <br>
  <br>
  
  So here after doing git add and commit, git will track .gitignore file but since files inside gitignore aren't to be tracked, so git will not track files inside gitignore.


<br>

### Creating copy of our git folder

Now for future projects, just create a copy of your git folder and remove git repository & files as follows 

### Windows 

```powershell
Remove-Item -Path .git, .gitignore -Recurse -Force
```

### Mac & Linux
```bash
rm -rf .git .gitignore
```


