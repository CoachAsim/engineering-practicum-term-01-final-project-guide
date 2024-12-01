## Documentation Requirements

### README Template
```markdown
# [Project Name]

## Problem Statement
Clearly explain the problem you're solving and why it matters.

## Dataset
- Source: [Where you got the data]
- Description: [What the data contains]
- Size: [Number of records/features]

## Features
- Feature 1: [Description]
- Feature 2: [Description]
- Feature 3: [Description]

## Installation
```bash
# Required packages
pip install pandas matplotlib seaborn
```

## Usage
```python
python src/main.py
```

## Analysis Results
[Summary of key findings]

## Future Improvements
[What you'd add with more time]
```

### Code Documentation
```python
"""
Module: analysis.py
Purpose: Data analysis functions for [project name]
Author: [Your name]
Date: [Current date]
"""

def analyze_column(data, column_name):
    """
    Analyze a single column of data
    
    Args:
        data (pd.DataFrame): Input dataframe
        column_name (str): Name of column to analyze
        
    Returns:
        dict: Analysis results including mean, median, etc.
    """
    results = {
        'mean': data[column_name].mean(),
        'median': data[column_name].median(),
        'std': data[column_name].std()
    }
    return results
```

## Data Analysis Guide

### 1. Data Loading
```python
import pandas as pd

def load_data(filepath):
    """Load and validate dataset"""
    try:
        df = pd.read_csv(filepath)
        print(f"Loaded {len(df)} rows and {len(df.columns)} columns")
        return df
    except Exception as e:
        print(f"Error loading data: {e}")
        return None
```

### 2. Data Cleaning
```python
def clean_data(df):
    """Clean and prepare data"""
    # Remove duplicates
    df = df.drop_duplicates()
    
    # Handle missing values
    df = df.fillna(df.mean(numeric_only=True))
    
    # Convert data types
    numeric_columns = ['column1', 'column2']
    for col in numeric_columns:
        df[col] = pd.to_numeric(df[col], errors='coerce')
    
    return df
```

### 3. Basic Analysis
```python
def basic_analysis(df):
    """Perform basic statistical analysis"""
    stats = {
        'summary': df.describe(),
        'missing': df.isnull().sum(),
        'correlations': df.corr()
    }
    return stats
```

### 4. Visualization
```python
def create_visualizations(df, output_dir):
    """Create standard visualizations"""
    # Histogram
    plt.figure(figsize=(10, 6))
    df['main_metric'].hist()
    plt.title('Distribution of Main Metric')
    plt.savefig(f'{output_dir}/histogram.png')
    
    # Time series
    plt.figure(figsize=(12, 6))
    df.plot(x='date', y='value')
    plt.title('Trend Over Time')
    plt.savefig(f'{output_dir}/trend.png')
```

## Time Management Tips

### Dividing Your 1.5 Hours
For each coding session:
- First 10 minutes: Review previous work and plan today's tasks
- Next 70 minutes: Main development work
- Last 10 minutes: Document what you did and plan for tomorrow

### Staying on Track
- Set a timer for your 1.5-hour session
- Keep your README updated as you go
- Comment your code while writing it
- If you get stuck, spend max 20 minutes before asking for help

### Documentation During Development
Add comments as you code:
```python
# Good - Quick comments while coding (5 seconds)
def calculate_average(values):
    """Get mean of values."""  # Basic docstring
    return sum(values) / len(values)

# Better - Complete when you have time
def calculate_average(values):
    """
    Calculate the average of a list of numbers.
    
    Args:
        values (list): List of numbers
        
    Returns:
        float: Average value
    """
    return sum(values) / len(values)
```

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

### 2. Indentation
```python
# GOOD - Use 4 spaces for indentation (not tabs)
def process_data(data):
    if data:
        for item in data:
            print(item)
    return True

# BAD - Inconsistent or incorrect indentation
def process_data(data):
  if data:  # Only 2 spaces
        for item in data:  # Different indentation
          print(item)  # Inconsistent
    return True  # Wrong indentation after block
```

### 3. Whitespace
```python
# GOOD - Proper spacing around operators and after commas
x = 5
y = x + 3
numbers = [1, 2, 3, 4]
result = some_function(x, y, numbers)

# BAD - Inconsistent or missing spaces
x=5
y=x+3
numbers=[1,2,3,4]
result=some_function(x,y,numbers)
```

### 4. Line Length
```python
# GOOD - Lines under 79 characters
students = [
    "Alice",
    "Bob",
    "Charlie",
    "David"
]

# BAD - Lines too long
students = ["Alice", "Bob", "Charlie", "David", "Eve", "Frank", "George", "Henry", "Isabel", "Jack", "Karen"]
```

### 5. Comments
```python
# GOOD - Clear, helpful comments
# Calculate average score for all students
total = sum(scores)
average = total / len(scores)

# BAD - Obvious or unhelpful comments
# Add numbers
total = sum(scores)  # Add all scores together
# Divide by length
average = total / len(scores)  # Get average
```

### 6. Imports
```python
# GOOD - Organize imports properly
import pandas as pd
import numpy as np
from matplotlib import pyplot as plt

# BAD - Don't import everything or mix styles
from pandas import *
import pandas as pd, numpy as np
from matplotlib.pyplot import *
```

### 7. Function and Class Definitions
```python
# GOOD - Two blank lines before functions/classes, clear docstrings
def calculate_grade(score):
    """
    Calculate letter grade from numerical score.
    
    Args:
        score (float): Numerical score from 0-100
        
    Returns:
        str: Letter grade (A, B, C, D, or F)
    """
    if score >= 90:
        return "A"
    elif score >= 80:
        return "B"
    # ... etc


# BAD - Missing spacing, no docstring
def calculate_grade(score):
    if score >= 90:
        return "A"
    elif score >= 80:
        return "B"
```

### 8. Variables and Constants
```python
# GOOD - Clear naming conventions
MAX_STUDENTS = 30  # Constants in ALL_CAPS
student_count = 25  # Variables in snake_case
PASSING_GRADE = 70

# BAD - Unclear or inconsistent naming
maximumStudents = 30
StudentCount = 25
passing = 70
```

### Key Rules to Remember:
1. Use 4 spaces for indentation (not tabs)
2. Use snake_case for functions and variables
3. Use UPPER_CASE for constants
4. Keep lines under 79 characters
5. Add space around operators (=, +, -, etc.)
6. Add space after commas
7. Use clear, descriptive names
8. Add helpful comments, but don't state the obvious
9. Be consistent with spacing and formatting
10. Put two blank lines before function and class definitions

### Common Beginner Mistakes to Avoid:
- Mixing tabs and spaces
- Inconsistent indentation
- No spaces around operators
- Names that don't describe purpose
- Too many blank lines
- No docstrings for functions
- Importing everything with *
- Lines that are too long
- Unhelpful or obvious comments
- Inconsistent naming styles

Remember: Consistent, clean code is easier to read, debug, and maintain!

## Code Review and Debugging Guide

### Common Python Errors and Solutions

#### 1. File Handling Errors
```python
# Common mistake
data = pd.read_csv('data.csv')  # No error handling

# Better approach
def load_data(filename):
    try:
        data = pd.read_csv(filename)
        print(f"Successfully loaded {len(data)} rows")
        return data
    except FileNotFoundError:
        print(f"Error: Could not find {filename}")
        return None
    except pd.errors.EmptyDataError:
        print(f"Error: {filename} is empty")
        return None
```

#### 2. Data Type Errors
```python
# Common mistake
total = data['value'] + 10  # Might fail if 'value' contains strings

# Better approach
def process_numeric_column(df, column_name):
    try:
        # Convert to numeric, making non-numeric values NaN
        df[column_name] = pd.to_numeric(df[column_name], errors='coerce')
        # Remove rows with NaN values
        df = df.dropna(subset=[column_name])
        return df
    except Exception as e:
        print(f"Error processing {column_name}: {str(e)}")
        return None
```

#### 3. Index and Key Errors
```python
# Common mistake
value = data_dict['key']  # Crashes if key doesn't exist

# Better approach
def safe_get_value(dictionary, key, default=None):
    if key in dictionary:
        return dictionary[key]
    print(f"Warning: Key '{key}' not found, using default value")
    return default
```

### Debugging Techniques

#### 1. Print Debugging
```python
def analyze_data(df):
    print(f"Starting analysis with {len(df)} rows")  # Check input
    
    result = df.groupby('category').mean()
    print(f"Group means:\n{result}")  # Check intermediate result
    
    return result
```

#### 2. Data Validation
```python
def validate_dataframe(df, required_columns):
    """Check if DataFrame meets requirements"""
    issues = []
    
    # Check for required columns
    missing_cols = [col for col in required_columns if col not in df.columns]
    if missing_cols:
        issues.append(f"Missing columns: {missing_cols}")
    
    # Check for empty DataFrame
    if df.empty:
        issues.append("DataFrame is empty")
    
    # Report all issues
    if issues:
        print("Data validation failed:")
        for issue in issues:
            print(f"- {issue}")
        return False
    return True
```

#### 3. Code Organization Check
```python
def review_code_organization():
    """Checklist for code organization"""
    checklist = {
        "Functions documented": False,
        "Error handling added": False,
        "Print statements cleaned up": False,
        "Variables properly named": False,
        "Code properly indented": False
    }
    
    print("\nCode Review Checklist:")
    for item in checklist:
        response = input(f"Is {item} complete? (y/n): ")
        checklist[item] = response.lower() == 'y'
    
    return all(checklist.values())
```

### Common Pitfalls to Check

1. Data Processing
   - Empty DataFrames
   - Missing columns
   - Incorrect data types
   - Missing value handling
   - Incorrect calculations

2. Visualization
   - Missing labels
   - Incorrect plot types
   - Unreadable text
   - Missing titles
   - Color choice issues

3. Code Structure
   - Repeated code
   - Missing error handling
   - Unclear variable names
   - Insufficient comments
   - Unorganized functions

### Debug Checklist

```markdown
## Before Submission Debug Checklist

### Data Loading
- [ ] File paths correct
- [ ] Error handling in place
- [ ] Data loading confirmed
- [ ] Data structure validated

### Data Processing
- [ ] No empty results
- [ ] Calculations verified
- [ ] Edge cases handled
- [ ] Results make sense

### Visualizations
- [ ] All labels present
- [ ] Axes correct
- [ ] Colors appropriate
- [ ] Sizes readable

### Code Quality
- [ ] Functions documented
- [ ] Variables clear
- [ ] Comments helpful
- [ ] Code organized

### Documentation
- [ ] README complete
- [ ] Comments updated
- [ ] Instructions clear
- [ ] Examples added
```

## Presentation Guidelines (30-Minute Prep Time)

Your presentation should be ready to deliver in 5 minutes:

1. Introduction (1 minute)
   - What problem did you investigate?
   - What dataset did you use?

2. Code Demo (2 minutes)
   - Show your main analysis function
   - Run your program
   - Show key visualizations

3. Findings (1.5 minutes)
   - What did you discover?
   - What was challenging?
   - What would you do with more time?

4. Q&A (30 seconds)
   - Be ready for questions about your code
   - Have your data insights ready to discuss

### Tips
- Practice your timing
- Prepare backup screenshots
- Focus on key findings
- Be ready for questions

## Competency-Based Rubric

### Core Competencies

#### 1. Programming (40%)
- [ ] Algorithm implementation
- [ ] Function organization
- [ ] Error handling
- [ ] Code documentation

#### 2. Data Analysis (40%)
- [ ] Data cleaning
- [ ] Statistical analysis
- [ ] Visualization
- [ ] Insights documentation

#### 3. Project Management (20%)
- [ ] Timeline adherence
- [ ] Documentation quality
- [ ] Presentation clarity
- [ ] Code organization

### Extension Competencies (Bonus)
- [ ] Class implementation
- [ ] UI development
- [ ] Advanced analysis
- [ ] Additional features

## Resources

### Recommended Libraries
- Pandas: Data analysis
- Matplotlib: Basic plotting
- Seaborn: Statistical visualization

### Documentation Links
- [Pandas Documentation](https://pandas.pydata.org/docs/)
- [Matplotlib Documentation](https://matplotlib.org/)
- [Python Documentation](https://docs.python.org/3/)

### Dataset Resources
- [Kaggle Datasets](https://www.kaggle.com/datasets)
- [Google Dataset Search](https://datasetsearch.research.google.com/)
- [Data.gov](https://data.gov/)

Remember:
- Start simple, add complexity later
- Test frequently
- Document as you go
- Ask for help when stuck
- Focus on core requirements first