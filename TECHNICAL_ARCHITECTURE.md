# F# WPF Dice Guessing Game - Technical Architecture

## Software Architecture

### MVVM Pattern Implementation
The application follows the Model-View-ViewModel (MVVM) architectural pattern to ensure separation of concerns and testability.

#### Components:
1. **Model Layer**
   - `DiceGameModel`: Core game logic and state management
   - `Dice`: Represents individual dice with value and position
   - `GameState`: Enum for game states (Initial, Guessing, Invalid, Win)

2. **View Layer**
   - `MainWindow.xaml`: Main window layout and controls
   - `DiceControl.xaml`: Custom control for dice visualization
   - `InputControl.xaml`: Custom control for guess input

3. **ViewModel Layer**
   - `MainViewModel`: Orchestrates game flow and user interactions
   - `DiceViewModel`: Manages dice display and animations
   - `InputViewModel`: Handles guess input and validation

## Core Classes and Responsibilities

### Model Classes
```fsharp
type Dice = {
    Value: int
    Position: int
}

type GameState =
    | Initial
    | Guessing
    | Invalid
    | Win

type DiceGameModel = {
    Dice: Dice array
    Sum: int
    GameState: GameState
    Guesses: int array option
}
```

### ViewModel Classes
```fsharp
type MainViewModel() =
    member val GameModel: DiceGameModel = initialModel with get, set
    member val FeedbackMessage: string = "" with get, set
    member val IsSubmitEnabled: bool = false with get, set
    
    member this.NewGame() = // Initialize new game
    member this.SubmitGuess() = // Validate and process guess
    member this.UpdateGuess(index, value) = // Update individual guess
```

## Data Flow

### Game Initialization
1. `NewGame()` called from ViewModel
2. Model generates random dice values
3. Dice are sorted internally
4. Sum is calculated
5. GameState set to Initial
6. View updates to display sum

### Guess Processing
1. User clicks input areas to set guesses
2. ViewModel updates Guesses array
3. Submit button enabled when all guesses set
4. `SubmitGuess()` validates in this order:
   - Non-decreasing order
   - Correct sum
   - Correct values
5. Feedback provided based on validation result
6. GameState updated accordingly

## Validation Logic

### Validation Functions
```fsharp
let validateNonDecreasing (guesses: int array) =
    guesses |> Array.pairwise |> Array.forall (fun (a, b) -> a <= b)

let validateCorrectSum (guesses: int array) (sum: int) =
    Array.sum guesses = sum

let validateCorrectValues (guesses: int array) (dice: Dice array) =
    guesses = (dice |> Array.map (fun d -> d.Value))
```

## UI Framework Integration

### WPF Specifics
- **Data Binding**: Two-way binding between ViewModel and View
- **Commands**: `ICommand` implementation for button actions
- **Triggers**: Visual state changes based on GameState
- **Animations**: Storyboard animations for feedback

### Custom Controls
1. **DiceControl**
   - Dependency properties for Value and IsAnimated
   - Template with dot positioning logic
   - Animation triggers for state changes

2. **InputControl**
   - Click command for value cycling
   - Visual feedback for selection state
   - Value property binding

## State Management

### Observable Pattern
- `DiceGameModel` implements `INotifyPropertyChanged`
- ViewModel subscribes to model changes
- View binds to ViewModel properties
- Automatic UI updates on state changes

### Game State Transitions
```
Initial → Guessing: After dice generation
Guessing → Invalid: On failed validation
Invalid → Guessing: After new guess attempt
Guessing → Win: On correct guess
Win → Initial: On New Game
```

## Error Handling

### Validation Errors
- Immediate visual feedback for invalid input
- Error messages displayed in feedback area
- Game state preserved for retry

### Exception Handling
- Try-catch blocks around random generation
- Graceful handling of unexpected states
- User-friendly error messages

## Testing Strategy

### Unit Tests
- Model validation functions
- Game logic edge cases
- State transition correctness

### UI Tests
- Control behavior verification
- Animation timing
- User interaction flow

## Performance Considerations
- Minimal memory allocation in game loop
- Efficient array operations for validation
- UI thread optimization for smooth animations