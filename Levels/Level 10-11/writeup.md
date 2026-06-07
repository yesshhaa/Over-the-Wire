# OverTheWire Bandit — Level 10 → Level 11

## Objective
The password is stored in `data.txt`, which contains **Base64 encoded** data.

## Connection Details
| Field    | Value                             |
|----------|-----------------------------------|
| Host     | `bandit.labs.overthewire.org`     |
| Port     | `2220`                            |
| Username | `bandit10`                        |
| Password | `FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey` |

## Command Used to Login
```bash
ssh bandit10@bandit.labs.overthewire.org -p 2220
```

![Level 10 SSH Login](images/level10-login.png)

---

## The Challenge
`data.txt` contains a Base64 encoded string. It looks like random characters and is unreadable until decoded.

```bash
ls
```

## Solution

Use `base64 -d` to decode the file contents:

```bash
cat data.txt | base64 -d
```

![base64 decode output showing password](images/level10-solution.png)

Output:
```
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```

## Password Found
```
dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```

## Logging into Level 11
```bash
ssh bandit11@bandit.labs.overthewire.org -p 2220
```

---

## What is Base64?

Base64 is an encoding scheme that converts binary data into ASCII text using 64 printable characters. It is **not encryption** — it can be decoded by anyone without a key.

| Concept | Detail |
|---------|--------|
| Purpose | Encode binary data as text (email, web, APIs) |
| Recognizable by | String ends with `=` or `==` padding |
| Security | None — it's encoding, not encryption |
| Decode command | `base64 -d` or `base64 --decode` |

---

## Key Takeaways
- Base64 is encoding, not encryption — never confuse the two
- Base64 strings often end with `=` padding characters
- `base64 -d` decodes; `base64` (no flag) encodes
- Commonly seen in web tokens (JWT), email attachments, and CTF challenges

---

## Commands Reference

| Command | Purpose |
|---------|---------|
| `cat data.txt` | View raw Base64 string |
| `cat data.txt \| base64 -d` | Decode the Base64 content |

---

