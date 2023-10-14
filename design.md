# Gambit Design

## Summary 
The goal for Gambit is to generage mainline and sideline variations for opening preperation.
It will use a UCI chess engine along with LiChess's games database to generate and explore the variations.
It will use a SQL like language to help generate the resulting PNG which could be imported to LiChess or 
another tool for further analysis. 

Gambit will be a command line application. You can supply the gambit command with a .gambit file or nothing 
at all. The .gambit file will contain the SQL like language to generate the PGN file. If you don't supply the
.gambit file, it will allow to use the REPL interface.

## Command Usage
* `gambit` will take you to the REPL interface
* `gambit run <.gambit file>` will evaluate the gambit file. 
* `gambit set-engine <engine binary location>` sets the default engine.
* `gambit set-engine <engine binary location> <engine-name>` assigns the engine to a name
  
## Gambit Chess Position Analysis Language
This is the SQL like language that will be used in the .gambit files and the REPL interface to compute variations and 
perform analysis on the chess position. The reasoning behind this is that there are certain facts about a chess position
that can be queried. For example,
* If you wanted to know all moves in a position, then the query could look like this `select moves from position`
* If you wanted to know the best move in a position, then the query could look like this
  `select top(moves) from position`
* If you wanted a list of moves that masters have played in the position ranked by popularity, then the query could look like this, `select moves from position where master_games > 0 order by master_games` 

The language will also allow you to do the following:
* Load PGN's from a file and store as a variable
* Load FEN's from a file and store as a variable
* Save results of computation to a PGN file