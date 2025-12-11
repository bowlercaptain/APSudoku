# APSudoku
Classic Sudoku Game
- Play Sudoku at 4 different difficulty levels:
  - **Easy**: 46 givens, 10% progression hint chance
  - **Normal**: 35 givens, 40% progression hint chance
  - **Hard**: 26 givens, 80% progression hint chance
  - **Killer**: 26 givens, 60% progression hint chance
    - In Killer mode, outlined cages must sum to the indicated total
    - Each cage follows standard Sudoku rules (no repeated digits within a cage)
- Connect to [Archipelago Randomizer](https://archipelago.gg/)
  - Earn hints:
    - Completing a puzzle grants you a random hint for a location in the slot you are connected to
    - Harder difficulty puzzles are more likely to hint a 'Progression' type item
  - DeathLink support (Set before connecting!)
    - Lose a life if you check an incorrect puzzle (not an _incomplete_ puzzle), or quit a puzzle without solving it (including disconnecting).
    - Life count customizable (default 0). Dying with 0 lives left kills linked players AND resets your puzzle.
    - On receiving a DeathLink from another player, your puzzle resets.

## Planned Variant Features
Future updates will expand the game with additional Sudoku variants:

### Parity Lines
- Lines marked on the grid where digits must alternate between odd and even
- Solver/setter will enforce that consecutive cells along parity lines have different parity
- Rendered as colored lines connecting cell centers

### Off-board Numbers
- Clue numbers placed outside the grid indicating sums or other constraints
- Examples include:
  - **Sandwich Sudoku**: Numbers outside indicate the sum of digits between 1 and 9
  - **X-Sums**: Numbers outside indicate the sum of the first X digits (where X is the first digit)
  - **Skyscraper**: Numbers outside indicate how many "buildings" are visible from that direction
- Solver/setter will validate these external constraints during puzzle generation and solving
- Rendered with numbers positioned outside the grid borders with directional indicators

### Implementation Plan
These variants will require:
1. **Data Structure Extensions**: Add variant metadata to puzzle representation (line coordinates, external clue positions/values)
2. **Solver Enhancement**: Extend constraint checking to validate variant-specific rules during puzzle validation
3. **Generator Enhancement**: Modify puzzle generation algorithm to incorporate variant constraints and ensure unique solutions
4. **Renderer Updates**: Add visual rendering for variant elements (colored lines, external numbers, etc.)
5. **UI Updates**: Add variant selection options to the difficulty menu

## Building
Clone with `--recursive` to include the submodules!

### Windows
- Install CMake
- Install NuGet CLI
- Run `initialize.bat`, which should install dependencies via NuGet and run CMake for you.

### Linux
- Install CMake
- Install NuGet CLI
- Install libfmt-dev
- Run `initialize.bat`, which should install dependencies via NuGet and run CMake for you.
- Go to `build/` and run `make`.
