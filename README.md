# PSU_Navy_2019
 You sunk my battelship !

### SUBJECT
You must code a terminal version of this game.
The two players are ONLY allowed to comunicate using the signals SIGUSER1 and SIGUSER2.
The map size is 8x8. On each turn, you must display your positions, and then your enemy’s positions.
At the end of the game (when all the ships of a player have been hit), you must display whether “I won” (and return 0) or “Enemy won” (and return 1).

```
∼/B-PSU-200> ./navy -h
USAGE
  ./navy [first_player_pid] navy_positions
DESCRIPTION
  first_player_pid: only for the 2nd player. pid of the first player.
  navy_positions: file representing the positions of the ships.
```
The file passed as parameter must contain lines formatted the following way:
```
LENGTH : FIRST_SQUARE : LAST_SQUARE
```
where LENGTH is the length of the ship, FIRST_SQUARE and LAST_SQUARE its first and last positions.
In this file, you must have 4 ships (of lengths 2,3,4 and 5).
If the navy file is invalid, you have to quit the program and consider it as an error.

### EXAMPLE
Here is an example game.
The user inputs are written between *.
```
∼/B-PSU-200> cat pos1
2:C1:C2
3:D4:F4
4:B5:B8
5:D7:H7
```
```
∼/B-PSU-200> cat pos2
2:C4:D4
3:H1:H3
4:E6:H6
5:B1:F1
```

### CONNECTION
Player 1
```
∼/B-PSU-200> ./navy pos1
my_pid: 4242
waiting for enemy connection...
enemy connected
```
Player 2
```
∼/B-PSU-200> ./navy 4242 pos2
my_pid: 4250
successfully connected
```

### TURN #1
Player 1 
```
my positions:
|A B C D E F G H
-+---------------
1|. . 2 . . . . .
2|. . 2 . . . . .
3|. . . . . . . .
4|. . . 3 3 3 . .
5|. 4 . . . . . .
6|. 4 . . . . . .
7|. 4 . 5 5 5 5 5
8|. 4 . . . . . .
enemy’s positions:
|A B C D E F G H
-+---------------
1|. . . . . . . .
2|. . . . . . . .
3|. . . . . . . .
4|. . . . . . . .
5|. . . . . . . .
6|. . . . . . . .
7|. . . . . . . .
8|. . . . . . . .
attack: *Z0*
wrong position
attack: *B6*
B6: missed
```

Player 2
```
my positions:
|A B C D E F G H
-+---------------
1|. 5 5 5 5 5 . 3
2|. . . . . . . 3
3|. . . . . . . 3
4|. . 2 2 . . . .
5|. . . . . . . .
6|. . . . 4 4 4 4
7|. . . . . . . .
8|. . . . . . . .
enemy’s positions:
|A B C D E F G H
-+---------------
1|. . . . . . . .
2|. . . . . . . .
3|. . . . . . . .
4|. . . . . . . .
5|. . . . . . . .
6|. . . . . . . .
7|. . . . . . . .
8|. . . . . . . .
waiting for enemy’s attack...
B6: missed
attack: *4*
wrong position
attack: *C1*
C1: hit
```

### LAST TURN
Player 1
```
attack: *H6*
H6: hit
my positions:
|A B C D E F G H
-+---------------
1|o . x o . o . o
2|. . 2 . . o . .
3|. o . . o . . .
4|. . . x x x . .
5|. x o . . o o .
6|. x . . . . . .
7|o x . x x x 5 5
8|. x . o . o . o
enemy’s positions:
|A B C D E F G H
-+---------------
1|. x x x x x . x
2|. . . o . o . x
3|. o . . . . o x
4|. . x x o . . o
5|. . . . . o . .
6|. o . . x x x x
7|. . o . . . o .
8|. . . . . o . .
I won
```
Player 2
```
waiting for enemy’s attack...
H6: hit
my positions:
|A B C D E F G H
-+---------------
1|. x x x x x . x
2|. . . o . o . x
3|. o . . . . o x
4|. . x x o . . o
5|. . . . . o . .
6|. o . . x x x x
7|. . o . . . o .
8|. . . . . o . .
enemy’s positions:
|A B C D E F G H
-+---------------
1|o . x o . o . o
2|. . . . . o . .
3|. o . . o . . .
4|. . . x x x . .
5|. x o . . o o .
6|. x . . . . . .
7|o x . x x x . .
8|. x . o . o . o
Enemy won
```

### BONUS
Here are some example of bonus :
- play against an AI,
- a nice interface, music, etc...,
- multiplayer mode with more than two players,
- customize game,
- networking,
- and whatever you feel like.
