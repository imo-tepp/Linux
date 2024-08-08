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
Vim is a file editor for Linux, it has 2 modes: *Insert* and *Command*. Command mode takes in command and execute actions where insert takes in input and displays them in vim.
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

### Vim Commands
- `:wq`: Save and Quit
- `:w` : Save
- `:q` : Quit
- `:w fname`: Save as fname
- `ZZ` : Save and Quit
- `:q!`: Quit discarding changes made
- `:w!`: Save(and write to non-writable file)

## Linux Processes
There are different types of process that runs on linux, for example:
- User Processess: Processess that are executed on behalf of a given user
- Kernel Processess: Seperated from user processess, it runs the processess for the operating system.
- Daemon processes: are processess that continuously run in the background.
- The `ps` command shows the currently running processes on the computer.
- The `top` command shows the current usage 
- `fg` & `bg`: bring a process to the foreground or background
- `&`: runs the command or script in the background, while linked to the shell.
- `kill` : terminate a process
- `jobs`: active jobs that are running in the shell.

### Process Monitoring and Exit Codes
- `strace -p <pid>`: shows information about the process
- File descriptors for each process is stored in */proc/<pid>/fd*
- The `$?` is a exit code and can be used to check if the process has run successfuly.

### Network Monitoring 
TCP is a connnection oriented protocol, whereas UDP is a connectionless protocol.
- UDP is faster and a more efficient protocol
- Only TCP is capable of retransmitting lost data packets.
- `ip`: show the current network parameters
- `ifconfig` : configure network parameters 
- `ping`: sends an ICMP request to the host to verify that the destination exists . (kinda like ping pong)
- `traceroute`: shows a map of how the data travel from the source to the destination.
- `netstat`: shows network information like hosts and socket.
- `tcpdump`: analyse the current system network traffic
- `Isof -p <pid>`: Shows everything that has been generated by process.

### System Monitoring
- `/var/log` : directory that contains the system logs
- `ac`: shows the connection time for the user.
- `vmstat`: shows the virtual machine information, such as memory available or used.
- `iostat`: used to monitor the input and output devices.
- `mpstat`: monitors the logical processor
- `df`: stands for *disk free* , use to find available space and disk usage on linux
- `systemctl`: is the command line tool that manages the systems and service manager in linux.

### Disk Space
- `du` - displays how much storage each file and folder are using
- `gzip` & `gunzip` - Zips and unzips file with .gz extension
- `tar`: can create and compress files into an archive or extract them.

## Scheduling Tasks
Scheduling is used to make sure that a process doesn't start without the proper trigger or data available. There are a few tools that we can use to scheduling tasks, such as:
- Control-M (Workload automation)
- Autosys (automated job managment tool)
- AS400 (Database managment system)
- Tibco (GUI tool for business process integration)
- Crontab (Unix command that execute scripts at a specified time or schedule)

### Date in Linux
By default, the data is displayed like : `Wed Jul 8 12:43:04 BST 2024`.
- it's useful for dynamic file name generation for files like logs.
- Possible to do operation on date like : `date +%Y:%m:%d -d "yesterday"`
- Working with dates is important in automation as it relies on dates and time to trigger certain process.

### Arithmetics in BASH
- Double brackets (()) are used to arithmetics in linux 
- `TOTAL=$((1+1))` : it'll perform the calculations and produce the results
- Alternatively you can use *bc* or *awk* command
- `echo 1+1 | bc` or `awk -F '{sum+=$57;} END{print sum;}' file.txt`

### Scripting Commands
- `awk`: Scripting language that manipulates data and reports
- `sed`: Stream editor that can update files without opening them
- `tr` : translate or replace characters
- `cut` : Slice(cut) a line and extract the results 
- `wc` : Word count command that counts the number of lines, words and characters in the file.