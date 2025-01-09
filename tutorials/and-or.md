# Tutorial: Using `&&` and `||` Operators in Bash

In bash scripting, the `&&` (AND) and `||` (OR) operators are used to combine multiple commands in a conditional way. These operators allow you to control the flow of execution based on the success or failure of previous commands.

## 1. `&&` - AND Operator

The `&&` operator is used to execute the second command **only if the first command succeeds** (i.e., returns an exit status of `0`).

### Syntax:
```bash
command1 && command2
```
- `command2` will execute only if `command1` exits with status `0` (success).

### Example 1: Basic `&&` Example
```bash
#!/bin/bash
mkdir /tmp/new_directory && echo "Directory created successfully."
```
**Explanation**:
- If `mkdir /tmp/new_directory` is successful (i.e., the directory is created), the `echo` command will execute, printing "Directory created successfully."

**Output (if successful)**:
```bash
Directory created successfully.
```

### Example 2: Chaining Multiple Commands with `&&`
```bash
#!/bin/bash
cd /some/directory && touch file.txt && echo "File created."
```
**Explanation**:
- If `cd /some/directory` is successful, the script will run `touch file.txt`, which will create a new file.
- If `touch file.txt` is successful, the `echo` command will print "File created."

---

## 2. `||` - OR Operator

The `||` operator is used to execute the second command **only if the first command fails** (i.e., returns a non-zero exit status).

### Syntax:
```bash
command1 || command2
```
- `command2` will execute if `command1` exits with a non-zero status (failure).

### Example 3: Basic `||` Example
```bash
#!/bin/bash
mkdir /tmp/new_directory || echo "Failed to create directory."
```
**Explanation**:
- If the `mkdir` command fails (for example, if the directory already exists), `echo "Failed to create directory."` will execute.

**Output (if the directory already exists)**:
```bash
Failed to create directory.
```

### Example 4: Chaining Commands with `||`
```bash
#!/bin/bash
cd /nonexistent/directory || echo "Directory not found." || exit 1
```
**Explanation**:
- If the `cd /nonexistent/directory` command fails, it will print "Directory not found."
- If the `cd` command fails, the script will exit with status `1`.

---

## 3. Combining `&&` and `||` Operators

You can combine both `&&` and `||` operators to create more complex control flows. This is useful when you want to execute commands depending on the success or failure of the previous commands.

### Example 5: Using Both `&&` and `||`
```bash
#!/bin/bash
mkdir /tmp/new_directory && echo "Directory created." || echo "Failed to create directory."
```
**Explanation**:
- If `mkdir /tmp/new_directory` is successful, the message "Directory created." will be printed.
- If `mkdir` fails, it will print "Failed to create directory."

---

### Example 6: Full Example with `&&` and `||`
```bash
#!/bin/bash
echo "Step 1: Start process." && mkdir /tmp/process_folder && cd /tmp/process_folder && touch process.txt || echo "Process failed. Cleaning up..." && rm -rf /tmp/process_folder
```
**Explanation**:
- The script attempts to create a folder (`mkdir`) and change into that folder (`cd`).
- If all steps are successful, it will create a file (`touch process.txt`).
- If any step fails, it will print "Process failed." and remove the created directory with `rm -rf`.

---

## 4. Exit Status in Bash

- **Success**: A command that completes successfully returns an exit status of `0`.
- **Failure**: A command that fails returns a non-zero exit status (commonly `1`).

### Example 7: Checking Exit Status
```bash
#!/bin/bash
mkdir /tmp/new_directory && echo "Directory created successfully."
echo "Exit status of mkdir: $?"
```
**Explanation**:
- The `$?` variable holds the exit status of the last command.
- If the `mkdir` command is successful, `$?` will be `0`.

---

## 5. Summary

### `&&` - AND Operator:
- Executes the second command only if the first command is successful (exit status `0`).

### `||` - OR Operator:
- Executes the second command only if the first command fails (non-zero exit status).

### Combining `&&` and `||`:
- You can chain multiple commands with `&&` and `||` to create conditional execution based on the success or failure of previous commands.

---

## Practice Exercises

1. **Exercise 1**: Write a script that checks if a directory exists and prints an appropriate message (using `&&` and `||`).
2. **Exercise 2**: Create a script that attempts to create a file, and if it fails, prints an error message and exits the script.
3. **Exercise 3**: Write a script that tries to change to a non-existent directory, prints an error message if it fails, and creates the directory if successful.
4. **Exercise 4**: Create a script that runs multiple commands with both `&&` and `||` to perform a sequence of tasks and handle errors accordingly.
