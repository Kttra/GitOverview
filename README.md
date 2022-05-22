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

- git config --global user.name "My Name"
  - Setting the default user name 
- git config --global user.email myemail@gmail.com
  - Setting the default email
- git config --global core.editor "code --wait"
  - Setting the default editor (we use VS code in this example), wait flag tells the terminal window to wait until we close the new VS code instance
- git config --global -e
  - These configuration settings are stored in a txt file, we can edit that file using our default editor with this command
