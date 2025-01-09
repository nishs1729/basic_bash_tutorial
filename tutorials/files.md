# Bash Command Tutorial: File Permissions and Ownership

## Introduction
In Linux and other Unix-like operating systems, file permissions and ownership are essential concepts for managing access control to files and directories. Bash provides commands that allow you to view, modify, and manage file permissions and ownership. This tutorial covers the basics of file permissions, ownership, and how to use commands like `chmod`, `chown`, and `chgrp` to manage these settings.

## Understanding File Permissions
Every file and directory in Linux has three types of permissions that apply to three categories of users:

- **Permissions:**
  - **Read (`r`)**: Allows a user to view the contents of a file or list the contents of a directory.
  - **Write (`w`)**: Allows a user to modify the contents of a file or add/remove files in a directory.
  - **Execute (`x`)**: Allows a user to execute a file (if it's a program or script) or enter a directory.

- **User Categories:**
  - **Owner (user)**: The user who owns the file.
  - **Group**: A group of users that share the same permissions for the file.
  - **Others**: All users who are neither the owner nor part of the group.

Each of these categories (Owner, Group, Others) can have different levels of access (read, write, execute).

### Viewing File Permissions
To view the permissions of a file, use the `ls -l` command:

```bash
ls -l filename
```

Example output:
```bash
-rwxr-xr-- 1 user group 12345 Jan 1 12:00 filename
```

- The first column shows the file's permissions:
  - `-rwxr-xr--`
    - The first character (`-`) indicates it's a regular file (it would be `d` for a directory).
    - The next three characters (`rwx`) are the owner's permissions (read, write, execute).
    - The next three (`r-x`) are the group's permissions (read, execute).
    - The last three (`r--`) are others' permissions (read only).
  
- The second column (`1`) shows the number of hard links to the file.
- The third and fourth columns (`user` and `group`) show the owner and group of the file.
- The last column (`filename`) is the file name.

## Modifying File Permissions

### Using `chmod` (Change Mode)
The `chmod` command is used to change the permissions of a file or directory.

#### Symbolic Mode:
In symbolic mode, you use letters to specify the user category and permission to add or remove. The syntax is:

```bash
chmod [user][operator][permission] file
```

- **User**: `u` for owner (user), `g` for group, `o` for others, or `a` for all.
- **Operator**: `+` to add a permission, `-` to remove a permission, or `=` to set the exact permission.
- **Permission**: `r` for read, `w` for write, and `x` for execute.

#### Examples:
1. **Grant execute permission to the owner**:
   ```bash
   chmod u+x filename
   ```

2. **Remove write permission for the group**:
   ```bash
   chmod g-w filename
   ```

3. **Give read and write permissions to everyone**:
   ```bash
   chmod a+rw filename
   ```

4. **Set permissions to read-only for others**:
   ```bash
   chmod o=r filename
   ```

#### Numeric Mode:
In numeric mode, you represent permissions with numbers. Each permission has a corresponding value:
- **Read (`r`) = 4**
- **Write (`w`) = 2**
- **Execute (`x`) = 1**

These values are added together for each user category. For example:
- `7` (4+2+1) means read, write, and execute.
- `6` (4+2) means read and write.
- `5` (4+1) means read and execute.

The syntax for numeric mode is:

```bash
chmod [permissions] file
```

#### Example:
To set read, write, and execute permissions for the owner, and read and execute for the group and others:
```bash
chmod 755 filename
```
This results in:
- Owner: read, write, execute (7)
- Group: read, execute (5)
- Others: read, execute (5)

### Changing Ownership with `chown` (Change Owner)
The `chown` command is used to change the owner and/or group of a file or directory.

The syntax is:

```bash
chown [owner][:[group]] file
```

- **Owner**: The username or user ID to set as the owner.
- **Group**: The group name or group ID to set as the file’s group (optional).

#### Examples:
1. **Change the owner of a file**:
   ```bash
   chown user filename
   ```

2. **Change the owner and the group of a file**:
   ```bash
   chown user:group filename
   ```

3. **Change only the group of a file**:
   ```bash
   chown :group filename
   ```

### Changing Group Ownership with `chgrp` (Change Group)
The `chgrp` command is used to change the group of a file or directory.

The syntax is:

```bash
chgrp [group] file
```

#### Example:
To change the group of a file:
```bash
chgrp admin filename
```

## Special Permissions

### Setuid (Set User ID)
The **setuid** permission allows a user to run an executable with the permissions of the file’s owner, typically used for programs that need elevated privileges.

To set the setuid permission, use:
```bash
chmod u+s filename
```

### Setgid (Set Group ID)
The **setgid** permission allows a file to be executed with the permissions of the group. For directories, it ensures that new files created within the directory inherit the directory's group.

To set the setgid permission, use:
```bash
chmod g+s directoryname
```

### Sticky Bit
The **sticky bit** is typically used on directories to prevent users from deleting files they do not own, even if they have write access to the directory.

To set the sticky bit on a directory, use:
```bash
chmod +t directoryname
```

## Viewing and Modifying Permissions Recursively
To change the permissions or ownership of files and directories recursively, use the `-R` option with `chmod`, `chown`, or `chgrp`.

#### Example:
Recursively change the permissions of all files in a directory to `755`:
```bash
chmod -R 755 directoryname
```

Recursively change the owner of all files in a directory to `user`:
```bash
chown -R user directoryname
```

## Conclusion
Understanding file permissions and ownership is crucial for managing access control in Linux. By using the `chmod`, `chown`, and `chgrp` commands, you can effectively manage who has access to your files and what actions they can perform. 

With this tutorial, you should now be able to work with file permissions, ownership, and special permissions, allowing you to control file access securely in your system.

## Practice Exercises

1. Change the permissions of a file so that only the owner can read and write, but no one else can access it.
2. Recursively change the group of all files in a directory to `developers`.
3. Set the setuid permission on an executable file.
4. Change the owner and group of a file to `john:admin`.
5. Make a directory where only the owner can delete files, but others can add files.