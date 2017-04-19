# Descriptors and ORM concept

## Helpful information

Study following links:
 - https://docs.python.org/2/howto/descriptor.html
 - http://www.ibm.com/developerworks/library/os-pythondescriptors/
 - https://speakerdeck.com/lig/your-own-orm-in-python-how-and-why
 - https://www.smallsurething.com/python-descriptors-made-simple/

Additional topics which might help you with home tasks:
 - https://github.com/coleifer/peewee/blob/master/peewee.py
 - https://peewee.readthedocs.org/en/latest/
 - https://wiki.python.org/moin/HigherLevelDatabaseProgramming


## Subtask 1

Create simple data descriptors like `BirthdayField`, `NameField`, `PhoneField`
which can perform simple check of types and values.

Example:

```python
>>> from datetime import datetime
>>> from fields import BirthdayField, NameField, PhoneField
>>> class Person(object):
...     name = NameField()
...     birthday = BirthdayField()
...     phone = PhoneField()
...
>>> yury = Person()
>>> print yury.name
None
>>> yury.name = "Yury Krasouski"
>>> print yury.name
Yury Krasouski
>>> yury.birthday = datetime.strptime("1986-04-09", "%Y-%m-%d")
>>> yury.phone = "375 25 9355570"
>>> print yury.phone
375 (25) 935-55-70
>>> print yury.birthday
1986-04-09 00:00:00
>>> yury.birthday = "April 09"
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: Birthday must be datetime type
>>> yury.name = None
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: Name must be str type
>>> yury.phone = "375 (25) 9355570"
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: Phone must be in format XXX XX XXXXXXX
etc.
```


## Subtask 2

Create non-data descriptor like `DocAPI` which can provide class-level and
instance-level documentation about methods and attributes.

Example:

```python
>>> from miscripts import DocAPI
>>> class Foo(object):
...     __doc__ = API()
...     def __init__(self, x):
...         self.x = x
...     def meth(self, y):
...         """Multiplies two values self.x and y."""
...         return self.x * y
...
>>> print Foo.__doc__
meth : Multiplies two values self.x and y.
>>> foo = Foo(10)
>>> print foo.__doc__
x : int
meth : Multiplies two values self.x and y.
```


## Subtask 3

Create simple [ORM] using data descriptors like in `Subtask 1` which stores
descriptor values in a database or files. E.g and [SQLite3].

Example:

```python
>>> from ormapi import Model, BirthdayField, NameField, PhoneField
>>> class Person(Model):
...    name = NameField()
...    birthday = BirthdayField()
...    phone = PhoneField()
...
>>> p = Person()  # New row in table *persons* are created with default values for fields.
>>> p.name = "Yury"  # Cell updated with new value.
>>> # Or you can create special method to save (commit) the values to DB like bellow.
>>> p.phone = "375 25 9355570"  # Not yet stored in DB.
>>> p.save()  # All changes saved.
```
_Note: Implementation of method `Model.save()` is up to you. You can save
value within `__set__` method of descriptors._

_Note: This task requires knowledge of class decorators or metaclasses magic._


[ORM]: https://en.wikipedia.org/wiki/Object-relational_mapping
[SQLite3]: https://en.wikipedia.org/wiki/SQLite
