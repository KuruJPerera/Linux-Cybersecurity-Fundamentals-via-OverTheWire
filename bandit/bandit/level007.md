# Bandit Level 6 → Level 7

## Level Goal

The goal for this level was to find the password for the next level. I knew it was stored somewhere in the `/home/bandit7` directory, but not in a straightforward file—it had specific properties:  
It was **human-readable**, **1033 bytes in size**, **not executable**, and **owned by user bandit7** and group bandit6.

---

## Access Details

Here’s how I connected to the server:

- **Username**: `bandit6`  
- **Password**: *[password from the previous level]*  
- **Host**: `bandit.labs.overthewire.org`  
- **Port**: `2220`

---

## Steps to Solve

### Step 1: Navigating to the Directory

I started by moving into the target directory:

```bash
cd /home/bandit7
```

---

### Step 2: Using the `find` Command with Filters

Since the password file had very specific attributes, I used the `find` command with multiple options:

```bash
find . -type f -size 33c -user bandit7 -group bandit6
```

Here's what each part does:

- `.` – search in current directory  
- `-type f` – regular file  
- `-size 33c` – exactly 1033 **bytes** (`c` = bytes)  
- `-user bandit7` – owned by user `bandit7`  
- `-group bandit6` – owned by group `bandit6`

---

### Step 3: Reading the File

The command returned a relative path to a file. I used `cat` to read it:

```bash
cat ./<filename>
```

That revealed the password for **Level 7**.

---

## Commands I Used

```bash
cd /home/bandit7
find . -type f -size 33c -user bandit7 -group bandit6
cat ./<filename>
```

