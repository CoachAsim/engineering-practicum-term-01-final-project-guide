# 11-pep8-basics.md

# Python Style Guide for Interactive Data Analysis

This guide covers Python style rules with examples specific to interactive data analysis programs.

## 1. Naming Rules 🏷️

### Variables and Functions
```python
# ✅ GOOD - Clear, descriptive names
user_selection = input("Enter choice: ")
data_filename = "analysis.csv"
def calculate_average(values):
    pass

# ❌ BAD - Unclear or incorrect style
ch = input("Enter choice: ")    # Too short
dataFile = "analysis.csv"       # No camelCase
def CalculateAvg(values):       # No CapWords
```

### Constants
```python
# ✅ GOOD - Uppercase for constants
MENU_OPTIONS = {
    '1': 'Analyze Data',
    '2': 'Show Plot',
    '3': 'Exit'
}
MAX_RETRIES = 3

# ❌ BAD
menuOptions = {'1': 'Analyze'}  # Not uppercase
max_retries = 3                 # Not uppercase
```

## 2. Function Definitions
```python
# ✅ GOOD - Clear function structure
def get_user_choice(options):
    """
    Get validated user input from available options.
    
    Args:
        options (dict): Available menu options
        
    Returns:
        str: Validated user choice
    """
    while True:
        choice = input("Enter your choice: ")
        if choice in options:
            return choice
        print("Invalid choice. Please try again.")

# ❌ BAD - Poor structure and documentation
def get_choice(o):
    c = input("Choice: ")
    if c in o: return c
    print("Invalid")
```

## 3. Error Handling
```python
# ✅ GOOD - Clear error handling
def load_data(filename):
    """Load data file with error handling."""
    try:
        with open(filename, 'r') as file:
            data = file.read()
        return data
    except FileNotFoundError:
        print(f"Error: Could not find {filename}")
        return None
    except Exception as e:
        print(f"Error loading file: {e}")
        return None

# ❌ BAD - Poor error handling
def load_data(filename):
    data = open(filename).read()  # No try/except
    return data
```

## 4. User Interaction
```python
# ✅ GOOD - Clear user interface
def display_menu():
    """Display main program menu."""
    print("\n=== Data Analysis Menu ===")
    print("1. Load Data")
    print("2. Analyze")
    print("3. Exit")
    return input("\nChoice: ")

# ❌ BAD - Poor interface
def menu():
    print("1-Load 2-Analyze 3-Exit")
    return input()
```

## 5. Comments and Documentation
```python
# ✅ GOOD - Clear documentation
def analyze_column(data, column):
    """
    Analyze a single column of data.
    
    Calculates basic statistics and handles missing values.
    
    Args:
        data (pd.DataFrame): Input dataframe
        column (str): Column to analyze
        
    Returns:
        dict: Analysis results
    """
    # Remove missing values
    clean_data = data[column].dropna()
    
    # Calculate statistics
    stats = {
        'mean': clean_data.mean(),
        'median': clean_data.median()
    }
    
    return stats

# ❌ BAD - Poor documentation
def analyze(d, c):
    # analyze the data
    clean = d[c].dropna()
    return {'mean': clean.mean()}
```

## Style Checklist for Interactive Programs

### User Interface
- [ ] Clear menu formatting
- [ ] Consistent input prompts
- [ ] Helpful error messages
- [ ] Logical flow

### Code Organization
- [ ] Imports at top
- [ ] Constants after imports
- [ ] Functions grouped by purpose
- [ ] Main execution at bottom

### Documentation
- [ ] Module docstring
- [ ] Function docstrings
- [ ] Clear comments
- [ ] Usage examples

### Error Handling
- [ ] Input validation
- [ ] File operations
- [ ] Data processing
- [ ] User feedback

## Remember
- Style affects usability
- Consistent interfaces help users
- Clear code is maintainable code
- Documentation helps future you

## Common Mistakes to Avoid
1. Mixing tabs and spaces (use only spaces!)
2. Using unclear variable names (x, y, z)
3. Forgetting spaces around operators
4. Writing lines that are too long
5. Writing comments that don't add value
6. Inconsistent indentation

## Quick Tips for Success
1. Use a code editor that shows spaces (like VS Code)
2. Learn your editor's auto-formatting shortcuts
3. Review your code before submitting
4. When copying code from the internet, fix its style
5. Ask for help when stuck

## PEP 8 Basics Checklist
- [ ] Use 4 spaces for indentation
- [ ] Lines should be 79 characters or less
- [ ] Use blank lines to separate functions and classes
- [ ] Use spaces around operators and after commas
- [ ] Use clear variable and function names
- [ ] Add docstrings to functions and modules
- [ ] Import statements at the top of the file
- [ ] One import per line
- [ ] Consistent naming conventions throughout
- [ ] Comments should be complete sentences
