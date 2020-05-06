# Welcome Git Fundamental
##### Table of Contents  
- [1. What is Git](#1-what-is-git)
- [2. How It Works](#2-how-it-works)
  * [2.1 State](#21-state)
  * [2.2 Flow](#22-flow)
  * [2.3 File status life circle](#23-file-status-life-circle)
- [3. Clone Repository](#3-clone-repository)
- [4. Create Branch](#4-create-branch)
- [5. Delete Branch](#5-delete-branch)
  * [5.1 Delete local branch](#51-delete-local-branch)
  * [5.2 Delete remote branch](#52-delete-remote-branch)  
- [6. Checkout Branch](#6-checkout-branch)
- [7. Git Add & Commit](#7-git-add--commit)
- [8. Git Push](#8-git-push)
- [9. Git Fetch](#9-git-fetch)
- [10. Git Merge](#10-git-merge)
- [11. Git Rebase](#11-git-rebase)
- [12. Git Reset](#12-git-reset)
- [13. Git Revert](#13-git-revert)
- [14. Git Cherry-Pick](#14-git-cherry-pick)
- [15. Git Squash](#15-git-squash)
- [16. Update latest source code from a branch to your branch](#16-update-latest-source-code-from-a-branch-to-your-branch)
- [17. Checking the Status of Your Files](#17-checking-the-status-of-your-files)
- [18. Clean Working Directory](#18-clean-working-directory)

## 1. What is Git			
 - A free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.
 - Developed in 2005 by Linus Torvalds, the famous creator of the Linux operating system kernel.
											 ![Git icon](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git.png)
## 2. How It Works
### 2.1 State
Git has three main states that your files can reside in: modified, staged, and committed:
 - Modified means that you have changed the file but have not committed it to your database yet.
 - Staged means that you have marked a modified file in its current version to go into your next commit snapshot.
 - Committed means that the data is safely stored in your local database.

This leads us to the three main sections of a Git project: the working directory(tree), the staging area, and the Git directory.
![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/three_states.png)

 - The working tree is a single checkout of one version of the project. These files are pulled out of the compressed database in the Git directory and placed on disk for you to use or modify.
 - The staging area is a file, generally contained in your Git directory, that stores information about what will go into your next commit. Its technical name in Git parlance is the “index”, but the phrase “staging area” works just as well.
 - The Git directory is where Git stores the metadata and object database for your project. This is the most important part of Git, and it is what is copied when you clone a repository from another computer.
### 2.2 Flow
The basic Git workflow goes something like this:
 - You modify files in your working directory.
 - You stage the files, adding snapshots of them to your staging area.
 - You do a commit, which takes the files as they are in the staging
   area and stores that snapshot permanently to your Git directory.
- Finally you push your local repository to the remote repository.

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/flow.png)
### 2.3 File status life circle
Remember that each file in your working directory can be in one of two states:  _tracked_  or  _untracked_. Tracked files are files that were in the last snapshot; they can be unmodified, modified, or staged. In short, tracked files are files that Git knows about.

Untracked files are everything else — any files in your working directory that were not in your last snapshot and are not in your staging area. When you first clone a repository, all of your files will be tracked and unmodified because Git just checked them out and you haven’t edited anything.

As you edit files, Git sees them as modified, because you’ve changed them since your last commit. As you work, you selectively stage these modified files and then commit all those staged changes, and the cycle repeats.

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/lifecycle.png)

## 3. Clone Repository
Command:
```diff
+ git clone  <repo> <directory>
```

Clone the repository located at `<repo>` into the folder called `~<directory>!` on the local machine.
		
	Example: git clone https://github.com/PhongLE1411/gitfundamental.git "C:\Github"

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/repo_clone.png)

## 4. Create Branch
	Command: git branch <branch_name>
Create a new branch called `<branch_name>`. This does _not_ check out the new branch.

	Command: git checkout -b <new_branch_name>
The above example simultaneously creates and checks out `<new-branch>`. The `-b` option is a convenience flag that tells Git to run `git branch <new-branch>` before running `git checkout <new-branch>`.

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/branch_master.png)

	Example: git branch hotfix
![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/branch_hotfix.png)

	Example: git checkout -b hotfix
![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/branch_hotfix2.png)	
## 5. Delete Branch
### 5.1 Delete local branch
	Command: git -d <branch_name>
Delete the specified branch. This is a “safe” operation in that Git prevents you from deleting the branch if it has unmerged changes.
			
	Example: git branch -d hotfix
Delete `<hotfix>` branch.

	Command: git  branch -D <branch_name>
Force delete the specified branch, even if it has unmerged changes. This is the command to use if you want to permanently throw away all of the commits associated with a particular line of development.

	Example: git branch -D hotfix
Delete `<hotfix>`  branch
### 5.2 Delete remote branch
	Command: git push origin --delete <branch_name>
Delete a remote branch

	Example: git push origin --delete hotfix	

`<hotfix>` branch will be deleted on remote.

## 6. Checkout Branch
	Command: git checkout <branch_name>
Switch to other branch.

	Example: git checkout hotfix
Switch to `<hotfix>` branch.

Note : Please make sure you pull all remote branches into you local. To do that run command:

	git fetch --all
## 7. Git Add & Commit
The git commit command captures a snapshot of the project's currently staged changes. Committed snapshots can be thought of as “safe” versions of a project—Git will never change them unless you explicitly ask it to. Prior to the execution of git commit, The git add command is used to promote or 'stage' changes to the project that will be stored in a commit. These two commands git commit and git add are two of the most frequently used.

	Command: 	git add <file or directory>
If you want to add all files/directories. You can use `git add -A`

	Command: git commit -am <your message>

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/repo_current.png)

After commit

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/repo_add.png)

## 8. Git Push
The git push command is used to upload local repository content to a remote repository. Pushing is how you transfer commits from your local repository to a remote repo.
	
	Command: git push
If you want to push your code but you don't care the remote repo has change or not. You can use `git push -f`

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_push.png)

## 9. Git Fetch
The git fetch command downloads commits, files, and refs from a remote repository into your local repo. Fetching is what you do when you want to see what everybody else has been working on. It’s similar to svn update in that it lets you see how the central history has progressed, but it doesn’t force you to actually merge the changes into your repository

	Command: 	git fetch <remote>
Fetch all of the branches from the repository. This also downloads all of the required commits and files from the other repository.

	Command: git fetch <remote>  <branch>
Same as the above command, but only fetch the specified branch.

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_fetch.png)
## 10. Git Merge
`Git merge` will combine multiple sequences of commits into one unified history. In the most frequent use cases, `git merge` is used to combine two branches. The following examples in this document will focus on this branch merging pattern. In these scenarios, `git merge` takes two commit pointers, usually the branch tips, and will find a common base commit between them. Once Git finds a common base commit it will create a new "merge commit" that combines the changes of each queued merge commit sequence.

Before:

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_merge_before.png)

After:

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_merge.png)
## 11. Git Rebase
Rebasing is the process of moving or combining a sequence of commits to a new base commit. Rebasing is most useful and easily visualized in the context of a feature branching workflow.

	Command: git rebase <base>

Before:

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_rebase_before.png)

After:

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_rebase.png)
## 12. Git Reset
On the commit-level, resetting is a way to move the tip of a branch to a different commit. This can be used to remove commits from the current branch

	Command: git reset head~<number>
	Example: git reset head~2
![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_reset.png)
## 13. Git Revert
Reverting undoes a commit by creating a new commit. 
This is a safe way to undo changes, as it has no chance of re-writing the commit history. For example, the following command will figure out the changes contained in the 2nd to last commit, create a new commit undoing those changes, and tack the new commit onto the existing project.

	Command: git revert head~<number>
	Example: git revert head~2
![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_revert.png)
## 14. Git Cherry-Pick
git cherry-pick is a useful tool but not always a best practice. Cherry picking can cause duplicate commits and many scenarios where cherry picking would work, traditional merges are preferred instead. With that said git cherry-pick is a handy tool for a few scenarios.

	Command: git cherry-pick <commit>
![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_cherrypick.png)
## 15. Git Squash
As normally, a branch will be created for each feature/user story. Also there are many commits in this branch.
	It is very hard to review for reviewer when you make pull request because they go through every commit to review. Now, you can squash these commits into one commit.

	Command: git rebase -i head~<number_of_commit>

Example: I would like to squash/merge 3 first commits into one commit.
![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_squash_step0.png)

 1. Step 1: Run this command: `git rebase -i head~3`
 2. Step 2: A dialog will be shown
 ![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_squash_step2.png)
 3. Step 3 Change `pick` to `squash` except the first line like this
![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_squash_step3.png)
 
 4. Save and close the dialog. Another dialog will be shown.
![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_squash_step4.png)

 Delete all messages except the first message. You can amend the first message if you like.
![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_squash_step4_2.png)

 Save and close the dialog.
 
 5. Check your log history now by using `git log`
![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_squash_step5.png)

 To quit log history, please type `letter q`
 
 7. Finally, update to remote repo by using push command.
	`git push -f`
 8. Done!
![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_squash.png)

## 16. Update latest source code from a branch to your branch
When you create new branch (hotfix) from a branch (master), master branch has 5 versions at this time. After a few day, there are some branches are merged into master branch, it means the master version is different your branch version.
	Now, you want to be all versions of master are merged into your branch. You can use `rebase command`.Why do you you use `rebase` instead of `merge`. Because we want to be your branch versions is on the top of master version. For instance,  you want to update latest source code of master branch for your branch (development branch).

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/update_before.png)

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/update_after.png)
	
Please following the below steps:

 1. Get latest source code which you want to rebase from (e.g.: master)
`git checkout master`
`git pull`
 2. Switch to your branch (e.g.: development)
	`git checkout development`
	`git pull`
 3. Start rebase from master to development branch.
 NOTE: make sure that you are at your branch (development branch). You can check by: `git branch` (your current branch is in green)
3.1. REBASE
`git rebase master`
If there are any conflicts. Please resolve them. You can resolve by manual or tool. In here, I use kdiff tool and use command to resolve.
3.2. Resolve conflicts
	3.2.1. `git mergetool`
	After that, there is a editor is shown, you must resolve. After they are resolved. Continue with next step.
	3.2.2. `git add -A`
	3.2.3. `git rebase --continue`
	If there are still some conflicts. Do again step 3.2.1 to 3.2.3 until there is no conflict.
 4. Check history after rebase.
 `git log`
 Note: If you want to exist log, type letter "q"
 5. If you make sure everything is good. Please push your rebase
 `git push -f`
 7. WELL DONE 

## 17. Checking the Status of Your Files
The main tool you use to determine which files are in which state is the git status command. If you run this command directly after a clone, you should see something like this:

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/f_status_clean.png)	 
	
Let’s say you add a new file to your project, a simple README file. If the file didn’t exist before, and you run git status, you see your untracked file like so:
![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/f_status_untracked.png)

In order to begin tracking a new file, you use the command git add. To begin tracking the README.txt file, you can run this:

	git add README.txt
	
If you run your status command again, you can see that your README file is now tracked and staged to be committed:
![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/f_status_tracked.png)

You can tell that it’s staged because it’s under the “Changes to be committed” heading.	
Let’s change a file that was already tracked. If you change a previously tracked file called README.md and then run your git status command again, you get something that looks like this:
![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/f_status_modified.png)	
	
The README.md file appears under a section named "Changes not staged for commit" - which means that a file that is tracked has been modified in the working directory but not yet staged. To stage it, you run the git add command. git add is a multipurpose command - you use it to begin tracking new files, to stage files, and to do other things like marking merge-conflicted files as resolved. It may be helpful to think of it more as "add precisely this content to the next commit" rather than “add this file to the project”. Let’s run git add now to stage the README.md file, and then run git status again:

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/f_status_modified_staged.png)	
	
Both files are staged and will go into your next commit. At this point, suppose you remember one little change that you want to make in README.md before you commit it. You open it again and make that change, and you’re ready to commit.

Now that your staging area is set up the way you want it, you can commit your changes. Remember that anything that is still unstaged - any files you have created or modified that you haven’t run git add on since you edited them - won’t go into this commit. They will stay as modified files on your disk. In this case, let’s say that the last time you ran git status, you saw that everything was staged, so you’re ready to commit your changes. The simplest way to commit is to type git commit and check status again.

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/f_status_commit.png)	
	
Now you’ve created your first commit! You can see that the commit has given you some output about itself: which branch you committed to (master), what SHA-1 checksum the commit has (463dc4f), how many files were changed, and statistics about lines added and removed in the commit.
	
If you want to be your change is commited to remote repo. Please run git push.
![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/f_status_push.png)

## 18. Clean Working Directory 
Sometimes, you want to clean your Working Directory, it means there is no unstaged files, modifed files in your Working Directory. You can run some commands below:

	git reset --hard
	git clean -f -d
