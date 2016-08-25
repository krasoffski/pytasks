# Pyttleship

Pyttleship is python implementation of world-popular game [Battleship].

## Battleship game rules

In our python implementation of game we are going to follow Russian rules:

 - It is played on a 10x10 grid.
 - Player takes another shot on the same turn if an enemy ship is hit.
 - Ships cannot occupy squares next to each other, horizontally, vertically or
   diagonally.

|Type of ship | Deckers | Ships |
|-------------|--------:|------:|
|battleship   |    4    |   1   |
|cruiser      |    3    |   2   |
|destroyer    |    2    |   3   |
|submarine    |    1    |   4   |


## Pyttleship mandatory requirements

 - Implemented with Python 2.7/3.5 (or compatible with both of them).
 - Uses only python standard library.
 - Respects [PEP8].
 - Utilizes [REST] , as a communication mechanism.
 - Uses powerful of [OOP] where it makes sense.
 - Provides usefull logging.
 - Should be launched on Linux.
 - Well documented.
 - Covered by unit tests.


## Pyttleship not mandatory requirements

 - Providers game statistics for all/each user.
 - Can be installed in system as python package (setup.py and whl).
 - Game statistics can be exported to csv file/stdout.
 - Provides API for adding plug-ins for exporting game statistics to other
   formats.
 - Supports multi-player model (a few games at the same time).


##### Author
Yury Krasouski

##### Version
1.1.2

[battleship]:https://en.wikipedia.org/wiki/Battleship_(game)
[REST]:https://en.wikipedia.org/wiki/Representational_state_transfer
[OOP]:https://en.wikipedia.org/wiki/Object-oriented_programming
[PEP8]:https://www.python.org/dev/peps/pep-0008/
