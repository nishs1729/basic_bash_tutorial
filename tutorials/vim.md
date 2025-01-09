# Basic Vim Tutorial

Vim is a highly configurable text editor for efficiently creating and editing any kind of text, especially code. It is widely used by programmers and system administrators.

This tutorial will cover the basics of navigating and editing text in Vim.

## 1. Opening Vim

To open Vim, simply type `vim` in your terminal, followed by the file name (if any). If the file doesn't exist, Vim will create a new file.

### Syntax:
```bash
vim filename.txt
```

- If the file `filename.txt` already exists, it will open that file.
- If the file doesn't exist, a new empty file will be created.

---

## 2. Vim Modes

Vim has multiple modes, but the two most important modes for basic use are:

- **Normal Mode** (default mode when you open Vim)
- **Insert Mode**

### Normal Mode (Navigation Mode)
- In **Normal Mode**, you can navigate the document, delete text, copy and paste, and perform other editing actions.
- Press `Esc` to ensure you are in **Normal Mode**.

### Insert Mode (Editing Mode)
- In **Insert Mode**, you can type and edit the content.
- To enter **Insert Mode**, press `i` (for insert before the cursor), `I` (for insert at the beginning of the line), `a` (to append after the cursor), or `A` (to append at the end of the line).

To return to **Normal Mode** from **Insert Mode**, press `Esc`.

---

## 3. Moving the Cursor

In **Normal Mode**, you can move the cursor around using the following commands:

- **Arrow keys**: Move up, down, left, right.
- **h**: Move left (one character).
- **j**: Move down (one line).
- **k**: Move up (one line).
- **l**: Move right (one character).

Additionally, you can move the cursor word-by-word:
- **w**: Move the cursor forward to the beginning of the next word.
- **b**: Move the cursor backward to the beginning of the previous word.

---

## 4. Editing Text

### Insert Mode

To start typing, press `i` to enter **Insert Mode**.

- After entering **Insert Mode**, type your text as usual.
- Press `Esc` to return to **Normal Mode**.

### Deleting Text

- **x**: Delete the character under the cursor.
- **dd**: Delete the entire line.
- **dw**: Delete from the cursor to the beginning of the next word.
- **d$**: Delete from the cursor to the end of the line.

### Copying and Pasting Text

- **yy**: Copy (yank) the entire current line.
- **p**: Paste the copied text after the cursor.
- **P**: Paste the copied text before the cursor.

### Undo and Redo

- **u**: Undo the last action.
- **Ctrl + r**: Redo the last undone action.

---

## 5. Saving and Exiting

Once you’ve made changes, you’ll want to save your work or exit Vim.

### Save and Exit
- **:wq**: Save and exit.
- **:x**: Save and exit (same as `:wq`).

### Save Without Exiting
- **:w**: Save the file but remain in Vim.

### Exit Without Saving
- **:q!**: Exit Vim without saving changes.

### Exit if No Changes
- **:q**: Exit if no changes have been made.

---

## 6. Searching Text

To search for a word or phrase in Vim:

- **/search_term**: Search forward for `search_term`.
- **?search_term**: Search backward for `search_term`.
- **n**: Move to the next occurrence of the search term.
- **N**: Move to the previous occurrence of the search term.

---

## 7. Basic Commands Summary

| Command | Action                                  |
|---------|-----------------------------------------|
| `i`     | Enter **Insert Mode**                   |
| `Esc`   | Exit **Insert Mode** and return to Normal Mode |
| `h`, `j`, `k`, `l` | Move cursor left, down, up, and right |
| `w`     | Move forward to the next word          |
| `b`     | Move backward to the previous word     |
| `dd`    | Delete the current line                 |
| `x`     | Delete character under the cursor      |
| `yy`    | Copy (yank) the current line           |
| `p`     | Paste text after the cursor            |
| `u`     | Undo the last change                   |
| `Ctrl + r` | Redo the last undone change          |
| `:w`    | Save the file                          |
| `:q`    | Exit Vim                               |
| `:wq`   | Save and exit                          |
| `:q!`   | Exit without saving                    |

---

## 8. Practice Exercises

1. Open a file using `vim` and start typing some text.
2. Move the cursor around using the `h`, `j`, `k`, and `l` keys.
3. Try deleting a word with `dw` and deleting an entire line with `dd`.
4. Save your changes with `:w`, and then exit with `:q`.
5. Use the search feature (`/search_term`) to find specific text in the file.
6. Try copying (`yy`) and pasting (`p`) text.
