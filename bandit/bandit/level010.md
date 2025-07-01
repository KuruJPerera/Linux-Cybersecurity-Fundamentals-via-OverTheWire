# Bandit Level 9 → Level 10

## Level Goal

The objective of this level was to find the password for the next level, which was stored in a file named `data.txt`. I was told the password was hidden among **human-readable strings**, and it was **preceded by several `=` characters**.

---

## Access Details

Here’s how I connected to the server:

- **Username**: `bandit9`  
- **Password**: *[password from the previous level]*  
- **Host**: `bandit.labs.overthewire.org`  
- **Port**: `2220`

---

## Steps to Solve

### Step 1: Listing the File

After logging in, I ran:

```bash
ls
```

I saw a file named `data.txt`. When I tried to read it using:

```bash
cat data.txt
```

It showed a lot of unreadable binary content, which told me it wasn’t a plain text file.

---

### Step 2: Extracting Readable Text with `strings`

To extract just the human-readable parts, I used the `strings` command:

```bash
strings data.txt
```

This displayed all the printable character sequences in the file. Many were random strings, but I was looking for something **preceded by `=` characters**, as mentioned in the level description.

---

### Step 3: Filtering with `grep`

To narrow it down, I piped the output into `grep` and looked for lines containing `===`, assuming the password line would have multiple `=` signs:

```bash
strings data.txt | grep '==='
```

This returned a line that looked like:

```
==========kAguVoP6hPlujesygL6U3ebfUzJ2dg
```

The string after the `=` characters was clearly the password for **Level 10**.

---

## Commands I Used

```bash
ls                             # check for files
strings data.txt               # extract readable text from binary
strings data.txt | grep '==='  # find line containing multiple '=' characters
```

---

## Conclusion

This level taught me how to extract useful strings from binary files and how to use patterns (like multiple `=` characters) to zero in on the hidden password using `grep`.

