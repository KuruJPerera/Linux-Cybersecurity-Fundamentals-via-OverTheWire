# Bandit Level 3 → Level 4

## Level Goal

The goal for this level was to log into the Bandit server and find the password for the next level. The password was stored in a **hidden file** in the **`inhere/`** directory.

---

## Access Details

I logged into the server using the following credentials:

- **Username**: `bandit3`  
- **Password**: *[password from the previous level]*  
- **Host**: `bandit.labs.overthewire.org`  
- **Port**: `2220`

---

## Steps to Solve

### Step 1: Navigating to the Target Directory

After logging in, I changed into the `inhere/` directory where the file was located:

```bash
cd inhere
```

---

### Step 2: Listing Hidden Files

At first, I used the regular `ls` command, but I didn’t see anything useful. Then I remembered the file was **hidden**, meaning its name begins with a `.` (dot). So I ran:

```bash
ls -a
```

This showed all files in the directory, including hidden ones. Among the results, I saw a file that looked suspicious—it had a dot at the beginning of its name, like `.hidden`.

---

### Step 3: Reading the Hidden File

To confirm it contained the password, I used:

```bash
cat .hidden
```

Sure enough, it printed the password for **Level 4**.

---

## Commands I Used

```bash
cd inhere     # navigate into the target directory
ls -a         # list all files, including hidden ones
cat .hidden   # read the contents of the hidden file
```
