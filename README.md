# Git Overview
Git is the most popular version control system in the world. It records changes made to our code over time in a database called a repository. We can look at the project history and see changes made. If something got messed up in the changes, we can revert our project to an earlier state. This is powerful as we can track our history and work together with others.

**Using Git**
-----------------
There are multiple ways we can use git.
- Command line
- Code editors & IDE (Ex: VS Code GitLens)
- Graphical user interfaces (Ex: GirKraken, SourceTree)

**Global Settings**
----------------
GUI tools have limitations. GUI tools are not always available hence the use of a command line.

- ```git config --global user.name "My Name"```
  - Setting the default user name 
- ```git config --global user.email myemail@gmail.com```
  - Setting the default email
- ```git config --global core.editor "code --wait"```
  - Setting the default editor (we use VS code in this example), wait flag tells the terminal window to wait until we close the new VS code instance
- ```git config --global -e```
  - These configuration settings are stored in a txt file, we can edit that file using our default editor with this command
- ```git config --global core.autocrlf true```
  - A command used to change how Git handles line endings (for windows). In window devices, lines end with a carriage returns and line feed. This command makes it so git removes the carriage return character. This is helpful for working with other people with different operating systems.
- ```git config --global core.autocrlf input```
  - A command used to change how Git handles line endings (for linux or mac). If carriage return is accidentally added to end of lines, git will remove it with this command.
- ```git config --global diff.tool vscode```
  - Set VS Code to be our default diff tool.
- ```git config --global difftool.vscode.cmd "code --wait --diff $LOCAL $REMOTE"```
  - Tell git how to launch VS Code.

**Creating a Directory**
-------------------
- ```mkdir myProject```
  - Making a directory/folder called myProject 
- ```cd myProject```
  - Going into the folder
- ```git init```
  - Initializing the repository
- ```open .git```
  - Open the git repository where information about our project history is stored. You usually don't need to touch this.

**Git Workflow**
----------------------
When working on projects, we modify files. When the project reaches a state we want to record, we commit those changes to our repository (repo). Creating a commit is like creating a snapshot of our repo. There is a step in the middle called a staging. 

Staging is where we propose something for the next commit. When we're done making changes, we add the modified files to the staging area, review our changes, and then make a commit once we're satisfied. The staging step allows us to review our work before we commit it. If there are parts we decide we no longer want to commit, we can unstage it and commit it later.

<p align="center">
<img src="https://user-images.githubusercontent.com/100814612/169715462-b978ada9-0eb9-4774-8cfa-18fce18d34d1.png"  width = "620", height = "441"><img>
</p>

**Commit**
------------------
A commit contains information on the unique id (revision number), message/edit, date, time, author, and a complete snapshot. Git stores the full content which allows us to quickly restore to a previous snapshot.

**Commands**
------------------
- ```git status```
  - To see the status of the working directory and the staging area.
- ```git status -s```
  - Short summary of changes.
- ```git add file1 file2```
  - Add specific files to the staging area
- ```git add *.txt```
  - Add all .txt files to the staging area
- ```git add.```
  - Adds the entire directory recursively.
- ```git commit -m "Initial commit."```
  - Commit the changes. The "-m" sends for message.
- ```git commit```
  - If you want to add a longer message.

**Skipping the Staging Area (Index Area)**
-------------
It is possible to skip the staging area step. Only do this if you are 100% sure that your code and changes don't need to be reviewed.

- ```git commit -a -m "Fixed a bug"```
  - Commit all modified files.
- ```git commit -am "Fixed a bug"```
  - Same as the command above.

**Removing files**
-------------
- ```git rm file2.txt```
  - Remove the file from both the working directory and the staging area.
- ```git ls-files```
  - To see the files in our staging area.

**Renaming Files**
-------------
- ```git mv main.js file1.js```
  - Rename the file main.js to file1.js. Applied to both the working directory and staging area.

**Ignoring Files**
-----------------
- ```echo logs/ > .gitignore```
  - Create a file called .gitignore
- ```code .gitignore```
  - Open the file with VS Code
The code below is how the file .gitignore could be formatted. "logs/" indicates a directory named logs. We can list any files and directories we want to ignore in file file.
```
logs/
main.log
*.log
bin/
debug/
```
- ```git add .gitignore```
  - Add the file to our staging area
- ```git commit -m "Add gitignore"```
  - Commit
- ```git rm --cached -r bin/```
  - Remove bin folder from the staging area. "-r" allows recursive removal and "--cached" means remove only from the staging area.

**Viewing the Staged and Unstaged Changes**
--------------
- ```git diff --staged```
  - See what we have in the staging area that will go to the next commit. Comparing old copies with the newer copies.
- ```git diff```
  - See changes in our working directory that are not staged yet.
- ```git difftool```
  - Launch our visual diff tool. Compare working directory with what we have in our staging area.
- ```git difftool --staged```
  - Launch our visual diff tool. To look at state changes.

  **Viewing History**
- ```git log```
  - Shows all the commits we have created. Sorted from the lastest to the earliest. Each commit has a unique identifier, authoer, date/time of commit, and branches.
  - To go through commit pages, press space. To quit, press q.
- ```git log --oneline```
  - Short summary of the commits.
- ```git log --oneline --reverse```
  - Reverse order of the short summary of the commits.

**Viewing a Commit**
---------------
- ```git show 7e3f```
  - Referencing a commit.
- ```git show HEAD```
  - Show the last commit
- ```git show HEAD~1```
  - Show the commit that is one step back from the head.
- ```git show HEAD~1:bin/log.txt```
  - Show the exact file that is stored in the commit that was made one step back from the head.
- ```git ls-tree HEAD~1```
  - List all the files in the tree.
- ```git show bafb8```
  - If you have an object's unique identifier, you can view it by using this command. Replace "bafb8" with the unique identifier.

**Unstaging a File**
-------------------
- ```git restore --staged file1```
  - Unstage file1. Git takes the last copy of file1 from the last snapshot and puts it in the staging area.
  - If you restore a file that does not previously exist in a previous commit, git will remove the file from the staging area and take it back to its previous state.

**Discarding Local Changes**
--------------
- ```git restore file1```
  - Git takes file1 from our next environment and copy it into our working directory.
- ```git clean -fd```
  - Forcibly remove untracked files (also removes untracked whole directories).

**Restoring a File to a Previous Version**
---------------------
- ```git restore --source=HEAD~1 file1```
  - Restore file1 that is located one step back from the head.

**Other Commands**
------------------
- ```git checkout master```
  - Switch to mater branch
- ```git pull origin master```
  - Fetches all the code from the remote repo and merges it to the master branch.
- ```git checkout -b testing```
  - Create a new branch called testing.
- ```git add .```
- ```git commit -m "Added files"```
- ```git push origin testing```
  - Pushes the testing branch
- Creating a pull request
  - Putting a request that we want to merge the testing branch into the master branch.

**Checkout**
-----------
The git checkout command lets you navigate between the branches created by git branch. Checking out a branch updates the files in the working directory to match the version stored in that branch, and it tells Git to record all new commits on that branch. Think of it as a way to select which line of development you’re working on.

**Pull**
---------
You can think of git pull as Git's version of svn update. It’s an easy way to synchronize your local repository with upstream changes. The following diagram explains each step of the pulling process.

**Git fetch**
-----------------
The git fetch command imports commits from a remote repository into your local repo. The resulting commits are stored as remote branches instead of the normal local branches that we’ve been working with. This gives you a chance to review changes before integrating them into your copy of the project.

# Sourcetree Overview
Sourcetree is a git GUI that offers a visual representation of your repositories that can be obtained from [here](https://www.sourcetreeapp.com/). This section will go over the basics of using it. I will skip over cloning a repository as the steps for that can vary. In the following examples, I will be using a project called Encryption-Testing.

**Layout**
------------
Here is an example of how sourcetree looks. On the top we have our basic functions: commit, pull, push, fetch, branch, and merge.
<p align="center">
<img src="https://user-images.githubusercontent.com/100814612/171548581-368269aa-fa55-497e-bb4c-fb8596543df8.png" width = "850", height = "558"><img>
</p>

**Stage and Commit**
-------------
If we make any changes, we can go ahead and stage our file by going to the file status tab under workspace. Then we can stage the file by pressing the "+" icon on the right of the file or pressing stage all if you wish to stage all the files.

<p align="center">
<img src="https://user-images.githubusercontent.com/100814612/171549146-b91ce95a-a3ab-4d3f-bd76-551cd3972517.png" width = "600", height = "544"><img>
</p>

After staging the file we can press commit on the top left to bring up the commit menu on the bottom. Inside of the textbox we can add in our commit description. Additionally, if there are any files you wish for sourcetree to ignore, you can right click and press on ignore (the file will be added to the gitignore file).
<p align="center">
<img src="https://user-images.githubusercontent.com/100814612/171549608-0e02c1c5-8f09-4f45-a21a-bca32f50b58d.png" width = "850", height = "558"><img>
</p>

**Creating a Branch and Merging**
-------------
To create a new branch we press on the branch button on the top toolbar.

<p align="center">
<img src="https://user-images.githubusercontent.com/100814612/171776519-96ccf53d-b859-4875-b22b-629defd93f98.png"><img>
</p>

A new menu pops up where we can name our branch and decide whether we want to check it out or not. We can also specify which commit we want to branch from (working copy parent is the latest commit).

<p align="center">
<img src="https://user-images.githubusercontent.com/100814612/171776661-d1930009-873d-4826-90a4-0ea1972244c6.png"><img>
</p>

On the left we can see that we have switched to our new branch.

<p align="center">
<img src="https://user-images.githubusercontent.com/100814612/171776866-01e4ef2f-716e-4024-89c9-e8b18c9e9464.png"><img>
</p>

**Deleting a Branch**
-----------------
To delete a branch, we have to first make sure we're not on the branch. We can switch to another branch by double clicking on it or right click and selecting checkout. Them to delete the branch, we right click and press on delete.

<p align="center">
<img src="https://user-images.githubusercontent.com/100814612/171777140-8f339349-d193-4bd3-886d-22502e894f6d.png"><img>
</p>

**Merging a Branch**
-----------------
First you want to make sure you're checked in to the master branch or whatever branch you want to merge your target branch into. Next you want to press on merge. A menu will pop up and you get to choose which branch to merge in.
<p align="center">
<img src="https://user-images.githubusercontent.com/100814612/171778561-ed18d5ee-e0df-4c1a-a6bf-8aeb30ba2fcd.png"><img>
</p>

**Push & Pull Request**
-----------------------
After we commit any changes, we can go ahead and push them to our repo by pushing on push.

<p align="center">
<img src="https://user-images.githubusercontent.com/100814612/171778989-c7cc4628-16c0-4229-b0e0-e37d8ab62659.png"><img>
</p>

After we press on push, a new menu pops up. In this menu we can select which branches to push to our repository.

<p align="center">
<img src="https://user-images.githubusercontent.com/100814612/171779011-f4a3a2d4-053a-4f96-9a95-d3ee00a95e11.png"><img>
</p>

Now if we want to pull updates from our repository to our local machine, we can press on the pull button.
<p align="center">
<img src="https://user-images.githubusercontent.com/100814612/171779197-bd95e69b-7ec1-4b08-ac48-fa4d8e5e1a53.png"><img>
</p>

The opposite of pulling would be creating a pull request. A pull request (merge request) is an event that takes place in software development when a contributor/developer is ready to begin the process of merging new code changes with the main project repository. To create one, we right click on the branch we want to create a pull request on and press create pull request.

<p align="center">
<img src="https://user-images.githubusercontent.com/100814612/171779706-1fced305-2fef-4fe1-a3d9-252ee1b66f5b.png"><img>
</p>

