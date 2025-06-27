# Bandit Level 0 → Level 1

## Level Goal

The goal for this level is to connect to the Bandit server using SSH and find the password for the next level. The password is stored in a file called `readme` located in the home directory.

---

## Access Details

To get started, I used the following credentials:

- **Username**: `bandit0`  
- **Password**: `bandit0`  
- **Host**: `bandit.labs.overthewire.org`  
- **Port**: `2220`

---

## Steps to Solve

### Step 1: Listing Files in the Home Directory

I ran the `ls` command to list the files in the home directory:

```bash
ls
```

This showed a single file named `readme`, which looked like what I needed.

---

### Step 2: Reading the Contents of the File

To read the contents of the file and get the password for the next level, I ran:

```bash
cat readme
```

The output was the password for **Level 1**.

---

## Commands Used

```bash
ls          # to list the files in the directory
cat readme  # to read the contents of the readme file
```
