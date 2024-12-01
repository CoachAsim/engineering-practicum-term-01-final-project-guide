# Python Style Guide for Beginners

This guide covers the most important Python style rules you should follow. These rules help make your code easier to read and understand!

## 1. Naming Rules 🏷️

### Variables and Functions
```python
# ✅ GOOD - Use lowercase with underscores
student_name = "Alice"
total_score = 0
def calculate_average():
    pass

# ❌ BAD - Don't use these styles
studentName = "Alice"    # No camelCase
StudentName = "Alice"    # No CapWords
t = "Alice"             # Too short/unclear
```

### Constants
```python
# ✅ GOOD - Use uppercase with underscores
MAX_STUDENTS = 30
PASSING_GRADE = 70

# ❌ BAD
maxStudents = 30        # Not uppercase
passing_grade = 70      # Not uppercase
```

## 2. Spacing Rules 📏

### Around Operators
```python
# ✅ GOOD - Space around operators
x = 5 + 3
name = "Alice" + " Smith"
total = sum(numbers) / len(numbers)

# ❌ BAD - No spaces
x=5+3
name="Alice"+"Smith"
total=sum(numbers)/len(numbers)
```

### After Commas
```python
# ✅ GOOD - Space after commas
numbers = [1, 2, 3, 4]
calculate_score(homework, test, participation)

# ❌ BAD - No spaces after commas
numbers = [1,2,3,4]
calculate_score(homework,test,participation)
```

## 3. Indentation 🔸

```python
# ✅ GOOD - Use 4 spaces for each level
def calculate_grade(score):
    if score >= 90:
        return "A"
    elif score >= 80:
        return "B"
    else:
        return "C"

# ❌ BAD - Wrong indentation
def calculate_grade(score):
  if score >= 90:       # Only 2 spaces
      return "A"        # Inconsistent
    elif score >= 80:   # Misaligned
        return "B"
```

## 4. Line Length 📏

```python
# ✅ GOOD - Keep lines under 79 characters
student_names = [
    "Alice Smith",
    "Bob Jones",
    "Charlie Brown"
]

# ❌ BAD - Line too long
student_names = ["Alice Smith", "Bob Jones", "Charlie Brown", "David Wilson", "Eve Johnson", "Frank Williams", "Grace Davis"]
```

## 5. Comments 💭

```python
# ✅ GOOD - Clear, helpful comments
# Calculate average test score
average = sum(scores) / len(scores)

def calculate_final_grade(scores):
    """
    Calculate the final grade from a list of test scores.
    Takes the average and rounds to nearest integer.
    """
    return round(sum(scores) / len(scores))

# ❌ BAD - Obvious or unhelpful comments
# Add numbers                    # Too obvious
total = sum(numbers)            

# This function calculates grade # Repeats what code already shows
def calculate_grade(score):
    return "A" if score >= 90 else "B"
```

## 6. Imports 📥

```python
# ✅ GOOD - One import per line, at the top of file
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# ❌ BAD - Don't do these
import pandas as pd, numpy as np  # Multiple on one line
from matplotlib.pyplot import *   # Don't import everything
```

## 7. Whitespace Tips 📝

### Blank Lines
```python
# ✅ GOOD - Use blank lines to separate logical sections
def calculate_average(numbers):
    """Calculate average of numbers."""
    total = sum(numbers)
    count = len(numbers)
    
    return total / count


def calculate_grade(score):
    """Determine letter grade from score."""
    if score >= 90:
        return "A"
    
    if score >= 80:
        return "B"
    
    return "C"
```

## Quick Checklist ✅

Before submitting your code, check:
- [ ] Used clear variable names with underscores
- [ ] Added spaces around operators (+, -, =, etc.)
- [ ] Used 4 spaces for indentation
- [ ] Kept lines under 79 characters
- [ ] Added helpful comments
- [ ] Put imports at top of file
- [ ] Used blank lines to separate code sections

## Remember 🌟
- Style matters! It makes your code easier to read
- Consistent style helps others understand your code
- When in doubt, keep it simple and clear
- These rules will become natural with practice

## Common Mistakes to Avoid ⚠️
1. Mixing tabs and spaces (use only spaces!)
2. Using unclear variable names (x, y, z)
3. Forgetting spaces around operators
4. Writing lines that are too long
5. Writing comments that don't add value
6. Inconsistent indentation

## Quick Tips for Success 💡
1. Use a code editor that shows spaces (like VS Code or PyCharm)
2. Learn your editor's auto-formatting shortcuts
3. Review your code before submitting
4. When copying code from the internet, fix its style
5. Ask for feedback on your code style