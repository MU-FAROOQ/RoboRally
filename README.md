# RoboRally
This is a grid based board game. Players have to touch/collect all flags in order of number. First to do this wins.

CS1410 - Java Program Development - 2019

# Usage
The game uses 2 files. A Program (.prg) file and a Board (.brd) file.

## Program File
Maximum of 4 players.

This file contains the player moves. There are 5 different actions.

• F - Move forward one space

• B - Back up one space

• L - Rotate 90 degrees Left

• R - rotate 90 degrees Right

• U - do a U-turn

• W - Wait

You may not repeat an action twice in a row: “FFLWF” is not valid, but “FWFLF” would be valid.

### Example 1
```
format 1
Alice Bob
RFLFW LFWFR
FWLWB LRLRL
```

### Example 2
```
format 1
Alice Bob Charlie Doug
FLFWF WFWFL RFWFL FRWRF
```

Robots will operate in player order, executing the action in the first slot, then the locations where
the robots are will activate, and the first player token pases to the next player. This is repeated
with the second, third, fourth and fifth slots.

As an example, with player A and player B having decided on “FLFWF” and “WFWFL”, and with
A starting with the first player token, this will happen:

(a) A “F” is executed, then B “W”. Board activates. First player token passes to B.

(b) B “F” is executed, then A “L”. Board activates. First player token passes to A.

(c) A “F” is executed, then B “W”. Board activates. First player token passes to B.

(d) B “F” is executed, then A “W”. Board activates. First player token passes to A.

(e) A “F” is executed, then B “F”. Board activates. First player token passes to B.

There are some additional rules for movement:

• If a robot moves into a position occupied by another robot, it pushes that other robot one space
away in the same direction. The robot being pushed may push another robot, and so on.

• If a robot moves outside the board, it is destroyed. Move the robot back to its starting position.
If the starting position is occupied, try the position adjacent to the north, then east, south, and
finally west.


## Board File
Maximum 8x12 board size.

This file contains the structure of the board/grid. There are 5 different actions.

• A period (.) represents a position with no locations (it is empty).

• A to D are the starting positions of the maximum 4 players we can have in the game.

• + and - are gears (+ rotates clockwise, - rotates counter-clockwise).

• 1 to 4 are the maximum 4 flags you can have, to be visited in this order.

• x is a pit, which destroys your robot and returns it to its starting position.

• v, >, < and ˆ are straight conveyor belts which upon activation, move your robot one space
down, right, left or up, respectively.

• N, E, S and W are the clockwise corner conveyor belts, and n, e, s and w are the counter-clockwise corner conveyor belts. The clockwise conveyor belts will turn your robot to the right if and only if it is carried onto that location by another
conveyor belt. Likewise, the counter-clockwise conveyor belts will turn the robot to the left
on that situation.

Upon activation, N/n will move the robot north, S/s south, W/w west, and E/e east.

### Example 1
```
format 1
........
...1....
........
..A..B..
........
```

### Example 2
```
format 1
.....+......
.1.s<<w.E>>S
...v.2^.^..v
...e>>n.N<<W
...-........
.x....x.....
.....CABD...
............
```
