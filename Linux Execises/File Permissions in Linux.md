# File Permissions in Linux

## Create a New User
Create a new user named orderbook
- `sudo adduser orderbook`
Give the user the defaut password *academy*
- `echo 'orderbook:academy' | sudo chpasswd`
Set the password to expire next time a user enters it
- `sudo passwd --expire orderbook`
Add the user to sudoers group
- `sudo visudo`: if vim isn't the default editor , use `sudo EDITOR=vim visudo`
Copy and paste the following command in the file:
- `orderbook ALL=(ALL:ALL) NOPASSWD:ALL` if it doesn't work, use `orderbook ALL=(ALL) NOPASSWD:ALL`.

## Log in As the New User
log in as the new user
- `su orderbook`
Go to the home directory
- `cd ~`
Create a directory
- `mkdir /home/test`: this command will fail since the user does not have the appropriate access.
Try again with sudo:
- `sudo mkdir /home/test`
list the *Home folder* with *-l* to see ownership and permission.
- `ls -l /home`
Examine the groups
 - `cat /etc/group `
 Create a group call *admins* and list the groups again
 - `sudo groupadd admins`
 - `cat /etc/group`
 check what group orderbook is in, add orderbook to admins then list the group again.
 - `groups orderbook`
 - `sudo usermod -a -G admins orderbook`
 - `groups orderbook`
 Log in again to refresh the list of groups
 - `exit`
 - `su orderbook`
 Change the group owner of test to admins, then check the group for test.
 - `sudo chgrp -R admins /home/test`
 - `ls -l /home/`
 Change the group permissions, both commands below changes the permission to have write access.
 - `sudo chmod 771 /home/test/`
 - `sudo chmod g+w /home/test/` 

Permissions table:
| Number | Access Permissions | rwx value |
| ------ | ------------------ | --------- |
| 7 | read, write and execute | rwx |
