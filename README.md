# Welcome Git Fundamental Command Lines 

##  1. Git Clone

## 1. Git Clone
	 Command: git clone <repo> <directory>
Clone the repository located at `<repo>` into the folder called \<directory> on the local machine.

	Example: git clone https://github.com/PhongLE1411/gitfundamental.git C:\Github\gitfundamental

## 2. Git Branch
### 2.1- Create branch
	Command: git branch <branch_name>
Create a new branch called `<branch_name>`. This does _not_ check out the new branch.
			
	Example: git branch development
### 2.2- Delete locally branch
	Command: git -d <branch_name>
Delete the specified branch. This is a “safe” operation in that Git prevents you from deleting the branch if it has unmerged changes.
			
	Example: git branch -d hotfix
Delete **hotfix** branch.

	Command: git  branch -D <branch_name>
Force delete the specified branch, even if it has unmerged changes. This is the command to use if you want to permanently throw away all of the commits associated with a particular line of development.

	Example: git branch -D hotfix
Delete **hotfix**  branch
### 2.3- Delete remotely branch
	Command: git push origin --delete <branch_name>
Delete a remote branch

	Example: git push origin --delete hotfix	

**hotfix** branch will be deleted on remote.
