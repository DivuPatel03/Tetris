# Console Tetris in C++

## Description
This is a feature-rich console-based Tetris game written in C++ for Windows. The game recreates the classic Tetris experience where players manipulate falling tetrominos to create complete horizontal lines. It features colorful console graphics, ghost piece preview, score tracking, difficulty progression, and smooth gameplay using Windows console functions.

## Features
- Console-based graphics with colored tetrominos
- Next piece preview window
- Ghost piece showing where the tetromino will land
- Progressive difficulty with increasing speed as lines are cleared
- Score system with bonuses for hard drops (2 points) and soft drops (1 point)
- Wall kick implementation for rotation near boundaries
- Pause menu with options to continue, restart, or quit
- Game over screen with high score tracking
- Smooth rendering using console buffer techniques

## Data Structure Analysis
This game utilizes several data structures for efficient game logic:
- **2D Vectors (`board`, `currentTetromino`, `nextTetromino`)**: Store the game board state and tetromino shapes
- **CHAR_INFO Array (`consoleBuffer`)**: Double-buffering technique for smooth console rendering
- **Constants (`TETROMINOS`)**: 3D vector storing all possible tetromino shapes (I, O, T, S, Z, J, L)
- **Enum (`ConsoleColor`)**: Defines color values for visual representation of different tetrominos
- **Integer Variables (`score`, `highScore`, `level`, `linesCleared`)**: Track player progress and game state
- **Random Number Generator (`mt19937`)**: Provides randomized tetromino generation

## Controls
```
← → - Move tetromino horizontally
↑ - Rotate tetromino clockwise
↓ - Soft drop (faster descent with points)
Space - Hard drop (instant placement with bonus points)
ESC - Pause game
R - Restart game (when paused or game over)
Q - Quit game (when paused or game over)
C - Continue game (when paused)
```

## How to Run
1. Compile the code using a C++ compiler with Windows API support
2. Run the compiled executable in a console window
3. Follow the on-screen instructions to play the game

## Compilation Instructions
Using g++:
```sh
g++ Tetris.cpp -o Tetris.exe
```
Run the executable:
```sh
./Tetris.exe
```

## Game Logic
1. The game starts with a welcome screen displaying controls
2. Tetrominos fall from the top of the board at a rate determined by the current level
3. Players can move, rotate, and accelerate the descent of tetrominos
4. A ghost piece shows where the current tetromino will land
5. When a horizontal line is filled completely, it clears and awards points
6. The game speeds up as the player clears more lines (every 10 lines)
7. Game ends when a new tetromino cannot spawn without collision
8. High scores are tracked between game sessions

## Technical Implementation Details
- **Console Buffer Rendering**: Uses `CHAR_INFO` array and `WriteConsoleOutput` for flicker-free rendering
- **Block Characters**: Uses ASCII character 219 (█) for blocks and 176 (░) for ghost pieces
- **Color Coding**: Each tetromino type has a unique color for easy visual distinction
- **Time Management**: Uses `chrono` library for controlling tetromino falling speed
- **Rotation System**: Implements wall kicks to allow rotation near walls and other blocks
- **Scoring System**: 
  - Line clears: `100 * level * linesCompleted * linesCompleted`
  - Soft drop: 1 point per cell
  - Hard drop: 2 points per cell

## Dependencies
- Windows Console API (for console manipulation functions)
- Standard C++ libraries
- C++11 or higher compiler support

## Known Issues
- The game is designed for Windows console only and won't run on other platforms
- Console dimensions must be sufficient to display the game board and UI elements
- Some terminals may not properly support all color combinations

## Future Improvements
- Add sound effects for line clears and game events
- Implement a hold piece feature
- Create a global leaderboard system
- Add customizable control options
- Support for Linux and macOS terminals

## License
This project is open-source and free to use. Modify and improve as needed!
