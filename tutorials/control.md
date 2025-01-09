# Control Statements in Bash

Control statements in bash allow you to control the flow of your scripts based on conditions, perform loops, and make decisions. This tutorial will introduce the most common control statements used in bash scripting, including `if`, `else`, `elif`, `for`, `while`, and `until`.

## 1. `if` Statement

The `if` statement evaluates a condition and runs a block of code if the condition is true.

### Syntax:
```bash
if [ condition ]; then
  # code to be executed if condition is true
fi
```

### Example 1: Basic `if` statement
```bash
#!/bin/bash
number=10
if [ $number -gt 5 ]; then
  echo "Number is greater than 5."
fi
```
**Output:**
```bash
Number is greater than 5.
```

### Explanation:
- `[ $number -gt 5 ]`: The condition checks if the variable `number` is greater than 5.
- `then` marks the beginning of the block that runs if the condition is true.

---

## 2. `else` Statement

The `else` statement provides an alternative block of code to execute when the `if` condition is false.

### Syntax:
```bash
if [ condition ]; then
  # code if condition is true
else
  # code if condition is false
fi
```

### Example 2: `if-else` statement
```bash
#!/bin/bash
number=3
if [ $number -gt 5 ]; then
  echo "Number is greater than 5."
else
  echo "Number is not greater than 5."
fi
```
**Output:**
```bash
Number is not greater than 5.
```

### Explanation:
- If `$number` is greater than 5, the first `echo` runs. Otherwise, the `else` block executes.

---

## 3. `elif` Statement

The `elif` (else if) statement allows checking multiple conditions in a single `if` block.

### Syntax:
```bash
if [ condition1 ]; then
  # code if condition1 is true
elif [ condition2 ]; then
  # code if condition2 is true
else
  # code if no conditions are true
fi
```

### Example 3: `if-elif-else` statement
```bash
#!/bin/bash
number=8
if [ $number -gt 10 ]; then
  echo "Number is greater than 10."
elif [ $number -eq 8 ]; then
  echo "Number is equal to 8."
else
  echo "Number is less than 8."
fi
```
**Output:**
```bash
Number is equal to 8.
```

### Explanation:
- The script checks if `$number` is greater than 10. If false, it checks if `$number` is equal to 8, then prints the corresponding message.

---

## 4. `case` Statement

The `case` statement provides a way to execute different code based on the value of a variable. It is used as an alternative to multiple `if`-`elif`-`else` statements when you have several possible conditions.

### Syntax:
```bash
case $variable in
  pattern1)
    # code if $variable matches pattern1
    ;;
  pattern2)
    # code if $variable matches pattern2
    ;;
  *)
    # code if no pattern matches
    ;;
esac
```

### Example 4: `case` statement
```bash
#!/bin/bash
day="Monday"
case $day in
  "Monday")
    echo "Start of the week."
    ;;
  "Friday")
    echo "Almost weekend!"
    ;;
  *)
    echo "Midweek day."
    ;;
esac
```
**Output:**
```bash
Start of the week.
```

### Explanation:
- The `case` statement checks the value of `$day`. If it matches `"Monday"`, it runs the corresponding block. The `*` (wildcard) is a catch-all for any unmatched values.

---

## 5. `for` Loop

The `for` loop is used to iterate over a range of values or a list of items.

### Syntax (iterating over a range):
```bash
for variable in value1 value2 ... valueN
do
  # code to execute
done
```

### Example 5: `for` loop
```bash
#!/bin/bash
for i in 1 2 3 4 5
do
  echo "Number: $i"
done
```
**Output:**
```bash
Number: 1
Number: 2
Number: 3
Number: 4
Number: 5
```

### Explanation:
- The loop iterates through the values `1 2 3 4 5`, and for each iteration, it prints the current number.

---

## 6. `while` Loop

The `while` loop runs as long as a given condition is true.

### Syntax:
```bash
while [ condition ]
do
  # code to execute
done
```

### Example 6: `while` loop
```bash
#!/bin/bash
counter=1
while [ $counter -le 5 ]
do
  echo "Counter: $counter"
  ((counter++))  # Increment the counter
done
```
**Output:**
```bash
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
```

### Explanation:
- The `while` loop runs as long as the condition `[ $counter -le 5 ]` is true. It increments the `counter` after each iteration.

---

## 7. `until` Loop

The `until` loop works similarly to the `while` loop, but it executes the block of code **until** the condition is true (the opposite of `while`).

### Syntax:
```bash
until [ condition ]
do
  # code to execute
done
```

### Example 7: `until` loop
```bash
#!/bin/bash
counter=1
until [ $counter -gt 5 ]
do
  echo "Counter: $counter"
  ((counter++))  # Increment the counter
done
```
**Output:**
```bash
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
```

### Explanation:
- The loop runs **until** the condition `[ $counter -gt 5 ]` becomes true, which happens when the counter exceeds 5.

---

## 8. `break` and `continue`

- **`break`**: Exits the current loop (whether `for`, `while`, or `until`).
- **`continue`**: Skips the current iteration of the loop and moves to the next iteration.

### Example 8: `break` and `continue`
```bash
#!/bin/bash
for i in {1..5}
do
  if [ $i -eq 3 ]; then
    continue  # Skip the iteration when i equals 3
  elif [ $i -eq 4 ]; then
    break  # Exit the loop when i equals 4
  fi
  echo "Number: $i"
done
```
**Output:**
```bash
Number: 1
Number: 2
Number: 4
```

### Explanation:
- The loop skips printing when `i` equals 3 (`continue`), and it exits the loop when `i` equals 4 (`break`).

---

## Practice Exercises

1. Write a script that checks if a given number is even or odd.
2. Create a script that loops through a list of file names and prints whether each file exists.
3. Use a `while` loop to count down from 10 to 1 and print each number.
4. Create a script using a `case` statement to perform actions based on a user's input (e.g., "start", "stop", "status").