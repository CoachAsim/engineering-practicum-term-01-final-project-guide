# 06-documentation-requirements.md

# Documentation Requirements

## README Template
```markdown
# [Project Name]

## Problem Statement
Clearly explain the problem you're solving and why it matters.

## Dataset
- Source: [Where you got the data]
- Description: [What the data contains]
- Size: [Number of records/features]
- Quality: [Any data quality notes]

## Features
1. Interactive Analysis
   - Feature 1: [Description of interactive feature]
   - Feature 2: [Description of interactive feature]
   
2. Data Processing
   - Feature 1: [Description of processing feature]
   - Feature 2: [Description of processing feature]

3. Visualizations
   - Type 1: [Description]
   - Type 2: [Description]

## Program Structure
project/
├── README.md
├── main.py        # Main program with all code
└── data/          # Data directory
    └── dataset.csv
```

## Implementation Details
### Core Programming Concepts Used
- Data Types: [List examples of data type usage]
- Variables: [Explain key variables]
- Control Structures: [List key control structures]
- Functions: [List main functions]
- File Operations: [Describe file handling]

### Analysis Methods
[Describe analysis approaches]

## Results
[Summary of key findings]

## Future Improvements
[What you'd add with more time]

## Code Documentation
### Function Documentation Template
```python
def function_name(param1, param2):
    """
    Brief description of function purpose.
    
    Args:
        param1 (type): Description of param1
        param2 (type): Description of param2
    
    Returns:
        type: Description of return value
    
    Example:
        >>> function_name(1, "test")
        Expected output
    """
    # Implementation
```

### Interactive Feature Documentation
```python
def display_menu():
    """
    Display main program menu and get user choice.
    
    The menu shows numbered options and validates input.
    
    Returns:
        str: User's validated menu choice
    
    Example:
        >>> display_menu()
        === Main Menu ===
        1. Option One
        2. Option Two
        3. Exit
        
        Choice: 1
        '1'
    """
    # Implementation
```

### Documentation During Development
- Add function docstrings immediately. Docstrings are comments created with an opening and closing set of 3 quotation marks. """
- Comment complex logic
- Explain any non-obvious choices
- Document interactive features thoroughly
