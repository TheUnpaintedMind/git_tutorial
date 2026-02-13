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

### Windows

```powershell
cd C:\Users\YourName\Desktop\git_folder
```

### Mac

```zsh
cd ~/Desktop/git_folder
```

### Linux

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



