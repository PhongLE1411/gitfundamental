# Welcome Git Fundamental

## 1. What is Git
	Command: git clone <repo> <directory>
Clone the repository located at `<repo>` into the folder called \<directory> on the local machine. 

	Example: git clone https://github.com/PhongLE1411/gitfundamental.git C:\Github\gitfundamental
 

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
### 1.2 Flow
The basic Git workflow goes something like this:
 - You modify files in your working directory.
 - You stage the files, adding snapshots of them to your staging area.
 - You do a commit, which takes the files as they are in the staging
   area and stores that snapshot permanently to your Git directory.
- Finally you push your local repository to the remote repository.

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/flow.png)
### 1.3 File status life circle
Remember that each file in your working directory can be in one of two states:  _tracked_  or  _untracked_. Tracked files are files that were in the last snapshot; they can be unmodified, modified, or staged. In short, tracked files are files that Git knows about.

Untracked files are everything else — any files in your working directory that were not in your last snapshot and are not in your staging area. When you first clone a repository, all of your files will be tracked and unmodified because Git just checked them out and you haven’t edited anything.

As you edit files, Git sees them as modified, because you’ve changed them since your last commit. As you work, you selectively stage these modified files and then commit all those staged changes, and the cycle repeats.

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/lifecycle.png)

## 2. Clone Repository
	Command: git clone  <repo> <directory>

Clone the repository located at `<repo>` into the folder called `~<directory>!` on the local machine.
		
	Example: git clone https://github.com/PhongLE1411/gitfundamental.git "C:\Github"

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/repo_clone.png)

## 3. Create Branch
	Command: git branch <branch_name>
Create a new branch called `<branch_name>`. This does _not_ check out the new branch.

	Command: git checkout -b <new_branch_name>
The above example simultaneously creates and checks out `<new-branch>`. The `-b` option is a convenience flag that tells Git to run `git branch <new-branch>` before running `git checkout <new-branch>`.

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/branch_master.png)

	Example: git branch hotfix
![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/branch_hotfix.png)

	Example: git checkout -b hotfix
![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/branch_hotfix2.png)	
## 4. Delete Branch
### 4.1 Delete local branch
	Command: git -d <branch_name>
Delete the specified branch. This is a “safe” operation in that Git prevents you from deleting the branch if it has unmerged changes.
			
	Example: git branch -d hotfix
Delete `<hotfix>` branch.

	Command: git  branch -D <branch_name>
Force delete the specified branch, even if it has unmerged changes. This is the command to use if you want to permanently throw away all of the commits associated with a particular line of development.

	Example: git branch -D hotfix
Delete `<hotfix>`  branch
### 4.2 Delete remote branch
	Command: git push origin --delete <branch_name>
Delete a remote branch

	Example: git push origin --delete hotfix	

`<hotfix>` branch will be deleted on remote.

## 5. Checkout Branch
	Command: git checkout <branch_name>
Switch to other branch.

	Example: git checkout hotfix
Switch to `<hotfix>` branch.

Note : Please make sure you pull all remote branches into you local. To do that run command:

	git fetch --all
## 6. Git Add & Commit
The git commit command captures a snapshot of the project's currently staged changes. Committed snapshots can be thought of as “safe” versions of a project—Git will never change them unless you explicitly ask it to. Prior to the execution of git commit, The git add command is used to promote or 'stage' changes to the project that will be stored in a commit. These two commands git commit and git add are two of the most frequently used.

	Command: 	git add <file or directory>
If you want to add all files/directories. You can use `git add -A`

	Command: git commit -am <your message>

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/repo_current.png)

After commit

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/repo_add.png)

## 7. Git Push
The git push command is used to upload local repository content to a remote repository. Pushing is how you transfer commits from your local repository to a remote repo.
	
	Command: git push
If you want to push your code but you don't care the remote repo has change or not. You can use `git push -f`

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_push.png)

## 8. Git Fetch
The git fetch command downloads commits, files, and refs from a remote repository into your local repo. Fetching is what you do when you want to see what everybody else has been working on. It’s similar to svn update in that it lets you see how the central history has progressed, but it doesn’t force you to actually merge the changes into your repository

	Command: 	git fetch <remote>
Fetch all of the branches from the repository. This also downloads all of the required commits and files from the other repository.

	Command: git fetch <remote>  <branch>
Same as the above command, but only fetch the specified branch.

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_fetch.png)
## 9. Git Merge
`Git merge` will combine multiple sequences of commits into one unified history. In the most frequent use cases, `git merge` is used to combine two branches. The following examples in this document will focus on this branch merging pattern. In these scenarios, `git merge` takes two commit pointers, usually the branch tips, and will find a common base commit between them. Once Git finds a common base commit it will create a new "merge commit" that combines the changes of each queued merge commit sequence.

Before:

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_merge_before.png)

After:

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_merge.png)
## 10. Git Rebase
Rebasing is the process of moving or combining a sequence of commits to a new base commit. Rebasing is most useful and easily visualized in the context of a feature branching workflow.

	Command: git rebase <base>

Before:

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_rebase_before.png)

After:

![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_rebase.png)
## 11. Git Reset
On the commit-level, resetting is a way to move the tip of a branch to a different commit. This can be used to remove commits from the current branch

	Command: git reset head~<number>
	Example: git reset head~2
![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_reset.png)
## 12. Git Revert
Reverting undoes a commit by creating a new commit. 
This is a safe way to undo changes, as it has no chance of re-writing the commit history. For example, the following command will figure out the changes contained in the 2nd to last commit, create a new commit undoing those changes, and tack the new commit onto the existing project.

	Command: git revert head~<number>
	Example: git revert head~2
![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_revert.png)
## 13. Git Cherry-Pick
git cherry-pick is a useful tool but not always a best practice. Cherry picking can cause duplicate commits and many scenarios where cherry picking would work, traditional merges are preferred instead. With that said git cherry-pick is a handy tool for a few scenarios.

	Command: git cherry-pick <commit>
![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_cherrypick.png)
## 14. Git Squash
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
 To quite log history, please type `letter q`
 7. Finally, update to remote repo by using push command.
	`git push -f`
 8. Done!
![enter image description here](https://github.com/PhongLE1411/gitfundamental/blob/master/Images/git_squash.png)

## 15. Update latest source code from a branch to your branch.
When you create new branch (hotfix) from a branch (master), master branch has 5 versions at this time. After a few day, there are some branches are merged into master branch, it means the master version is different your branch version.
	Now, you want to be all versions of master are merged into your branch. You can use `rebase command`.Why do you you use `rebase` instead of `merge`. Because we want to be your branch versions is on the top of master version. For instance,  
	master branch: C0->C1->C2->C3->C4->C5->C6->C7
	your branch: C0->C1->C2->C3->C4->C5->C1'->C2'
After rebase, your branch will be:
C0->C1->C2->C3->C4->C5->C6->C7`->C1'->C2'`

Please following the below steps:

 1. Get latest source code which you want to rebase from (e.g.: master)
`git checkout master`
`git pull`
 2. Switch to your branch (e.g.: hotfix)
	`git checkout hotfix`
	`git pull`
 3. Start rebase from master to hotfix branch.
 NOTE: make sure that you are at your branch (hotfix branch). You can check by: `git branch` (your current branch is in green)
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

## 15. Checking the Status of Your Files
## 16. Git Clean  
