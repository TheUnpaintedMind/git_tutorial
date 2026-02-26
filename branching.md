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





<<[Previous Chapter(GitHub)](github.md) &emsp;[Next Chapter(Branching and Merging)](branching.md)>>
