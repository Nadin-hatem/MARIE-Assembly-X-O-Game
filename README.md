# ❌⭕ X-O Game in MARIE Assembly

A low-level Tic Tac Toe (X-O) game written in **MARIE Assembly Language**.
> 🎮 Grid Layout:
 1 | 2 | 3
---+---+---
 4 | 5 | 6
---+---+---
 7 | 8 | 9


# 🧠 Features
- Turn-based player input
- Move validation (no overwriting)
- Grid printing after every move
- Win condition checks for 'X' (row, column, diagonal)
- ASCII output of winning message or invalid move


# 🏗 How It Works
- `UserInput`: Takes user input and maps it to grid positions.
- `CheckContains`: Checks if a cell is empty before allowing the move.
- `Print`: Displays the current grid using ASCII characters.
- `CheckWinX`: Evaluates all 8 win conditions for X.
- `AlreadyPlaced`: Prints an error if the spot is taken.
- `XWin`: Prints the winning message if X wins.

# 💾 Key Memory Labels
| Label           | Purpose                              |
|----------------|--------------------------------------|
| `Pos1`-`Pos9`   | Holds player moves (grid positions)  |
| `X` / `O`       | ASCII for X (`HEX 2715`), O (`HEX 25EF`) |
| `XPlayCount`    | Counts number of X moves             |
| `Xwinner`       | Message memory for "X Wins!"         |
| `AlreadyPlace`  | Message memory for "Invalid Position"|

# 🛠 Tech Stack
- 💻 MARIE Assembly (Simulator)
- 🧮 Low-level memory & instruction control
- 🖨 ASCII-based I/O operations

# 🧪 Sample Logic Flow
```asm
PlayX,  
  JnS UserInput        / get user input
  JnS CheckContains    / validate if empty
  JnS Print            / show updated board
  JnS CheckWinX        / did X win?
  Load XPlayCount
  Add One
  Store XPlayCount
  Subt Five
  Skipcond 400         / if 5 X moves reached, end
  Jump PlayX
  Halt
