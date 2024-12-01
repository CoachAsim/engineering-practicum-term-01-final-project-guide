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

## Code Documentation
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