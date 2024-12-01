# 05-development-process.md

# Development Process

## Example main.py Organizations

### 1. Interactive Data Analysis Project (e.g., Music Listening Habits)
```python
"""
Project: Music Listening Habits Analyzer
Author: [Your Name]
Date: [Current Date]

Interactive analysis of personal music listening data.
"""

import pandas as pd
import matplotlib.pyplot as plt

# Constants for menu options and configuration
MAIN_MENU = {
    '1': 'Analyze Top Artists',
    '2': 'Explore Listening Times',
    '3': 'Find Song Patterns',
    '4': 'Generate Report',
    '5': 'Exit'
}

def load_and_prepare_data(filename):
    """Load and prepare music listening data."""
    try:
        df = pd.read_csv(filename)
        # Convert timestamps to datetime
        df['timestamp'] = pd.to_datetime(df['timestamp'])
        return df
    except Exception as e:
        print(f"Error processing data: {e}")
        return None

def analyze_top_artists(df):
    """Analyze and display top artists."""
    try:
        count = int(input("How many top artists to show? "))
        top_artists = df['artist'].value_counts().head(count)
        
        print(f"\nTop {count} Artists:")
        for i, (artist, plays) in enumerate(top_artists.items(), 1):
            print(f"{i}. {artist}: {plays} plays")
        
        return top_artists
    except ValueError:
        print("Please enter a valid number")
        return None

def explore_listening_times(df):
    """Analyze listening patterns by time."""
    df['hour'] = df['timestamp'].dt.hour
    hourly_listens = df['hour'].value_counts().sort_index()
    
    print("\nListening Times Analysis:")
    print("Peak listening hour:", hourly_listens.idxmax())
    print("Quietest hour:", hourly_listens.idxmin())
    
    return hourly_listens

def main():
    """Main program loop."""
    df = load_and_prepare_data('listening_history.csv')
    if df is None:
        return
    
    while True:
        print("\n=== Music Listening Analysis ===")
        for key, value in MAIN_MENU.items():
            print(f"{key}. {value}")
            
        choice = input("\nEnter your choice: ")
        
        if choice == '1':
            top_artists = analyze_top_artists(df)
            if top_artists is not None:
                visualize = input("\nVisualize as chart? (y/n): ")
                if visualize.lower() == 'y':
                    top_artists.plot(kind='bar')
                    plt.title("Top Artists by Play Count")
                    plt.show()
        
        elif choice == '2':
            hourly_data = explore_listening_times(df)
            visualize = input("\nVisualize listening times? (y/n): ")
            if visualize.lower() == 'y':
                hourly_data.plot(kind='line')
                plt.title("Listening Activity by Hour")
                plt.show()
        
        elif choice == '5':
            print("Thanks for using the Music Analyzer!")
            break
        
        input("\nPress Enter to continue...")

if __name__ == "__main__":
    main()
```

### 2. Data Validation and Cleaning
```python
def check_data_quality(df):
    """Interactive data quality assessment."""
    issues = []
    
    # Check missing values
    missing = df.isnull().sum()
    if missing.any():
        issues.append("Missing values found")
    
    # Check duplicates
    duplicates = df.duplicated().sum()
    if duplicates:
        issues.append("Duplicate rows found")
    
    # Check numeric columns for outliers
    for col in df.select_dtypes(include=['number']):
        Q1 = df[col].quantile(0.25)
        Q3 = df[col].quantile(0.75)
        IQR = Q3 - Q1
        outliers = df[(df[col] < Q1 - 1.5*IQR) | (df[col] > Q3 + 1.5*IQR)]
        if len(outliers) > 0:
            issues.append(f"Outliers found in {col}")
    
    if issues:
        print("\nData Quality Issues Found:")
        for issue in issues:
            print(f"- {issue}")
        
        handle_issues = input("\nWould you like to address these issues? (y/n): ")
        if handle_issues.lower() == 'y':
            return clean_data(df)
    
    return df
```

## Debug Checklist

```markdown
## Before Submission Debug Checklist

### Interactive Features
- [ ] All menu options work
- [ ] Input validation in place
- [ ] Clear error messages
- [ ] Easy to navigate
- [ ] Exit options available

### Data Processing
- [ ] Data loads correctly
- [ ] Cleaning options work
- [ ] Analysis functions correct
- [ ] Results make sense
- [ ] Error handling works

### User Experience
- [ ] Clear instructions
- [ ] Consistent formatting
- [ ] Helpful feedback
- [ ] Logical flow
- [ ] Progress indicators

### Code Quality
- [ ] Functions documented
- [ ] Variables clear
- [ ] Comments helpful
- [ ] Code organized
- [ ] PEP8 compliant
```