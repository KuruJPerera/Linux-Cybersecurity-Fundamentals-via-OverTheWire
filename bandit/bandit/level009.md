# Bandit Level 8 → Level 9

## Level Goal

The goal for this level was to find the password for the next level. The password was stored in a file called `data.txt`, and I was told that it is the **only line** in the file that occurs **exactly once**.

---

## Access Details

I logged in with the following:

- **Username**: `bandit8`  
- **Password**: *[password from the previous level]*  
- **Host**: `bandit.labs.overthewire.org`  
- **Port**: `2220`

---

## Steps to Solve

### Step 1: Listing and Viewing the File

After connecting, I ran:

```bash
ls
```

I saw a file called `data.txt`. I opened it to check its contents:

```bash
cat data.txt
```

The file was filled with many lines—most of them repeated multiple times.

---

### Step 2: Sorting the File

To find the line that appeared only once, I first sorted the file. This groups identical lines together in numerial order first and then alpabetical order, which is required for the next step:

```bash
sort data.txt
```

---

### Step 3: Counting Unique Occurrences

Then I piped the sorted output into the `uniq -c` command, which shows how many times each line appears:

```bash
sort data.txt | uniq -c
```

This returned output like:

```
      2 abcdefg
      1 5Te9wO9hg2
      5 xxxxxxxx
```

I scanned the output for the line with a count of **1**, since that was the only line that occurred once—and therefore, the password.

---

### Step 4: Extracting the Password

Once I spotted the line with a count of `1`, I copied the line (ignoring the count itself), and that was the password for **Level 9**.

---

## Commands I Used

```bash
ls                      # list directory contents
cat data.txt            # view raw content of the file
sort data.txt           # sort the lines alphabetically
sort data.txt | uniq -c # count how many times each line appears
```

---

## Conclusion

This level taught me how to analyze text files by frequency of line occurrences. Using `sort` and `uniq -c` together helped me efficiently locate the line that only appeared once—which turned out to be the password for the next level.

