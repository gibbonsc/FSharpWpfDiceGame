# F# WPF Dice Guessing Game - UI Design Specifications

## Window Layout

### Main Window Structure
- **Window Size**: 400x600 pixels (fixed size)
- **Background**: Light gray (#F0F0F0)
- **Title**: "Dice Guessing Game"
- **Window Style**: Single border, no resize

### Layout Sections (from top to bottom)

#### 1. Game Title (Top)
- **Position**: Top 10% of window
- **Content**: Large centered text "Dice Guessing Game"
- **Font**: Segoe UI, 24pt, bold
- **Color**: Dark blue (#1E3A8A)

#### 2. Dice Display Area (Middle-top)
- **Position**: Next 20% of window
- **Content**: Visual representation of three dice (values hidden until correct guess)
- **Layout**: Three dice side by side, centered
- **Dice Size**: 60x60 pixels each
- **Spacing**: 20 pixels between dice

#### 3. Sum Display (Below dice)
- **Position**: Next 10% of window
- **Content**: "Sum: [value]" centered text
- **Font**: Segoe UI, 18pt, bold
- **Color**: Green (#10B981)

#### 4. Guess Input Area (Middle)
- **Position**: Next 30% of window
- **Layout**: Three input controls in a row
- **Input Type**: Custom clickable areas (no text boxes)
- **Size**: Each input area 80x80 pixels
- **Spacing**: 15 pixels between inputs

#### 5. Feedback Display (Below input)
- **Position**: Next 10% of window
- **Content**: Dynamic feedback messages
- **Font**: Segoe UI, 14pt
- **Color**: Red (#EF4444) for errors, Green (#10B981) for success

#### 6. Control Buttons (Bottom)
- **Position**: Bottom 10% of window
- **Layout**: Centered horizontal buttons
- **Buttons**: "Submit Guess", "New Game"
- **Size**: 120x40 pixels each
- **Spacing**: 10 pixels between buttons

## Visual Elements

### Dice Representation
- **Shape**: Rounded rectangles with border
- **Border**: 2px dark gray (#6B7280)
- **Background**: White (#FFFFFF)
- **Dots**: Black circles (hidden until correct guess)
- **Animation**: None

### Input Areas
- **Default State**: Light gray background (#E5E7EB)
- **Hover State**: Slightly darker (#D1D5DB)
- **Selected State**: Blue highlight (#3B82F6)
- **Click Animation**: Brief scale effect (0.95x)

### Feedback Messages
- **Error Messages**: Red text, shake animation
- **Success Messages**: Green text, fade-in animation
- **Position**: Centered below input area

## User Interaction

### Mouse Controls
- **Click**: Select input areas, submit guesses
- **Hover**: Visual feedback on interactive elements
- **Drag**: Not supported (click-only interface)

### Input Flow
1. Player clicks on first input area
2. Number increments with each click (1→2→3→...→6→1)
3. Player clicks on second input area
4. Number increments similarly
5. Player clicks on third input area
6. Number increments similarly
7. Player clicks "Submit Guess" button
8. Game validates and provides feedback

### Button Functions
- **Submit Guess**: Validates current input, provides feedback
- **New Game**: Resets game state, generates new dice

## Color Scheme
- **Primary**: Blue (#3B82F6)
- **Secondary**: Green (#10B981)
- **Accent**: Red (#EF4444)
- **Background**: Light gray (#F0F0F0)
- **Text**: Dark gray (#1F2937)
- **Borders**: Dark gray (#6B7280)

## Typography
- **Headings**: Segoe UI, bold
- **Body Text**: Segoe UI
- **Numbers**: Digital/LED style font for dice values