# Linux Users, Root, sudo, and User Management

Linux provides different levels of access for users. Understanding users, groups, privileges, and account management is important for system administration and cybersecurity.

---

# 1. Root User

The **root user** is the Linux superuser and has very high privileges over the system.

The root user can:

* Create and delete user accounts
* Modify system files
* Change file ownership and permissions
* Install and remove software
* Start and stop system services
* Access files that regular users normally cannot
* Change system configurations

The root user is identified by the user ID (`UID`) **0**.

You can check the current user with:

```bash
whoami
```

You can check user and group IDs with:

```bash
id
```

Example:

```text
uid=1000(analyst) gid=1000(analyst) groups=1000(analyst)
```

---

# 2. Problems With Logging in as Root

Although root has powerful privileges, logging in directly as root can create security risks.

### Risk 1 — Accidental system changes

A command executed as root can modify or delete important system files.

For example:

```bash
rm important-file
```

A mistake made with root privileges can have serious consequences.

### Risk 2 — Malware impact

If malicious software runs with root privileges, it may gain extensive control over the system.

### Risk 3 — Least privilege violation

Users should normally have only the permissions they need to perform their tasks.

Using root for everyday activities gives a user more privileges than necessary.

### Risk 4 — Accountability

When multiple people use the root account, it can become difficult to determine which person performed a particular administrative action.

For these reasons, Linux systems commonly use regular accounts together with `sudo` for administrative tasks.

---

# 3. `sudo`

The `sudo` command allows an authorized user to execute a command with elevated privileges.

`sudo` means **superuser do**.

Example:

```bash
sudo apt update
```

The user may be asked to enter their own password.

Another example:

```bash
sudo useradd researcher9
```

This allows an authorized user to create a new user account.

You can check whether you have sudo access with:

```bash
sudo -l
```

`sudo` supports the principle of **least privilege** because a user can receive administrative privileges when needed instead of logging in as root for normal activities.

---

# 4. `useradd`

The `useradd` command creates a new user account.

Basic example:

```bash
sudo useradd researcher9
```

This creates a user named `researcher9`.

You can check whether the user exists with:

```bash
id researcher9
```

or:

```bash
getent passwd researcher9
```

---

# 5. `useradd -g`

The `-g` option specifies the user's **primary group**.

Example:

```bash
sudo useradd -g sales_team researcher9
```

This creates `researcher9` and assigns `sales_team` as the user's primary group.

The group normally needs to exist before using it as the primary group.

You can check the group with:

```bash
getent group sales_team
```

---

# 6. `useradd -G`

The `-G` option specifies one or more **secondary groups** for the new user.

Example:

```bash
sudo useradd -G sales_team researcher9
```

This creates `researcher9` and adds the user to `sales_team` as a supplementary/secondary group.

Multiple groups can be specified using commas:

```bash
sudo useradd -G sales_team,developers researcher9
```

---

# 7. Difference Between `-g` and `-G`

| Option | Purpose                             |
| ------ | ----------------------------------- |
| `-g`   | Sets the primary group              |
| `-G`   | Sets supplementary/secondary groups |

Example:

```bash
sudo useradd -g employees -G sales_team researcher9
```

Here:

* `employees` → primary group
* `sales_team` → secondary group

---

# 8. `userdel`

The `userdel` command deletes a user account.

Example:

```bash
sudo userdel researcher9
```

This removes the user account but may leave the user's home directory and files behind.

---

# 9. `userdel -r`

The `-r` option removes the user's account **and their home directory and mail spool** where applicable.

Example:

```bash
sudo userdel -r researcher9
```

This is more destructive than:

```bash
sudo userdel researcher9
```

Therefore, you should verify the account and its files before using `-r`.

---

# 10. `usermod`

The `usermod` command modifies an existing user account.

Basic example:

```bash
sudo usermod [options] username
```

For example:

```bash
sudo usermod -aG sales_team researcher9
```

This adds `researcher9` to the `sales_team` secondary group.

---

# 11. `usermod -d`

The `-d` option changes the user's **home directory**.

Example:

```bash
sudo usermod -d /home/researcher researcher9
```

This changes the configured home directory for `researcher9`.

If you also want to move the existing contents to the new home directory, `-m` can be used:

```bash
sudo usermod -d /home/researcher -m researcher9
```

---

# 12. `usermod -l`

The `-l` option changes the user's **login name**.

Example:

```bash
sudo usermod -l researcher10 researcher9
```

This changes the login name from `researcher9` to `researcher10`.

Changing the login name does not automatically rename or move the user's home directory.

---

# 13. `usermod -L`

The `-L` option **locks the user's password**, preventing password-based login.

Example:

```bash
sudo usermod -L researcher9
```

This can be useful when an account needs to be temporarily disabled without deleting it.

To unlock the account:

```bash
sudo usermod -U researcher9
```

`-U` unlocks the user's password.

---

# 14. `usermod -aG`

The `-aG` options are commonly used together to add a user to a secondary group without removing their existing supplementary group memberships.

Example:

```bash
sudo usermod -aG sales_team researcher9
```

Meaning:

```text
-a → append
-G → supplementary groups
```

After adding the user, you can check their groups with:

```bash
groups researcher9
```

or:

```bash
id researcher9
```

---

# 15. `chown`

The `chown` command changes the **owner and/or group** of a file or directory.

`chown` means **change owner**.

Basic syntax:

```bash
sudo chown [owner]:[group] file
```

---

# 16. Change the User/Owner With `chown`

Example:

```bash
sudo chown researcher9 notes.txt
```

This changes the owner of `notes.txt` to `researcher9`.

You can verify the ownership with:

```bash
ls -l notes.txt
```

---

# 17. Change the Group With `chown`

Example:

```bash
sudo chown :sales_team notes.txt
```

This changes the group ownership of `notes.txt` to `sales_team`.

The colon (`:`) separates the user and group.

---

# 18. Change Both User and Group

Example:

```bash
sudo chown researcher9:sales_team notes.txt
```

This changes:

```text
Owner → researcher9
Group → sales_team
```

You can verify it with:

```bash
ls -l notes.txt
```

---

# 19. `chown -R`

The `-R` option changes ownership **recursively** for a directory and its contents.

Example:

```bash
sudo chown -R researcher9:sales_team /home/researcher9/project
```

This changes the owner and group for the directory and the files/directories inside it.

Be careful when using `-R`, especially on system directories.

---

# 20. Checking User Information

### Check current username

```bash
whoami
```

### Display user ID and group information

```bash
id
```

### Check a specific user

```bash
id researcher9
```

### Display the groups of a user

```bash
groups researcher9
```

### Check user account information

```bash
getent passwd researcher9
```

### Check group information

```bash
getent group sales_team
```

---

# 21. Useful Command Summary

| Command       | Purpose                                             |
| ------------- | --------------------------------------------------- |
| `whoami`      | Shows the current username                          |
| `id`          | Shows user ID and group information                 |
| `sudo`        | Runs an authorized command with elevated privileges |
| `useradd`     | Creates a user                                      |
| `useradd -g`  | Sets the primary group                              |
| `useradd -G`  | Sets supplementary groups                           |
| `userdel`     | Deletes a user                                      |
| `userdel -r`  | Deletes a user and their home directory             |
| `usermod`     | Modifies an existing user                           |
| `usermod -d`  | Changes the home directory                          |
| `usermod -l`  | Changes the login name                              |
| `usermod -L`  | Locks the user's password                           |
| `usermod -U`  | Unlocks the user's password                         |
| `usermod -aG` | Adds a user to a supplementary group                |
| `chown`       | Changes file/directory owner and/or group           |
| `chown -R`    | Changes ownership recursively                       |

---

# 22. My Practice

I have practiced Linux user and privilege management as part of my cybersecurity learning journey.

I practiced:

* Understanding the root user
* Understanding risks associated with root access
* Using `sudo`
* Creating users with `useradd`
* Assigning primary and secondary groups
* Modifying users with `usermod`
* Locking and unlocking accounts
* Deleting users with `userdel`
* Understanding `userdel -r`
* Changing file ownership with `chown`
* Checking users and groups with `id` and `groups`

---

# Key Takeaway

Linux uses different levels of privileges to control access to system resources.

The **root user** has extensive privileges, so normal users should use `sudo` for authorized administrative tasks instead of logging in as root for everyday work.

User-management commands such as:

```bash
useradd
usermod
userdel
```

help administrators manage accounts, while:

```bash
chown
```

helps manage file and directory ownership.

Understanding users, groups, privileges, and ownership is an important foundation for Linux system administration and cybersecurity.
