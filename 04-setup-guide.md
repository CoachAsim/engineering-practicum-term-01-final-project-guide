# 04-setup-guide.md

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

## Project Structure
All projects will follow this simple structure:
"your_project/" should be a folder (aka directory) named after your project. "data/" should be the folder that contains your csv file. 

Be sure to maintain snake_case format 🐍
```
your_project/
├── README.md     # Project documentation
├── main.py       # All your Python code goes here
└── data/         # Your dataset files
```

## Code Organization Guidelines
Your `main.py` should be organized in this order:
1. Imports
2. Constants and configuration
3. Data processing functions
4. Analysis functions
5. Interactive features and menus
6. Visualization functions
7. Main program execution

### Example Structure with Interactive Features
```python
"""
Project: [Your Project Name]
Author: [Your Name]
Date: [Current Date]

Interactive data analysis program for [your topic].
"""

# 1. Imports
import pandas as pd
import matplotlib.pyplot as plt

# 2. Constants
MENU_OPTIONS = {
    '1': 'Analyze entire dataset',
    '2': 'Focus on specific feature',
    '3': 'Generate visualizations',
    '4': 'Exit program'
}

# 3. Data Processing Functions
def load_data(filename):
    """Load and validate dataset"""
    try:
        df = pd.read_csv(filename)
        print(f"Loaded {len(df)} rows")
        return df
    except Exception as e:
        print(f"Error loading data: {e}")
        return None

# 4. Analysis Functions
def analyze_data(df, feature=None):
    """Analyze data based on user selection"""
    if df is None:
        return None
    
    if feature:
        return df[feature].describe()
    return df.describe()

# 5. Interactive Features
def display_menu():
    """Show main menu and get user choice"""
    print("\n=== Data Analysis Menu ===")
    for key, value in MENU_OPTIONS.items():
        print(f"{key}. {value}")
    return input("Enter your choice: ")

# 6. Main Program
def main():
    df = load_data('data/dataset.csv')
    while True:
        choice = display_menu()
        if choice == '4':
            break
        # Handle other menu options...

if __name__ == "__main__":
    main()
```
