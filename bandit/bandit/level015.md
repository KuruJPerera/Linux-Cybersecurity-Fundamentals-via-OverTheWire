# Bandit Level 14 → Level 15

## Level Goal

The password for the next level could not be found in a file. Instead, it was provided by a **server listening on a specific port** on `localhost`. I had to connect to this port using a tool like `nc` (netcat), which is a simple utility for reading from and writing to network connections.

---

## Access Details

I connected with:

- **Username**: `bandit14`  
- **Password**: [password from the previous level] 
- **Host**: `bandit.labs.overthewire.org`  
- **Port**: `2220`

---

## Steps to Solve

### Step 1: Log into Level 14

I connected to the server as usual:

```bash
ssh bandit14@bandit.labs.overthewire.org -p 2220
```

Then I entered the password I got from Level 13.

---

### Step 2: Discover the Port Instructions

Once logged in, I ran:

```bash
ls
```

There were no unusual files to open. So I checked the level description again (via OverTheWire or `readme` files) and confirmed that the password would be provided by a **service running locally on port `30000`**.

---

### Step 3: Connect Using `nc`

I used the `nc` command (short for **netcat**) to connect to the service:

```bash
nc localhost 30000
```

This sent a connection request to port `30000` on `localhost`, which is the same machine I was logged into. The server immediately responded with the password for the next level.

---

## Explanation of `nc` Command

```bash
nc localhost 30000
```

- `nc`: The **netcat** utility, used to send and receive data over TCP or UDP.
- `localhost`: Refers to the **local machine** (same as `127.0.0.1`).
- `30000`: The **TCP port number** that the password service is listening on.

Once connected, netcat prints any data sent by the service to the screen. In this case, the password appeared immediately.

---

## Useful Commands I Used

```bash
ssh bandit14@bandit.labs.overthewire.org -p 2220  # Log in to Level 14
ls                                               # Check for files (none helpful)
nc localhost 30000                               # Connect to the password service
```

---

## Conclusion

This level taught me how to:

- Use `nc` (netcat) to connect to a TCP port
- Interact with a network service running locally
- Understand how services can deliver credentials without files

A simple yet powerful demo of networking basics and local TCP connections.
