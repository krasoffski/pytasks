Pyttleship
==========

Pyttleship is python implementation of world-popular game [Battleship].

Battleship game rules
---------------------

In our python implementation of game we are going to follow Russian rules:

 - It is played on a 10x10 grid.
 - Player takes another shot on the same turn if an enemy ship is hit.
 - Ships cannot occupy squares next to each other, horizontally, vertically or diagonally.

|Type of ship                | Deckers | Ships |
|----------------------------|--------:|------:|
|battleship (линкор)         |    4    |   1   |
|cruiser (крейсер)           |    3    |   2   |
|destroyer (эсминец)         |    2    |   3   |
|submarine (подводная лодка) |    1    |   4   |


Pyttleship mandatory requirements
---------------------------------

 - Implemented with Python 2.7.x.
 - Uses only python standard library.
 - Follows the Model–View–Controller ([MVC]) software architectural pattern.
 - Respects [PEP8].
 - Utilizes [REST], [XML-RPC] or [JSON-RPC] as a communication mechanism (*REST is preferable*).
 - Uses powerful of [OOP] where it makes sense.
 - Provides usefull logging.
 - Can be launched on Linux.
 - Well documented.


Pyttleship not mandatory requirements
-------------------------------------

 - Can be launched on Windows.
 - Providers game statistics for all/each user.
 - Can be installed in system as python package (setup.py and whl).
 - Covered by unit tests.
 - Game statistics can be expoted to cvs file/stdout.
 - Provides API for adding plugings for expoting game statistics to other formats.
 - Supports multiplayer for Client-Server model.

##### Author
[Yury Krasouski]

##### Version
1.1.0

[Client-Server]:http://en.wikipedia.org/wiki/Client%E2%80%93server_model
[battleship]:https://en.wikipedia.org/wiki/Battleship_(game)
[MVC]:https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller
[P2P]:https://en.wikipedia.org/wiki/Peer-to-peer
[REST]:https://en.wikipedia.org/wiki/Representational_state_transfer
[XML-RPC]:https://en.wikipedia.org/wiki/XML-RPC
[JSON-RPC]:https://en.wikipedia.org/wiki/JSON-RPC
[OOP]:https://en.wikipedia.org/wiki/Object-oriented_programming
[PEP8]:https://www.python.org/dev/peps/pep-0008/
[Yury Krasouski]:mailto:krasoffski@gmail.com
