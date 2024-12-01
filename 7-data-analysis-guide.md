# Data Analysis Guide

## 1. Data Loading
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

## 2. Data Cleaning
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

## 3. Basic Analysis
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

## 4. Visualization
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

## Common Pitfalls to Check

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