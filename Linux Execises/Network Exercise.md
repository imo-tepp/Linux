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
- The below command fetches infromation including headers and cookies.
``` 
curl -H "Authorization: Bearer token" https://api.google.com/data
curl -b "cookie1=value1; cookie2=value2" https:google.com 
```

#### Listening Ports
We can use the following commands to check what ports are currently open and attached to which hosts:
- `sudo lsof -i -P`: use sudo, to run the command as the root user.

#### Monitoring network traffic
Use the following command to monitor the network traffic on the computer:
- `netstat -c`: This command runs contionusly with *-c* and show how many connection are on the computer and what protocol they are using.

#### Private IP and Subnet
Use the `ifconfig` command to see the information about your network interface. Typically, there's 2 interface. One for the private netwrok and one for the localhost network(loopback).
- *Inet*: this is the IP address that is assinged to the network interface, can be in the form IPv4(private address) or IPv6(global address.)
- *netmask*: Indicates what part of the IP address is the network or the host. Typically, shown in the form of a subnet mask. For example:
1) 
    A netmask of 255.0.0.0 (or /8 in CIDR notation) indicates that the first 8 bits of the IP address are the network part. If an IP address is 172.0.5.1 with a netmask of 255.0.0.0, then all IPs in that network must start with 172.x.x.x.

2) 
    A netmask of 255.255.255.0 (or /24 in CIDR notation) indicates that the first 24 bits of the IP address are the network part. If an IP address is 172.39.44.1 with a netmask of 255.255.255.0, then all IPs in that network must start with 172.39.44.x.

3) 
    With a netmask of 255.255.255.0, the network can have 256 addresses, ranging from 172.39.44.0 to 172.39.44.255. The first address (172.39.44.0) is the network address, and the last address (172.39.44.255) is the broadcast address, leaving 254 usable IP addresses for hosts.
- *Broadcast*: Used to send data to all the devices on the network.

## Linux Exercise 

1) First, search for the stress package using apt search and then install it.

```
apt search stress
sudo apt install stress
```

2) Capture free memory before starting the stress test. Use the free command to retrieve the amount of free memory in megabytes and save it to a file named free_mega_before_stress
```
free --mega # make sure output aligns with awk
free --mega | awk 'NR==2 {print $4}' > free_mega_before_stress #NR==2 is for row 2 and $4 is col 4
```

3) Perfrom the stress test: Execute the stress command to stress the system with virtual memory for 300 seconds:
```
stress --vm 1 --vm-bytes 512M --vm-keep -t 300s & #press enter
```

4) Capture free memory during the stress test: While the stress test is running, again use the free command to get the amount of free memory in megabytes and save it to a file named free_mega_during_stress:
```
free --mega
free --mega | awk 'NR==2 {print $4}' > free_mega_during_stress
```

5) Capture the top 5 memeory-consuming processes during the stress test: Use the ps command to retrieve the PID, %mem, %cpu, and CMD of the 5 processes consuming the most memory
```
ps -eo pid,%mem,%cpu,cmd --sort=-%mem | head -n 6
```
6) Use BC to calculate the difference between how much memory the stress test used.
```
bc <<< "$(cat free_mega_before_stress) - $(cat free_mega_during_stress)"
```