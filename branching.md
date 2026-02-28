<<[Previous Chapter(GitHub)](github.md) &emsp;[Next Chapter(Branching and Merging)](branching.md)>>

### Branching
Suppose we are working on a feature of a project and while working on it, we want to keep adding bug fixes to it without affecting the features.

Hence we can create a feature branch which contains the feature that we want to add and our main branch can have bugfixes added to it, we can create our feature branch using the following command
``` bash
git branch <branchname>
```
After creating a new branch say "feature1", our git log looks like this
``` bash
PS>git log --all --graph --oneline --decorate
* 4b991b3 (HEAD -> main, origin/main, origin/HEAD, feature1) Update branching.md
* eaf510b Create branching.md
```

In order to actually start adding changes and making commits, we need to actually checkout to our feature1 branch, we can do that as follows
``` bash
git checkout feature1
git log --all --graph --decorate --oneline
```
**Git log**
``` bash
PS>git log --all --oneline --decorate --graph
* c59bb28 (HEAD -> feature1, origin/feature1) feature1
* 4b991b3 (origin/main, origin/HEAD, main) Update branching.md

```
Here our HEAD points to the current branch which is feature1, and since we didn't yet push this branch, the remote tracking branch origin/feature1 is also pointing to the same commit, if we had pushed earlier and made a new commit, then we would see that everytime we make a commit, origin/feature1 lags behing HEAD since we have to update the remote tracking branch using git push

Now suppose while adding features, we wanted to add bugfixes to our main branch, to do that we just have to checkout to the main or master branch using
``` bash
git checkout main
```
Now after making commits and pushing them our graph kinda looks like this
``` bash
PS>git log --all --graph --decorate --oneline
* 9bdd380 (HEAD -> main, origin/main, origin/HEAD) BUGFIX
| * f93414c (origin/feature1, feature1) feature2
| * c59bb28 feature1
|/
* 4b991b3 Update branching.md
* eaf510b Create branching.md
```
Since features 1 and 2 weren't a part of main branch's history hence they were branched out.

### Merging 
Now suppose we need to combine all our changes in different branches into a single change, such as actually implementing those features into our main branch which also contains bug fixes, hence we require merging of those branches into one single branch, we have two options and git doesn't require any specific order of merging.
We can either merge main branch into feature branch or merge feature branch into main branch, either ways we are going to merge the changes caused by both branches.

Suppose i have an html file, i have a "main/master" branch and i want to create another branch for adding features say "feature" branch, to create a new branch type
``` bash
git branch <branch_name>
```
Now my main branch contains the following code which has a bugfix
``` html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <p>This paragraph represents file - 1</p>
    <p>BUGFIX</p>
</body>
</html>  

```
And feature branch contains added features
``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <p>This paragraph represents file - 1</p>
    <p>BUGFIX</p>
    <p>Feature-1</p>
</body>
</html>
```
Now we want to add both these branches and merge them into a single branch, suppose we want to merge feature with main, we do the following
``` bash
git checkout main
git merge feature
```
Our merge file looks as follows 
``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <p>This paragraph represents file - 1</p>
    <p>BUGFIX</p>
    <p>Feature-1</p>
</body>
</html>
```
Since we added feature-1 to line 11 and no changes were done to line 11 in main branch, we could merge without any conflicts, but what if we added feature-2 and in feature branch added feature-3 in the same line of a file.

So in main and feature branch respectively code is shown as follows

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <p>Feature-2</p>
</body>
</html>
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <p>Feature-3</p>
</body>
</html>
```

Now since git doesn't understand if it should keep main or feature branch's changes, hence we have a merge conflict, there are 3 ways to resolve a merge conflict
1. **Manual way -** After merging we end up with a merge conflict and git opens our file with changes from both the branches showing as follows
   
   <img width="1006" height="441" alt="image" src="https://github.com/user-attachments/assets/768f5e57-d4e7-45af-9de9-49afc304bfcd" />
   <br>
   <br>
   1.1) If we want to keep main branch's changes, just erase the code written for feature branch along with the arrow('>','<') and equality('===') markers<br>
   1.2) If we want to keep feature branch's changes, just erase the code written for main branch and erase markers and arrows<br>
   1.3) If we wish to keep both branch changes then just erase the markers manually<br>
2. **Using Merge Editor -** We can also open the merge editor, the merge editor looks as follows

   <img width="1035" height="471" alt="image" src="https://github.com/user-attachments/assets/81966847-9acf-4f5c-a9c1-1075531a2728" />
   <br>
   <br>
   2.1) If we want to keep main branch's changes, just click on the tick mark along main branch's changes and click complete merge<br>
   2.2) If we want to keep feature branch's changes, just click on the tick mark along feature branch's changes and click complete merge<br>
   2.3) If we wish to keep both branch changes then just click on both tick marks in the order you want your main and feature code to appear and then click complete merge<br>
3. **Using git commands(only 1 order for both changes) -** We can also use the git commands as follows<br>
   3.1) If we want to keep main branch's changes then type the following command, it will discard changes of the feature branch<br>
   ```bash
   git merge -X ours feature
   ```
   3.2) If we want to keep feature branch's changes then type the following command, it will discard changes of main branch<br>
   ```bash
   git merge -X theirs feature
   ```
   3.3) If we want to keep both changes, then we can use 'union' which only keeps the changes of current branch (main) first and then the incoming branch (feature)<br>
   ```bash
   git merge -X union feature
   ```
   

   
   















<<[Previous Chapter(GitHub)](github.md) &emsp;[Next Chapter(Branching and Merging)](branching.md)>>
