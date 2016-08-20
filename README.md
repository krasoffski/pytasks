# Python tasks for self-study

## Introduction

This repository contains Python tasks which might help to improve your Python
level. I'm going to add different tasks based on books, sites, real live
examples. Some of them might be tricky or not-well described. Feel free to ask
any question or add pull requests with clarification.

Not to mention the fact, that main goal of this tasks is use only Python
standard library. Task designed for `python2.7` but can be easily adopted for
3th version of Python.

## Conventions

Here is some notes about code conventions.

### Python examples

Usually python examples contain code and expected output which is commented
with `# ` characters. Let me show you example:

```python
from itertools import permutations
print list(permutations('abc', 2))
# [('a', 'b'), ('a', 'c'), ('b', 'a'), ('b', 'c'), ('c', 'a'), ('c', 'b')]
```

One more example with exception:

```python
with open('/tmp/file.txt') as fd:
    data = fd.read()
# Traceback (most recent call last):
#   File "<stdin>", line 1, in <module>
# IOError: [Errno 2] No such file or directory: '/tmp/file.txt'
```

### Bash examples

### JSON examples

## Content
