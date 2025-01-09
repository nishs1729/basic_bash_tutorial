# Beginner's Guide to the `awk` Command in Bash

The `awk` command is a powerful text-processing tool in Bash. It is often used for pattern scanning and processing. With `awk`, you can manipulate data from files or pipelines, making it an essential tool for shell scripting and data analysis.

---

## What is the `awk` Command?
`awk` is:
- A programming language for text processing.
- Line-oriented, processing each line of input one at a time.
- Useful for extracting and manipulating text-based data.

---

## Syntax
```bash
awk 'pattern {action}' file
```
- **pattern**: Specifies which lines or records to process.
- **action**: Specifies what to do with those lines or records.
- **file**: The file to process (optional; `awk` reads from standard input if omitted).

---

## Common Options
- `-F`: Specifies the input field separator.
- `-v`: Defines variables to be used inside the `awk` script.

---

## Examples

### 1. Printing Entire Lines
Print every line in a file:
```bash
awk '{print}' file.txt
```
**Sample Input:**
```
Line 1
Line 2
Line 3
```
**Sample Output:**
```
Line 1
Line 2
Line 3
```

### 2. Printing Specific Columns
Print the first column of a file:
```bash
awk '{print $1}' file.txt
```
**Sample Input:**
```
John 25 Developer
Alice 30 Designer
Bob 22 Engineer
```
**Sample Output:**
```
John
Alice
Bob
```

Print the second and third columns:
```bash
awk '{print $2, $3}' file.txt
```
**Sample Input:**
```
John 25 Developer
Alice 30 Designer
Bob 22 Engineer
```
**Sample Output:**
```
25 Developer
30 Designer
22 Engineer
```

### 3. Specifying a Field Separator
If fields are separated by commas, use the `-F` option:
```bash
awk -F',' '{print $1, $2}' file.csv
```
**Sample Input:**
```
Name,Age,Role
John,25,Developer
Alice,30,Designer
Bob,22,Engineer
```
**Sample Output:**
```
Name Age
John 25
Alice 30
Bob 22
```

### 4. Using Patterns
Print lines containing "error":
```bash
awk '/error/ {print}' file.txt
```
**Sample Input:**
```
This is fine
An error occurred
All good here
```
**Sample Output:**
```
An error occurred
```

Print lines where the second column is greater than 25:
```bash
awk '$2 > 25 {print}' file.txt
```
**Sample Input:**
```
John 25 Developer
Alice 30 Designer
Bob 22 Engineer
```
**Sample Output:**
```
Alice 30 Designer
```

### 5. Using Actions
Print a formatted string with fields:
```bash
awk '{print "Name: "$1", Age: "$2}' file.txt
```
**Sample Input:**
```
John 25
Alice 30
Bob 22
```
**Sample Output:**
```
Name: John, Age: 25
Name: Alice, Age: 30
Name: Bob, Age: 22
```

Print the sum of values in the second column:
```bash
awk '{sum += $2} END {print "Total: ", sum}' file.txt
```
**Sample Input:**
```
John 25
Alice 30
Bob 22
```
**Sample Output:**
```
Total: 77
```

---

## Advanced Examples

### 1. Multiple Conditions
Print lines where the second column is greater than 20 and the third column is "Designer":
```bash
awk '$2 > 20 && $3 == "Designer" {print}' file.txt
```
**Sample Input:**
```
John 25 Developer
Alice 30 Designer
Bob 22 Engineer
```
**Sample Output:**
```
Alice 30 Designer
```

### 2. Modifying Field Values
Change the second column to "50" for all lines:
```bash
awk '{$2 = 50; print}' file.txt
```
**Sample Input:**
```
John 25 Developer
Alice 30 Designer
Bob 22 Engineer
```
**Sample Output:**
```
John 50 Developer
Alice 50 Designer
Bob 50 Engineer
```

### 3. Using Variables
Define a variable and use it in a condition:
```bash
awk -v threshold=25 '$2 > threshold {print}' file.txt
```
**Sample Input:**
```
John 25 Developer
Alice 30 Designer
Bob 22 Engineer
```
**Sample Output:**
```
Alice 30 Designer
```

---

## Practice Exercises
1. Print only the third column from a comma-separated file named `data.csv`.
2. Print lines where the first column starts with "A".
3. Calculate the average of numbers in the second column of `scores.txt`.
4. Print all lines in `employees.txt` where the role is "Engineer".
5. Replace the first column in `file.txt` with "Anonymous" and print the result.
