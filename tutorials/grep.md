# Bash Command Tutorial: Using `grep`

## Introduction
`grep` (short for **Global Regular Expression Print**) is one of the most commonly used commands in bash for searching through text. It allows you to search for specific patterns (strings, regular expressions) within files or output. `grep` is highly flexible and can be used for tasks ranging from simple string matching to advanced pattern searching using regular expressions.

In this tutorial, we will cover the basic usage of `grep`, its options, and various examples to help you become proficient with this powerful tool.

## Basic Syntax
```bash
grep [options] pattern [file...]
```

- **pattern**: The string or regular expression you are searching for.
- **file**: The file(s) in which you want to search (optional). If no file is specified, `grep` searches through the input passed from other commands.

## Common Options

- **`-i`**: Ignore case (case-insensitive search).
- **`-r` or `-R`**: Search recursively through directories.
- **`-l`**: Show only the names of files containing the pattern.
- **`-n`**: Show the line numbers along with the matching lines.
- **`-v`**: Invert the match (show lines that do not match the pattern).
- **`-c`**: Show the count of matching lines.
- **`-H`**: Show the filenames along with matching lines.
- **`-w`**: Match the whole word (i.e., the pattern must appear as a complete word).
- **`-A NUM`**: Show NUM lines after the match.
- **`-B NUM`**: Show NUM lines before the match.
- **`-C NUM`**: Show NUM lines before and after the match.

## Basic Usage Examples

### 1. **Search for a String in a File**
To search for a specific string in a file:
```bash
grep "hello" myfile.txt
```
This will print all lines in `myfile.txt` containing the string `"hello"`.

### 2. **Case-Insensitive Search**
By default, `grep` is case-sensitive. To make it case-insensitive, use the `-i` option:
```bash
grep -i "hello" myfile.txt
```
This will match "hello", "HELLO", "HeLlO", etc.

### 3. **Search Recursively in a Directory**
To search for a pattern recursively through all files in a directory:
```bash
grep -r "pattern" /path/to/directory
```
This will search for the pattern in all files inside the specified directory and its subdirectories.

### 4. **Show Line Numbers with Matches**
If you want to see the line numbers where the pattern appears, use the `-n` option:
```bash
grep -n "hello" myfile.txt
```
This will show the line numbers alongside the matching lines.

### 5. **Invert the Match**
To show lines that do not match the pattern, use the `-v` option:
```bash
grep -v "hello" myfile.txt
```
This will print all lines that do not contain the string `"hello"`.

### 6. **Count the Number of Matches**
To count how many lines match the pattern, use the `-c` option:
```bash
grep -c "hello" myfile.txt
```
This will print the number of lines in `myfile.txt` containing the string `"hello"`.

### 7. **Search for Whole Words**
To search for an exact match of a whole word (not part of a word), use the `-w` option:
```bash
grep -w "hello" myfile.txt
```
This will match `"hello"` but not `"hellos"` or `"shello"`.

### 8. **Show Context Around Matches**
If you want to display lines around the match, use the `-A`, `-B`, or `-C` options. For example:
- Show 2 lines after the match (`-A`):
  ```bash
  grep -A 2 "hello" myfile.txt
  ```
- Show 2 lines before the match (`-B`):
  ```bash
  grep -B 2 "hello" myfile.txt
  ```
- Show 2 lines before and after the match (`-C`):
  ```bash
  grep -C 2 "hello" myfile.txt
  ```

### 9. **Search for a Pattern in Multiple Files**
You can search for a pattern in multiple files by specifying multiple filenames:
```bash
grep "pattern" file1.txt file2.txt file3.txt
```
This will search for the pattern in `file1.txt`, `file2.txt`, and `file3.txt`.

### 10. **Search for Patterns Using Regular Expressions**
`grep` supports regular expressions, which allow for more advanced pattern matching.

Example with a regular expression:
```bash
grep "h.llo" myfile.txt
```
This will match `"hello"`, `"hallo"`, `"hxllo"`, etc. (any character in place of `.`).

## Practical Examples

### Example 1: Search for a Pattern in a Log File
If you have a log file and you want to find all occurrences of "error":
```bash
grep "error" logfile.txt
```

### Example 2: Find All Files Containing a Specific Pattern
To find all files in a directory that contain the pattern "TODO":
```bash
grep -r "TODO" /path/to/directory
```

### Example 3: Count the Number of Errors in a Log File
To count how many times the word "error" appears in a log file:
```bash
grep -c "error" logfile.txt
```

### Example 4: List Files Containing a Pattern
To list only the names of files that contain the word "database":
```bash
grep -l "database" *.txt
```

## Regular Expressions with `grep`
`grep` allows the use of **regular expressions (regex)** to perform complex searches. Here are a few examples:

### Example 1: Match Any Character
```bash
grep "a.b" file.txt
```
Matches any string where `a` is followed by any character and then `b` (e.g., `"aab"`, `"acb"`).

### Example 2: Match Start of Line
```bash
grep "^hello" file.txt
```
Matches lines that start with `"hello"`.

### Example 3: Match End of Line
```bash
grep "hello$" file.txt
```
Matches lines that end with `"hello"`.

### Example 4: Match a Range of Characters
```bash
grep "[a-z]" file.txt
```
Matches lines containing any lowercase letter from `a` to `z`.

### Example 5: Match One of Several Patterns
```bash
grep "apple\|banana" file.txt
```
Matches lines containing either "apple" or "banana".

## Conclusion
`grep` is an essential tool in bash for searching through files and streams of text. By mastering its various options and regular expressions, you can quickly search and manipulate large amounts of data in your files or terminal output. With the practical examples and exercises in this tutorial, you should now be able to use `grep` effectively in your own bash scripts and command-line tasks.

## Practice Exercises

1. Search for all occurrences of the word "error" in a log file.
2. Count how many times the word "hello" appears in a file.
3. Find all files in a directory containing the word "TODO".
4. Display lines from a file that do not contain the word "example".
5. Use regular expressions to search for lines starting with "test" and ending with "done".
6. Show 3 lines before and after the match when searching for "data" in a file.
