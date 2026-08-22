# Linux File Permissions

Linux uses file permissions to control who can access, modify, or execute files and directories.

Understanding permissions is important in cybersecurity because incorrect permissions can allow unauthorized users to access or modify sensitive information.

---

## 1. Types of Owners

Linux permissions are divided into three categories of users:

### User / Owner (`u`)

The **user** is the person who owns the file or directory.

### Group (`g`)

The **group** represents a collection of users who share permissions for the file or directory.

### Others (`o`)

**Others** means all users who are not the file owner and are not members of the assigned group.

---

## 2. Permission Types

Linux has three basic permissions:

| Permission | Symbol | Meaning                                          |
| ---------- | ------ | ------------------------------------------------ |
| Read       | `r`    | Allows viewing the contents of a file            |
| Write      | `w`    | Allows modifying a file                          |
| Execute    | `x`    | Allows executing a file or accessing a directory |

### Read (`r`)

For a file, read permission allows a user to view its contents.

```bash
cat file.txt
```

### Write (`w`)

Write permission allows a user to modify the contents of a file.

### Execute (`x`)

Execute permission allows a user to run an executable file.

For a directory:

* `r` → allows listing directory contents
* `w` → allows creating, deleting, or renaming entries
* `x` → allows accessing/traversing the directory

---

# 3. Understanding `-rwxrwxrwx`

When you run:

```bash
ls -l
```

you may see:

```text
-rwxrwxrwx 1 analyst security 1234 Aug 22 10:30 script.sh
```

The first part:

```text
-rwxrwxrwx
```

can be divided into:

```text
- rwx rwx rwx
  │   │   │
  │   │   └── Others
  │   └────── Group
  └────────── Owner/User
```

---

# 4. First Character — File Type

The first character indicates the type of filesystem object.

### `-` — Regular File

```text
-rwxrwxrwx
^
```

`-` means it is a regular file.

### `d` — Directory

```text
drwxrwxrwx
^
```

`d` means it is a directory.

Other possible indicators include:

* `l` → symbolic link
* `c` → character device
* `b` → block device

---

# 5. Permission Groups

After the first character, the remaining nine characters are divided into three groups:

```text
-rwx rwx rwx
    │   │   │
    │   │   └── Others
    │   └────── Group
    └────────── Owner
```

Each group contains:

```text
rwx
```

The three positions represent:

```text
r = Read
w = Write
x = Execute
```

A `-` in a permission position means that permission is not granted.

For example:

```text
rw-
```

means:

* `r` → Read allowed
* `w` → Write allowed
* `-` → Execute not allowed

---

# 6. Example: `-rwxrwxrwx`

```text
-rwxrwxrwx
```

This means:

* Owner → read, write, execute
* Group → read, write, execute
* Others → read, write, execute

Therefore, everyone has full permissions on the file.

---

# 7. Example: `-rw-r--r--`

```text
-rw-r--r--
```

This means:

* Owner → read + write
* Group → read
* Others → read

The owner can modify the file, while the group and others can only read it.

---

# 8. Example: `drwxr-xr-x`

```text
drwxr-xr-x
```

This means:

* Owner → read, write, execute
* Group → read, execute
* Others → read, execute

This is a common permission configuration for directories.

---

# 9. `ls -l`

The `ls -l` command displays files and directories in **long listing format**.

```bash
ls -l
```

Example:

```text
-rw-r--r-- 1 analyst security 125 Aug 22 10:30 notes.txt
```

The output provides information such as:

```text
Permissions
     ↓
-rw-r--r--

Number of hard links
     ↓
1

Owner
     ↓
analyst

Group
     ↓
security

File size
     ↓
125

Modification date/time
     ↓
Aug 22 10:30

Filename
     ↓
notes.txt
```

`ls -l` is useful when inspecting **ownership and permissions**.

---

# 10. `ls -a`

The `ls -a` command displays **all files and directories**, including hidden files.

```bash
ls -a
```

Example:

```text
.
..
.bashrc
.profile
Documents
notes.txt
```

Linux hidden files normally begin with a dot (`.`).

Examples:

```text
.bashrc
.profile
```

---

# 11. `ls -la`

You can combine the two options:

```bash
ls -la
```

This displays:

* Hidden files
* File permissions
* Ownership
* Group
* File size
* Modification time

Example:

```text
drwxr-xr-x 2 analyst security 4096 Aug 22 10:30 .
-rw-r--r-- 1 analyst security  125 Aug 22 10:30 notes.txt
-rwxr-xr-x 1 analyst security  250 Aug 22 10:30 script.sh
```

---

# 12. `chmod`

The `chmod` command is used to **change the permissions of a file or directory**.

`chmod` stands for **change mode**.

Basic syntax:

```bash
chmod [permissions] [file]
```

Example:

```bash
chmod u+x script.sh
```

This adds execute permission for the owner of `script.sh`.

---

# 13. Using `+` with `chmod`

The `+` operator **adds** a permission.

### Add execute permission to the owner

```bash
chmod u+x script.sh
```

* `u` → user/owner
* `+` → add
* `x` → execute

### Add write permission to the group

```bash
chmod g+w file.txt
```

### Add read permission to others

```bash
chmod o+r file.txt
```

### Add read, write, and execute permissions to the owner

```bash
chmod u+rwx file.txt
```

### Add execute permission to everyone

```bash
chmod a+x script.sh
```

Here, `a` means **all users**: owner, group, and others.

---

# 14. Using `-` with `chmod`

The `-` operator **removes** a permission.

### Remove execute permission from the owner

```bash
chmod u-x script.sh
```

### Remove write permission from the group

```bash
chmod g-w file.txt
```

### Remove read permission from others

```bash
chmod o-r file.txt
```

### Remove execute permission from everyone

```bash
chmod a-x script.sh
```

---

# 15. Using `=` with `chmod`

The `=` operator **sets the permissions exactly as specified**.

For example:

```bash
chmod u=rwx file.txt
```

This sets the owner's permissions to read, write, and execute.

Another example:

```bash
chmod g=r file.txt
```

This sets the group's permission to read only.

You can set permissions for multiple categories:

```bash
chmod u=rwx,g=rx,o=r file.txt
```

This gives:

* Owner → `rwx`
* Group → `r-x`
* Others → `r--`

---

# 16. Symbolic `chmod` Permission Format

The basic symbolic format is:

```text
[who][operator][permission]
```

### Who

```text
u = User/Owner
g = Group
o = Others
a = All
```

### Operators

```text
+ = Add permission
- = Remove permission
= = Set exact permission
```

### Permissions

```text
r = Read
w = Write
x = Execute
```

Example:

```bash
chmod g+w file.txt
```

Meaning:

```text
g → Group
+ → Add
w → Write
```

Therefore, it adds **write permission for the group**.

---

# 17. Multiple `chmod` Permissions

You can change multiple permissions in one command.

Example:

```bash
chmod u+rwx,g+rx,o+r file.txt
```

This adds:

* Owner → read, write, execute
* Group → read, execute
* Others → read

Another example:

```bash
chmod u-x,g-w,o-r file.txt
```

This removes:

* Execute from owner
* Write from group
* Read from others

---

# 18. Numeric `chmod` Permissions

Permissions can also be represented using numbers.

```text
r = 4
w = 2
x = 1
```

The values are added together.

### Examples

```text
r-- = 4
-w- = 2
--x = 1
rw- = 6
r-x = 5
-wx = 3
rwx = 7
--- = 0
```

For example:

```bash
chmod 755 script.sh
```

means:

```text
Owner  → 7 = rwx
Group  → 5 = r-x
Others → 5 = r-x
```

So:

```text
755 = rwxr-xr-x
```

Another common example:

```bash
chmod 644 file.txt
```

means:

```text
Owner  → 6 = rw-
Group  → 4 = r--
Others → 4 = r--
```

So:

```text
644 = rw-r--r--
```

---

# 19. Why `chmod` Matters in Cybersecurity

File permissions are important because they control who can access or modify files.

For example, giving write permission to everyone can create a security risk:

```bash
chmod a+w important.txt
```

This allows the owner, group, and others to write to the file.

A cybersecurity professional should follow the **principle of least privilege**, which means users should receive only the permissions they need.

---

# 20. My Practice

I have practiced Linux file permissions and the `chmod` command as part of my cybersecurity learning journey.

I practiced:

* Understanding users, groups, and others
* Reading permission strings
* Using `ls -l`
* Using `ls -a`
* Using `ls -la`
* Understanding `r`, `w`, and `x`
* Adding permissions with `+`
* Removing permissions with `-`
* Setting permissions with `=`
* Using symbolic permissions with `chmod`
* Understanding numeric permissions such as `644` and `755`

---

# Key Takeaway

Linux permissions use three categories:

```text
Owner (u)
Group (g)
Others (o)
```

and three basic permissions:

```text
Read    (r)
Write   (w)
Execute (x)
```

The `chmod` command changes permissions.

```text
+ :- Add
- :- Remove
= :- Set
```

For example:

```bash
chmod u+x script.sh
```

adds execute permission to the owner.

```bash
chmod g-w file.txt
```

removes write permission from the group.

```bash
chmod 755 script.sh
```

sets the permissions to:

```text
rwxr-xr-x
```

Understanding Linux permissions and `chmod` is an important foundation for cybersecurity and system administration.
