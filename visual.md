
<<[Previous Chapter(Setup Git)](setup.md) &emsp;[Next Chapter(Branches in Git)](b&m.md)>>

# Visualising Git + Git Fundamentals 
*There are numerous ways to visualise changes in files using Git, here are some of them given below :-*

### Using VS Code
Suppose we make changes to file1 and file2, after clicking on version control in VSCode, we can see our previous and our current file

<img width="1582" height="361" alt="image" src="https://github.com/user-attachments/assets/519a3a9f-da86-4bbf-8e22-b01fc8d92635" />
<br>
Here the green side represents our current file and the red side represents our file before we made changes.
<br>
<br>

* To stage any file for commit that is to add a file, just press the + icon besides the file name in VS Code File Explorer
* To add all files of the folder just click on + icon besides the folder name

<img width="300" height="218" alt="image" src="https://github.com/user-attachments/assets/3d9eafeb-2a9f-408f-938b-ec99acde4356" />

### Working Area & Staging Area
It is that area which contains files that are not being added for tracking(staged for commits), basically if we make changes to a file and not add it, then it exists inside the working area. Whereas files staged for commits are kept in a staging area.

<img width="292" height="120" alt="image" src="https://github.com/user-attachments/assets/d8ee1056-ad4c-47a6-aa00-65699842a48f" />

<br>
Here Changes denotes the Working Area where only modified unstaged files are stored and Staged Changes denotes the area where files from Changes have been added for making commits/versions.

### Example of how Git works 
Now suppose the file is inside Staging Area, is there any way for it to be inside Working Area also ?

<img width="1237" height="234" alt="image" src="https://github.com/user-attachments/assets/efdc953c-5905-4fdb-9ed5-ebee2100e2a7" />

Well the above image is very real and it basically implies that Git works by tracking changes and doesn't care where the file should be located. Since file2 was already staged, making another change will again put it inside the Working Area since the Staged Version became its previous version.  
<br>
Now if one wanted to unstage changes, just click on the - icon besides the desired file in the Staging Area

<img width="307" height="183" alt="image" src="https://github.com/user-attachments/assets/44ce4ce3-f382-4f6f-a2b4-0b0505369a3f" />
<br>
Similar logic is applied if whole folder(all files of the folder) has to be unstaged.

### Unstaging Files
To unstage files ie to remove them from the Staging Area, we use the following command 
```powershell
git reset filename
```
To unstage all files of the folder use 
```powershell
git reset .
```
Suppose we reset file2.cpp, it gets removed from the Staging Area and gets added back to the Working Area
```powershell
Unstaged changes after reset:
M       file1.cpp
M       file2.cpp
```

### Reset changes made to files in Working Area
If we bymistakenly made a change to our file and didn't add it using git add, using the following command undo's those changes, (.) is used to undo all file's changes.
```powershell
git checkout -- filename
git checkout .
```
To see all commits/versions, use the following command 
```powershell
git log --all
git log --all --graph
```

### Going back to different versions
The key difference between Google Docs and Git is that the former automatically creates versions of our file based on changed while for the latter we have to manually add those changes using Git commands such as add, commit, push etc.

Now assume we have Version 1 of our file and we make changes and add its second and third versions.
<img width="661" height="191" alt="image" src="https://github.com/user-attachments/assets/7069a128-cbaf-4d09-9f4b-d831468c1ff6" />

Let's get a list of all versions upto the current one, we can do this using 
```powershell
git log --all
```
<img width="511" height="235" alt="image" src="https://github.com/user-attachments/assets/25777c4a-369e-4225-b261-67557639a8c7" />

<br>
<br>

Suppose we want to see version 2 of this file, in order to do so, we need the commit hash of that version, so we use

<br>
<br>

<img width="517" height="249" alt="image" src="https://github.com/user-attachments/assets/2c123aee-6c9c-4411-acf1-6e88a6e26d76" />

<br>

<img width="516" height="288" alt="image" src="https://github.com/user-attachments/assets/62b6a450-9c2c-41db-8f94-204eaff9e496" />

<br>

**After using git log, press q to exit and keep typing normally inside the terminal**

<br> 
From above, we can see that we are in the detached head state, Head is basically a pointer to the most recent commit in the commit history, since we are currently in the second version of our file our Head is still pointing to version 2 but our master branch (which is the name of the default branch) master being a movable pointer points to most recent version of our file irrespective of the position of head.

### Adding a commit before the master branch
Now suppose we checked out to a commit preceding the master branch and made a commit ?

<img width="1106" height="649" alt="image" src="https://github.com/user-attachments/assets/225bf951-25e8-4d82-9586-868e45caddb0" />

<br><br>
Now if one wants to make a commit , since the history of the master branch did not have this commit ,hence this commit will be branched off. This occurs because Git can't have "version 1 updated" and "version 2" both in the same position inside master branch's history. Hence as a result, a different branch is created.

Now to return back to the master branch, we use the following command 
```powershell
git checkout master
```

<img width="520" height="318" alt="image" src="https://github.com/user-attachments/assets/492cf49e-c49e-405e-a2f2-d077c01a403b" />

<br><br>

Using git log again, we don't see our updated version 1 commit since it wasn't a part of our master branch's history, git still stores it in memory.

<img width="504" height="246" alt="image" src="https://github.com/user-attachments/assets/b5795d19-19d0-4570-8cfa-51e00c3ed409" />

### Restore the previous version of a file similar to google docs

Now instead of actually checkout out to a previous commit, we can restore the contents of a file to that version by using the following command 

```powershell
git checkout <commithash> filename.ext
```

<img width="527" height="311" alt="image" src="https://github.com/user-attachments/assets/5736423f-ddfe-4487-a1ec-c98cec16088a" />

<br>
If we don't want those changes , then we can simply unstage it and then remove it from the working area

```powershell
git reset filename.ext
git checkout -- filename.ext
```


  


