# User Management
## Who is a User?
In Linux, a User is an entity, one that can manipulate files and perform other actions. Every user is assigned an unique ID. ID 0 is assigned to root user, 1 - 999 is assigned to system users and 1000 onwards are local users.

## Creating a User
Use the following commands to create a user:
1) `sudo adduser username`
2) Enter a password for the new user and confirm.
3) Enter the details of the user and confirm.

## Deleting or disabling  account
Use the following command to delete a user:
- To disable a user account , use `sudo passwd -l 'username'`
- To delete a user account, use `sudo userdel -r 'username'`

## Add users to the usergroup
Use the following commands to add users to the usergroup.
1) View the current usergroup by typing `groupmod` and pressing the tab key twice.
2) use `sudo usermod -a -G GROUPNAME USERNAME` to add a user to a group.
3) Enter your password to pass the authentication and it would complete the action.
4) Use `cat /etc/group/` to check if the user been added to the group
5) To delete the user from the group, use `sudo deluser USER GROUPNAME`

## Additional Commands
Use the *Finger* command to find information on all users that are logged on to the local and remote machine.
- use `finger username` to find information on specifc user.

## Points to Remember
- `useradd`: adds new user to the linux system
- When a new user is created, a new home directory with required ownership and permissions gets created as well.
- These files are edited when a new user is created:
```
/etc/group
/etc/shadow
/etc/gshadow
/etc/passwd
```
- The 0 UID is for root users
- 1 - 999 UIDs are for groups and system users
- GID = Group Identifcation number and is provided to every group.
- GID are stored in /etc/groupfile
- `useradd -m -d /MyHome user1` used to create a specific user in the specified directory named *MyHome*
- `passwd`: used to assing a password to the user
- user can be created with a expiry date, and their account will delete after that date.
- Commands to check the current user:
```
who
whoami
who am i
w
```
- `id`: shows the user, group and the list of gorups that belong to the user.
- `su` can change user role to root user
- `sudo` can be used to create new user without becoming root user
- The *etc/shadow* contains encrypted user password and non-root user can read the files in that folder.
- *openssl password* creates an encrypted password
- In *etc/login.defs* the minimum number of day allowed between password changes and maximum number of days that a password can be used are defined here.
- *change* checks the password information
- *usermod* enable or disable password for a user.
```
usermod -L <usernmae> #disable password for user
groupadd #creates a new group
groups #checks the group for the user
groupmod #renmae the group
groupdel #delete a group
gpasswd #pass control of the group to another user
```
