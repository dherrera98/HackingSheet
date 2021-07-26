# Sublist3r

> Sublist3r is a python tool designed to enumerate subdomains of websites using OSINT. It helps penetration testers and bug hunters collect and gather subdomains for the domain they are targeting. Sublist3r enumerates subdomains using many search engines such as Google, Yahoo, Bing, Baidu and Ask. Sublist3r also enumerates subdomains using Netcraft, Virustotal, ThreatCrowd, DNSdumpster and ReverseDNS.
>
> 📖 Repository and official documentation: [https://github.com/aboul3la/Sublist3r](https://github.com/aboul3la/Sublist3r)

## ❓ Help

```text
usage: sublist3r [-h] -d DOMAIN [-b [BRUTEFORCE]] [-p PORTS] [-v [VERBOSE]]
                 [-t THREADS] [-e ENGINES] [-o OUTPUT]

OPTIONS:
  -h, --help            show this help message and exit
  -d DOMAIN, --domain DOMAIN
                        Domain name to enumerate it's subdomains
  -b [BRUTEFORCE], --bruteforce [BRUTEFORCE]
                        Enable the subbrute bruteforce module
  -p PORTS, --ports PORTS
                        Scan the found subdomains against specified tcp ports
  -v [VERBOSE], --verbose [VERBOSE]
                        Enable Verbosity and display results in realtime
  -t THREADS, --threads THREADS
                        Number of threads to use for subbrute bruteforce
  -e ENGINES, --engines ENGINES
                        Specify a comma-separated list of search engines
  -o OUTPUT, --output OUTPUT
                        Save the results to text file
```

## Basics commands

### List the subdomains of the specified domain in the search engines

```shell
sublist3r -d example.com
```

### List the subdomains of the specified domain in the search engines which have port 80 and 443 open

```shell
sublist3r -d example.com -p 80,443
```

### List the subdomains of the specified domain in real-time search engines

```shell
sublist3r -v -d example.com
```

### List the subdomains of the specified domain in search engines and using brute force

```shell
sublist3r -b -d example.com
```

### List the subdomains of the specified domain in the specified search engines

```shell
sublist3r -e google,yahoo,virustotal -d example.com
```

## 📚 References

* [github.com/aboul3la/Sublist3r](https://github.com/aboul3la/Sublist3r)
* [pentesttools.net](https://pentesttools.net/sublist3r-fast-subdomains-enumeration-tool-for-penetration-testers/)

