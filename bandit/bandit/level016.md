# Bandit Level 15 → Level 16

## Level Goal

The password for the next level was not stored in a file or accessible via a basic TCP connection. Instead, a server on `localhost` was listening on port `30001`, and it required **an SSL-encrypted connection** to communicate. I needed to use **`ncat` with SSL enabled** to connect and retrieve the password.

---

## Access Details

I connected with:

- **Username**: `bandit15`  
- **Password**: *[password from the previous level]*  
- **Host**: `bandit.labs.overthewire.org`  
- **Port**: `2220`

---

## Steps to Solve

### Step 1: Log into Level 15

I connected via SSH:

```bash
ssh bandit15@bandit.labs.overthewire.org -p 2220
```

Then I entered the password from Level 14.

---

### Step 2: Understand the Requirement

The level description stated that the service running on port `30001` **expects SSL connections**, unlike the previous level (which used plain TCP).

This meant a basic `nc` or `ncat` command like:

```bash
ncat localhost 30001
```

would not work — the connection would fail silently or show a protocol error.

---

### Step 3: Use the `man` Command to Find Help

To find the right way to enable SSL in `ncat`, I checked the manual:

```bash
man ncat
```

I searched inside the man page by typing `/ssl` and found this flag:

```text
--ssl        Enable SSL
```

This meant I could enable encryption by adding the `--ssl` option.

---

### Step 4: Connect Using `ncat` with SSL

I ran the following command to establish the encrypted connection:

```bash
ncat --ssl localhost 30001
```

Once connected, the server immediately responded with the password for **bandit16**.

---

## Useful Commands I Used

```bash
ssh bandit15@bandit.labs.overthewire.org -p 2220  # SSH login
man ncat                                         # Look up SSL options
/ssl                                             # Search inside man page
ncat --ssl localhost 30001                       # Connect to SSL-enabled service
```

---

## Conclusion

This level taught me how to:

- Use the `man` command to read documentation and search for relevant options
- Recognize when a service requires **SSL encryption**
- Use `ncat --ssl` to connect securely to encrypted services over TCP

It emphasized reading documentation carefully and adapting tools to meet protocol requirements.
