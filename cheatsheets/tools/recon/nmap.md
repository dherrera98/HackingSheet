# NMAP

> Nmap \(Network Mapper\) is a free and open-source network scanner and is used to discover hosts and services on a computer network by sending packets and analyzing the responses.
>
> 📖 Repository and official documentation: [https://nmap.org/](https://nmap.org/)

## ❓ Help

nmap -h

```text
Nmap 7.91 ( https://nmap.org )
Usage: nmap [Scan Type(s)] [Options] {target specification}
TARGET SPECIFICATION:
  Can pass hostnames, IP addresses, networks, etc.
  Ex: scanme.nmap.org, microsoft.com/24, 192.168.0.1; 10.0.0-255.1-254
  -iL : Input from list of hosts/networks
  -iR : Choose random targets
  --exclude : Exclude hosts/networks
  --excludefile : Exclude list from file
HOST DISCOVERY:
  -sL: List Scan - simply list targets to scan
  -sn: Ping Scan - disable port scan
  -Pn: Treat all hosts as online -- skip host discovery
  -PS/PA/PU/PY[portlist]: TCP SYN/ACK, UDP or SCTP discovery to given ports
  -PE/PP/PM: ICMP echo, timestamp, and netmask request discovery probes
  -PO[protocol list]: IP Protocol Ping
  -n/-R: Never do DNS resolution/Always resolve [default: sometimes]
  --dns-servers : Specify custom DNS servers
  --system-dns: Use OS's DNS resolver
  --traceroute: Trace hop path to each host
SCAN TECHNIQUES:
  -sS/sT/sA/sW/sM: TCP SYN/Connect()/ACK/Window/Maimon scans
  -sU: UDP Scan
  -sN/sF/sX: TCP Null, FIN, and Xmas scans
  --scanflags : Customize TCP scan flags
  -sI : Idle scan
  -sY/sZ: SCTP INIT/COOKIE-ECHO scans
  -sO: IP protocol scan
  -b : FTP bounce scan
PORT SPECIFICATION AND SCAN ORDER:
  -p : Only scan specified ports
    Ex: -p22; -p1-65535; -p U:53,111,137,T:21-25,80,139,8080,S:9
  --exclude-ports : Exclude the specified ports from scanning
  -F: Fast mode - Scan fewer ports than the default scan
  -r: Scan ports consecutively - don't randomize
  --top-ports : Scan  most common ports
  --port-ratio : Scan ports more common than 
SERVICE/VERSION DETECTION:
  -sV: Probe open ports to determine service/version info
  --version-intensity : Set from 0 (light) to 9 (try all probes)
  --version-light: Limit to most likely probes (intensity 2)
  --version-all: Try every single probe (intensity 9)
  --version-trace: Show detailed version scan activity (for debugging)
SCRIPT SCAN:
  -sC: equivalent to --script=default
  --script=:  is a comma separated list of
           directories, script-files or script-categories
  --script-args=: provide arguments to scripts
  --script-args-file=filename: provide NSE script args in a file
  --script-trace: Show all data sent and received
  --script-updatedb: Update the script database.
  --script-help=: Show help about scripts.
            is a comma-separated list of script-files or
           script-categories.
OS DETECTION:
  -O: Enable OS detection
  --osscan-limit: Limit OS detection to promising targets
  --osscan-guess: Guess OS more aggressively
TIMING AND PERFORMANCE:
  Options which take  are in seconds, or append 'ms' (milliseconds),
  's' (seconds), 'm' (minutes), or 'h' (hours) to the value (e.g. 30m).
  -T: Set timing template (higher is faster)
  --min-hostgroup/max-hostgroup : Parallel host scan group sizes
  --min-parallelism/max-parallelism : Probe parallelization
  --min-rtt-timeout/max-rtt-timeout/initial-rtt-timeout : Specifies
      probe round trip time.
  --max-retries : Caps number of port scan probe retransmissions.
  --host-timeout : Give up on target after this long
  --scan-delay/--max-scan-delay : Adjust delay between probes
  --min-rate : Send packets no slower than  per second
  --max-rate : Send packets no faster than  per second
FIREWALL/IDS EVASION AND SPOOFING:
  -f; --mtu : fragment packets (optionally w/given MTU)
  -D : Cloak a scan with decoys
  -S : Spoof source address
  -e : Use specified interface
  -g/--source-port : Use given port number
  --proxies : Relay connections through HTTP/SOCKS4 proxies
  --data : Append a custom payload to sent packets
  --data-string : Append a custom ASCII string to sent packets
  --data-length : Append random data to sent packets
  --ip-options : Send packets with specified ip options
  --ttl : Set IP time-to-live field
  --spoof-mac : Spoof your MAC address
  --badsum: Send packets with a bogus TCP/UDP/SCTP checksum
OUTPUT:
  -oN/-oX/-oS/-oG : Output scan in normal, XML, s|: Output in the three major formats at once
  -v: Increase verbosity level (use -vv or more for greater effect)
  -d: Increase debugging level (use -dd or more for greater effect)
  --reason: Display the reason a port is in a particular state
  --open: Only show open (or possibly open) ports
  --packet-trace: Show all packets sent and received
  --iflist: Print host interfaces and routes (for debugging)
  --append-output: Append to rather than clobber specified output files
  --resume : Resume an aborted scan
  --stylesheet : XSL stylesheet to transform XML output to HTML
  --webxml: Reference stylesheet from Nmap.Org for more portable XML
  --no-stylesheet: Prevent associating of XSL stylesheet w/XML output
MISC:
  -6: Enable IPv6 scanning
  -A: Enable OS detection, version detection, script scanning, and traceroute
  --datadir : Specify custom Nmap data file location
  --send-eth/--send-ip: Send using raw ethernet frames or IP packets
  --privileged: Assume that the user is fully privileged
  --unprivileged: Assume the user lacks raw socket privileges
  -V: Print version number
  -h: Print this help summary page.
```

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

### Scan targets from a shell file

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

### Scan 100 most common ports \(Fast\)

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

### Scan using TCP SYN scan \(default\)

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

## 📚 References

* [nmap.org](https://nmap.org/)
* [github.com/rackerlabs/scantron](https://github.com/rackerlabs/scantron)
* [github.com/cloudflare/flan](https://github.com/cloudflare/flan)
* [appsecco.com/books/subdomain-enumeration/](https://appsecco.com/books/subdomain-enumeration/)
* [gtfobins.github.io/gtfobins/nmap/\#shell](https://gtfobins.github.io/gtfobins/nmap/#shell)
* [operator-handbook](https://www.netmux.com/blog/operator-handbook)

