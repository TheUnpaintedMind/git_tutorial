# Git Setup
*It is important to create two files say file1 & file2 of any language(can even be text files) which can be said to be version 1 and version 2 respectively. Create and store these files inside a folder say "git_folder"*

In file 1 :-
```cpp
#include <bits/stdc++.h>
using namespace std;
int main(){
    cout<<"This is file 1!";
    cout<<"\nVersion 1";
}
```
In file 2 :-
```cpp
#include <bits/stdc++.h>
using namespace std;
int main(){
    cout<<"This is file 2!";
    cout<<"\nVersion 2";
}
```


### Setting up path to the folder:-

#### Windows

```powershell
cd C:\Users\YourName\Desktop\git_folder
```

#### Mac

```zsh
cd ~/Desktop/git_folder
```

#### Linux

```bash
cd ~/Desktop/git_folder
```
### Setup Git inside a folder:-

1) To setup git inside the folder, open command line inside that folder and type the following command:
   <br>
   ```powershell
   git init
   ```
   **git init** - basically initialises our folder/repository as a git repository implying that git is now tracking all the changes in our files inside our folder.
   <br><br>
2) After initialising our Git folder, we now check the state of our folder since its previous commit/version :
   <br><br>
   **commit/version** - a commit or version is a saved state/snapshot of a specific state of the folder. So initially if we had 3 lines inside our file and we changed it to 2 lines, then this state of our file will be the current version of our file and the one having 3 lines will be the previous version of the file.

3) To check the current state of our folder, we use the following command :-
   <br>
   ```powershell
   git status
   ```
   <br><br>
   **It gives us the following output :-**
   ```
   On branch master

    No commits yet
    
    Untracked files:
      (use "git add <file>..." to include in what will be committed)
            file1.cpp
            file2.cpp
            out.exe

    nothing added to commit but untracked files present (use "git add" to track)
   ```
   
4) To add a file with extension ext for tracking changes, we can use the following command :-
   <br>
   ```powershell
   git add file.ext
   ```
   
   <br>

   To add a folder, git add will track all files and subfolders of the given folder :-
   
   ```powershell
   git add dir1
   ```
    To add all files of a folder, the following command is used :-

   ```powershell
   git add .
   ```
   
5) Before making commits using git command, it is important to properly configure credentials so that git can associate our credentials with our git folder :-

   <br>
   
   ```powershell
   git config --global user.email "useremail@email.com"
   git config --global user.name "username"
   ```
6) Now we can finally make a version/commit using the following command :-
   <br>
   ```powershell
   git commit -m "added all files"
   ```
   <br><br>

   Following will be displayed on the command line :-

   ```
    2 files changed, 12 insertions(+)
     create mode 100644 file1.cpp
     create mode 100644 file2.cpp
   ```

   Here -m **flag**(used to modify the behaviour of a command) is used to type a message for our commit. If we don't specify -m flag then a text editor automatically opens up. Click on insert key and began typing your commit, to exit the editor press escape and write ":wq" (write and quit) inside the editor.

    <br>

    **Now one has to follow some rules for writing commit messages inside the text editor.**
   <br>
   
   The widely accepted convention for Git commit messages, known as the "50/72 rule", recommends the following lengths     for commit messages written in a text editor:
   
    * Subject line: Limit to 50 characters or less. The subject should be a short, concise summary of the change, written     in the imperative mood (e.g., "Fix bug", not "Fixed bug").
    * Body text: The body should be separated from the subject by a single blank line and each line in the body should be     wrapped at 72 characters. This convention improves readability in various command-line tools and interfaces.
    * Overall length: The body can span multiple paragraphs or use bullet points to provide as much detail as necessary,as long as lines are wrapped appropriately. 
<br>

**If one doesn't want to create a new version, they can make changes to the current version by using the following flag**

```powershell
git commit -m "same commit" --amend
```
<br>
Here the amend flag overwrites the topmost(current) commit and adds our message to it instead of creating another commit on top of this.







