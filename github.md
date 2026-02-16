<<[Previous Chapter(Miscellaneous Features)](extra.md) &emsp;[Next Chapter(GitHub)](github.md)>>

# GitHub
*Suppose one day we don't have our device to store and manage files, so since we have a different device right now it would be better if there was a global entity from which we can access our files irrespective of any device. So GitHub is this global backup which stores repositories/files/folders and can be accessed anywhere.*

### Steps to create a GitHub repository

1. Create a GitHub account by going to the official [GitHub](https://github.com) website
2. After creating new account, sign in and create a new repository
   
   <img width="678" height="406" alt="image" src="https://github.com/user-attachments/assets/23aaa34f-37a5-442a-994e-28e84370a9ec" />

   <br>
   Now click on new repository as shown below 
   <br>

   <img width="698" height="221" alt="image" src="https://github.com/user-attachments/assets/07451780-6935-4da5-9e67-04cc0ab1e922" />

  <br>
  
3. Give the name, description of the repository and click create , so whenever we mention local repository we are referring to the repos on our computer and global/remote basically refers to files/folders on GitHub.

### Add remote repository 

Now to effectively add the GitHub repo to our folder and began uploading files to it, go to your git folder's path and use the following command. But first of all copy the https link to our GitHub repo and paste it as follows
<br><br>

<img width="654" height="102" alt="image" src="https://github.com/user-attachments/assets/dc354943-6c95-41c2-95dd-c251b53d0741" />

<br><br>

<img width="520" height="101" alt="image" src="https://github.com/user-attachments/assets/8d5e0bac-585f-40cd-952b-eb7a3a0bd449" />

<br><br>
The above is verified using "git remote", to get more details use the -v(verbose) flag

<img width="506" height="55" alt="image" src="https://github.com/user-attachments/assets/ce7ac085-ccf8-4d84-b483-76989de554ff" />

<br><br>

### Remove remote repository
To remove the remote repository just use 
```powershell
git remote <reponame>
```

<br>

<img width="498" height="55" alt="image" src="https://github.com/user-attachments/assets/c4db77e8-ada5-47a4-9d79-12a1ae36640e" />

<br><br>
Here our repo name was origin and hence we removed it. To add it back again use the previous command


### Configuring and using GitHub
In order to upload/download things from our remote repo, we must authenticate through GitHub our credentials like username 
<br><br>

<img width="510" height="31" alt="image" src="https://github.com/user-attachments/assets/0d7caee2-a5b7-4810-a37e-cd0f7cfc2bbc" />

<br><br>
Type "git push origin master" and after that, on Windows/Linux a login window might open and the user can login to their GitHub account, for Mac you would be prompted to enter your password of GitHub account.Refresh the page and you will see that our local repo is uploaded successfully to GitHub!
<br><br>

<img width="686" height="333" alt="image" src="https://github.com/user-attachments/assets/97b119f6-8761-437f-a31f-1dd3ea81c4ea" />

<<[Previous Chapter(Miscellaneous Features)](extra.md) &emsp;[Next Chapter(GitHub)](github.md)>>






   

