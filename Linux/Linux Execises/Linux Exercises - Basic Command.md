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
