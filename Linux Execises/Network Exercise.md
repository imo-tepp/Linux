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

## Network
### Network Diagnostic Tools
#### Ping
Ping command uses the ICMP(Internet Control Message Protocol) to test the connection between the computer and another host. For example:
- `ping 8.8.8.8`: This will ping the Google DNS Server continously unless interrupted by *Ctrl + C*
- `ping -c 3 8.8.8.8`: The `-c` defines how mnay times should the ping be send, in this case, 3 times.

#### nslookup 
nslookup is used to query the DNS to obtain the domain name or IP address mapping. 
- `nslookup google.com`: This command looks up the IP address of google.
- `nslookup 8.8.8.8`: This command looks up the domain name.

#### traceroute
Do `sudo apt install traceroute` if you don't have the packagte installed.
- `traceroute google.com`: traces the path that the packets take to reach the networkhost.

#### dig 
Dig stands for *Domain Information groper* and is used to provide detailed information about DNS records.

```
dig google.com
# can also query specific DNS record types, like A, MX, TXT, etc
dig google.com A
dig google.com MX
dig -x 8.8.8.8 # reverse DNS lookup
```
#### curl
curl is used to transfer date to or from a server and support various protocols like HTTP, HTTPS, FTP etc. See below for some examples:
- `curl https://google.com`: this retrieves the basic HTML layout from google
- `curl -o index.html https://google.com` : same as the above, except it outputs the result into a file.
- `curl -L -o redirected.html https://google.com`: Follow the redirects and output the result into a file.
- `curl -X POST -d 'username=user&password=pass' https://google.com/login -f`: Send POST data to google, the -f is to end the process if a http error occurs.
``` 
curl -H "Authorization: Bearer token" https://api.google.com/data
curl -b "cookie1=value1; cookie2=value2" https:google.com 
```

## Linux Exercise 

ps aux --sort