# WFUZZ

> This simple concept allows any input to be injected in any field of an HTTP request, allowing to perform complex web security attacks in different web application components such as: parameters, authentication, forms, directories/files, headers, etc.
>
> 📖 Repository and official documentation: [https://github.com/xmendez/wfuzz](https://github.com/xmendez/wfuzz)

## ❓ Help

```text
Usage:  wfuzz [options] -z payload,params <url>

    FUZZ, ..., FUZnZ  wherever you put these keywords wfuzz will replace them with the values of the specified payload.
    FUZZ{baseline_value} FUZZ will be replaced by baseline_value. It will be the first request performed and could be used as a base for filtering.


Options:
    -h/--help           : This help
    --help              : Advanced help
    --version           : Wfuzz version details
    -e <type>           : List of available encoders/payloads/iterators/printers/scripts
   
    --recipe <filename>     : Reads options from a recipe
    --dump-recipe <filename>    : Prints current options as a recipe
    --oF <filename>         : Saves fuzz results to a file. These can be consumed later using the wfuzz payload.
   
    -c              : Output with colors
    -v              : Verbose information.
    -f filename,printer         : Store results in the output file using the specified printer (raw printer if omitted).
    -o printer                  : Show results using the specified printer.
    --interact          : (beta) If selected,all key presses are captured. This allows you to interact with the program.
    --dry-run           : Print the results of applying the requests without actually making any HTTP request.
    --prev              : Print the previous HTTP requests (only when using payloads generating fuzzresults)
   
    -p addr             : Use Proxy in format ip:port:type. Repeat option for using various proxies.
                      Where type could be SOCKS4,SOCKS5 or HTTP if omitted.
   
    -t N                : Specify the number of concurrent connections (10 default)
    -s N                : Specify time delay between requests (0 default)
    -R depth            : Recursive path discovery being depth the maximum recursion level.
    -L,--follow         : Follow HTTP redirections
    -Z              : Scan mode (Connection errors will be ignored).
    --req-delay N           : Sets the maximum time in seconds the request is allowed to take (CURLOPT_TIMEOUT). Default 90.
    --conn-delay N              : Sets the maximum time in seconds the connection phase to the server to take (CURLOPT_CONNECTTIMEOUT). Default 90.
   
    -A              : Alias for --script=default -v -c
    --script=           : Equivalent to --script=default
    --script=<plugins>      : Runs script's scan. <plugins> is a comma separated list of plugin-files or plugin-categories
    --script-help=<plugins>     : Show help about scripts.
    --script-args n1=v1,...     : Provide arguments to scripts. ie. --script-args grep.regex="<A href="(.*?)">"
   
    -u url                      : Specify a URL for the request.
    -m iterator         : Specify an iterator for combining payloads (product by default)
    -z payload          : Specify a payload for each FUZZ keyword used in the form of name[,parameter][,encoder].
                      A list of encoders can be used, ie. md5-sha1. Encoders can be chained, ie. md5@sha1.
                      Encoders category can be used. ie. url
                                  Use help as a payload to show payload plugin's details (you can filter using --slice)
    --zP <params>           : Arguments for the specified payload (it must be preceded by -z or -w).
    --slice <filter>        : Filter payload's elements using the specified expression. It must be preceded by -z.
    -w wordlist         : Specify a wordlist file (alias for -z file,wordlist).
    -V alltype          : All parameters bruteforcing (allvars and allpost). No need for FUZZ keyword.
    -X method           : Specify an HTTP method for the request, ie. HEAD or FUZZ
   
    -b cookie           : Specify a cookie for the requests. Repeat option for various cookies.
    -d postdata             : Use post data (ex: "id=FUZZ&catalogue=1")
    -H header           : Use header (ex:"Cookie:id=1312321&user=FUZZ"). Repeat option for various headers.
    --basic/ntlm/digest auth    : in format "user:pass" or "FUZZ:FUZZ" or "domain\FUZ2Z:FUZZ"
   
    --hc/hl/hw/hh N[,N]+        : Hide responses with the specified code/lines/words/chars (Use BBB for taking values from baseline)
    --sc/sl/sw/sh N[,N]+        : Show responses with the specified code/lines/words/chars (Use BBB for taking values from baseline)
    --ss/hs regex           : Show/hide responses with the specified regex within the content
    --filter <filter>       : Show/hide responses using the specified filter expression (Use BBB for taking values from baseline)
    --prefilter <filter>        : Filter items before fuzzing using the specified expression.
```

## Basics commands

### List subdomains of a specific domain

```shell
wfuzz -w <wordlist> https://FUZZ.domain.com/
```

### Brute force directories

```shell
wfuzz -w <wordlist> https://domain.com/FUZZ
```

### Hides status codes from server response

```shell
wfuzz --hc=404,302,301 -w <wordlist> http://domain.com/FUZZ
```

### Hide the lines that contain X number of words

```shell
wfuzz --hw=100 -w <wordlist> http://domain.com/FUZZ
```

### Brute force to file with extension

```shell
wfuzz -w <wordlist> http://domain.com/cgi-bin/FUZZ.cgi
```

## 📚 References

* [github.com/xmendez/wfuzz](https://github.com/xmendez/wfuzz)

