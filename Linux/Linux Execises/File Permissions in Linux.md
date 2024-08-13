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

#### Permissions table:
| Number | Access Permissions | rwx value |
| ------ | ------------------ | --------- |
| 7 | read, write and execute | rwx |
| 6 | read and write | rw- |
| 5 | read and execute | r-x |
| 4 | read only | r-- |
| 3 | write and execute | -wx |
| 2 | write only | -w- |
| 1 | execute only | --x |
| 0 | none | ---|

if the command fails, log out and log in again to try again.
- `exit` 
- `su orderbook`
- `sudo chmod 771 /home/test/`

Now add test.txt to the test folder. If you tried before the previous steps , it would fail since it didn't have the correct permissions.
- `touch /home/test/test.txt` then check with `ls -l /home/test`
Make orderbook the owner of the test.txt file
- `sudo chown -R orderbook /home/test` then check `ls -l /home`
Create a script in *home/test*

```
cat <<EOF> /home/test/orderbook.sh
echo "welcome to orderbook"
echo "Anyone can execute this script!!!"
echo "But not everyone can edit it"
EOF

```
Any of the following commands will add execute and read to all other users for the script file.
- `chmod a+x+r /home/test/orderbook.sh`
- `chmod o+x+r /home/test/orderbook.sh`
- `chmod 755 /home/test/order.sh`
Log out , look at the file permission and try to edit and execute the script
- `exit`
- `vi /home/test/orderbook.sh`: can only read the file
- `bash /home/test/orderbook.sh`: anyone can execute.

