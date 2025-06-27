# Bandit Level 1 → Level 2

## Level Goal

The goal for this level was to connect to the Bandit server using SSH and find the password for the next level. I knew the password was stored in a file called `-` located in the home directory.

---

## Access Details

To begin, I used the following credentials to log in:

- **Username**: `bandit1`  
- **Password**: *[password from the previous level]*  
- **Host**: `bandit.labs.overthewire.org`  
- **Port**: `2220`

---

## Steps to Solve

### Step 1: Listing Files in the Home Directory

Once I logged in, I ran the `ls` command to see what files were in the home directory:

```bash
ls
```

I saw a single file named `-`. At first, this was confusing since the dash character is usually used to represent standard input in Unix commands.

---

### Step 2: Reading the File Named `-`

I realized that using `cat -` wouldn’t work, because that tells `cat` to read from standard input. To read an actual file named `-`, I needed to specify the relative path explicitly. So, I ran:

```bash
cat ./- or < - bith gave the same output
```

This command worked and revealed the password for **Level 2**.

---

## Commands I Used

```bash
ls        # listed files in the home directory
cat ./-   # read the contents of the file named '-'
```
