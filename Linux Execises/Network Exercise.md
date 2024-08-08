## Memory Commands
Commands that can be run to check the memory of the system
- `cat /proc/meminfo` : shows the memory of the system
- `free --mega -h` : (--mega for megabytes, -h for human readability)
- `ps aux --sort -rss`: (rss is Resident Set Size (memory descending))
- `ps aux --sort -%mem`: (% of rss used by the process. The minus sign before %mem indicates descending order, where as a plus sign would do ascending)
- `ps -eo user,pid,%mem,stat,cmd --sort=-%mem`: (only include output -o columns that we want (user,pid,%mem,stat,cmd))
- `ps aux --sort -%cpu`: (can also sort by cpu)
- `ps aux --forest` : useful to see a tree of parent processes
- `watch 'ps aux --sort -%mem | head'`: run the command every 2 seconds
- `top` : use top 


## Inodes
An inode is a data structure that stores metedata about a file, like size, ownership, permissions and timestamps, along with pointers that points to the block that has the actual file data stored. Each file/directory is represented by an inode, which has a unique inode number.

### Example
To experiment, create a 8kb file using the following command:
- `dd if=/dev/urandom of=8kb_file bs=1k count=8`
Use the next command to check the metadata for the file:
- `stat 8kb_file`
You can also run out of inodes, use the next command to check how many you have used:
- `df -i`



## Linux Exercise 

ps aux --sort