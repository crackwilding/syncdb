# HOW TO USE THIS SCRIPT AND BE LAZY

## Server/local prep

1) Create a file in the home directory of the remote server titled `.my.cnf`. It should contain:

```
[mysqldump]
user=DATABASE USERNAME
password=DATABASE PASSWORD
```
2) Chmod this file 500 to prevent it being read by nefarious individuals.

3) Create a directory in the home directory of the remote server titled .dbdumps. Make sure the user
you log in with can write to it.

4) Create a file in your local home directory titled `.my.cnf`. It should be the same as step 1 (but with your local credentials).

5) Create a directory in your local home directory titled .dbdumps.

## Installation

1) Move the script ("syncdb") to /usr/local/bin or whatever weird alternate location you prefer. Make 
sure its location is in your PATH. 

2) Do `chmod +x syncdb` to make it executable.

3) Put "syncdb.conf" in /usr/local/etc. This is where the script expects this to be, so if you don't
   want it there you'll need to edit the script to reflect its new location.
   
4) Edit syncdb.conf as required. Details are available as an example (the first item) in the configuration file itself.

5) On any server you'll be working with you'll need to do a bit of prep. To wit:

   - In the home directory of the user you log in as, add a folder titled .dbdumps.
   - In the same directory, create a file called .my.cnf. It should look like this:

      [mysqldump]
      user=A_USER_WITH_SELECT_PRIVS
      password=THE_USERS'S_PASSWORD

   Make sure that this file is NOT READABLE BY ANY USERS OTHER THAN THE OWNER, which should be the 
   database owner.

6) You will probably want to make sure your public key is on the server because this script logs
   in like three times and will get to be a real pain in the ass otherwise.

## Usage

To use the script, simply type `syncdb`. The script will ask you for the name of the site you wish
to sync -- this is keyed to the name field in syncdb.conf.

## Updates

Please. 
