# Search Assignment Package

<a href="https://octodex.github.com/linktocat/" target="_blank">
<img src="https://octodex.github.com/images/linktocat.jpg" align="right" width="448px" title="Linktocat from Octodex" border="0"/>
</a>

Reference Implementation for Search Assignment  
Requires [pygame] :snake:  
Tested with [Python](https://www.python.org/) 2.7.9  
Check out this [Python](http://learnpython.org/) tutorial!

### Source:
- **common.py**             - Constants and map reading method
- **game.py**               - Engine with drawing functions
- **pathfinder.py**         - A* solver reference implementation
- **player.py**             - Character drawing calls

### Tests
- **test_pathfinder.py**    - Test suite for pathfinder

### Execution
- Execute interface with default map or filename.map
```
python game.py [filename.map]
```
- Execute terminal with default map or filename.map
```
python pathfinder.py [filename.map]
```
- Execute tests
```
python test_pathfinder.py
```

### Questions

Questions are in the [readme.txt](readme.txt) to be sent together with the code.

### Maps
- Maps hold the initial configuration of the scenario:
  - Where the player start, ```(X,Y)```
  - The tiles used at each cell in the grid, ```(0: Clear, 1: Closed, 2: Goal)```
- The method ```read_map(filename)``` of **common.py** loads maps from the **maps/** folder

- All maps are text-based files **(.txt)** and follow this specification:
```
player_x (0...width - 1)
player_y (0...height - 1)
cell0x0 cell1x0 ... cell(width-1)x0
cell0x1   ...
...
cell0x(height-1) ... cell(width-1)x(height-1)
```  

  - First line is player ```X```
  - Second line is player ```Y```
  - Map data in the following lines

- Why?
    - Uncompressed format that any text editor can modify
    - Easy to generate and check if valid:
        - Use **Find 2** to check if single goal tile is present
        - Use **Monospaced font** to see if map data matches a rectangle
    - Player position is defined outside of map data to allow any start configuration
        - Starting above the goal for example
- Constraints
    - All maps must be equal or larger than ```1x1```, and all rows must have same length
    - Only one player can be defined and must be within the limits of the map
    - Only one goal position can be defined
    - All tiles must be clear, closed or goal tiles
- Example
```
4
8
1111111111
1111111111
1111000211
1111011111
1000000111
1111011111
1111011111
1111011111
1111011111
1111111111
```

### Sprites
- Folder **sprites/** contains the images used.  
- The images must match the sizes specified by common.py both in dimensions and poses.  
- Default character poses are ```(Right 0, Left 1, Up 2, Down 3)```, therefore ```MOVE_UP = 2```.  
- Tileset is loaded according to hardcoded numbers, default is ```3``` tiles in a single line: ```[][][]```
- The current sprites are copyrighted by Nintendo from **The Legend of Zelda: A Link to the Past** and **Pokemon Red/Blue** games, they are a subset of the original being used for educational purposes.
- Linktocat is part of the Octodex: https://octodex.github.com/linktocat/
[pygame]:http://www.pygame.org/news.html

### Python 3.4

Ops, some things do not work as expected on Python 3.4:

- prints require parenthesis ```print("Hello")```.
- Queue does not need to be imported, comment line ```import Queue``` from file pathfinder.py.
