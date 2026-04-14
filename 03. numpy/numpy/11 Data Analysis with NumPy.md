### **1. Statistical Operations**

Statistical functions help you understand the distribution and central tendencies of your data.

- **Mean:** The mathematical average of the array values.
    
- **Median:** The middle value when the data is sorted. It is often more robust than the mean when your data contains outliers.
    
- **Variance:** A measure of how spread out the data is from the mean. High variance indicates data points are widely scattered.
    
- **Standard Deviation (Std Dev):** The square root of the variance. It is heavily used because it is expressed in the exact same units as the original data.
    

![[Pasted image 20260414143517.png]]


**Example:**

```Python
import numpy as np

# Sample data: Ages of a group of people
ages = np.array() # Note the outlier '85'

print("--- Statistical Operations ---")
print("Data:", ages)

# Mean
print("Mean (Average):", np.mean(ages)) 
# Output: 32.75

# Median (Notice how the median is not heavily skewed by the 85 year old)
print("Median:", np.median(ages)) 
# Output: 24.5

# Variance
print("Variance:", np.var(ages))
# Output: 388.9375

# Standard Deviation
print("Standard Deviation:", np.std(ages))
# Output: ~19.72 (The ages deviate from the mean by about 19.7 years on average)
```

---

### **2. Aggregation Methods**

Aggregations reduce your array down to a single value (or an array of summary values) by combining elements.

A crucial concept here is the `axis` parameter when working with 2D arrays (matrices) or higher:

- `axis=None` (Default): Flattens the array and aggregates everything.
    
- `axis=0`: Aggregates vertically (down the rows/columns).
    
- `axis=1`: Aggregates horizontally (across the columns/rows).
    

**Example:**


```Python
import numpy as np

# 2D Array: Sales data (Rows = Stores, Columns = Quarters Q1, Q2, Q3)
sales = np.array([
   , # Store A
   , # Store B
     # Store C
])

print("--- Aggregation Methods ---")
print("Sales Data:\n", sales)

# 1. Global Aggregation (Default)
print("\nTotal Sales (All stores, all quarters):", np.sum(sales)) 
# Output: 1530

print("Highest Single Quarter Sale:", np.max(sales))
# Output: 300

print("Lowest Single Quarter Sale:", np.min(sales))
# Output: 90

# 2. Aggregation along Axes
# Total sales PER STORE (sum across columns -> axis=1)
print("\nTotal Sales per Store:", np.sum(sales, axis=1))
# Output: [450 330 750]

# Highest sale PER QUARTER (max down rows -> axis=0)
print("Max Sales per Quarter:", np.max(sales, axis=0))
# Output: [250 200 300]
```

---

### **3. Managing Missing Data**

In real-world data, you will often encounter missing values. In NumPy, missing numerical data is represented by `np.nan` (Not a Number), which is technically a floating-point value.

**The Problem:** Standard mathematical and statistical operations in NumPy will return `nan` if even a single `nan` is present in the data being calculated.

**The Solution:** NumPy provides specialized "nan-safe" functions that ignore `np.nan` values during calculations.

**Example:**


```Python
import numpy as np

# Data with missing values (e.g., faulty sensor readings)
readings = np.array([12.5, 14.1, np.nan, 15.0, np.nan, 13.8])

print("--- Managing Missing Data ---")
print("Original Data:", readings)

# 1. The Problem with Standard Functions
print("\nStandard Mean (Fails due to NaN):", np.mean(readings))
# Output: nan
print("Standard Sum (Fails due to NaN):", np.sum(readings))
# Output: nan

# 2. Using NaN-Safe Functions
print("\nSafe Mean:", np.nanmean(readings))
# Output: 13.85 (Calculates mean of [12.5, 14.1, 15.0, 13.8])

print("Safe Sum:", np.nansum(readings))
# Output: 55.4

print("Safe Max:", np.nanmax(readings))
# Output: 15.0

# 3. Finding and Filtering NaNs
# np.isnan() creates a boolean mask of where the NaNs are
nan_mask = np.isnan(readings)
print("\nBoolean Mask of NaNs:", nan_mask)
# Output: [False False  True False  True False]

# Use the bitwise NOT operator (~) to invert the mask and filter out NaNs
clean_data = readings[~np.isnan(readings)]
print("Cleaned Data (NaNs removed):", clean_data)
# Output: [12.5 14.1 15.  13.8]
```