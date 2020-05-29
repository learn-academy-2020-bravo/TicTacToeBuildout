# Tic Tac Toe Buildout

**As a user, I should start off seeing a 3x3 grid on the main page.**

- Create a component called Square.js with a div
- Give square some dimensions and a border
- Since we need to map over the squares, we need an array to hold those values
- Create a state object
- Map over the Square component to generate 9 squares on the board
- Pass value/index to Square.js
- Format the Squares to create a gameboard
- Add a Header

**As a user, I should be able to click on a square to mark it.**
- Start with getting the index of each square onClick in Square.js with a method called handleClick
- Having each Square knowing where it lives isn't super helpful
- Move the logic into App.js
- Create a method in App.js called squareClick that takes an argument creates an alert
- Pass this method as props to Square.js
- Update handleClick in Square.js to call squareClick and pass the argument of this.props.index
- Now we get the same result but App.js is handling the logic and not Square.js
- Update the method to show the index in the square when the box is clicked rather than as an alert
- Now rather than the index, set the board with a marker - just starting with one player
- Add a current player to the state object, currentPlayer: "🍣"
- Update the squareClick method
- Add more styling to square

**As a user, my partner should be able to click on a square after me and see their mark.**

- Current player needs to be able to toggle
- Update the currentPlayer item in state after every click with a ternary operator

**As a user, I shouldn't be able to click on a square that has already been selected.**

- The state should only be set if the current value is null
- Wrap all the logic in squareClick in an if statement

**As a user, when someone has won the game (3 squares in a row: horizontally, vertically, or diagonally) I should see a notice telling me who won.(done)**

- The big daddy of user stories
- Create a separate function to handle the winning condition
- Create a matrix (an array of arrays) for all the possible combinations of winning indexes
```
winning = () => {
   let winningConditions = [
     [0, 1, 2],
     [3, 4, 5],
     [6, 7, 8],
     [0, 3, 6],
     [1, 4, 7],
     [2, 5, 8],
     [0, 4, 8],
     [2, 4, 6],
   ]
 }
 ```
- map over the array so that each value is one set of three indexes
- Call the winning method in the squareClick method and see the value log on each click
- Destructure the array and log each item, a/b/c represents each index listed in the array
```
const [a, b, c] = value
```
- check for the initial value and log `a`
- This console log shows the three possible trilogies of win conditions for this player starting at index 0
- The index of 0 in the gameboard has been updated to hold the value of sushi emoji
- Update the if statement to look for more values held by one player
- The value at location [a] on gameBoard is sushi, then value at location [b] is sushi
- Now clicking on just one square doesn't satisfy the condition anymore, they both must be held by sushi to meet the condition
- Add in the evaluator for `b == c`
- Now we have to set the state to declare a winner
- Add an item to the state object: winner: null
- Set the state of the current player in the winning method
- Print the winner on the page

**As a user, I should not be able to continue playing the game after the game has been won.**

- Update the if statement in squareClick so the click can only happen if winner === null
- Wrap the winning function call in an if statement that only runs if winner === null
