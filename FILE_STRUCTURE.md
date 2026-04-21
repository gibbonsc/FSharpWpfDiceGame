# F# WPF Dice Guessing Game - File Structure Specification

## Project Root Directory

```
FSharpWpfDiceGame/
├── .gitignore                    # Git ignore rules
├── README.md                     # Project documentation
├── DiceGuessingGame.slnx         # Visual Studio solution file
├── DiceGuessingGame/
│   ├── DiceGuessingGame.csproj   # Main project file
│   ├── App.xaml                  # Application resources and startup
│   ├── App.xaml.cs               # Code-behind for application events
│   ├── MainWindow.xaml           # Main window layout
│   ├── MainWindow.xaml.cs        # Code-behind for main window
│   ├── Properties/
│   │   ├── AssemblyInfo.cs       # Assembly metadata
│   │   └── Settings.settings      # Application settings
│   ├── Models/                   # Model layer
│   │   ├── Dice.fs               # Dice type and functions
│   │   ├── GameState.fs          # Game state enumeration
│   │   └── DiceGameModel.fs      # Main game model
│   ├── ViewModels/               # ViewModel layer
│   │   ├── MainViewModel.fs      # Main game orchestration
│   │   ├── DiceViewModel.fs      # Dice display logic
│   │   └── InputViewModel.fs     # Guess input handling
│   ├── Controls/                 # Custom WPF controls
│   │   ├── DiceControl.xaml      # Dice visualization control
│   │   ├── DiceControl.xaml.cs   # Code-behind for dice control
│   │   ├── InputControl.xaml     # Guess input control
│   │   └── InputControl.xaml.cs  # Code-behind for input control
│   └── Themes/                   # UI styling and themes
│       ├── Generic.xaml          # Default control styles
│       └── DiceGameTheme.xaml    # Custom theme resources
├── DiceGuessingGame.Tests/       # Test project
│   ├── DiceGuessingGame.Tests.csproj  # Test project file
│   ├── ModelTests.fs            # Model layer tests
│   ├── ViewModelTests.fs        # ViewModel layer tests
│   └── IntegrationTests.fs      # Integration tests
└── docs/                        # Additional documentation
    ├── user-guide.md            # User documentation
    ├── developer-guide.md       # Developer documentation
    └── api-reference.md         # API documentation
```

## File Details and Purpose

### Root Level Files
- **.gitignore**: Excludes build outputs, user-specific files, and IDE files from version control
- **README.md**: Contains project overview, build instructions, and usage guide
- **DiceGuessingGame.slnx**: Visual Studio solution file that organizes all projects (newer .slnx format)

### Main Project Files
- **DiceGuessingGame.csproj**: Defines project configuration, dependencies, and build settings
- **App.xaml**: Application-level resources, styles, and startup configuration
- **App.xaml.cs**: Code-behind for application lifecycle events
- **MainWindow.xaml**: Primary UI layout with data bindings and control definitions
- **MainWindow.xaml.cs**: Code-behind for window events and initialization

### Properties Folder
- **AssemblyInfo.cs**: Assembly metadata including version, company, and copyright information
- **Settings.settings**: Application settings and user preferences storage

### Models Folder
- **Dice.fs**: F# module defining the Dice type, dice generation, and sorting functions
- **GameState.fs**: F# module defining the GameState discriminated union
- **DiceGameModel.fs**: F# module containing the main game model with validation logic

### ViewModels Folder
- **MainViewModel.fs**: F# module implementing the main ViewModel with game orchestration
- **DiceViewModel.fs**: F# module managing dice display and animation states
- **InputViewModel.fs**: F# module handling guess input and validation

### Controls Folder
- **DiceControl.xaml**: WPF UserControl for visual dice representation with dot positioning
- **DiceControl.xaml.cs**: Code-behind for dice control animations and interactions
- **InputControl.xaml**: WPF UserControl for clickable guess input areas
- **InputControl.xaml.cs**: Code-behind for input control behavior and state management

### Themes Folder
- **Generic.xaml**: Default styles for WPF controls used in the application
- **DiceGameTheme.xaml**: Custom theme resources including colors, fonts, and control templates

### Test Project
- **DiceGuessingGame.Tests.csproj**: Test project configuration with testing frameworks
- **ModelTests.fs**: Unit tests for model layer validation functions
- **ViewModelTests.fs**: Unit tests for ViewModel logic and commands
- **IntegrationTests.fs**: Integration tests for complete game flow

### Documentation Folder
- **user-guide.md**: End-user documentation with gameplay instructions
- **developer-guide.md**: Developer documentation with architecture and implementation details
- **api-reference.md**: API documentation for public interfaces and functions

## Naming Conventions

### Files
- **C# files**: PascalCase with .cs extension
- **F# files**: PascalCase with .fs extension
- **XAML files**: PascalCase with .xaml extension
- **Folders**: PascalCase

### Project Structure
- **Main project**: DiceGuessingGame
- **Test project**: DiceGuessingGame.Tests
- **Solution**: DiceGuessingGame.slnx (newer .slnx format)

## Build Output Structure

After building, the following directories will be generated:

```
FSharpWpfDiceGame/
├── bin/                          # Build outputs
│   ├── Debug/
│   │   └── net10.0-windows/
│   └── Release/
│       └── net10.0-windows/
├── obj/                          # Temporary build files
└── DiceGuessingGame.exe         # Executable application
```

## Configuration Files

### .csproj Configuration
- **Target framework**: net10.0-windows
- **Output type**: WinExe
- **Language**: F# support enabled
- **WPF dependencies**: Included automatically

### Test Project Configuration
- **Test framework**: xUnit
- **F# support**: Enabled
- **Target framework**: net10.0

## Version Control Structure

### Files to Include
- All source code files (.fs, .xaml, .cs)
- Project files (.csproj, .slnx)
- Documentation files
- Configuration files

### Files to Exclude (via .gitignore)
- bin/ and obj/ directories
- .vs/ directory
- .user files
- .suo files
- .userosscache files
- .sln.docstates file