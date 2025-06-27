# Bandit Level 4 → Level 5

## Level Goal

The goal for this level was to find the password for the next level. The password was stored in the only **human-readable file** in the `inhere/` directory. The challenge was to distinguish this file from others, which were likely binary or unreadable.

---

## Access Details

I logged into the server using the following credentials:

- **Username**: `bandit4`  
- **Password**: *[password from the previous level]*  
- **Host**: `bandit.labs.overthewire.org`  
- **Port**: `2220`

---

## Steps to Solve

### Step 1: Navigating to the Target Directory

After logging in, I moved into the `inhere/` directory, which was located in the home directory:

```bash
cd inhere
```

The `cd` command stands for "change directory" and is used to move between folders.

---

### Step 2: Listing All Files

I listed all files in the directory using:

```bash
ls -la
```

- `ls` lists files and directories.
- `-l` shows a detailed "long" format (permissions, size, date, etc.).
- `-a` shows all files, including hidden ones (those starting with `.`).

This showed a collection of files with seemingly random names.

---

### Step 3: Identifying the Human-Readable File

To determine which file was human-readable (plain text), I used the `file` command:

```bash
file ./*
```

- `file` checks each file and tells you what type of data it contains.
- `./*` targets all files in the current directory.

The output listed the file types. Most were binary, but one file showed as `ASCII text`, indicating it's human-readable.

---

### Step 4: Reading the File

Once I found the readable file, I used the `cat` command to view its contents:

```bash
cat ./-file07
```


- `cat` stands for "concatenate" and is used to read the contents of text files.
- The `./` prefix ensures the filename is interpreted correctly, especially if it starts with a dash `-`.

The file contained the password for **Level 5**.

---

## Commands I Used

```bash
cd inhere       # navigate into the target directory
ls -la          # list all files (including hidden ones) with details
file ./*        # identify the type of each file
cat ./filename  # read the contents of the human-readable file
```
