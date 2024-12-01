# Setup Guide

## Installing Required Libraries

First, let's install the libraries we need. Open VS Code, and follow these steps:
1. Open a new terminal in VS Code:
   * Use the keyboard shortcut: `Cmd + `` (backtick)
   * Or go to `Terminal > New Terminal` in the menu
2. Install pandas, matplotlib, and seaborn using pip3:

```bash
pip3 install pandas matplotlib seaborn
```

3. Verify the installation by running:

```bash
python3 -c "import pandas; import matplotlib; import seaborn; print('Success! 🎉')"
```
If you see "Success! 🎉", you're ready to start exploring the cosmos through data!

## Project Structure
All projects will follow this simple structure:
```
your_project/
├── README.md     # Project documentation
├── main.py       # All your Python code goes here
└── data/         # Your dataset files
```

## Code Organization in main.py
Your code should be organized in this order:
1. Import statements
2. Function definitions (grouped by purpose)
3. Main program execution

### Example Structure
```python
"""
Project: [Your Project Name]
Author: [Your Name]
Date: [Current Date]

Brief description of what your program does.
"""

# 1. Imports
import pandas as pd
import matplotlib.pyplot as plt

# 2. Data Processing Functions
def load_data(filename):
    """Load and validate dataset"""
    try:
        df = pd.read_csv(filename)
        print(f"Loaded {len(df)} rows")
        return df
    except Exception as e:
        print(f"Error loading data: {e}")
        return None

# 3. Analysis Functions
def analyze_data(df):
    """Calculate key statistics"""
    if df is None:
        return None
    
    results = {
        'average': df['value'].mean(),
        'maximum': df['value'].max(),
        'minimum': df['value'].min()
    }
    return results

# 4. Visualization Functions
def create_plots(df, results):
    """Create data visualizations"""
    if df is None:
        return
    
    plt.figure(figsize=(10, 6))
    df['value'].plot(kind='bar')
    plt.title(f"Data Analysis (Avg: {results['average']:.2f})")
    plt.savefig('analysis.png')

# 5. Main Program
def main():
    # Load data
    data = load_data('data/dataset.csv')
    
    # Analyze
    results = analyze_data(data)
    
    # Visualize
    create_plots(data, results)
    
    # Print findings
    if results:
        print("\nAnalysis Results:")
        for key, value in results.items():
            print(f"{key}: {value:.2f}")

# This is a special Python condition that checks if this file is being run directly
# (python main.py) or if it's being imported as a module into another file.
# 
# When you run a Python file directly: __name__ equals "__main__"
# When the file is imported: __name__ equals the file's name
#
# This is useful because:
# 1. It prevents code from running automatically when the file is imported
# 2. It helps organize the main execution of your program
# 3. It's a common Python pattern you'll see in many programs
#
# In simple terms: The code below this line only runs if you execute this file directly
if __name__ == "__main__":
    main()
```

## Initial Setup Steps
1. Create project directory
2. Create main.py file
3. Download selected dataset
4. Create README.md file

## Code Style Guidelines

### 1. Naming Conventions
```python
# GOOD - Clear, descriptive names using snake_case for functions and variables
student_name = "Alice"
total_score = 0
def calculate_average(numbers):
    pass

# BAD - Unclear or incorrectly formatted names
x = "Alice"  # Too vague
totalScore = 0  # camelCase isn't Python style
def CalculateAverage(numbers):  # Don't use CamelCase for functions
    pass
```

### 2. Indentation and Spacing
- Use 4 spaces for indentation (not tabs)
- Add space around operators (=, +, -, etc.)
- Add space after commas
- Keep lines under 79 characters

### 3. Comments and Documentation
- Add helpful comments, but don't state the obvious
- Use docstrings for functions
- Keep documentation up to date
- Comment complex logic