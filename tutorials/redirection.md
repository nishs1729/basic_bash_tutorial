# Bash Command Tutorial: Input and Output Redirection

## Introduction
In bash, **input and output redirection** allows you to control where the data comes from (input) and where the data goes (output). This is achieved using special symbols that redirect the flow of data to or from files, other programs, or devices. Redirection is one of the most powerful features in bash, as it allows you to work with files and commands in a more flexible and automated way.

## What is Input and Output Redirection?

- **Input Redirection** (`<`): Redirects input to a command from a file instead of the standard input (keyboard).
- **Output Redirection** (`>` and `>>`): Redirects output from a command to a file instead of the standard output (screen).
- **Appending Output** (`>>`): Redirects output to a file, appending it to the file without overwriting it.

### Basic Syntax:
```bash
command < input_file
command > output_file
command >> output_file
```

- **`command < input_file`**: Uses the file `input_file` as the input to `command`.
- **`command > output_file`**: Redirects the output of `command` to `output_file`, overwriting the file.
- **`command >> output_file`**: Redirects the output of `command` to `output_file`, appending to the file instead of overwriting.

## Redirection of Output

### 1. **Redirecting Standard Output to a File** (`>`)
By default, commands send their output to the terminal (standard output). You can redirect this output to a file using the `>` symbol. This will overwrite the file if it already exists.

Example:
```bash
echo "Hello, World!" > output.txt
```

This will create a file `output.txt` containing the text "Hello, World!". If `output.txt` already exists, it will be overwritten.

### 2. **Appending Output to a File** (`>>`)
If you want to append output to an existing file (instead of overwriting it), you can use the `>>` operator.

Example:
```bash
echo "Goodbye, World!" >> output.txt
```

This appends the text "Goodbye, World!" to `output.txt`. If the file doesn't exist, it will be created.

### 3. **Redirecting Both Standard Output and Standard Error**
You can redirect both the standard output (`stdout`) and standard error (`stderr`) to a file. This is useful for logging purposes.

Example:
```bash
command > output.txt 2>&1
```

This redirects both `stdout` (file descriptor 1) and `stderr` (file descriptor 2) to `output.txt`.

Alternatively, you can use the `&>` operator:
```bash
command &> output.txt
```

This will also redirect both output and error streams to `output.txt`.

## Redirection of Input

### 1. **Redirecting Input from a File** (`<`)
By default, commands read from the terminal (standard input). You can redirect input to a command from a file using the `<` operator.

Example:
```bash
sort < unsorted.txt
```

This will sort the contents of `unsorted.txt` as if they were typed in the terminal.

### 2. **Here Document (`<<`)**
A **here document** allows you to provide multiple lines of input directly within the script or command line. The `<<` operator is used to specify the delimiter, which marks the end of the input.

Example:
```bash
cat << EOF
Hello, World!
This is a here document.
EOF
```

This will display:
```
Hello, World!
This is a here document.
```

## Redirection with `tee`

The `tee` command is used to read from standard input and write to both standard output and one or more files. This allows you to see the output on the screen and save it to a file at the same time.

Example:
```bash
echo "This is a test" | tee output.txt
```

This will display "This is a test" on the terminal and write it to `output.txt`.

You can also append the output to an existing file with the `-a` option:
```bash
echo "Another line" | tee -a output.txt
```

## Practical Examples

### Example 1: Redirecting Output to a File
You want to save the list of files in a directory to a file:
```bash
ls > file_list.txt
```
This will save the list of files in the current directory to `file_list.txt`.

### Example 2: Appending Output to a File
You want to add a timestamp to a log file:
```bash
date >> logfile.txt
```
This appends the current date and time to `logfile.txt`.

### Example 3: Redirecting Input for a Command
If you have a file with a list of names, you can use the `sort` command to sort them:
```bash
sort < names.txt
```
This sorts the contents of `names.txt` without displaying the original file contents on the screen.

### Example 4: Using Here Document to Input Multiple Lines
You can provide a block of text to a command using a here document:
```bash
cat << EOF > file.txt
Line 1
Line 2
Line 3
EOF
```
This creates `file.txt` containing:
```
Line 1
Line 2
Line 3
```

### Example 5: Redirecting Both Output and Error
You can redirect both the standard output and errors to a log file:
```bash
ls non_existent_directory > output.log 2>&1
```
This will capture both the output and error messages of the `ls` command in `output.log`.

## Practice Exercises

1. **Redirecting Output to a File**: Run the `ls` command to list files and redirect the output to a file named `file_list.txt`.

2. **Appending Output**: Run the `date` command and append the output to a file named `logfile.txt`.

3. **Redirecting Input**: Create a file `names.txt` with a list of names and use the `sort` command to sort them by redirecting input from the file.

4. **Using Here Document**: Create a script that uses a here document to generate a configuration file with multiple lines of text.

5. **Redirect Both Output and Errors**: Use a command that will produce both output and errors (e.g., `ls` with a non-existent directory) and redirect both to a file.

6. **Using `tee` Command**: Redirect output to a file and display it on the screen at the same time using the `tee` command.
