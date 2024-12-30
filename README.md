# About
Our project is a minesweeper game inspired by Google's "Minesweeper".
The object of the game is to uncover all non-mine cells in the grid without
setting off any hidden mines.

Click on cells in the grid to reveal if there is a hidden mine.
Cells clicked on will either end the game if there is a mine, 
say how many mines are adjacent, or be blank meaning there are no adjacent mines.

This project was developed on the GitHub Enterprise repository located at this URL: <https://github.coecis.cornell.edu/ire2/CANIT> <br>
This repository was created to organize and clean up parts of the original project for showcase purposes. To see full commit history, please refer to the original repository linked above.

## Authors

- Caroline Gaudet (cmg283)
- AjayPaul Nagyal (asn68)
- Ignacio Estrada Cavero (ire2)
- Teg Singh (ts647)


## Installation instructions

Ensure you have the following installed:

- **OCaml**: for compiling the code.
- **Dune**: OCaml’s build system.
- **Js_of_ocaml Packages**: for compiling OCaml to JavaScript.
```bash
opam install js_of_ocaml js_of_ocaml-ppx js_of_ocaml-lwt
``` 
- **Python**: to run a local server for viewing the game in a browser.


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

## Troubleshooting

- If nothing appears on the screen:
  - Ensure `dune build` completed without errors.
  - Check the browser’s console for any JavaScript errors.
  - Verify that `main.js` is correctly linked in `index.html`.

### 4. **How to Play**

- Once the game loads, you will enter a username to begin playing. Then you must select a difficulty, corresponding to board size. Hit the "play" button to officially start the game.
- **Revealing Cells**: 
  - Click on any cell to reveal it.
  - If the cell contains a mine, you lose, and the game ends.
  - If the cell is empty or displays a number, the game continues.


## Project Structure

```
project-root/
│
├── lib/
|   ├── dune
│   ├── board.mli           # Board logic
│   ├── board.ml       
│   ├── load.mli            # Rendering and drawing
│   ├── load.ml
│   ├── canvas_utils_js.mli # JS OCaml functions and type aliases for better readability
│   ├── canvas_utils_js.ml
│   ├── canvas_utils.mli    # Other functions and type aliases
│   ├── canvas_utils.ml
│   ├── csv_manager.ml      # Managing of CSV files that keep track of player scores
│   ├── timer.mli           # Countint seconds in gameplay
│   ├── timer.ml
|
|── test/
|   |── dune
|   |── test_canit.ml       # Main test suite file
│   ├── test_csv_manager.ml # CSV manager test suite
│   ├── test_timer.ml       # Timer test suite
│
|── images/
│   ├── timer.svg           # Stopwatch icon for game timer
|
├── main.ml                 # Main game logic
│
├── index.html              # HTML for displaying the game
|
├── AUTHORS.md              # Acknowledgements and citations
│
├── dune                    # Dune build configuration
├── dune-project            # Dune project descriptor
```