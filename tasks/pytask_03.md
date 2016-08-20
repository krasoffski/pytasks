Python Home Task 03
===================

Helpful information
-------------------

Study following links:
 - http://habrahabr.ru/post/114576
 - http://habrahabr.ru/post/114585
 - http://habrahabr.ru/post/114587
 - https://docs.python.org/2/reference/datamodel.html
 - https://docs.python.org/2/library/collections.html

Additional topics which might help you with home task (tips):
 - http://habrahabr.ru/post/186608/
 - http://pymotw.com/2/multiprocessing/mapreduce.html
 - http://habrahabr.ru/post/103467/


Subtask 1
---------

 - Create `Fake` object which does not rise any exception for calling non-existing methods, keys, indexes.
 - Can return `Fake` object after calling non-existing method.
 - It allows any name of method, attribute, index, key, etc.
 - Don't use `try/catch`.

Let me show you example:
```python
>>> fake = Fake()
>>> fake.non_existing_method('asdfa')
>>> fake.attribute
>>> fake[4]
>>> fake['non existing key']
>>> fake2 = fake.blablabla()
>>> fake2.some_name()
>>> fake2.whatever.again_whatever().and_again['yury'][1]
etc.
```

Subtask 2
---------

Create multiprocessed frunction or generator `links_finder` to find links on sites using HTML parser or regular expression like on example:

```python

if __name__ == "__main__":
    links = links_finder(["http://www.goole.com", "http://www.github.com"])
    pprint(links)
```

Output should look like:

```python
{
    "http://www.goole.com": ["link1", "link2", "link3"],
    "http://www.github.com": ["link1", "link2", "link3"]
}
```

Subtask 3
---------

Create multiprocessed function or generator `grep` to produce search in a file using regular expression.

```python

if __name__ == "__main__":
    lines = grep(r"error", "/var/log/messages")
    pprint(lines)
```

Output should look like:

```python
[
    (355, "Error message1"),
    (534, "Error message2"),
    ...
]
```


Subtask 4
---------

Create multiprocessed function or generator `words_counter` to count occurrence of words in text files in specified path like on example:

```python
if __name__ == "__main__":
    exclude = ["if", "else", "on", "at"]
    words = words_counter('/home/keda',
                          ext=["py", "txt"],
                          ignored=exclude,
                          minlen=2)
    pprint(words)
```

Output should look like:

```python
{
    "import", 33,
    "print", 65,
    ...
}
```

**NOTE:** Try to implement your own words counter, link finder (do not just copy from examples above).

**NOTE:** Try to implement your home tasks for multiprocessing using different aproches.

