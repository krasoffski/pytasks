Python Home Task 05
===================


Helpful information
-------------------

Study following links:
 - http://www.toptal.com/python/an-introduction-to-mocking-in-python


Subtask 1
---------

Create simple threaded http server like in *pytask_02* which can be extended using class-based plug-in model for handing requests.


Example:

```python
>>> from datetime import datetime
>>> from server import run, Handler
>>> class Date(Handler):
...     __url__ = '/date'
...     def get_handler(self):
...         return datetime.now()
...
>>> run()
```

And at the same time:

```bash
$ curl -s 'http://192.168.1.2:8080/date'
2015-03-10 12:24:43.492631
```


Subtask 2
---------

Create simple threaded http server like in *pytask_02* which can be extended using decorator-based plug-in model for handing requests.


Example:

```python
>>> from datetime import datetime
>>> from server import run, get_handler
>>> @get_handler('/date')
... def date():
...     return datetime.now()
...
>>> run()
```

And at the same time:

```bash
$ curl -s 'http://192.168.1.2:8080/date'
2015-03-10 12:24:43.492631
```


Subtask 3
---------

Comming soon...

