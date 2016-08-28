# Curses based ssh config file viewer


## Useful information

Study following links:
 - https://docs.python.org/2/howto/curses.html
 - https://docs.python.org/2/howto/regex.html
 - https://pymotw.com/2/re/index.html
 - https://pymotw.com/2/subprocess/index.html
 - https://docs.python.org/2/library/subprocess.html
 - https://jimmyg.org/blog/2009/working-with-python-subprocess.html


## Subtask 1

Create utility which shows `Host` entries from `~/.ssh/config` file using
curses interface and opens connection to selected `Host` by pressing `Enter` or
`o` keys.

Some notes about implementation:
 - Uses system ssh command.
 - Supports vim-like motion (`j`, `k`).
 - Open shh connection via user shell.

For example, your `~/.ssh/config` contains following entries:

```bash
$ cat ~/.ssh/config
Host *
    ServerAliveInterval 300
    ServerAliveCountMax 2

Host cobbler
    IdentityFile ~/.ssh/cobbler.id_rsa
    User cobbler
    Hostname 10.10.10.1

Host jenkins
    User jenkins
    Hostname 10.10.10.2
    IdentityFile ~/.ssh/jenkins.id_rsa

Host git
    Hostname 10.12.13.2
    IdentityFile ~/.ssh/git.id_rsa

Host minion1
    Hostname salt-minion1.int.example.com
    User root

Host minion2
    User root
    Hostname salt-minion2.int.example.com
```

The simplified screen of your curses application might look like:
![SSH viewer](https://raw.githubusercontent.com/krasoffski/pytasks/master/assets/ssh_curses.png)

Usage case is next:
 1. User starts script in a Linux termnal.
 2. Using `j` or `k` keys selects required row with host entry.
 3. Pressing `Enter` or `o` keys opens remote session using system ssh command.
 4. System ssh command uses settion from `~/.ssh/config` file.
