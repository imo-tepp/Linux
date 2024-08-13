## Pre-Requisite
- Either have an EC2 instance with an ubuntu image or just use a virtual machine to run linux.

## Exercise
1) Start by creating a folder to store the memory reports and open the new folder.
- `mkdir memory_report`
- `cd memory_report`
2) Create a file that lists all of the files in the home folder, sorted by size with the largest file on the top. Name the file homefiles_sorted.txt.
- `du ~ -a | sort -k1,1nr > homefiles_sorted.txt`
- `less homefiles_sorted.txt`
3) Repeat the task for all files on the system.
- `sudo du / -a | sort -k1,1nr > allfiles_sorted.txt`
- `less allfiles_sorted.txt`
4) How large are the files you just created?
- `du . -ha` #actual sizes used (The h option is for human readable and a is for all files.)
- `ls -la` #size is "apparent" size, not actual
5) Next, look at how much room is left in the file system. Save the results to a file named filesystems.txt.
- `df -h > filesystems.txt`
6) The following command tars all files with the .txt extension into a new file named memory.tar.
- `tar -cvf memory.tar *.txt`
7) Use the command below to examine what files are in the tar. The output will include a size estimate of each file.
- `tar -tvf memory.tar`
8) Now turn the tar into a gzip. Gzip is a tool for compressing a file. We can use it to compress the tar, a common task in Linux.
- `gzip memory.tar` 
- `gzip -c memory.tar > memory.tar.gz` (command to keep original tar file)
9) Look at the storage size of the compression and note that it is smaller than the original files.
- `du . -ha`
10) Delete the original files and extract the compressed tarball. Look at your disk file usage again.
- `rm *.txt `
- `rm memory.tar` (if you still have this file)
- `du . -ha`
11) Decompress the gzip file with gunzip, and then extract (-x) the tar and examine the size again.
- `gunzip memory.tar.gz`
- `tar -xvf memory.tar`
- `du . -ha`
12) The -z flag with tar is a shortcut to creating a compressed tarball. Examine the memory to be sure it is compressed. Finally, uncompress it again with -z.
- `tar -czvf memory.tar.gz *.txt`
- `du . -ha`
- `tar -xzvf memory.tar.gz`
- `du . -ha`

