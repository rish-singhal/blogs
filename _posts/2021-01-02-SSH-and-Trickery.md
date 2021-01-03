---
title: "SSH and Trickery"
mathjax: true
layout: post
comments: true
---

## Introduction

---

- Protocol to communicate with other nodes (secure shell)
    - Other examples of protocol are HTTP, HTTPS, FTP, ... (each one have some port of their own) like 22 for SSH, 21 for FTP
- Traffic is encrypted <3

The server must have SSHD *server*  (Open SSH Daemon) — for listening to the requests 

```bash
> ssh [username]@[IP Address]
```

## Authentication Methods

---

- Password
- SSH keys — can be used with git
- Host

## Generate SSH key & Commands

---

```bash
> ssh-keygen [-T rsa]

~/.ssh/id_[rsa/something].pub -> Public Key

> ssh-add [path_to_file]

~/.ssh/authorized_keys -> file for adding public keys on server
```

After generating keys, they can be uploaded to the server so as to get authorized access without traditional username-password pair.

## Extras

---

```bash
> usermod -aG sudo [username]
-- For adding sudo permissions to the [username]
```

- PORT — 22 can be seen in the config file *sshd_config*

```bash
> sudo vim /etc/ssh/sshd_config
-- SSH config file

> sudo systemctl reload sshd 
-- After updating --
```

- Some UNIX commands

```bash
> sudo chown [Do Not Include~"change owner"] -R [user]:[group] [path to directory]
```

## Queries

---

- SCP? — secure file copy, drag and drop file to suvey?
    - For copying files across local and server

## Resource

---

- [SSH Crash Course | With Some DevOps]([https://www.youtube.com/watch?v=hQWRp-FdTpc](https://www.youtube.com/watch?v=hQWRp-FdTpc))