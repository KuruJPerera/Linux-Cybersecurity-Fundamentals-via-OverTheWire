# Bandit Level 11 → Level 12

## Level Goal

The goal for this level was to retrieve the password for the next level from a file named `data.txt`. The level description said the file had been **encoded using ROT13**.

---

## Access Details

To begin, I connected with the following credentials:

- **Username**: `bandit11`  
- **Password**: *[password from the previous level]*  
- **Host**: `bandit.labs.overthewire.org`  
- **Port**: `2220`

---

## Steps to Solve

### Step 1: Understanding ROT13

Before doing anything, I looked up **ROT13** on Wikipedia. I learned that:

- ROT13 is a **simple letter substitution cipher**.
- Each letter is replaced with the letter **13 places after it** in the alphabet.
- It only affects **alphabetic characters (A–Z, a–z)**.
- Applying ROT13 twice gets you back the original text (because 13 + 13 = 26 letters in the alphabet).

So, it’s a reversible and symmetric cipher.

---

### Step 2: Viewing the File

After logging in, I listed the file:

```bash
ls
```

I saw `data.txt`. I opened it with:

```bash
cat data.txt
```

The contents looked like random letters—but they were all readable, suggesting some simple substitution like ROT13.

---

### Step 3: Decoding ROT13

Since ROT13 is very simple, I used the `tr` command to decode it. I had seen this trick before or could have learned it from online or `man tr`:

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

This tells `tr` to substitute letters from the first set with the matching letter from the second set — which effectively performs ROT13 decryption.

The command printed a decoded line to the screen, which was the password for **Level 12**.

---

## Commands I Used

```bash
ls                                           # list directory contents
cat data.txt                                 # view ROT13-encoded password
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'    # decode ROT13 using tr
```

---

## Conclusion

This level introduced me to **ROT13**, a basic but fun cipher. With the help of the Wikipedia article, I understood how it worked and then used the `tr` command to decode the password. The simplicity of ROT13 made it easy to solve once I knew what to look for.

