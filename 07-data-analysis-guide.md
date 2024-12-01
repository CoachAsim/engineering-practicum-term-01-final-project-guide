# 07-data-analysis-guide.md

# Interactive Data Analysis Guide

## 1. Data Loading with User Input
```python
def load_data():
    """Interactive data loading with user feedback."""
    while True:
        try:
            print("\nAvailable datasets:")
            print("1. dataset1.csv")
            print("2. dataset2.csv")
            choice = input("Select dataset (1-2): ")
            
            filename = f"dataset{choice}.csv"
            df = pd.read_csv(filename)
            print(f"Successfully loaded {len(df)} rows")
            
            # Show preview
            preview = input("Would you like to see the first few rows? (y/n): ")
            if preview.lower() == 'y':
                print("\nData Preview:")
                print(df.head())
                
            return df
            
        except FileNotFoundError:
            print("Error: File not found. Please try again.")
        except Exception as e:
            print(f"Error loading data: {e}")
```

## 2. Interactive Data Cleaning
```python
def clean_data(df):
    """Interactive data cleaning with user choices."""
    print("\n=== Data Cleaning Options ===")
    
    # Handle missing values
    if df.isnull().any().any():
        print("\nFound missing values in:")
        for col in df.columns[df.isnull().any()]:
            print(f"- {col}: {df[col].isnull().sum()} missing")
        
        print("\nHow would you like to handle missing values?")
        print("1. Remove rows with missing values")
        print("2. Fill with mean/mode")
        print("3. Keep as is")
        
        choice = input("Enter choice (1-3): ")
        if choice == '1':
            df = df.dropna()
            print(f"Removed rows with missing values. {len(df)} rows remaining.")
        elif choice == '2':
            for col in df.select_dtypes(include=['number']):
                df[col].fillna(df[col].mean(), inplace=True)
            print("Filled missing values in numeric columns.")
    
    return df
```

## 3. Interactive Analysis
```python
def analyze_data(df):
    """Interactive data analysis with user-chosen features."""
    while True:
        print("\n=== Analysis Options ===")
        print("Available columns:")
        for i, col in enumerate(df.columns, 1):
            print(f"{i}. {col}")
        print(f"{len(df.columns) + 1}. Exit Analysis")
        
        try:
            choice = int(input("\nSelect column to analyze: "))
            if choice == len(df.columns) + 1:
                break
                
            column = df.columns[choice - 1]
            
            print(f"\nAnalysis of {column}:")
            print("-" * 40)
            
            if df[column].dtype in ['int64', 'float64']:
                print(f"Mean: {df[column].mean():.2f}")
                print(f"Median: {df[column].median():.2f}")
                print(f"Std Dev: {df[column].std():.2f}")
                
                visualize = input("\nCreate visualization? (y/n): ")
                if visualize.lower() == 'y':
                    create_visualization(df, column)
            else:
                print("Value counts:")
                print(df[column].value_counts().head())
                
            input("\nPress Enter to continue...")
            
        except (ValueError, IndexError):
            print("Invalid choice. Please try again.")
```

## 4. Interactive Visualization
```python
def create_visualization(df, column):
    """Create visualizations with user input."""
    print("\n=== Visualization Options ===")
    print("1. Histogram")
    print("2. Box Plot")
    print("3. Time Series (if date/time)")
    
    choice = input("Select visualization type: ")
    
    plt.figure(figsize=(10, 6))
    
    if choice == '1':
        df[column].hist()
        plt.title(f"Distribution of {column}")
    elif choice == '2':
        df.boxplot(column=column)
        plt.title(f"Box Plot of {column}")
    elif choice == '3':
        if pd.api.types.is_datetime64_any_dtype(df[column]):
            df[column].value_counts().sort_index().plot()
            plt.title(f"Time Series of {column}")
        else:
            print("Column is not datetime type")
            return
            
    plt.show()
```

## Common Analysis Patterns

### 1. Exploratory Analysis Flow
1. Load data with user input
2. Show initial statistics
3. Offer cleaning options
4. Present analysis choices
5. Create visualizations
6. Allow for iteration

### 2. Data Quality Checks
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
    
    return issues
```