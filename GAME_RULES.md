# F# WPF Dice Guessing Game - Game Rules and Mechanics

## Core Game Flow
1. **Dice Generation**: Computer randomly generates three dice values (1-6 each)
2. **Sorting**: Dice values are sorted from smallest to largest
3. **Sum Display**: The sum of all three dice is revealed to the player
4. **Player Guessing**: Player inputs guesses for each die value
5. **Validation**: Game validates guesses against multiple criteria
6. **Feedback**: Appropriate feedback is provided based on validation results
7. **Win Detection**: Game checks for correct guess and ends if successful

## Validation Rules (in order of priority)

### Rule 1: Non-decreasing Order
- **Requirement**: Guesses must be in non-decreasing order (smallest to largest)
- **Example**: [2, 3, 5] is valid, [3, 2, 5] is invalid
- **Feedback**: "Guesses must be in non-decreasing order (smallest to largest)"

### Rule 2: Correct Sum
- **Requirement**: Sum of guesses must equal the revealed total
- **Example**: If sum is 10, [2, 3, 5] is valid, [1, 3, 5] is invalid
- **Feedback**: "Guesses must add up to the revealed total"

### Rule 3: Correct Values
- **Requirement**: Guesses must match the actual dice values
- **Example**: If dice are [2, 3, 5], [2, 4, 4] is incorrect (passes sum but wrong values)
- **Feedback**: "Incorrect guess, try again"

### Rule 4: Win Condition
- **Requirement**: All three guesses match the actual dice values
- **Result**: Player wins, game ends with victory message

## Input Constraints
- Each die guess must be an integer between 1 and 6
- Player must provide exactly three guesses
- Input is done via mouse-driven UI (no keyboard input)

## Game States
1. **Initial State**: Dice generated, sum displayed, waiting for first guess
2. **Guessing State**: Player entering guesses, validation in progress
3. **Invalid State**: Guess rejected, feedback displayed, waiting for new guess
4. **Win State**: Correct guess detected, victory message displayed

## Error Handling
- Invalid input (non-numeric, out of range) is rejected with appropriate message
- Partial guesses are not accepted until all three values are provided
- Game maintains state between invalid guesses