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

Now to effectively add the GitHub repo to our folder and began uploading files to it, go to your git folder's path and use the following command. Note that we can give any name to our remote repository not just "origin". But first of all copy the https link to our GitHub repo and paste it as follows
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
git remote remove <reponame>
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
Type "git push origin master" and after that, on Windows/Linux a login window might open and the user can login to their GitHub account, for Mac you would be prompted to enter your password of GitHub account. Refresh the page and you will see that our local repo is uploaded successfully to GitHub!
<br><br>

<img width="686" height="333" alt="image" src="https://github.com/user-attachments/assets/97b119f6-8761-437f-a31f-1dd3ea81c4ea" />

<<[Previous Chapter(Miscellaneous Features)](extra.md) &emsp;[Next Chapter(GitHub)](github.md)>>

### What if git push didn't work ?

So if git push didn't authenticate us , there are several ways to fix this issue 

1. Check that you are using HTTP and not SSH or any other method, to verify this, use the following command

   <img width="526" height="43" alt="image" src="https://github.com/user-attachments/assets/94476cdd-8b71-478a-8fe8-db23c4d61692" />

   <br>
   Now remove the remote repo and again add it using the HTTP link
   <br>
   
   <img width="514" height="40" alt="image" src="https://github.com/user-attachments/assets/8df9cf1f-4731-4eae-a97d-8b74e6799124" />

   <br>
   
2. Make sure that git config was used
<br>

<img width="1087" height="50" alt="image" src="https://github.com/user-attachments/assets/1358cfdb-b694-49a7-93ca-67c2db63fd1e" />

3. Copy your git URL and then paste your username
   <br>

   <img width="1086" height="57" alt="image" src="https://github.com/user-attachments/assets/9d5a62aa-27eb-42ee-aff8-3f8dba982cb4" />

   <br>
   Here there is an '@' after the username 'supersimpledev-test2'

4. If none of the above steps work then , we began creating a Personal Access Token (PAT) :-

   * Go to Settings/Developer Settings/Personal Access Tokens
   * Click on create new token and confirm access
   * Enter the name for your token
   * In scopes, select repo and click generate token
   * Copy the token and store it inside a safe place, you can't access it after going out of the page
   * Now go to terminal and again type git push origin master, when it asks for password, just paste your token to authenticate yourself

5. If that also didn't work then our last resort is to use SSH keys

   **MAC**
   
   1. Go to GitHub set up SSH key
      
      <img width="1546" height="441" alt="image" src="https://github.com/user-attachments/assets/e9ea070b-01f2-427e-8071-71075b4dfabc" />

      <br>
      <br>
      
      * First we check if we have existing SSH keys, hence go to terminal and type the following command

      ```zsh
      ls -al ~/.ssh
      ```
      Check if you have any of the files shown below starting from id
      
      <img width="1476" height="788" alt="image" src="https://github.com/user-attachments/assets/e9e888bc-7f23-4b80-b830-fb5bf0ac3616" />

      <br>
      <br>

   2. Go to Github add SSH keys
      
      * If we don't have SSH keys then we need to generate them , copy paste the following command on your terminal and replace the given email with your GitHub email id

        ```zsh
        ssh-keygen -t ed25519 -C "your_email@example.com"
        ```

        When it asks some additional detials, click enter to skip them and create your passphrase(password) after doing these steps, we need to add our key to ssh agent

   3. Add SSH keys to SSH-agent

      * Now copy paste the following command in terminal
        ```zsh
        $ eval "$(ssh-agent -s)"
        ```
        
        You will get agent pid as an output

      * Type the following touch command
        ```zsh
        touch ~/.ssh/config
        ```
      * Now since we created our ~/.ssh/config file, we need to open it using the following command
        ```zsh
        ~/.ssh/config
        ```
      * Copy and paste the following command in the config file which opens after using the previous command
        ```
           Host github.com
           AddKeysToAgent yes
           UseKeychain yes
           IdentityFile ~/.ssh/id_ed25519
        ```
        
      Click on the add SSH key to GitHub account

   4. Add SSH to GitHub account

      * Copy and paste the following command to the terminal
        ```zsh
        pbcopy < ~/.ssh/id_ed25519.pub
        ```
      * Go to settings/SSH and GPG keys, on SSH keys click on new SSH key, give it a name and in the key section just click on paste since the previous command copies all contents of the file
      * After that click on add SSH key and enter your password when prompted

   **Windows**

   1. Go to PowerShell and type the following command and check if we don't have any of the files in the output

      <img width="1370" height="695" alt="image" src="https://github.com/user-attachments/assets/3d2b9d18-5c7d-4805-ba19-f52c48347571" />
      <br>
      <br>
      Now if we saw any of those files, then it means that we already have an SSH key and need to add it to SSH agent, if not the follow this step
      
   3. Now type the following command, click enter for default configurations and type your passphrase
      
      <img width="1101" height="90" alt="image" src="https://github.com/user-attachments/assets/15090f14-fed0-4f7c-a5b6-ee2d583a3e6b" />
      <br>
      <br>
   4. Go to Services and click on OpenSSH Authentication Agent, make the following changes , click on apply and then start

      <img width="504" height="374" alt="image" src="https://github.com/user-attachments/assets/4750d1a2-b2e3-4adf-b566-0464c1a5c021" />
      <br>
      <br>

   5. Now for our final step, use the following command

      <img width="1112" height="146" alt="image" src="https://github.com/user-attachments/assets/2198b2ab-5a49-4c0a-968b-767817a90d34" />

   6. Now type the following command in the terminal and copy the contents of the notepad file

      <img width="747" height="37" alt="image" src="https://github.com/user-attachments/assets/ea85696e-b79f-4c84-87cf-8125c7183cd2" />
      <br>
      <br>
   7. Now go to Settings/SSH and GPG keys and similarly name your SSH and paste the contents into key section, then click add SSH key and confirm passphrase/password when prompted.


### Using SSH keys

* Go to terminal/powershell and change directory to the git repo folder
* Now type the following command to check our repo URL
  ```
  git remote -v
  ```
* Since the URL is an HTTP URL, hence we need to change it to git URL, hence we need to remove our HTTP
  ```
  git remote remove origin
  ```
* Now go to your GitHub repo and copy the SSH link and paste it as follows
  ```
  git remote add origin <SSH_LINK>
  ```

* Now open your git folder in a code editor and make changes, then type these following commands to finally push these changes to the GitHub repository
  ```
  git add .;git commit -m <commit_msg>;git push origin master
  ```
**Note - Here angular brackets are used as a placeholder to place data rather than typing it explicitly, for example if the name of my branch was main instead of master then for the following command main should be entered inplace of the angular brackets**
```
git push origin <branch_name>
```



      

        


   

