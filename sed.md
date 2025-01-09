# Beginner's Guide to the `sed` Command in Bash

The `sed` command in Bash is a stream editor used for text manipulation. It can perform basic text transformations on an input stream (a file or input from a pipeline). With `sed`, you can easily replace, delete, insert, or modify lines in a file or text input.

---

## What is the `sed` Command?
The `sed` command:
- Processes text line by line.
- Allows for pattern-based text manipulation.
- Can be used for automated editing of configuration files or scripts.

---

## Syntax
```bash
sed [OPTIONS] 'script' [file]
```
- **script**: The set of commands or patterns to be applied.
- **file**: The file to process (optional; if omitted, `sed` reads from standard input).

---

## Common Options
- `-e`: Allows adding multiple scripts.
- `-i`: Edits files in place (modifies the file directly).
- `-n`: Suppresses automatic printing of pattern space.
- `-f`: Reads commands from a file.

---

## Examples

### 1. Replacing Text
Replace the first occurrence of "hello" with "world" in each line:
```bash
sed 's/hello/world/' file.txt
```
**Sample Input:**
```
hello everyone
hello world
```
**Sample Output:**
```
world everyone
world world
```

Replace all occurrences of "hello" with "world":
```bash
sed 's/hello/world/g' file.txt
```
**Sample Input:**
```
hello hello hello
hello world
```
**Sample Output:**
```
world world world
world world
```

Make the replacement case-insensitive:
```bash
sed 's/hello/world/gi' file.txt
```
**Sample Input:**
```
Hello HELLO hello
```
**Sample Output:**
```
world world world
```

### 2. Deleting Lines
Delete lines containing the word "error":
```bash
sed '/error/d' file.txt
```
**Sample Input:**
```
This is fine
An error occurred
All good here
```
**Sample Output:**
```
This is fine
All good here
```

Delete the 3rd line in a file:
```bash
sed '3d' file.txt
```
**Sample Input:**
```
Line 1
Line 2
Line 3
Line 4
```
**Sample Output:**
```
Line 1
Line 2
Line 4
```

Delete lines from 2 to 5:
```bash
sed '2,5d' file.txt
```
**Sample Input:**
```
Line 1
Line 2
Line 3
Line 4
Line 5
Line 6
```
**Sample Output:**
```
Line 1
Line 6
```

### 3. Inserting and Appending Text
Insert a line before the 2nd line:
```bash
sed '2i\
This is a new line' file.txt
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
This is a new line
Line 2
Line 3
```

Append a line after the 3rd line:
```bash
sed '3a\
This is an appended line' file.txt
```
**Sample Input:**
```
Line 1
Line 2
Line 3
Line 4
```
**Sample Output:**
```
Line 1
Line 2
Line 3
This is an appended line
Line 4
```

### 4. Printing Specific Lines
Print only the 1st line:
```bash
sed -n '1p' file.txt
```
**Sample Input:**
```
First line
Second line
Third line
```
**Sample Output:**
```
First line
```

Print lines containing "info":
```bash
sed -n '/info/p' file.txt
```
**Sample Input:**
```
No information here
Some info is present
Nothing else matters
```
**Sample Output:**
```
Some info is present
```

Print lines 5 to 10:
```bash
sed -n '5,10p' file.txt
```
**Sample Input:**
```
Line 1
Line 2
Line 3
Line 4
Line 5
Line 6
Line 7
Line 8
Line 9
Line 10
Line 11
```
**Sample Output:**
```
Line 5
Line 6
Line 7
Line 8
Line 9
Line 10
```

### 5. Using `-i` for In-Place Editing
Replace all occurrences of "foo" with "bar" directly in the file:
```bash
sed -i 's/foo/bar/g' file.txt
```
**Sample Input:**
```
foo bar foo
bar foo bar
```
**Sample Output (file.txt):**
```
bar bar bar
bar bar bar
```

Delete all empty lines in a file:
```bash
sed -i '/^$/d' file.txt
```
**Sample Input:**
```
Line 1

Line 2

Line 3
```
**Sample Output (file.txt):**
```
Line 1
Line 2
Line 3
```

---

## Advanced Examples

### 1. Multiple Commands
Replace "cat" with "dog" and "fish" with "bird" in one command:
```bash
sed -e 's/cat/dog/g' -e 's/fish/bird/g' file.txt
```
**Sample Input:**
```
cat fish cat
fish cat fish
```
**Sample Output:**
```
dog bird dog
bird dog bird
```

### 2. Modify Only Specific Lines
Replace "error" with "warning" only on the 2nd line:
```bash
sed '2s/error/warning/' file.txt
```
**Sample Input:**
```
Line 1: error
Line 2: error
Line 3: error
```
**Sample Output:**
```
Line 1: error
Line 2: warning
Line 3: error
```

### 3. Backing Up Files
Create a backup before making in-place changes:
```bash
sed -i.bak 's/foo/bar/g' file.txt
```
**Sample Input:**
```
foo bar foo
```
**Sample Output (file.txt):**
```
bar bar bar
```
**Backup File (file.txt.bak):**
```
foo bar foo
```

### 4. Working with Pipelines
Replace "yes" with "no" in the output of a command:
```bash
echo "yes yes yes" | sed 's/yes/no/g'
```
**Sample Output:**
```
no no no
```

---

## Practice Exercises
1. Replace all instances of "http" with "https" in a file named `urls.txt`.
2. Delete all lines that start with a `#` (comments) in a configuration file.
3. Append "End of line" to every line in `logfile.txt`.
4. Extract lines 10 to 20 from a file named `data.csv`.
5. Replace multiple spaces with a single space in `textfile.txt`.

---

By practicing these examples and exercises, you'll quickly become proficient in using the `sed` command. It is a vital tool for text processing in Linux systems!

