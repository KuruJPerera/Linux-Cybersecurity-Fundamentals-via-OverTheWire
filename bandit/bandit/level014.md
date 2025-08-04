# Bandit Level 13 → Level 14

## Level Goal

The password for the next level was stored on the server, but it could only be retrieved by logging in with an **SSH private key** located in the home directory of `bandit13`. Instead of using a password, I had to use this private key to authenticate as `bandit14`.

---

## Access Details

I connected with:

- **Username**: `bandit13`  
- **Password**: *[password from the previous level]*  
- **Host**: `bandit.labs.overthewire.org`  
- **Port**: `2220`

---

## Steps to Solve

### Step 1: Log into Level 13

I connected using SSH with the known credentials:

```bash
ssh bandit13@bandit.labs.overthewire.org -p 2220
```

After entering the password from Level 12, I was in the home directory of `bandit13`.

---

### Step 2: Locate the Private Key

I listed the files in the home directory:

```bash
ls
```

There was a file named:

```bash
sshkey.private
```

I verified its contents and confirmed it was an SSH private key.

---

### Step 3: Set Proper Permissions (if copying locally)

If I wanted to copy the key to my local machine, I could use `scp`:

```bash
scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .
chmod 600 sshkey.private
```

This ensures only I can read the file — a requirement for SSH.

---

### Step 4: Log in to Level 14 with the Key

I used the private key to SSH into the next user:

```bash
ssh -i sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org
```

No password was required — the key handled authentication.

---

### Step 5: Retrieve the Password

Once logged in as `bandit14`, I simply ran:

```bash
cat /etc/bandit_pass/bandit14
```

This revealed the password for the next level.

---

## Useful Commands I Used

```bash
ssh bandit13@bandit.labs.overthewire.org -p 2220     # Log into Level 13
ls                                                  # List files to find the private key
scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .  # (Optional) Copy key
chmod 600 sshkey.private                             # Secure private key file
ssh -i sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org  # Login as bandit14
cat /etc/bandit_pass/bandit14                        # Get the password for Level 14
```

---

## Conclusion

This level introduced me to SSH key-based authentication. I learned how to:

- Use private keys for SSH login
- Handle file permissions for SSH keys
- Access user accounts without passwords when keys are used

A great exercise in practical SSH usage and secure authentication.

