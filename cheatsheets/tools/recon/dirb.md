# Dirb

> DIRB is a Web Content Scanner. It looks for existing \(and/or hidden\) Web Objects. It basically works by launching a dictionary based attack against a web server and analyzing the response.
>
> DIRB comes with a set of preconfigured attack wordlists for easy usage but you can use your custom wordlists. Also DIRB sometimes can be used as a classic CGI scanner, but remember is a content scanner not a vulnerability scanner.
>
> DIRB main purpose is to help in professional web application auditing. Specially in security related testing. It covers some holes not covered by classic web vulnerability scanners. DIRB looks for specific web objects that other generic CGI scanners can’t look for. It doesn’t search vulnerabilities nor does it look for web contents that can be vulnerables.
>
> 📖 Repository and official documentation: [http://dirb.sourceforge.net/](http://dirb.sourceforge.net/)

## ❓ Help

dirb ----------------- DIRB v2.21 By The Dark Raver ----------------- ./dirb \[\] \[options\] ========================= NOTES ========================= : Base URL to scan. \(Use -resume for session resuming\) : List of wordfiles. \(wordfile1,wordfile2,wordfile3...\) ======================== HOTKEYS ======================== 'n' -&gt; Go to next directory. 'q' -&gt; Stop scan. \(Saving state for resume\) 'r' -&gt; Remaining scan stats. ======================== OPTIONS ======================== -a : Specify your custom USER\_AGENT. -c : Set a cookie for the HTTP request. -f : Fine tunning of NOT\_FOUND \(404\) detection. -H : Add a custom header to the HTTP request. -i : Use case-insensitive search. -l : Print "Location" header when found. -N: Ignore responses with this HTTP code. -o : Save output to disk. -p : Use this proxy. \(Default port is 1080\) -P : Proxy Authentication. -r : Don't search recursively. -R : Interactive recursion. \(Asks for each directory\) -S : Silent Mode. Don't show tested words. \(For dumb terminals\) -t : Don't force an ending '/' on URLs. -u : HTTP Authentication. -v : Show also NOT\_FOUND pages. -w : Don't stop on WARNING messages. -X / -x : Append each word with this extensions. -z : Add a miliseconds delay to not cause excessive Flood.

## Basics commands

### Simple test

```text
dirb http://example.com/directory/
```

### Simple Test with SSL

```text
dirb https://example.com/directory/
```

### Test files with extension \(Example with html\)

```text
dirb http://example.com/ -X .html
```

### Test with wordlist

```text
dirb http://example.com/ /usr/share/dirb/wordlists/vulns/apache.txt
```

### Specific user agent

```text
dirb http://example.com /path/to/wordlist -a "Mozilla-firefox"
```

### Use proxy with authentication or without it

```text
dirb http://example.com /path/to/wordlist -p proxy:port -P username:password
```

### Save results in a file

```text
dirb http://example.com /path/to/wordlist -o output_file
```

### Ignore Unnecessary Status-Code

```text
dirb http://example.com/dvwa/ -N 404
```

### Don't stop on warning messages

```text
dirb http://example.com -w
```

### Speed delay

```text
dirb http://example.com/dvwa/ -z 100
```

### Not recursively

```text
dirb http://example.com/dvwa/ -r
```

### Show not Existence Pages

```text
dirb http://example.com/dvwa/ -v
```

### Not forcing an ending ‘/’ on URLs \(-t\)

```text
dirb http://example.com/dvwa/index.php -t
```

### HTTP authorization

```text
dirb http://example.com/dvwa/login.php -u test:test
```

## 📚 References

* [dirb.sourceforge.net](http://dirb.sourceforge.net/)
* [tools.kali.org](https://tools.kali.org/web-applications/dirb)
* [byte-mind.net](https://byte-mind.net/dirb-domain-brute-force-tool/)
* [hackingarticles.in](https://www.hackingarticles.in/comprehensive-guide-on-dirb-tool/)

