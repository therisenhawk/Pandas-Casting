# Pandas Cast

This project contains examples of reshaping data from long format to wide format using pandas. The first example shows how to do it manually, while the other examples use a reusable `cast()` function.

## What is Casting?

Casting is the process of converting values from one column into separate columns.

For example, the original data contains cities, weather types, and their corresponding values.

| city | weather | value |
|---|---|---:|
| Podgorica | temperature | 25 |
| Podgorica | rain | 10 |
| Nikšić | temperature | 22 |
| Nikšić | rain | 15 |

After casting, each weather type becomes its own column.

| city | temperature | rain |
|---|---:|---:|
| Podgorica | 25 | 10 |
| Nikšić | 22 | 15 |

This makes it easier to compare different categories side by side.

## Files and Examples

### 1. Manual Casting

The first example shows how to reshape the data without creating a general function.

The process is:

1. Select the rows for one weather type.
2. Remove the `weather` column because its values will become column names.
3. Rename the `value` column to the corresponding weather type.
4. Repeat the process for the other weather types.
5. Merge the resulting DataFrames using `pd.merge()`.

This example helps explain how casting works step by step.

### 2. Custom Cast Function: Weather Data

The second example implements a reusable `cast()` function.

The function takes the following arguments:

- `df`: the DataFrame being reshaped.
- `key`: the column containing the values that will become new column names.
- `value`: the column containing the values that will fill the new columns.
- `join_how`: the type of join used when merging the resulting DataFrames. The default is `outer`.

The function identifies the columns that should remain unchanged, loops through the unique values in the key column, and creates a separate DataFrame for each value. It then merges the resulting tables using the columns that were kept.

### 3. Custom Cast Function: Student Scores

The third example applies the same approach to student scores.

The original data contains students, subjects, and scores. The function converts the unique subjects into separate columns, making it easier to compare each student's results.

For example, the `subject` column becomes `Math` and `English`, while the `score` column provides the corresponding values.

This demonstrates how the same function can be used with different datasets without rewriting the entire process.

## Requirements

- Python 3
- pandas

Install pandas if needed:

```bash
pip install pandas
```

## What I Learned

This project helped me understand how to reshape data from long format to wide format, select and filter rows, rename columns, and merge DataFrames.

It also helped me understand how to use loops and functions to automate repeated operations and apply the same approach to different types of data.
