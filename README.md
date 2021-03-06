# Generate Some Email addresses

wget https://raw.githubusercontent.com/insidetrust/statistically-likely-usernames/master/top-formats.txt  
  
awk '{print $1"@domain.com"}' top-formats.txt > top-formats.domain.txt  
  
  

# office365userenum.py
From: https://bitbucket.org/grimhacker/office365userenum/src/master/  

Enumerate valid usernames from Office 365 using ActiveSync  

Change the password it attemts in the python file itself
  
  
Example usage:
  
python2.7 office365userenum.py -u user_list -o output.txt

### Results of enum  

| Response Code | Description                                 |
|---------------|---------------------------------------------|
| 200           | Successful login (good user/password)       |
| 401           | Valid Username, bad password                |
| 403           | Valid Username, good password, 2FA required |
| 404           | Invalid Username                            |
  


# o365recon
script to retrieve information via O365 with a valid cred

## setup
For most people, you will just have to install the MsOnline module
```
Install-Module MSOnline
```

If you want to use the commented out Azure stuff, you will have to install AzureAD
```
Install-Module -Name AzureAD
```

## usage (updated: 1/5/2019)

Now, with FLAGS! By default, will grab all data.

```
FLAGS
-U               Get Userlist
-users_detailed  Get detailed information for each user
-users_ldap      Pull down user list in ldap style format
-G               Get Group list
-M               Get Group Membership
-D               Get Domain list
-C               Get Company info

-all             Do simple enum - like enum4linux (-U -G -M -D -C). This is run if no other options are selected.
-outputfile      Output file prefix
```

````
Example Usage:

.\o365recon.ps1 -outputfile TEST_OUTPUT
````
No parameters are required to run. It will prompt you to log in, and then it will retrieve all information it can about that account's O365 configuration.

Retrieves:
- Company Info (address, etc)
- Domain Info (other domains)
- Full user list
- Full group list
- Group membership for every group


You'll see that the code for the Azure version is commented out, but it can be swapped in if you prefer that method.
