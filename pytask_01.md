Python Home Task 01
===================


## Helpful information

Study following links:
 - https://docs.python.org/2/library/functools.html
 - https://docs.python.org/2/library/functions.html
 - https://docs.python.org/2/library/operator.html
 - https://docs.python.org/2/howto/functional.html
 - http://youtu.be/Ta1bAMOMFOI


## Subtask 1

Create function factory `add_factory` using 5 different approaches like this:

```python
>>> add5 = add_factory(5)
>>> print add5(10)
15
```


## Subtask 2

Create function `reddit` for downloading popular topics from www.reddir.org using closure and generator.

E.g. `reddit` returns function which returns generator over titles from reddit page:

```python
>>> python = reddit(“http://www.reddit.com/r/python.json”)
>>> golang = reddit(“http://www.reddit.com/r/golang.json”)
>>> for title in python():  # here json data is fetched
...    print repr(title)
u'Porting to Python 3 book is on github'
u'An Overview of using WebSockets in Python'
- // -
>>> for title in golang():  # here json data is fetched
...     print title
- // -
```
