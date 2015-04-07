Python Home Task 06
===================


Helpful information
-------------------

Study following links:
 - http://habrahabr.ru/post/145835/
 - http://blog.ionelmc.ro/2015/02/09/understanding-python-metaclasses/

Additional topics:
 - http://habrahabr.ru/post/135913/
 - http://habrahabr.ru/post/117236/
 - https://docs.python.org/2/howto/unicode.html


Subtask 1
---------

Create method for creating new type with special behaviour (mixins).

Example:

```python
>>> class Creature(object):
...     def __init__(self, genus):
...         self.genus = genus
...     def sound(self, msg):
...         print "{0}: {1}".format(self.genus, msg)
...

>>>	class Man(Creature):
...     def __init__(self, name):
...         super(Man, self).__init__("man")
...         self.name = name
...

>>> class SingMixin(object):
...     def sing(self):
...         self.sound('La la li la, la la la!')
...

>>> man = Man('Yury')
>>> # I cannot sing!
>>> man.sing()
Traceback (most recent call last):
  File "...", line 20, in <module>
    man.sing()
AttributeError: 'Man' object has no attribute 'sing'
>>> Singner = Man.make_with_mixin(SingMixin)
>>> pavel = Singner("Pavel")
>>> pavel.sing()
man: La la li la, la la la!
```


Subtask 2
---------

Create simple linter metaclass wich can produce following checks:
 - All attrubutes have snake-case style.
 - All user methods do not empty docstrings.
 - All docstrings have one space delimeter between words.
 - Any additinal checks you would like to add.

Example:

```python
>>> from miscripts import LinterMeta
>>> class Creature(object):
...     __metaclass__ = LinterMeta
...     def __init__(self, genus):
...         self.genus = genus
...     def sound(self, msg):
...         print "{0}: {1}".format(self.genus, msg)
...

>>> man = Creature('man')
Traceback (most recent call last):
  File "...", line 20, in <module>
    man.sound
AttributeError: 'sound' has no documentation sting.
```


Subtask 3
---------

Create metaclass which can add cache with common life time (cache expires after 10 sec, e.g.) to all user methods:

Example:

```python
>>> from miscripts import CacheMeta
>>> from time import sleep
>>> class Foo(object):
...     __metaclass__ = CacheMeta
...     def __init__(self, x):
...         self.x = x
...     def mul(self, y):
...         # There is very long processing
...         sleep(10)
...         return self.x * y
...

>>> foo = Foo(100)
>>> # First calculatin
>>> foo.mul(10)  # Tooks 10 sec to get result.
1000
>>> # Second call with the same values reutrn result from cache.
>>> foo.mul(10)  # Returns result immidiatelly.
>>> # Third call after 15 sec tooks again about 10 sec.
>>> foo.mul(10)  # Tooks 10 sec to get result again. Cache expired.
1000
```

