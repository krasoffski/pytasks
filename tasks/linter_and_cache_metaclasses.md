# Class linter and cache metaclasses


## Helpful information

Study following links:
 - http://blog.ionelmc.ro/2015/02/09/understanding-python-metaclasses/


## Subtask 2

Create simple linter metaclass which can perform following checks:
 - All attributes have snake-case style.
 - All user methods do not have empty documentation strings.
 - All documentation strings have one space delimiter between words.
 - Any additional checks you would like to add.

Example:

```python
class Creature(Linter):
    def __init__(self, genus):
        self.genus = genus
    def sound(self, msg):
        print("{0}: {1}".format(self.genus, msg))
```

Interactive usage example:
```python
>>> man = Creature('man')
Traceback (most recent call last):
 File "...", line 20, in <module>
   man.sound
LinterError: 'sound' has no documentation sting.
```


## Subtask 2

Create metaclass which can add cache with common life time 
(cache expires after 10 sec, e.g.) for all user methods:

Example:

```python
from cache import Cache
from time import sleep


class Foo(Cache):
    def __init__(self, x):
        self.x = x
    def mul(self, y):
        # Here is very long computation.
        sleep(10)
        return self.x * y
```

Interactive usage example:
```python
>>> foo = Foo(100)
>>> # First calculation.
>>> foo.mul(10)  # Takes 10 sec to get result.
1000
>>> # Second call with the same values return result from cache.
>>> foo.mul(10)  # Returns result immediately.
1000
>>> # Third call after 15 sec takes again about 10 sec.
>>> foo.mul(10)  # Takes 10 sec to get result again. Cache expired.
1000
```
