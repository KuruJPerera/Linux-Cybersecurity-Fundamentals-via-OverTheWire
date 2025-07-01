# Bandit Level 10 → Level 11

## Level Goal

The goal for this level was to retrieve the password for the next level from a file named `data.txt`. The description mentioned that the file was **encoded in base64**, and I needed to decode it to get the password.

---

## Access Details

To begin, I connected using the following credentials:

- **Username**: `bandit10`  
- **Password**: *[password from the previous level]*  
- **Host**: `bandit.labs.overthewire.org`  
- **Port**: `2220`

---

## Steps to Solve

### Step 1: Viewing the File

After logging in, I checked for the file:

```bash
ls
```

The file `data.txt` was present. I previewed its contents:

```bash
cat data.txt
```

The output looked like a long string of random-looking characters, but it matched the pattern of base64-encoded data.

---

### Step 2: Checking the `base64` Manual

I wasn’t sure what the exact syntax was to decode a file, so I used:

```bash
man base64
```

From the manual, I found that the flag to decode a base64-encoded input is:

```bash
-d, --decode
```

---

### Step 3: Decoding the File

Using what I learned from `man base64`, I decoded the file using:

```bash
base64 -d data.txt
```

This printed a clean, readable password to the terminal — this was the password for **Level 11**.

---

## Commands I Used

```bash
ls                    # list the file
cat data.txt          # view the encoded content
man base64            # learn how to use the decode flag
base64 -d data.txt    # decode base64 and reveal the password
```

---

## Conclusion

This level helped me understand how to recognize base64-encoded data and use the `base64` tool with the `-d` option to decode it. Reading the manual with `man base64` was essential in figuring out the right flag to use.

