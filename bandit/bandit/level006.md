# Bandit Level 5 → Level 6

## Level Goal

The goal for this level was to find the password for the next level. The password was stored in a file somewhere under the **`inhere/`** directory, and the file had the following properties:

- It was a **regular file**.
- It was exactly **1033 bytes** in size.
- It was **not executable**.

---

## Access Details

I logged into the Bandit server using the following credentials:

- **Username**: `bandit5`  
- **Password**: *[password from the previous level]*  
- **Host**: `bandit.labs.overthewire.org`  
- **Port**: `2220`

---

## Steps to Solve

### Step 1: Exploring the `inhere` Directory

After logging in, I navigated to the `inhere/` directory:

```bash
cd inhere
```

---

### Step 2: Finding the Correct File

To locate the file with the specific properties described, I used the following `find` command:

```bash
find . -type f -size 1033c ! -executable
```

Let’s break this down:

- `find` — A command-line utility for searching files and directories.
- `.` — Tells `find` to start searching in the current directory.
- `-type f` — Limits the search to **regular files** only (not directories or symbolic links).
- `-size 1033c` — Matches files that are **exactly 1033 bytes** in size. The `c` suffix means “bytes”.
- `! -executable` — Excludes files that are executable. The `!` acts as a negation operator.

This command efficiently filters for the exact file we’re looking for.

---

### Step 3: Reading the File

The command returned the file: `./maybehere07/.file2`. I used `cat` to read its contents:

```bash
cat ./maybehere07/.file2
```

The content of the file was the password for **Level 6**.

---

## Commands I Used

```bash
cd inhere                                  # move into the inhere directory
find . -type f -size 1033c ! -executable  # search for the target file
cat ./maybehere07/.file2                  # read the contents of the file
```
