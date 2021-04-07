# Gobuster
> Gobuster is a tool used to brute-force:
> - URIs (directories and files) in web sites.
> - DNS subdomains (with wildcard support).
> - Virtual Host names on target web servers.
> - Open Amazon S3 buckets

> 📖 Repository and official documentation: https://github.com/OJ/gobuster

---

## ❓ Help
<details>
<summary>gobuster -h</summary>
<pre>
Usage:
  gobuster [command]

Available Commands:
  dir         Uses directory/file enumeration mode
  dns         Uses DNS subdomain enumeration mode
  fuzz        Uses fuzzing mode
  help        Help about any command
  s3          Uses aws bucket enumeration mode
  version     shows the current version
  vhost       Uses VHOST enumeration mode

Flags:
      --delay duration    Time each thread waits between requests (e.g. 1500ms)
  -h, --help              help for gobuster
      --no-error          Don't display errors
  -z, --no-progress       Don't display progress
  -o, --output string     Output file to write results to (defaults to stdout)
  -p, --pattern string    File containing replacement patterns
  -q, --quiet             Don't print the banner and other noise
  -t, --threads int       Number of concurrent threads (default 10)
  -v, --verbose           Verbose output (errors)
  -w, --wordlist string   Path to the wordlist

Use "gobuster [command] --help" for more information about a command.
</pre>
</details>


---

## DNS Mode

### Brute force to dns specifying domain, showing the ips
```shell
gobuster dns -d <domain> -w <word_list.txt> -i
```
### Brute force to dns specifying domain, showing the cname
```shell
gobuster dns -d <domain> -w <word_list.txt> -c
```
### Brute force to dns specifying the domain, showing the ips, using 10 threads and verbose mode
```shell
gobuster dns -d <domain> -w <word_list.txt> -i -v -t 10
```

## Dir Mode
### Brute force to directories, specifying files types
```shell
gobuster dir -u <url> -w <wordlist_file.txt> -x <file_extensions>
```
### Brute force to directories, specifying file types, showing extended information and body length
```shell
gobuster dir -u <url> -w <wordlist_file.txt> -x <file_extensions> -e -l
```
### Brute force directories by adding cookies to the request and skipping the TLS check
```shell
gobuster dir -u <url> -w <wordlist_file.txt> -x <file_extensions> -c <cookie> -k
```

---

## 📚 References

- [github.com/OJ/gobuster](https://github.com/OJ/gobuster)
- [tools.kali.org/web-applications/gobuster](https://tools.kali.org/web-applications/gobuster)
- [null-byte.wonderhowto.com/how-to/scan-websites-for-interesting-directories-files-with-gobuster-0197226/](https://null-byte.wonderhowto.com/how-to/scan-websites-for-interesting-directories-files-with-gobuster-0197226/)