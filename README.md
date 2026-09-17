# **ECE2112-PA-3**


---


**De Guia, Maxine Juliana S.**  
2ECE-D  

This repository contains the Pandas implementation for ECE2112 Experiment 3: Python Data Analysis. It covers fundamental Pandas library operations for loading CSV datasets into DataFrames, performing positional (`.iloc`) and label-based (`.loc`) indexing, applying Boolean mask filtering on DataFrame columns, and extracting structured data subsets without modifying the original source dataset.

```python
import pandas as pd
```

## **A. POSITIONAL AND LABEL-BASED SLICING**

`pd.read_csv('cars.csv')` reads the raw dataset and stores it in memory as a 2D table called a DataFrame named `cars`.

```python
cars = pd.read_csv('cars.csv')
cars

```

`cars.shape` returns a tuple `(32, 12)` indicating the total dimensions of the dataset (32 rows and 12 columns) while `cars.columns` retrieves the column headers. Wrapping it in `list()` formats it into a standard Python list.

```python
print("Shape of cars:", cars.shape)
print("Columns:", list(cars.columns))

```

`cars.iloc[6:11]` stands for integer location. It selects rows based on their 0-indexed position. In Python slicing `start:stop`, the stop index is exclusive. Index `6:11` extracts index positions 6, 7, 8, 9, and 10 which correspond to data rows 7 through 11 in 1-based counting.

```python
cars_6_to_10 = cars.iloc

```

`[['Model', 'mpg', 'cyl', 'hp', 'gear']]` uses double square brackets to perform label-based column selection, extracting only the specified columns from `cars_6_to_10` without altering row selections.

```python
selected_cols = cars_6_to_10[['Model', 'mpg', 'cyl', 'hp', 'gear']]
selected_cols

```

---

## **B. MODEL LOOKUP SLICING**

`cars['Model'] == 'Toyota Corolla'` creates a boolean mask checking every row in the `Model` column. `cars[]` wraps the condition inside the outer DataFrame brackets to filter and return only the rows where the mask evaluates to `True`.

```python
toyota = cars[cars['Model'] == 'Toyota Corolla']
display(toyota)

```

`cars.loc[row_condition, column_list]` uses label-based indexing `.loc[]` to select specific rows and columns simultaneously.

Using `cars['Model'] == 'Pontiac Firebird'` finds the matching row dynamically without hardcoding row numbers. For filters to four target columns `['Model', 'mpg', 'hp', 'wt']` is used.

```python
Pontiac = cars.loc[(cars['Model'] == 'Pontiac Firebird'), ['Model', 'mpg', 'hp', 'wt']]
display(Pontiac)

```

---

## **C. MULTI-MODEL SUBSETTING**

To define a Python list containing the exact target string values and column names to keep code structured and readable, list setup is used.

```python
target_models = ['Datsun 710', 'Lotus Europa', 'Ferrari Dino']
target_cols = ['Model', 'mpg', 'cyl', 'gear']

```

`.isin(target_models)` checks if the string in the model column matches any item inside the `target_models` list, generating a single Boolean filter, while `[target_cols]` immediately chains a column selection onto the filtered rows to retain only the desired variables.

```python
selected_cars = cars[cars['Model'].isin(target_models)][target_cols]

```

`display()` renders the resulting subset as a formatted HTML table in Jupyter. `.shape` displays `(3, 4)`, confirming the required check of 3 rows and 4 columns.

```python
display(selected_cars)
display("Shape of selected_cars:", selected_cars.shape)

```

---

## **README File Version History**

* **September 7, 2026**: Added function implementations and detailed discussions for Problems A, B, and C.
* **September 8, 2026**: Initialized project repository and created initial README file structure.
* **September 9, 2026**: Finalization and checking.

---

## **References**

* Python program for PA3: [Code_Experiment 3.ipynb](https://www.google.com/search?q=https://github.com/maxinedgia-dot/Experiment-3/blob/f01a8ba7d5f2bc66066ae7edc73e96663613c3ed/Code_Experiment%25203.ipynb)

