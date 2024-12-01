# High School Computer Science Final Project Guide

## What You'll Build
During this 7-day project (1.5 hours each day), you'll create a program that analyzes real data related to your interests. While your finished project won't solve global challenges, it will demonstrate how programming and data analysis can be used to understand and address important problems.

## Project Scope
- Total time: 7 days × 1.5 hours = 10.5 hours total
- One Python file (main.py) containing all code
- Analysis of one dataset
- At least two visualizations
- Clear documentation

## Example Project Timelines

### Water Quality Analysis Project Example
```python
# Day 1 (1.5 hrs) - By the end of this day, you should have:
data = pd.read_csv('water_quality.csv')  # Basic data loading working

# Day 2 (1.5 hrs) - Add basic analysis:
def calculate_safe_water_percentage(data):
    return (data['quality_score'] >= SAFETY_THRESHOLD).mean() * 100

# Day 3 (1.5 hrs) - Clean data and handle errors:
def clean_water_data(data):
    data['quality_score'] = pd.to_numeric(data['quality_score'], errors='coerce')
    return data.dropna()

# Day 4 (1.5 hrs) - Core analysis functions:
def analyze_water_quality(data):
    regional_stats = data.groupby('region')['quality_score'].agg(['mean', 'min'])
    return regional_stats

# Day 5 (1.5 hrs) - Create visualizations:
plt.figure(figsize=(10, 6))
data.boxplot(column='quality_score', by='region')
plt.title('Water Quality by Region')

# Day 6 (1.5 hrs) - Connect everything:
def main():
    data = load_data()
    clean_data = clean_water_data(data)
    results = analyze_water_quality(clean_data)
    create_visualizations(clean_data)

```

# Day 7 (1.5 hrs) - Documentation and presentation
"""
Complete docstrings, README, and presentation prep
"""
This final project is your opportunity to create something meaningful that aligns with your interests while applying the programming and data analysis skills you've learned. Let's look at some examples of what you could build, based on different interests:

### Example Projects

#### For Clean Water Access Interest
Build a program that:
- Analyzes water quality data across different regions
- Creates visualizations showing access to clean water by location
- Calculates key statistics about water quality metrics
- Identifies areas most in need of clean water infrastructure

Example Features:
- Load and clean water quality datasets
- Create maps or charts showing water access patterns
- Calculate important metrics like population without access
- Generate reports highlighting critical areas

#### For Audio Safety Interest
Build a program that:
- Analyzes audio level data from different environments
- Visualizes safe vs dangerous sound levels
- Identifies patterns in noise exposure
- Suggests safe listening durations

Example Features:
- Process decibel level datasets
- Create visualizations of sound exposure over time
- Calculate average exposure levels
- Generate safety recommendations

#### For Transportation Systems Interest
Build a program that:
- Analyzes public transit usage data
- Visualizes peak travel times
- Identifies busy routes and stations
- Suggests service improvements

Example Features:
- Process transit ridership data
- Create charts showing usage patterns
- Calculate station capacity utilization
- Generate reports on system efficiency

#### For Education Access Interest
Build a program that:
- Analyzes educational resource distribution
- Visualizes access to learning materials
- Identifies areas needing more resources
- Suggests resource allocation improvements

Example Features:
- Process education access datasets
- Create visualizations of resource distribution
- Calculate equity metrics
- Generate recommendations for improvement

### What You'll Actually Build
While these examples might sound ambitious, your 14-hour project will be a focused version that demonstrates key concepts. For example, if you're interested in clean water access, you might:

1. Use a dataset of water quality measurements
2. Clean and process the data using Python
3. Calculate important statistics like:
   - Average quality metrics by region
   - Areas below safety thresholds
   - Population impact estimates
4. Create visualizations showing:
   - Quality metrics over time
   - Regional comparisons
   - Safety threshold violations
5. Generate a report with your findings and recommendations

The goal is to build something meaningful that:
- Uses real data related to your interests
- Demonstrates your programming skills
- Shows your data analysis capabilities
- Produces useful insights

## Overview
Welcome to your final project! Over the next 7 days, you'll create a project that combines programming and data analysis to solve a real-world problem. This comprehensive guide will walk you through every step of the process.

## Table of Contents
1. [Project Requirements](#project-requirements)
2. [Timeline](#timeline)
3. [Setup Guide](#setup-guide)
4. [Development Process](#development-process)
5. [Documentation Requirements](#documentation-requirements)
6. [Data Analysis Guide](#data-analysis-guide)
7. [Presentation Guidelines](#presentation-guidelines)
8. [Rubric](#rubric)
9. [Resources](#resources)

## Project Requirements

### Core Components
Your project must include:

#### Programming Component
- At least one algorithm that processes data or solves a problem
- Functions to organize code
- Lists and dictionaries for data storage
- Error handling for user input and file operations
- Clear code comments and documentation

#### Data Analysis Component
- Data loading and cleaning
- Basic statistical analysis
- At least two different types of visualizations
- Written analysis of findings

#### Documentation
- Flow diagram of main algorithm
- Step-by-step algorithm description
- Pseudocode
- Code comments
- README file
- Analysis report

### Extension Options (For Advanced Students)
- Classes for object-oriented design
- HTML & CSS interface
- Advanced data structures
- Additional visualizations
- Complex error handling
- API integration

## Timeline

### Example main.py Organizations

#### 1. For Data-Focused Projects (e.g., Clean Water Access Analysis)
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

#### 2. For Pattern Analysis Projects (e.g., Transportation Data)
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

- Organize code into clear sections:
  - Data loading and cleaning
  - Analysis functions
  - Visualization functions
  - Main execution flow

### Common Function Groups

1. Data Loading and Cleaning:
```python
def load_data(filename):
    """Load the dataset"""
    pass

def clean_data(df):
    """Clean and prepare data"""
    pass

def validate_data(df):
    """Check if data meets requirements"""
    pass
```

2. Analysis Functions:
```python
def calculate_statistics(df):
    """Calculate key statistics"""
    pass

def find_patterns(df):
    """Identify patterns in data"""
    pass

def analyze_trends(df):
    """Analyze trends over time"""
    pass
```

3. Visualization Functions:
```python
def create_basic_plots(df):
    """Create standard visualizations"""
    pass

def plot_findings(df, stats):
    """Plot analysis results"""
    pass

def save_visualizations(filename):
    """Save plots to files"""
    pass
```

4. Main Program Flow:
```python
def main():
    # 1. Load and prepare data
    data = load_data('dataset.csv')
    clean_data = clean_data(data)
    
    # 2. Analyze data
    statistics = calculate_statistics(clean_data)
    patterns = find_patterns(clean_data)
    
    # 3. Visualize results
    create_basic_plots(clean_data)
    plot_findings(clean_data, statistics)
    
    # 4. Print conclusions
    print_results(statistics, patterns)

if __name__ == "__main__":
    main()
```

### Implementation Steps

#### Daily Timeline (10.5 Hours Total - 1.5 hours per day)

##### Day 1: Planning & Setup (1.5 hours)
- Choose your project focus (15 min)
- Find and download appropriate dataset (15 min)
- Create project folder and main.py (15 min)
- Write project description in README.md (15 min)
- Test loading your dataset (30 min)

##### Day 2: Algorithm Design (1.5 hours)
- Write out your algorithm steps (20 min)
- Create flow diagram (20 min)
- Convert algorithm to pseudocode (20 min)
- Plan your functions (15 min)
- Document your plan in comments (15 min)

##### Day 3: Data Processing (1.5 hours)
- Implement data loading function (30 min)
- Add basic error handling (30 min)
- Write data cleaning function (30 min)

##### Day 4: Core Development (1.5 hours)
- Implement main analysis functions (45 min)
- Add error handling to analysis (15 min)
- Create first visualization (30 min)

##### Day 5: Analysis & Visualization (1.5 hours)
- Complete data analysis functions (45 min)
- Create remaining visualizations (45 min)

##### Day 6: Integration & Documentation (1.5 hours)
- Connect all components (30 min)
- Debug and fix issues (30 min)
- Complete code documentation (30 min)

##### Day 7: Finalization (1.5 hours)
- Final code review and cleanup (30 min)
- Complete README documentation (30 min)
- Prepare presentation (30 min)

Remember:
- Each day you have exactly 1.5 hours to work
- Focus on completing the core requirements before attempting extensions
- If you finish a day's tasks early, start on the next day's work
- If you're behind schedule, focus on the minimum requirements first

### Day 2: Algorithm Design (2 hours)
- Create flow diagram
- Write algorithm steps
- Develop pseudocode
- Test logic on paper

### Day 3: Data Preparation (2 hours)
- Load and examine dataset
- Clean data
- Document data structure
- Plan analysis approach

### Day 4: Core Development (3 hours)
- Morning (1.5 hours):
  - Implement main functions
  - Add error handling
  - Document code as you write

- Afternoon (1.5 hours):
  - Debug code using print statements
  - Review code organization
  - Check error handling works

### Day 5: Analysis & Debugging (2.5 hours)
- Morning (1.5 hours):
  - Create visualizations
  - Analyze results
  - Document findings

- Afternoon (1 hour):
  - Review code for common errors
  - Check all features work
  - Clean up code comments

### Day 6: Integration & Review (2 hours)
- Morning (1 hour):
  - Combine all components
  - Check data flow
  - Review documentation

- Afternoon (1 hour):
  - Final code review
  - Update comments
  - Prepare for presentation

### Day 7: Documentation & Submission (1.5 hours)
- Complete all documentation
- Final code cleanup
- Prepare presentation
- Submit project

## Setup Guide

### Development Guide

#### Project Structure
All projects will follow this simple structure:
```
your_project/
├── README.md     # Project documentation
├── main.py       # All your Python code goes here
└── data/         # Your dataset files
```

#### Code Organization in main.py
Your code should be organized in this order:
1. Import statements
2. Function definitions (grouped by purpose)
3. Main program execution

Example:
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

if __name__ == "__main__":
    main()
```

### Initial Setup Steps
1. Create project directory
2. Create main.py file
3. Download selected dataset
4. Create README.md file

## Development Process

### Step 1: Algorithm Development
```python
def process_data(input_data):
    """
    Example function showing proper documentation and error handling
    
    Args:
        input_data (list): List of numeric values to process
        
    Returns:
        float: Processed result
        
    Raises:
        ValueError: If input_data is empty or contains non-numeric values
    """
    if not input_data:
        raise ValueError("Input data cannot be empty")
        
    try:
        # Convert strings to numbers if needed
        numbers = [float(x) for x in input_data]
        # Process the data
        result = sum(numbers) / len(numbers)
        return result
    except ValueError as e:
        raise ValueError(f"Invalid input data: {str(e)}")
```

### Step 2: Data Analysis
```python
import pandas as pd
import matplotlib.pyplot as plt

def analyze_data(df):
    """
    Perform basic data analysis
    """
    # Basic statistics
    stats = df.describe()
    
    # Create visualization
    plt.figure(figsize=(10, 6))
    df.plot(kind='bar')
    plt.title('Data Analysis')
    plt.xlabel('Categories')
    plt.ylabel('Values')
    plt.tight_layout()
    plt.savefig('analysis_plot.png')
```

[Continuing in next section...]
