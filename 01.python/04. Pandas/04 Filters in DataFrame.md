Filtering is where Pandas truly shines. If you've ever used the "Filter" tool in Excel or written a `WHERE` clause in SQL, this is the exact same concept.

In Pandas, filtering is technically called **Boolean Indexing**. It sounds fancy, but it just means you are asking a True/False question for every row in your DataFrame, and Pandas only keeps the rows where the answer is "True."

Let's use a slightly expanded version of our student DataFrame to look at the most common ways to filter data.

### **The Setup**

Here is our starting data:



```Python
import pandas as pd

student_data = {
    "Name": ["Alice", "Bob", "Charlie", "David", "Eve"],
    "Age": [20, 21, 19, 22, 20],
    "Major": ["Biology", "Math", "Physics", "Art", "Math"],
    "Score": [95, 82, 88, 91, 79]
}

df = pd.DataFrame(student_data)
print(df)
```

**Our Starting DataFrame:**


```
      Name  Age    Major  Score
0    Alice   20  Biology     95
1      Bob   21     Math     82
2  Charlie   19  Physics     88
3    David   22      Art     91
4      Eve   20     Math     79
```

---

### **1. Filtering with a Single Condition**

To filter, you put your condition inside square brackets `[]` right after the DataFrame name.

Let's find all students who scored an A (90 or above):



```Python
# "Keep rows in 'df' where the 'Score' column is greater than or equal to 90"
a_students = df[df["Score"] >= 90]

print(a_students)
```

**Output:**


```
    Name  Age    Major  Score
0  Alice   20  Biology     95
3  David   22      Art     91
```

### **2. Filtering with Multiple Conditions**

You can combine conditions using special symbols:

- **`&` (AND):** Both conditions must be true.
    
- **`|` (OR):** At least one condition must be true.
    

_Important:_ When using multiple conditions, you **must** wrap each individual condition in parentheses `()`.

Let's find students who are Math majors **AND** scored above an 80:



```Python
# Math majors with a score > 80
top_math = df[(df["Major"] == "Math") & (df["Score"] > 80)]

print(top_math)
```

**Output:**


```
  Name  Age Major  Score
1  Bob   21  Math     82
```

_(Eve is a Math major, but her score is 79, so she is filtered out)._

### **3. Filtering using `.isin()`**

If you want to filter based on a list of specific values, typing out a bunch of "OR" conditions gets messy. The `.isin()` method checks if a row's value matches anything in a list you provide.

Let's find students who are majoring in either Biology or Physics:



```Python
# Keep rows where the Major is in this specific list
science_students = df[df["Major"].isin(["Biology", "Physics"])]

print(science_students)
```

**Output:**

```
      Name  Age    Major  Score
0    Alice   20  Biology     95
2  Charlie   19  Physics     88
```

### **4. Filtering Text using `.str.contains()`**

Sometimes you don't know the exact value, but you know what it contains. You can access Pandas' string methods using `.str`.

Let's find any student whose name starts with a "C" or contains a "v":



```Python
# Keep rows where the Name contains the letter 'v'
v_names = df[df["Name"].str.contains("v")]

print(v_names)
```

**Output:**

Plaintext

```
    Name  Age Major  Score
3  David   22   Art     91
4    Eve   20  Math     79
```