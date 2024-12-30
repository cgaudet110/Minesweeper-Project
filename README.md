# How to Play Minesweeper in OCaml

## Authors

- Caroline Gaudet (cmg283)
- AjayPaul Nagyal (asn68)
- Ignacio Estrada Cavero (ire2)
- Teg Singh (ts647)

## Prerequisites

Ensure you have the following installed:

- **OCaml**: for compiling the code.
- **Dune**: OCaml’s build system.
- **Js_of_ocaml**: for compiling OCaml to JavaScript.
- **Python** (optional): to run a local server for viewing the game in a browser.

## Project Structure

```
project-root/
│
├── lib/
|   ├── dune
│   ├── board.ml        # Board logic
│   ├── load.ml         # Rendering and drawing
|
|── test/
|   |── dune
|   |── test_canit.ml   # Test suite file
│
├── main.ml             # Main game logic
│
├── index.html          # HTML for displaying the game
│
├── dune                # Dune build configuration
├── dune-project        # Dune project descriptor
```

## How to Build & Run the Game

### 1. **Navigate to the Project Root**

Go to the main directory of the project:
```bash
cd <project-root>
```

### 2. **Build the Project**

Run the following command:
```bash
dune build
```

- This will compile the OCaml code and create the JavaScript output in `_build/default/main.js`.

### 3. **Serve the HTML File**

Use Python to start a local server and view the game in your browser:
```bash
python3 -m http.server
```

- Once the server is running, open a browser and navigate to:
  ```
  http://localhost:8000
  ```
- Locate `index.html` in the browser to load the game.

### 4. **How to Play**

- Once the game loads, you will see a 10x10 grid of cells.
- **Revealing Cells**: 
  - Click on any cell to reveal it.
  - If the cell contains a mine, you lose, and the game ends.
  - If the cell is empty or displays a number, the game continues.

### Key Code Lines

- **Initialize the Game**:
  - In `main.ml`, look for:
    ```ocaml
    let initial_state = Board.initialize_game ()
    ```
  - This line sets up the board and places the mines.

- **Render Board**:
  - The `Load.render_board` function handles drawing the cells on the canvas.
  - Located in `load.ml`, it updates the visual state of the board based on the current game state.

- **Handle Clicks**:
  - In `main.ml`, the `handle_click` function processes clicks on the grid, updates the game state, and triggers re-rendering.

### Known Limitations

- Mines are not yet flagged.
- Winning detection is not implemented.
- Refresh the page to reset the game.

## Troubleshooting

- If nothing appears on the screen:
  - Ensure `dune build` completed without errors.
  - Check the browser’s console for any JavaScript errors.
  - Verify that `main.js` is correctly linked in `index.html`.

## Next Steps

- Implement mine flagging.
- Add winning detection.
- Add a game restart button and an in-game timer.
- Add different board sizes
- Implement in a way so that more than one box appears at once (like it does on Google's minesweeper)
- Make it so that you can't click on a bomb with the first click