# SSH settings guide

- [SSH settings guide](#ssh-settings-guide)
  - [Domain name for IP](#domain-name-for-ip)
  - [Login without password](#login-without-password)
  - [Host jumping](#host-jumping)
  - [Auto host jumping](#auto-host-jumping)
  - [Forward X11](#forward-x11)

## Domain name for IP

> Windows) %HOMEPATH%\\.ssh\config
> (Linux) ~/.ssh/config

```txt
Host rasp.local
    HostName 192.168.1.69
    User pi
```

> `ssh rasp.local` will connect to pi@192.168.1.69

## Login without password

on client

Generate keys
> `ssh-keygen -t rsa`

Transfer those keys
> (Windows) `ssh remote-server "umask 077; test -d .ssh || mkdir .ssh ; cat >> .ssh/authorized_keys || exit 1" < .\id_rsa.pub`
> (Linux) `ssh-copy-id -i id_rsa.pub remote-server`

## Host jumping

```txt
 (local)           (target)
  kali   -> rasp -> enderpc
```

> `ssh -J rasp.remote enderpc.local`

```txt
 (local)                      (target)
  kali   -> rasp -> enderpc -> master
```

> `ssh -J rasp.remote,enderpc.local,master.local`

## Auto host jumping

```txt
Host rasp.remote
  HostName 87.246.50.116
  User pi

Host enderpc.remote
  HostName enderpc.local
  User hax
  ProxyCommand ssh rasp.remote -W %h:%p
```

Will connect to the raspberry pi and jump to local IP
> `ssh enderpc.remote`

## Forward X11

On remote
