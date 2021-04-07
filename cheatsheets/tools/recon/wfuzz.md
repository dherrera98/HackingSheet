# WFUZZ
> This simple concept allows any input to be injected in any field of an HTTP request, allowing to perform complex web security attacks in different web application components such as: parameters, authentication, forms, directories/files, headers, etc.

> 📖 Repository and official documentation: https://github.com/xmendez/wfuzz

---
## ❓ Help
<details>
<summary>wfuzz -h</summary>

    Usage:  wfuzz [options] -z payload,params <url>

        FUZZ, ..., FUZnZ  wherever you put these keywords wfuzz will replace them with the values of the specified payload.
        FUZZ{baseline_value} FUZZ will be replaced by baseline_value. It will be the first request performed and could be used as a base for filtering.


Options:
        -h                        : This help
        --help                    : Advanced help
        --version                 : Wfuzz version details
        -e <type>                 : List of available encoders/payloads/iterators/printers/scripts

        -c                        : Output with colors
        -v                        : Verbose information.
        --interact                : (beta) If selected,all key presses are captured. This allows you to interact with the program.

        -p addr                   : Use Proxy in format ip:port:type. Repeat option for using various proxies.
                                    Where type could be SOCKS4,SOCKS5 or HTTP if omitted.

        -t N                      : Specify the number of concurrent connections (10 default)
        -s N                      : Specify time delay between requests (0 default)
        -R depth                  : Recursive path discovery being depth the maximum recursion level (0 default)
        -D depth                  : Maximum link depth level (4 default)
        -L, --follow              : Follow HTTP redirections

        -u url                    : Specify a URL for the request.
        -z payload                : Specify a payload for each FUZZ keyword used in the form of type,parameters,encoder.
                                    A list of encoders can be used, ie. md5-sha1. Encoders can be chained, ie. md5@sha1.
                                    Encoders category can be used. ie. url
                                    Use help as a payload to show payload plugin's details (you can filter using --slice)
        -w wordlist               : Specify a wordlist file (alias for -z file,wordlist).
        -V alltype                : All parameters bruteforcing (allvars and allpost). No need for FUZZ keyword.
        -X method                 : Specify an HTTP method for the request, ie. HEAD or FUZZ

        -b cookie                 : Specify a cookie for the requests
        -d postdata               : Use post data (ex: "id=FUZZ&catalogue=1")
        -H header                 : Use header (ex:"Cookie:id=1312321&user=FUZZ")
        --basic/ntlm/digest auth  : in format "user:pass" or "FUZZ:FUZZ" or "domain\FUZ2Z:FUZZ"

        --hc/hl/hw/hh N[,N]+      : Hide responses with the specified code/lines/words/chars (Use BBB for taking values from baseline)
        --sc/sl/sw/sh N[,N]+      : Show responses with the specified code/lines/words/chars (Use BBB for taking values from baseline)
        --ss/hs regex             : Show/Hide responses with the specified regex within the content


</details>


---

## Basics commands

### List subdomains of a specific domain
```shell
wfuzz -w [wordlist] https://FUZZ.domain.com/
```
### Brute force directories
```shell
wfuzz -w[wordlist] https://domain.com/FUZZ 
```
### Hides status codes from server response
```shell
wfuzz --hc=404,302,301 -w[wordlist] http://domain.com/FUZZ
```
### Hide the lines that contain X number of words
```shell
wfuzz --hw=100 -w [wordlist] http://domain.com/FUZZ
```
### Brute force to file with extension
```shell
wfuzz -w[wordlist] http://domain.com/cgi-bin/FUZZ.cgi 
```

---

## 📚 References

- [github.com/xmendez/wfuzz](https://github.com/xmendez/wfuzz)
