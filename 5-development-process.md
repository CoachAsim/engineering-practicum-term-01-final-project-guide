# Development Process

## Example main.py Organizations

### 1. For Data-Focused Projects (e.g., Clean Water Access Analysis)
```python
"""
Project: Clean Water Access Analysis
Author: [Your Name]
Date: [Current Date]

Analyzes water quality data to identify areas needing improved access.
"""

import pandas as pd
import matplotlib.pyplot as plt

# Data Loading Functions
def load_data(filename):
    """Load the water quality dataset"""
    try:
        df = pd.read_csv(filename)
        return df
    except Exception as e:
        print(f"Error loading data: {e}")
        return None

# Data Cleaning Functions
def clean_data(df):
    """Clean and prepare the data"""
    if df is None:
        return None
    
    # Remove missing values
    df = df.dropna()
    
    # Convert water quality metrics to numeric
    df['quality_score'] = pd.to_numeric(df['quality_score'], errors='coerce')
    
    return df

# Analysis Functions
def calculate_statistics(df):
    """Calculate key water quality statistics"""
    if df is None:
        return None
    
    stats = {
        'average_quality': df['quality_score'].mean(),
        'below_standard': len(df[df['quality_score'] < 50]),
        'regions_affected': df[df['quality_score'] < 50]['region'].unique()
    }
    return stats

# Visualization Functions
def create_visualizations(df, stats):
    """Create visualizations of water quality data"""
    if df is None:
        return
    
    # Quality by Region Bar Chart
    plt.figure(figsize=(10, 6))
    df.groupby('region')['quality_score'].mean().plot(kind='bar')
    plt.title('Average Water Quality by Region')
    plt.xlabel('Region')
    plt.ylabel('Quality Score')
    plt.tight_layout()
    plt.savefig('water_quality_by_region.png')

def main():
    # Load and prepare data
    data = load_data('data/water_quality.csv')
    clean_data = clean_data(data)
    
    # Analyze data
    statistics = calculate_statistics(clean_data)
    
    # Create visualizations
    create_visualizations(clean_data, statistics)
    
    # Print findings
    print("\nKey Findings:")
    print(f"Average Water Quality: {statistics['average_quality']:.1f}")
    print(f"Regions Below Standard: {len(statistics['regions_affected'])}")

if __name__ == "__main__":
    main()
```

### 2. For Pattern Analysis Projects (e.g., Transportation Data)
```python
"""
Project: Transit System Analysis
Author: [Your Name]
Date: [Current Date]

Analyzes public transit usage patterns to identify peak times and busy routes.
"""

import pandas as pd
import matplotlib.pyplot as plt
from datetime import datetime

# Data Processing Functions
def load_and_prepare_data(filename):
    """Load and prepare transit data"""
    try:
        df = pd.read_csv(filename)
        # Convert time strings to datetime
        df['timestamp'] = pd.to_datetime(df['timestamp'])
        return df
    except Exception as e:
        print(f"Error processing data: {e}")
        return None

# Analysis Functions
def analyze_peak_times(df):
    """Find peak usage times"""
    if df is None:
        return None
        
    hourly_usage = df.groupby(df['timestamp'].dt.hour)['riders'].mean()
    peak_hour = hourly_usage.idxmax()
    return {
        'peak_hour': peak_hour,
        'hourly_usage': hourly_usage
    }

def analyze_routes(df):
    """Analyze route usage"""
    if df is None:
        return None
        
    route_stats = df.groupby('route')['riders'].agg(['mean', 'max'])
    busiest_route = route_stats['mean'].idxmax()
    return {
        'route_stats': route_stats,
        'busiest_route': busiest_route
    }

# Visualization Functions
def plot_usage_patterns(df, peak_data):
    """Create usage pattern visualizations"""
    if df is None or peak_data is None:
        return
        
    # Daily usage pattern
    plt.figure(figsize=(12, 6))
    peak_data['hourly_usage'].plot()
    plt.title('Average Hourly Transit Usage')
    plt.xlabel('Hour of Day')
    plt.ylabel('Average Riders')
    plt.grid(True)
    plt.savefig('hourly_usage.png')

def main():
    # Load and prepare data
    transit_data = load_and_prepare_data('data/transit_usage.csv')
    
    # Analyze patterns
    peak_times = analyze_peak_times(transit_data)
    route_analysis = analyze_routes(transit_data)
    
    # Create visualizations
    plot_usage_patterns(transit_data, peak_times)
    
    # Print findings
    print("\nKey Transit Insights:")
    print(f"Peak Usage Hour: {peak_times['peak_hour']}:00")
    print(f"Busiest Route: {route_analysis['busiest_route']}")

if __name__ == "__main__":
    main()
```

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