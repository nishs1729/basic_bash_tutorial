# Disk-Related Bash Commands

This tutorial provides an overview of common bash commands related to disk management. These commands are useful for checking disk space, managing partitions, and interacting with file systems. Understanding how to use these commands is important for system administration and general Linux usage.

---

## 1. `du` - Display Disk Usage of Files and Directories

The `du` command provides information about disk usage for files and directories. It's useful for monitoring storage consumption on your system.

### Example 1. **`-s`**: Human-readable format (e.g., KB, MB, GB)
```bash
du -h
```

**Output:**
```bash
4.0K    ./dir1
8.0K    ./dir2
12K     .
```

### Example 2. **`-s`**: Summarize (only show total usage)
Shows only the total disk usage for a directory, rather than listing the usage for each file and subdirectory.
```bash
du -sh /path/to/directory
```
**Output:**
```bash
500M    /path/to/directory
```

### Example 3. **`-a`**: Display disk usage for all files and directories
This option displays disk usage for each individual file and directory.
```bash
du -ah
```
**Output:**
```bash
4.0K    ./dir1/file1.txt
8.0K    ./dir2/file2.txt
12K     .
```

### Example 4. **`-c`**: Display a grand total at the end
This option adds a final line with the total disk usage for the directory.
```bash
du -ch /path/to/directory
```
**Output:**
```bash
4.0K    ./dir1
8.0K    ./dir2
12K     .
12K     total
```

### Example 5. **`-d <level>`**: Limit the depth of directory listing
Limits the depth of directory listing. For example, `-d 1` will only show the sizes of the immediate subdirectories and not their contents.
```bash
du -h -d 1
```
**Output:**
```bash
4.0K    ./dir1
8.0K    ./dir2
12K     .
```

### Example 6. **`--max-depth=<N>`**: Similar to `-d`, but allows specifying the depth more clearly.
```bash
du -h --max-depth=1
```

### Example 7. **`--exclude=<pattern>`**: Exclude files and directories matching a specific pattern
Excludes directories or files that match the given pattern.
```bash
du -h --exclude="*.log"
```
This will exclude all `.log` files from the output.

---

## `df` - Display Disk Space Usage

The `df` command reports the amount of disk space used and available on mounted file systems. It's an essential tool for checking disk space on your system.

### Common Options for `df`:

### Example 1. **`-h`**: Human-readable format
This option displays disk usage in a human-readable format (e.g., GB, MB).
```bash
df -h
```
**Output:**
```bash
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        50G   20G   30G  40% /
/dev/sdb1        100G  60G   40G  60% /mnt/data
```

### Example 2. **`-a`**: Include all file systems
This option shows information for all file systems, including those with zero space (e.g., pseudo filesystems like `proc` or `sysfs`).

```bash
df -a
```

### Example 3. **`-T`**: Display file system type
This option adds a column showing the file system type (e.g., ext4, xfs).

```bash
df -T
```
**Output:**
```bash
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sda1      ext4  50G   20G   30G  40% /
/dev/sdb1      xfs  100G  60G   40G  60% /mnt/data
```

### Example 4. **`-i`**: Show inode usage instead of block usage
Displays inode information (number of inodes used and available), which is useful for checking if your system is running out of inodes (used for tracking files).

```bash
df -i
```
**Output:**
```bash
Filesystem     Inodes  IUsed  IFree IUse% Mounted on
/dev/sda1       65536  15000  50536   23% /
/dev/sdb1      102400  20000  82400   20% /mnt/data
```

### Example 5. **`--total`**: Show total usage for all file systems
This option adds a summary row at the bottom of the output, showing the total disk space usage for all file systems.

```bash
df -h --total
```
**Output:**
```bash
Filesystem     Size  Used Avail Use% Mounted on
/dev/sda1       50G   20G   30G  40% /
/dev/sdb1       100G  60G   40G  60% /mnt/data
total           150G  80G   70G  53% -
```

### Example 6. **`-l`**: Limit to local file systems
This option shows information only for local file systems, excluding network file systems (e.g., NFS).

```bash
df -l
```

### Example 7. **`--exclude-type=<type>`**: Exclude file systems of a specific type
Excludes file systems of the specified type (e.g., NFS, tmpfs).

```bash
df --exclude-type=nfs
```

### Example 8. **`--block-size=<size>`**: Display sizes in a specified block size
Specifies the block size to use for displaying disk usage (e.g., 1K, 1M, 1G).

```bash
df --block-size=1M
```
**Output:**
```bash
Filesystem     1M-blocks  Used Avail Use% Mounted on
/dev/sda1         50000    20000  30000  40% /
/dev/sdb1        100000   60000  40000  60% /mnt/data
```

---

## 3. `fdisk` - Partition Table Manipulation

The `fdisk` command is used for manipulating disk partitions.

### Example 1: Display Partition Table
```bash
sudo fdisk -l
```
**Output:**
```bash
Disk /dev/sda: 500GB
...
Device     Boot  Start        End    Sectors   Size   Type
/dev/sda1  *     2048       1026047  1024000   500M   Linux
/dev/sda2       1026048   104857599  103831552  49.5G Linux
```
The `-l` option lists the partition tables of all the connected disks.

### Example 2: Start `fdisk` to Edit a Partition
```bash
sudo fdisk /dev/sda
```
This opens the `fdisk` utility for the `/dev/sda` disk, where you can create, delete, and modify partitions.

---

## 4. `lsblk` - List Information About Block Devices

The `lsblk` command lists information about all available block devices (disks, partitions, etc.).

### Example 1: List Block Devices
```bash
lsblk
```
**Output:**
```bash
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0  500G  0 disk 
├─sda1   8:1    0   500M  0 part /boot
└─sda2   8:2    0  499G  0 part /
```
This shows all block devices, their sizes, and their mount points.

---

## 8. `parted` - Partition Manipulation

The `parted` command is used to create, delete, and resize partitions on a disk.

### Example 1: Display the Partition Table
```bash
sudo parted /dev/sda print
```
**Output:**
```bash
Model: ATA VBOX HARDDISK (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
```

### Example 2: Create a New Partition
```bash
sudo parted /dev/sda mkpart primary ext4 1GB 5GB
```
This creates a new primary partition of type ext4 between 1GB and 5GB on the `/dev/sda` disk.

---

## 9. `fsck` - File System Check

The `fsck` command is used to check and repair a file system.

### Example 1: Check and Repair a File System
```bash
sudo fsck /dev/sda1
```
This checks the file system on `/dev/sda1` for errors and attempts to fix them.