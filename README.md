Markdown [Cheat](https://www.markdownguide.org/basic-syntax/#images-1)

## What is Linux 
- Free open source operating system
- Used for stability , performance , security and flexibility
- Accessed through a *Command-line interface* or *CLI*

## What do production support do?
- Provide L1/L2 support to application in production.
- Create and manage incident request in production environment
- Handles releases and devops support for the production.

## Linux File System
Linux file system store drives and date in a hierarchal tree-like structure.
The *"/"* directory is the root of the file system, that contains all the directory and files of the system.
- Naming rules: only use alphanumeric characters, periods, underscores and hyphens
- `find`: command to search for files in directories.

### Permissions
Files and folders are defined by rights
- *read* - allow the user to display the file or content
- *write* - allow the user to edit the file
- *execute* - allow the user to execute the script
Commands to manage permissions
- `chmod`: change read/write/execute permission on the file
- `chown`: change the owner of the file
- `sudo`: used to switch to admin level and can change files and folders owned by root.

## Linux Commands
Commands are programs executed by the shell. The General Syntax looks like this : command [-options][arguments]
- E.g *ls -l filename* (This is a command that list the contents of a directory)
- `pwd`: Shows the current working directory
- `ls`: lists the files and directory in the current working directory
- `cd`: Change directory
- `man`: Displays information about a command 
- `~`: represents the user home folder
- Tapping up arrow will show the previous commands
- *Ctrl + q* will create a new command shell.
- `history`: Show the previous commands executed on the command shell.
- `uname -a`: Shows all the details about the computer system.

### Special operators
- `|`: pipe operator, use to execute new commands using the previous command output
- `>`: output operator, use to redirect the command output into a file
- `<`: input operator, redirect the command input from a file.

### Absolute and Relative Path
Absolute path is the full specific path to a file or directory.
- E.g: */home/ec2/directory/file*
Relative path is a path that is taken relevant to the current directory.
- E.g I'm in EC2 directory so i would take */directory/file* to open the file in directory.

### Managing Files and Directories
- `touch`: creates an empty file
- `rm`: removes a file
- `mkdir`: create a directory 
- `rmdir` : remove a directory
- `mv`: move a file or directory to somewhere else
- `cp`: copy a file
- `scp` copy a file between servers
- `cat`: used to open files , stands for concatenate
- `head`: displays the head or the first lines of the file
- `tail`: displays the last lines of the file
- `less/more` : displays files one line at a time
- `grep` : search for a pattern

## Git Commands
Whenever you create a repository, ALWAYS RUN THESE COMMANDS.
- `git clone <repo_url>` (clones the repo)
- `sudo yum list installed` (checks what packages are installed)
- `sudo yum install git` (install a package in this case, git)
- `git config --global user.name "username"`
- `git config --global user.email "email@domain.com` (set up git credentials)

## VIM
Vim is a file editor for Linux, it has 2 modes: *Edit* and *Vi*
- `vi <filename>`: Create or open a file to edit.
- Tap *I* in Vi to enter the Insert mode to edit the file.
- `:set number`: displays the line number 
To delete a line, you can either:
- Select a line and press the *D* key twice to delete the entire line
- `%d`: will delete all the lines in the file.
To quit the vi editor and save the file:
- Press *ESC* key and use `:x!`
You can use Substitiue command to search and replace words within the text files. The syntax for search and replace : %s/pattern/replace/g
- `%s`: short for substitute and initate the command
- *pattern* is for the word that you want to replace
- *replace* what you want to replace the pattern with
- *g* : apply globally , so all the words will be replaced

## Linux Exercise - Basic Command
1) Run a command to find your current location on the server.
`pwd`
2) Change directory from your current location to */var/log*
`cd /var/log`
3) Go back up a directory
`cd ..`
4) Find your current location again
`pwd`
5) List all the files in the current directory
`ls`
6) Now list all the files with the long listing
`ls -l`
7) Now list all the files with the long listing in reverse order, with the newest appearing at the bottom of the screen
`ls -ltr`
8) Change to root directory
`cd /`
9) Change back to your home directory
`cd ~`
10) Go up a level in directory structure
`cd ..`
11) Find out more information about the *ls* command
`man ls`
12) Go back to */var*
`cd /var`
13) Show the contents of this directory with details reverse sorted by size
`du -h --max-depth=0 * | sort -hr`
14) Find out the hardware version you are running
`uname -i`

