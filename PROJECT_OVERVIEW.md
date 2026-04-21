# F# WPF Dice Guessing Game - Project Overview

## Project Description
A desktop application built with F# and WPF that implements a dice guessing game where players must deduce the values of three dice based on their sum and sorted order.

## Game Concept
The computer throws three dice, sorts them from smallest to largest, and reveals their sum. Players must guess the value of each die using a mouse-driven interface. The game provides feedback on guess validity and continues until the player correctly identifies all three dice.

## Key Features
- Three-dice random generation with sorting
- Sum calculation and display
- Interactive guess input via mouse
- Real-time validation feedback
- Win condition detection
- Clean, intuitive WPF user interface
- Track player's number of guesses
- Play again mechanism

## Technical Stack
- **Language**: F# 7.0+
- **UI Framework**: WPF (.NET 10.0+)
- **Architecture**: MVVM pattern
- **Build System**: .NET CLI

## Target Platform
- Windows 10/11
- .NET 10.0 Runtime or later

## Success Criteria
1. Game correctly generates and sorts three dice
2. Sum is accurately calculated and displayed
3. Player input is properly validated
4. Game provides appropriate feedback for invalid guesses
5. Win condition is correctly detected
6. User interface is responsive and intuitive