# NMAP
> Nmap (Network Mapper) is a free and open-source network scanner and
is used to discover hosts and services on a computer network by
sending packets and analyzing the responses.

> 📖 Repository and official documentation: https://nmap.org/

---

## Basics commands

### Scan a Single Target
```shell
nmap 10.0.0.1
```
### Scan a host
```shell
nmap www.testhostname.com
```
### Scan a range of IPs
```shell
nmap 10.0.0.1-20
```
### Scan a subnet
```shell
nmap 10.0.0.0/24
```
### Scan targets from a text file
```shell
nmap -iL list-of-ips.txt
```
### Scan a single Port
```shell
nmap -p 22 10.0.0.1
```
### Scan a range of ports
```shell
nmap -p 1-100 10.0.0.1
```
### Scan 100 most common ports (Fast)
```shell
nmap -F 10.0.0.1
```
### Scan all 65535 ports
```shell
nmap -p- 10.0.0.1
```
### Scan using TCP connect
```shell
nmap -sT 10.0.0.1
```
### Scan using TCP SYN scan (default)
```shell
nmap -sS 10.0.0.1
```
### Scan UDP ports
```shell
nmap -sU -p 123,161,162 10.0.0.1
```
### Scan selected ports - ignore discovery
```shell
nmap -Pn -F 10.0.0.1
```
### Detect OS and Services
```shell
nmap -A 10.0.0.1
```
### Standard service detection
```shell
nmap -sV 10.0.0.1
```
### More aggressive Service Detection
```shell
nmap -sV --version-intensity 5 10.0.0.1
```
### Lighter banner grabbing detection
```shell
nmap -sV --version-intensity 0 10.0.0.1
```
### Save default output to file
```shell
nmap -oN outputfile.txt 10.0.0.1
```
### Save results as XML
```shell
nmap -oX outputfile.xml 10.0.0.1 
```
### Save results in a format for grep
```shell
nmap -oG outputfile.txt 10.0.0.1
```
### Save in all formats
```shell
nmap -oA outputfile 10.0.0.1
```
### Scan using default safe scripts
```shell
nmap -sV -sC 10.0.0.1
```
### Get help for a script
```shell
nmap --script-help=ssl-heartbleed
```
### Scan using a specific NSE script
```shell
nmap -sV -p 443 –script=sslheartbleed.nse 10.0.0.1
```
### Scan with a set of scripts
```shell
nmap -sV --script=smb* 10.0.0.1
```
### Gather page titles from HTTP services
```shell
nmap --script=http-title 10.0.0.0/24
```
### Get HTTP headers of web services
```shell
nmap --script=http-headers 10.0.0.0/24
```
### Find web apps from known paths
```shell
nmap --script=http-enum 10.0.0.0/24
```
### Find Information about IP address
```shell
nmap --script=asn-query,whois,ipgeolocation-maxmind 10.0.0.0/24
```

---

## 📚 References
- [nmap.org](https://nmap.org/)
- [github.com/rackerlabs/scantron](https://github.com/rackerlabs/scantron)
- [github.com/cloudflare/flan](https://github.com/cloudflare/flan)
- [appsecco.com/books/subdomain-enumeration/](https://appsecco.com/books/subdomain-enumeration/)
- [gtfobins.github.io/gtfobins/nmap/#shell](https://gtfobins.github.io/gtfobins/nmap/#shell)
- [operator-handbook](https://www.netmux.com/blog/operator-handbook)
