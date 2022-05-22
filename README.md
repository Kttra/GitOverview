# Git Info
Git is the most popular version control system in the world. It records changes made to our code over time in a database called a repository. We can look at the project history and see changes made. If something got messed up in the changes, we can revert our project to an earlier state. This is powerful as we can track our history and work together with others.

**Using Git**
-----------------
There are multiple ways we can use git.
- Command line
- Code editors & IDE (Ex: VS Code GitLens)
- Graphical user interfaces (Ex: GirKraken, SourceTree)

**Command Line**
----------------
Why is command line the most popular? GUI tools have limitations. GUI tools are not always available.

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
