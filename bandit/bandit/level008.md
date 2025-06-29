# Bandit Level 7 → Level 8

## Level Goal

The goal for this level was to find the password for the next level. The password was stored in a file called `data.txt`, and I was told that it is the **only human-readable string** in the file that is **next to the word "millionth"**.

---

## Access Details

I logged in using the following:

- **Username**: `bandit7`  
- **Password**: *[password from the previous level]*  
- **Host**: `bandit.labs.overthewire.org`  
- **Port**: `2220`

---

## Steps to Solve

### Step 1: Listing the Target File

After logging in, I ran:

```bash
ls
```

I saw a file named `data.txt`. I tried opening it with `cat`:

```bash
cat data.txt
```

But the output was mostly unreadable binary junk, which made sense since it wasn't a plain text file.

---

### Step 2: Filtering Human-Readable Text with `strings`

To extract the readable content from a binary file, I used the `strings` command:

```bash
strings data.txt
```

This filtered out and displayed only the printable text portions of the file.

---

### Step 3: Searching for the Keyword with `grep`

From the problem description, I knew the password would be **next to the word "millionth"**. So I combined `strings` with `grep` to find the relevant line:

```bash
strings data.txt | grep "millionth"
```

This returned a line that looked like:

```
millionth <password>
```

---

## Commands I Used

```bash
ls                     # list files to find data.txt
strings data.txt       # extract readable text from binary
strings data.txt | grep millionth   # find the line containing the password
```

---

## Conclusion

This level taught me how to deal with binary files that contain embedded readable text. Using `strings` and `grep` together made it quick and efficient to extract the password for **Level 8**.

