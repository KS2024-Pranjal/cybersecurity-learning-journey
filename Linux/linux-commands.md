# Linux Commands — Learning Notes

This file contains Linux commands that I have learned and practiced during my cybersecurity learning journey. I am using these commands to build my Linux command-line and system administration skills.

---

## 1. `ls`

Lists files and directories in the current working directory.

```bash
ls
```

### Common options

```bash
ls -l
```

Displays files and directories in a detailed format.

```bash
ls -a
```

Displays all files, including hidden files.

```bash
ls -la
```

Displays all files, including hidden files, in detailed format.

---

## 2. `pwd`

Displays the absolute path of the current working directory.

```bash
pwd
```

Example output:

```text
/home/analyst
```

---

## 3. `cd`

Changes the current working directory.

```bash
cd /home/analyst
```

Example:

```bash
cd Documents
```

To go to the parent directory:

```bash
cd ..
```

---

## 4. `cat`

Displays the contents of a file in the terminal.

```bash
cat notes.txt
```

---

## 5. `head`

Displays the first lines of a file; by default, it displays the first 10 lines.

```bash
head notes.txt
```

Display the first 5 lines:

```bash
head -n 5 notes.txt
```

---

## 6. `whoami`

Displays the username of the currently logged-in user.

```bash
whoami
```

Example output:

```text
analyst
```

---

## 7. `tail`

Displays the last lines of a file; by default, it displays the last 10 lines.

```bash
tail notes.txt
```

Display the last 5 lines:

```bash
tail -n 5 notes.txt
```

---

## 8. `less`

Displays a file one screen at a time and allows you to scroll through large files.

```bash
less notes.txt
```

Useful keys:

* `Space` → Next page
* `b` → Previous page
* `/word` → Search for a word
* `q` → Quit

---

# 9. `grep`

Searches for specific text or patterns inside files or command output.

```bash
grep "error" logfile.txt
```

### `grep` with piping

The pipe `|` sends the output of one command as input to another command.

```bash
ls | grep ".txt"
```

This displays files from `ls` whose names contain `.txt`.

Another example:

```bash
cat logfile.txt | grep "failed"
```

This searches the contents of `logfile.txt` for the word `failed`.

### Common `grep` options

#### `grep -i`

Performs a case-insensitive search.

```bash
grep -i "error" logfile.txt
```

#### `grep -n`

Displays the line number of matching results.

```bash
grep -n "error" logfile.txt
```

#### `grep -v`

Displays lines that do not contain the specified text.

```bash
grep -v "error" logfile.txt
```

#### `grep -r`

Recursively searches files inside a directory and its subdirectories.

```bash
grep -r "password" /home/analyst/
```

#### `grep -c`

Counts the number of matching lines.

```bash
grep -c "failed" logfile.txt
```

#### `grep -w`

Searches for an exact word.

```bash
grep -w "user" file.txt
```

---

# 10. `find`

Searches for files and directories based on conditions such as name, type, and modification time.

```bash
find /home/analyst -type f
```

This searches for regular files inside `/home/analyst`.

---

## `find -name`

Searches for a file or directory by name using a case-sensitive pattern.

```bash
find /home/analyst -name "report.txt"
```

---

## `find -iname`

Searches for a file or directory by name without distinguishing between uppercase and lowercase letters.

```bash
find /home/analyst -iname "report.txt"
```

This can match:

```text
report.txt
Report.txt
REPORT.TXT
```

---

## `find -mtime`

Searches for files based on when they were last modified.

Find files modified within the last 7 days:

```bash
find /home/analyst -type f -mtime -7
```

Find files modified more than 7 days ago:

```bash
find /home/analyst -type f -mtime +7
```

Find files modified approximately 7 days ago:

```bash
find /home/analyst -type f -mtime 7
```

---

# 11. `mkdir`

Creates a new directory.

```bash
mkdir reports
```

Create nested directories:

```bash
mkdir -p projects/cybersecurity/linux
```

---

# 12. `rmdir`

Removes an empty directory.

```bash
rmdir reports
```

`rmdir` normally cannot remove a directory that contains files.

---

# 13. `rm`

Removes files or directories.

Remove a file:

```bash
rm notes.txt
```

Remove a directory and its contents:

```bash
rm -r old_project
```

> **Important:** Be careful when using `rm` because deleted files may not be recoverable through a normal recycle bin.

---

# 14. `touch`

Creates an empty file or updates the modification time of an existing file.

```bash
touch notes.txt
```

Example:

```bash
touch linux-commands.md
```

---

# 15. `cp`

Copies files or directories from one location to another.

Copy a file:

```bash
cp notes.txt backup.txt
```

Copy a directory:

```bash
cp -r project backup_project
```

The `-r` option copies a directory and its contents recursively.

---

# 16. `mv`

Moves a file or directory to another location and can also be used to rename files.

Move a file:

```bash
mv notes.txt Documents/
```

Rename a file:

```bash
mv oldname.txt newname.txt
```

---

# 17. `nano`

Opens the Nano text editor in the terminal so you can create or edit text files.

```bash
nano notes.txt
```

### Common Nano shortcuts

```text
Ctrl + O  → Save
Ctrl + X  → Exit
Ctrl + W  → Search
Ctrl + K  → Cut a line
Ctrl + U  → Paste
```

---

# My Practice

I have practiced these commands through hands-on Linux exercises as part of my cybersecurity learning journey.

Through this practice, I have developed familiarity with:

* Navigating the Linux filesystem
* Creating, copying, moving, and deleting files
* Creating and removing directories
* Viewing and searching file contents
* Using pipes with commands
* Searching files using `find`
* Working with file modification times
* Editing files using Nano
* Understanding basic Linux command-line operations

---

# Key Takeaway

Linux command-line skills are an important foundation for cybersecurity. Practicing these commands has helped me become more comfortable working with files, directories, users, system information, and data from the Linux terminal.
