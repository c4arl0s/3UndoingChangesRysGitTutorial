# [go back to content](https://github.com/c4arl0s/RysGitTutorial#rys-git-tutorial)

# [3 Undoing Changes Rys Git Tutorial - Content](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#go-back-to-content)

1. [x] [1. Display Commit Checksums](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#-display-commit-checksums)
2. [x] [2. View an Old Version](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#-view-an-old-version)
3. [x] [3. View an Older Version](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#-view-an-older-version)
4. [x] [4. Return to current version](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#-return-to-current-version)
5. [x] [5. Tag a Release](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#-tag-a-release)
6. [x] [6. Try a Crazy Experiment](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#-try-a-crazy-experiment)
7. [x] [7. Stage and Commit the Snapshot](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#-stage-and-commit-the-snapshot)
8. [x] [8. View the Stable Commit](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#-view-the-stable-commit)
9. [x] [9. Undo Committed Changes](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#-undo-committed-changes-revert) (revert)
10. [x] [10. Start a Smaller Experiment](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#-start-a-smaller-experiment)
11. [x] [11. Undo Uncommitted Changes](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#-undo-committed-changes-revert)
12. [x] [12. Conclusion](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#-conclusion)
13. [x] [13. Quick References](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#-quick-references)
 
# [3 Undoing Changes](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#3-undoing-changes-rys-git-tutorial---content-1)

In the last module, we learned how to record versions of a project into a Git repositoru.
**The whole point of maintaining these "safe" copies is peace of mind: should our project suddenly break, we will know that we have easy access to a functional version, and we will be able to pinpoint precisely where the problem was introduced**.

To this end, storing "safe" versions is not much help without the ability to restore them. **Our next task is to learn how to view the previous states of a project, revert back to them, and reset uncommitted changes**.

# 	* [Display Commit Checksums](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#3-undoing-changes-rys-git-tutorial---content)

Quick review

```console
$ git log --oneline
```

output

```console
453c8a4 Add navigation links
1047951 t Add blue an orange html files
6a442fc Create index page for the message
```

git only outputs the first seven characters of the checksum.
These first few characters effectively serve as a unique `ID` for each commit.

# 	* [View an Old Version](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#3-undoing-changes-rys-git-tutorial---content)

```console
$ git checkout 1047951
```

output

```console
Note: switching to '1047951'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 1047951 t Add blue an orange html files
```

![Screen Shot 2020-05-22 at 17 19 07](https://user-images.githubusercontent.com/24994818/82713376-60964900-9c50-11ea-81a9-6f1b73ca260d.png)

# 	* [View an Older Version](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#3-undoing-changes-rys-git-tutorial---content)

```console
$ git checkout 6a442fc
```

output

```console
Previous HEAD position was 1047951 t Add blue an orange html files
HEAD is now at 6a442fc Create index page for the message
```

![Screen Shot 2020-05-22 at 17 37 35](https://user-images.githubusercontent.com/24994818/82714202-427e1800-9c53-11ea-8dbe-92ec1f95695b.png)

# 	* [Return to current version](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#3-undoing-changes-rys-git-tutorial---content)

```console
$ git checkout master
```

output

```console
Previous HEAD position was 6a442fc Create index page for the message
Switched to branch 'master'
```

![Screen Shot 2020-05-22 at 17 41 33](https://user-images.githubusercontent.com/24994818/82714291-8244ff80-9c53-11ea-9a67-7949b919670b.png)

# 	* [Tag a Release](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#3-undoing-changes-rys-git-tutorial---content)

```console
$ git tag -a v1.0 -m "Stable Version of the website"
```

print all tags

```console
$ git tag
v1.0
```
# 	* [Try a Crazy Experiment](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#3-undoing-changes-rys-git-tutorial---content)

create crazy.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>A Crazy Experiment</title>
  <meta charset="utf-8" />
</head>
<body>
  <h1>A Crazy Experiment</h1>
  <p>We're trying out a <span style="color: #F0F">crazy</span>
  <span style="color: #06C">experiment</span>!
    
  <p><a href="index.html">Return to home page</a></p>
</body>
</html>
```

# 	* [Stage and Commit the Snapshot](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#3-undoing-changes-rys-git-tutorial---content)

```console
$ git add crazy.html 
```

commit

```console
$ git commit -m "Add a crazzy experiment"
[master 12e24f0] Add a crazzy experiment
 1 file changed, 14 insertions(+)
 create mode 100644 crazy.html
```

status

```console
commit 12e24f0c4e03b3c991b287230548d8bdad3882d7
Author: c4arl0s <c.santiago.cruz@gmail.com>
Date:   Fri May 22 20:34:06 2020 -0500

    Add a crazzy experiment

commit 453c8a4db079c3d235e3470754a79a22ea0f0afd
Author: c4arl0s <c.santiago.cruz@gmail.com>
Date:   Fri May 22 16:53:53 2020 -0500

    Add navigation links

commit 1047951bab2636a3bc90682e48d9fb32644da036
Author: c4arl0s <c.santiago.cruz@gmail.com>
Date:   Fri May 22 13:45:14 2020 -0500

    t Add blue an orange html files

commit 6a442fcc4ab51362713f09ed5eadc7af767db833
Author: c4arl0s <c.santiago.cruz@gmail.com>
Date:   Fri May 22 12:54:21 2020 -0500

    Create index page for the message

```
# 	* [View the Stable Commit](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#3-undoing-changes-rys-git-tutorial---content)

```console
$ git checkout v1.0
```

output

```console
HEAD is now at 453c8a4 Add navigation links
```

go back to master

```console
$ git checkout master
```

output

```console
Previous HEAD position was 453c8a4 Add navigation links
Switched to branch 'master'
```
# 	* [Undo Committed Changes](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#3-undoing-changes-rys-git-tutorial---content) (revert)

**We are ready to restore our stable tag by removing the most recent commit**.
Make sure to change the 12e24f0 to the ID to the crazy experiment's commit before running the next command:

```console
$ git revert 12e24f0
```

This will show you the vim editor with the default message "Revert "Add a crazzy experiment"
Save and close

```console
$ git revert 12e24f0
Removing crazy.html
[master 3553479] Revert "Add a crazzy experiment"
 1 file changed, 14 deletions(-)
 delete mode 100644 crazy.html
```

git log

```console
$ git log --oneline
```

output

```console
3553479 Revert "Add a crazzy experiment"
12e24f0 Add a crazzy experiment
453c8a4 Add navigation links
1047951 t Add blue an orange html files
6a442fc Create index page for the message
```

1. Notice that instead of deleting the "crazzy experiment" commit, Git figures out how to undo the changes it contains, the tacks on another commit with the resulting content.
2. So, our fifth commit and our third commit represent the exact same snapshot, as shown below.
3. **Again, Git is designed to never lose history: the fourth snapshot is still accessible, just in case we want to continue developing it**.

![111040590-3c7f4080-83f9-11eb-8b73-18b1a252e613](https://user-images.githubusercontent.com/24994818/112473181-a4a41f80-8d33-11eb-8ce5-e7ff917a51b0.png)

**When using git revert, remember to specify the commit that you want to undo-- not the stable commit that you want to return to**.
It helps to think of this command as saying **"undo this commit"** rather than "restore this version"

# 	* [Start a Smaller Experiment](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#3-undoing-changes-rys-git-tutorial---content)

Let's try a smaller experiment this time.
Create dummy.html and leave it as a blank file.
Then, add a link in the "Navigation Section" of index.html so that it resembles the following.

```html
<h2>Navigation</h2>
<ul>
  <li style="color: #F90">
    <a href="orange.html">The Orange Page</a>
  </li>
  <li style="color: #00F">
	<a href="blue.html">The Blue Page</a>
 </li>
 <li>
  <a href="dummy.html">The Dummy Page</a>
  </li>
</ul>
```

In the next section, we are going to abandon this uncommitted experiment. But since the git revert command requires a commit ID to undo, we can't use the method discussed above.

# 	* [Undo Uncommitted Changes](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#3-undoing-changes-rys-git-tutorial---content)

Before we start undoing things, let's take a look at the status of our repository

```console
$ git status
```

output

```console
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   index.html

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	dummy.html

no changes added to commit (use "git add" and/or "git commit -a")
```

We have a tracked file and an untracked file that need to be changed. First, we will take care of index.html

```console
$ git reset --hard
```

output

```console
HEAD is now at 3553479 Revert "Add a crazzy experiment"
```

 instead of deleting the "crazzy experiment" This changes all tracked files to match the most recent commit. Note that the `--hard` flag is what actually updates the file.
Running git reset without any flags will simply unstage index.html, leaving its contents as is.

```console
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	dummy.html
```

In either case, git reset only operates on the working directory and the staging area, so our git log history remains unchanged.

* Next, let's remove the `dummy.html` file.
* Of course, we could manually delete it, but using Git to reset changes eliminates human errors when working with several files in large teams.
Run the following commands,

```console
$ git clean -f
Removing dummy.html
```

This will remove all untracked files. With dummy.html gone, git status should now tell us that we have a "clean" working directory, meaning our project matches the most recent commit.

```console
$ git status
On branch master
nothing to commit, working tree clean
```

**Be careful with git reset and git clean**. **Both operate on the working directory, not on the committed snapshots**.
Unlike git revert, they permanently undo changes, so make sure you really want to trash what you are working on before you use them.

	
# 	* [Conclusion](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#3-undoing-changes-rys-git-tutorial---content)

1. **It helps to think of this command as saying "undo this commit" rather than "restore this version"**.
2.  **When using git revert, remember to specify the commit that you want to undo -- not the stable commit that you want to return to**.

![Screen Shot 2020-05-23 at 7 46 49](https://user-images.githubusercontent.com/24994818/82731017-94618500-9cc9-11ea-9d20-5bb40446c1b3.png)

# 	* [Quick References](https://github.com/c4arl0s/3UndoingChangesRysGitTutorial#3-undoing-changes-rys-git-tutorial---content)

```console
$ git checkout commitID
```
View a previous commit.

```console
$ git tag -a tagName -m "description"
```
Create an annotated tag pointing to the most recent commit.

```console
$ git revert commitID
```
Undo the specified commit by applying a new commit.

```console
$ git reset --hard
```
Reset tracked files to match the most recent commit.

```console
$ git clean -f
```
Remove untracked files.

```console
$ git reset --hard / git clean -f
```
Permanently undo uncommitted changes.
