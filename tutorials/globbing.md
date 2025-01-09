# Beginner's Guide to Globbing in Bash

Globbing in Bash refers to the use of wildcard patterns to match file and directory names. It simplifies file manipulation tasks by enabling you to work with multiple files that follow specific patterns.

---

## Common Wildcards
- `*`: Matches zero or more characters.
- `?`: Matches exactly one character.
- `[...]`: Matches any one of the characters inside the brackets.
- `{...}`: Matches any of the comma-separated patterns inside the braces.

---

## Examples with Outputs

### Match All Files
```bash
ls *
# Output:
# file1.txt  file2.log  image.jpg  script.sh
```

### Match Files with a Specific Extension
```bash
ls *.txt
# Output:
# file1.txt
```

### Match Files with a Single Character Difference
```bash
ls file?.txt
# Output:
# file1.txt  file2.txt
```

### Match a Range of Characters
```bash
ls file[1-3].txt
# Output:
# file1.txt  file2.txt  file3.txt
```

### Match Multiple Patterns
```bash
ls *.{jpg,png}
# Output:
# image1.jpg  image2.png
```

### Exclude Certain Patterns (Using `!` with `shopt -s extglob`)
Enable extended globbing:
```bash
shopt -s extglob
ls !(*.txt)
# Output:
# file1.log  image.jpg  script.sh
```

---

## Advanced Examples

### Recursively Match Files
Use the `**` pattern to match files in all subdirectories (requires `shopt -s globstar`):
```bash
shopt -s globstar
ls **/*.txt
# Output:
# subdir1/file1.txt  subdir2/file2.txt
```

### Combine Wildcards
Match all `.log` files starting with "error":
```bash
ls error*.log
# Output:
# error1.log  error2.log
```

### Escape Wildcards
To treat wildcard characters literally, use a backslash (`\`):
```bash
echo \*
# Output:
# *
```

---

## Practice Exercises
1. List all `.log` files in the current directory.
2. Find all files with exactly four characters in their names, ending with `.sh`.
3. Match files with names starting with "data" and having numeric suffixes (e.g., `data1`, `data2`).
4. Use globbing to find files in subdirectories with the extension `.conf`.
5. Exclude `.tmp` files while listing all other files.

---

By mastering globbing patterns, you can efficiently handle complex file operations in Bash. Practice these examples to deepen your understanding!

