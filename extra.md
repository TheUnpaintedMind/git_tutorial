<<[Previous Chapter(Setup Git)](visual.md) &emsp;[Next Chapter(Branches in Git)](b&m.md)>>

# Replicate Google Docs feature
*Suppose we checkout to an earlier commit, make changes to it and want our new commit to be on top of the master commit,
we can achieve this by using rebase and then calling master to point to where HEAD is pointing.*


**One can use the following command if they don't want to show their author and date/time of making a commit**

```powershell
git log --oneline --decorate --all
```

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

<img width="498" height="136" alt="image" src="https://github.com/user-attachments/assets/ea770b15-8f7e-4d9e-9e66-aa4ef325c2fa" />

<br>
Now here HEAD and master both point to the same commit, but if we make a commit then master will move ahead of HEAD
