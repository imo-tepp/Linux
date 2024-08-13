# Linux Security
Security helps secure the operational system from being crippled by outside attacks and ensure sensitive data isn't stolen.
## Security Requirements 
There are 6 security requirements:
- *** Authorization *** : Only allow authroize user to access the data.
- *** Authenticity *** : Authenicate or verify user's credentials.
- *** Privacy / Confidentiality *** : Ensure personal data is not compromised.
- *** Integrity *** : Ensuring data has not been tempered with.
- *** Non-repudiation *** : Confirmation that data is received.
- *** Availabilty *** : System is available to perform the required function.

## Sudo configuration and usage
Sudo(SuperUser Do) is a linux program that enables user to temporaliy(default 15 mins) use root privilages to perform certain task that requires the correct permissions.

## Shadow Password
The shadow password is only readable to those who have access to it. The file itself contains one line per entry, with each line representing a user. The format of a shadow password file is shown below:
- *** Username *** : user login name 
- *** Encrypted Password *** : Passwords thats been encrypted with *$type$salt$hashed and is 8-12 characters long.
- *** Last password change ***: Date of last password change
- *** Minimum password age ***: How long the user has to wait before changing the password again.
- *** Maximum password age ***: How long the password is available for before having to change.
- *** Warning period ***: When should a warning be sent out to the user to change the password.
- *** Inactivity period ***: How long the user has to be inactive before the account is disabled.
- *** Expiration date ***: Date on when the account will be disabled.
- *** Unused ***: Empty field , left for future use.

## Shadow Password commands
Only root user can use these commands.
- `passwd`: change the password
- `chage`: sets up password aging
- `pwck`: verify the integrity of the files.

## SSH