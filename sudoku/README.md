# CIS 552 final project: Sudoku Game

CIS 552 Project Proposal

********************************************************************************************************

Description:

The overall goal of our project is to create Sudoku playing and solving libraries in Haskell. To achieve this goal, we will need to create or adapt four main functionalities: board generation, game play, game solver, and graphics. We would use GADTs to implement game generation by imposing invariants which ensure that each row, column, and box of the Sudoku board contains one of each of the integers from 1 through 9. For game play, we would want users to be able to provide input to empty cells and check their input against the solution for the board. In our game solver, we would like to implement an artificial intelligence algorithm - probably using inference using the AC-3 algorithm and backtracking (using a modified DFS algorithm) - to get to the final solved state of a particular board. Finally, we will use graphics capabilities on Hackage to give our game a GUI, but we may need to modify them to suit our needs.

********************************************************************************************************

Use Cases:

Use Case 1 - New Game:
As a user, I should be able to click on the “Start new game” button to generate a new sudoku board.

Use Case 2 - Difficulty Selection:
    As a user, I should be able to select a difficult level and receive a board within this difficulty that is solvable.

Use Case 3 - User interaction:
    As a user, I should be able to fill in empty cells with a value between 1 and 9 and check if my solution is correct by pressing on the “Check” button. If I enter a number outside of this range, I should be prompted to enter a different number.

Use Case 4 - Sudoku Solver:
As a user, I should be able to press on the “Solve” button to view the solution to the current board

********************************************************************************************************

Our implementation would consist of three main modules: Board, Solver, and Game. The Board module would control the creation of valid boards, the Solver module would control the algorithms used to solve boards that contain empty cells, and the Game module would interact with the user.

Brief Overview of Modules:
Board
Use GADTs to define a correct sudoku board
The GADTs will make sure that no column, row, or box contains duplicate values
Solver (use Board module)
AI algorithms that solve the current board
A ‘successor’ function that generates possible next moves, Inference with AC-3, Backtracking with modified DFS
Check if state is valid
Game (use Board and Solver modules)
Allows for user interaction
Interact with graphics
Check if state is valid after user moves - necessary because we won’t use the GADTs for user interaction

********************************************************************************************************

Testing with QuickCheck:

We can test the correctness of our Sudoku solver using QuickCheck:
For example, we can make check that every cell has been filled out after running the algorithm. We would want to make sure that the solver’s solution is valid - the duplicates property should be implicit because of GADTs, but we may also want to check that the cells have only values from 1 through 9
We can also check that none of the originally provided cells had their values changed.

Modifications:
We will not use GADTs for the user interaction portion of the GUI - instead, we will perform checks for a valid board state after the user provides input. This is to ensure that the game can recognize invalid user input
For difficulty levels:
Easy: 1 empty cell in every row, column, and block of the board
Medium: 2 or 3 empty cells in every row, column, and block of the board
Hard: 4 empty cells in every row, column, and block of the board
We will run the solver to make sure boards are solvable with certain cells removed before using them in the game
Solver algorithms: A ‘successor’ function that generates possible next moves, Inference with AC-3, Backtracking with modified DFS

Group: 
* Saniyah Shaikh (saniyah-shaikh)
* Victoria Huang (victoriahuang1)
