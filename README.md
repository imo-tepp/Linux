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
- Linux file system store drives and date in a hierarchal tree-like structure.
- The "/" directory is the root of the file system, that contains all the directory and files of the system.
- Naming rules: only use alphanumeric characters, periods, underscores and hyphens
- Permissions: Read , Write and Execute are the 3 permission types in linux.
- Links: /directory/another/file that's how a link looks in Linux.

## Linux Commands
Commands are programs executed by the shell.
- The General Syntax looks like this : command [-options][arguments]
-E.g ls -l filename (This is a command that list the contents of a directory)
- use man [command] in case you're not familiar with a command. (just use google easier to understand)

## Git Commands
Whenever you create a repository, ALWAYS RUN THESE COMMANDS.
`git clone <repo_url>` (clones the repo)
`sudo yum list installed` (checks what packages are installed)
`sudo yum install git` (install a package in this case, git)
`git config --global user.name "username"`
`git config --global user.email "email@domain.com` (set up git credentials)


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