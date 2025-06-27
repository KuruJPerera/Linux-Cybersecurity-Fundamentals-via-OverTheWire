# Bandit Level 2 → Level 3

## Level Goal

The goal for this level was to log into the Bandit server and retrieve the password for the next level. I learned that the password was stored in a file called **`spaces in this filename`**, which is located in the home directory.

---

## Access Details

Here’s how I logged into the level:

- **Username**: `bandit2`  
- **Password**: *[password from the previous level]*  
- **Host**: `bandit.labs.overthewire.org`  
- **Port**: `2220`

---

## Steps to Solve

### Step 1: Listing the Files

Once I was connected, I ran the `ls` command to list the contents of the home directory:

```bash
ls
```

I saw a file named `spaces in this filename`. The spaces in the name made it tricky to work with, because the shell treats each word separated by a space as a separate argument.

---

### Step 2: Dealing with Spaces in the Filename

At first, I tried:

```bash
cat spaces in this filename
```

But this didn't work—it gave me an error because it thought I was referencing four different files.

---

### Step 3: Using Quotes or Escaping Spaces

To solve this, I had two options:

#### Option 1: Quoting the filename
I wrapped the filename in double quotes so the shell would treat it as a single string:

```bash
cat "spaces in this filename"
```

#### Option 2: Escaping the spaces
I could also escape each space using a backslash:

```bash
cat spaces\ in\ this\ filename
```

Both approaches worked, and the command displayed the password for **Level 3**.

---

## Commands I Used

```bash
ls                                   # listed files in the directory
cat "spaces in this filename"        # read the file using quotes
# or
cat spaces\ in\ this\ filename       # read the file using escaped spaces
```
