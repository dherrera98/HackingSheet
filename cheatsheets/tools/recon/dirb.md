# Dirb
> DIRB is a Web Content Scanner. It looks for existing (and/or hidden) Web Objects. It basically works by launching a dictionary based attack against a web server and analyzing the response.
>
>DIRB comes with a set of preconfigured attack wordlists for easy usage but you can use your custom wordlists. Also DIRB sometimes can be used as a classic CGI scanner, but remember is a content scanner not a vulnerability scanner.
>
>DIRB main purpose is to help in professional web application auditing. Specially in security related testing. It covers some holes not covered by classic web vulnerability scanners. DIRB looks for specific web objects that other generic CGI scanners can’t look for. It doesn’t search vulnerabilities nor does it look for web contents that can be vulnerables.

> 📖 Repository and official documentation: http://dirb.sourceforge.net/

---
## ❓ Help
<details>
<summary>dirb</summary>

    
    -----------------
    DIRB v2.21
    By The Dark Raver
    -----------------

    ./dirb <url_base> [<wordlist_file(s)>] [options]

    ========================= NOTES =========================
    <url_base> : Base URL to scan. (Use -resume for session resuming)
    <wordlist_file(s)> : List of wordfiles. (wordfile1,wordfile2,wordfile3...)

    ======================== HOTKEYS ========================
    'n' -> Go to next directory.
    'q' -> Stop scan. (Saving state for resume)
    'r' -> Remaining scan stats.

    ======================== OPTIONS ========================
    -a <agent_string> : Specify your custom USER_AGENT.
    -c <cookie_string> : Set a cookie for the HTTP request.
    -f : Fine tunning of NOT_FOUND (404) detection.
    -H <header_string> : Add a custom header to the HTTP request.
    -i : Use case-insensitive search.
    -l : Print "Location" header when found.
    -N <nf_code>: Ignore responses with this HTTP code.
    -o <output_file> : Save output to disk.
    -p <proxy[:port]> : Use this proxy. (Default port is 1080)
    -P <proxy_username:proxy_password> : Proxy Authentication.
    -r : Don't search recursively.
    -R : Interactive recursion. (Asks for each directory)
    -S : Silent Mode. Don't show tested words. (For dumb terminals)
    -t : Don't force an ending '/' on URLs.
    -u <username:password> : HTTP Authentication.
    -v : Show also NOT_FOUND pages.
    -w : Don't stop on WARNING messages.
    -X <extensions> / -x <exts_file> : Append each word with this extensions.
    -z <milisecs> : Add a miliseconds delay to not cause excessive Flood.
</details>


---

## Basics commands

### Simple test
```shell
dirb http://example.com/directory/
```
### Simple Test with SSL
```shell
dirb https://example.com/directory/
```
### Test files with extension (Example with html)
```shell
dirb http://example.com/ -X .html
```
### Test with wordlist 
```shell
dirb http://example.com/ /usr/share/dirb/wordlists/vulns/apache.txt
```
### Specific user agent
```shell
dirb http://example.com /path/to/wordlist -a "Mozilla-firefox"
```
### Use proxy with authentication or without it
```shell
dirb http://example.com /path/to/wordlist -p proxy:port -P username:password
```
### Save results in a file
```shell
dirb http://example.com /path/to/wordlist -o output_file
```

### Ignore Unnecessary Status-Code
```shell
dirb http://example.com/dvwa/ -N 404
```

### Don't stop on warning messages
```shell
dirb http://example.com -w
```

### Speed delay
```shell
dirb http://example.com/dvwa/ -z 100
```

### Not recursively 
```shell
dirb http://example.com/dvwa/ -r
```

### Show not Existence Pages
```shell
dirb http://example.com/dvwa/ -v
```

### Not forcing an ending ‘/’ on URLs (-t)
```shell
dirb http://example.com/dvwa/index.php -t
```

### HTTP authorization
```shell
dirb http://example.com/dvwa/login.php -u test:test
```
---

## 📚 References

- [dirb.sourceforge.net](http://dirb.sourceforge.net/)
- [tools.kali.org](https://tools.kali.org/web-applications/dirb)
- [byte-mind.net](https://byte-mind.net/dirb-domain-brute-force-tool/)
- [hackingarticles.in](https://www.hackingarticles.in/comprehensive-guide-on-dirb-tool/)