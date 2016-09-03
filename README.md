# Python tasks for self-study

## Introduction

This repository contains Python tasks which might help to improve your Python
level. I'm going to add different tasks based on books, sites, real live
examples. Some of them might be tricky or not-well described. Feel free to ask
any question or add pull requests with clarification. I try hard to add
interesting tasks so sometimes it requires a time. Moreover, I highly recommend
to perform final task [pyttleship](tasks/pyttleship.md).

Not to mention the fact, that main goal of this tasks is to use only Python
standard library. Most of all tasks designed for `python2.7` but can be easily
adopted for 3th version of Python.

## Conventions

Here are some notes about code conventions.

### Python examples

Usually python examples contain code and expected output which is commented
with `#` characters. Let me show you example:

```python
from itertools import permutations
print list(permutations('abc', 2))
# [('a', 'b'), ('a', 'c'), ('b', 'a'), ('b', 'c'), ('c', 'a'), ('c', 'b')]
```

Another python example with exception:

```python
with open('/tmp/file.txt') as fd:
    data = fd.read()
# Traceback (most recent call last):
#   File "<stdin>", line 1, in <module>
# IOError: [Errno 2] No such file or directory: '/tmp/file.txt'
```

### Bash examples

Usually all bash commands start with `PS1` prompt. It is a `$` sign for basic
user. In case we need a `root` privilege prompt will be a `#` sign.

```bash
$ curl -i http://localhost:8000/api/jobs
```

Long commands are wrapped with backslash to avoid scrolling. All lines
which belong to the command are indented using four spaces to distinguish with
command output. For example:

```bash
$ curl -X POST -H 'Content-Type: application/json' \
    -d '{"command": "cp /tmp/file /mnt/nfs/"}' http://localhost:8000/api/jobs
HTTP/1.0 202 Accepted
Location: /api/statuses/45
```

## Python tasks

### [Functions and generators](tasks/functions_and_generators.md)
 - Very simple function factory.
 - Generator for downloading topics from reddit using closure.
 - Function and generator for expanding nested sequences.

### [Subprocess and regular expressions](tasks/subprocess_curses_and_regexp.md)
 - Curses based ssh config file viewer.

### [REST service and threading](tasks/linux_http_rest_cmd_server.md)
 - REST service for background job execution.
 - Enhancements for existing REST service.

### [Multiprocess grep and word counter](tasks/grep_and_words_counter.md)
 - Word counter in text files.
 - Simple analogue of Linux `grep` command.

### Coming soon...
 - Descriptors and properties.
 - Plug-ins in python.
 - Metaclasses.

## [Battleship game](tasks/pyttleship.md)
`Pyttleship` is python implementation of world-popular game [Battleship].
The main idea of `Pyttleship` is to gather all tasks described above and build
interesting network game. At first look this game seems quite simple but
during thinking about the future game architecture many questions will arise.

Happy codding!

[battleship]:https://en.wikipedia.org/wiki/Battleship_(game)
