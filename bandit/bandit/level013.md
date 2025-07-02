# Bandit Level 12 → Level 13

## Level Goal

The password for the next level was stored in a file named `data.txt`, but the file had been **encoded and compressed multiple times** using various formats. I needed to identify the file type at each step, and decode or extract it using the appropriate commands — without using `gunzip` or `bunzip2`.

---

## Access Details

I connected with:

- **Username**: `bandit12`  
- **Password**: *[password from the previous level]*  
- **Host**: `bandit.labs.overthewire.org`  
- **Port**: `2220`

---

## Steps to Solve

### Step 1: Initial Inspection

I started by listing the file:

```bash
ls
```

There was a `data.txt`. I checked its type:

```bash
file data.txt
```

At each stage, `file` told me whether it was a `gzip compressed`, `bzip2 compressed`, `POSIX tar archive`, or something else.

---

### Step 2: Manual Decoding Process

#### ⬢ Gzip file

When `file` told me it was a **gzip** file, instead of using `gunzip`, I did:

```bash
mv data.txt data.gz
gzip -d data.gz
```

This created a new `data` file.

#### ⬢ Bzip2 file

When it was a **bzip2** file:

```bash
mv data data.bz2
bzip2 -d data.bz2
```

Again, this gave me a new `data` file.

#### ⬢ Tar archive

When I hit a **tar archive**, I used:

```bash
tar -xf data
```

This extracted the next file layer — often also named `data`.

####  xxd Hex dump

At one point, I encountered a file that `file` described as `ASCII text`, and it looked like a hex dump. So I reversed it with `xxd`:

```bash
xxd -r data.txt > data
```

I renamed files at every step to avoid confusion and ensure correct decompression.

#### Repeating

I repeated this process — checking the file type, renaming if needed, and applying the appropriate decompression or decoding tool — until I finally reached a plain text file containing the password.

---

## Useful Commands I Used

```bash
file data.txt            # Detect file type
mv data.txt data.gz      # Rename file to match expected extension
gzip -d data.gz          # Decompress .gz file
bzip2 -d data.bz2        # Decompress .bz2 file
tar -xf data             # Extract tar archive
xxd -r data.txt > data   # Reverse a hex dump
```

---

## Conclusion

This level helped me understand how to:
- Use `file` to inspect unknown file types
- Decompress files using `gzip`, `bzip2`, and `tar` **manually**
- Reverse hex-encoded files with `xxd`
  
It was a solid challenge in layered decoding and low-level Linux file operations.

