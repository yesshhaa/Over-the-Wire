# OverTheWire Bandit — Level 6 → Level 7
 
## Objective
The password is stored **somewhere on the server** in a file that is:
- Owned by user `bandit7`
- Owned by group `bandit6`
- 33 bytes in size
## Connection Details
| Field    | Value                             |
|----------|-----------------------------------|
| Host     | `bandit.labs.overthewire.org`     |
| Port     | `2220`                            |
| Username | `bandit6`                         |
| Password | `HWasnPhtq9AVKe0dmk45nxy20cvUa6EG` |
 
## Command Used to Login
```bash
ssh bandit6@bandit.labs.overthewire.org -p 2220
```
 
![Level 6 SSH Login](images/level6-login.png)
 
---
 
## The Challenge
The home directory is empty — the file is hidden **somewhere on the entire server**. We need to search from the root `/` directory using all three criteria.
 
```bash
ls
ls -la
```
 
![Empty home directory](images/level6-homedir.png)
 
## Solution
 
Search the entire filesystem with `find` using user, group, and size filters. Redirect errors to `/dev/null` to suppress "Permission denied" noise:
 
```bash
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
```
 
![find command output and password](images/level6-solution.png)
 
Output:
```
/var/lib/dpkg/info/bandit7.password
```
 
Then read it:
 
```bash
cat /var/lib/dpkg/info/bandit7.password
```
 
## Password Found
```
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```
 
## Logging into Level 7
```bash
ssh bandit7@bandit.labs.overthewire.org -p 2220
```
 
---
 
## Breaking Down the `find` Command
 
```bash
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
```
 
| Part | Meaning |
|------|---------|
| `find /` | Search from root — entire filesystem |
| `-type f` | Only regular files |
| `-user bandit7` | Owned by user `bandit7` |
| `-group bandit6` | Owned by group `bandit6` |
| `-size 33c` | Exactly 33 bytes |
| `2>/dev/null` | Suppress "Permission denied" errors |
 
---
 
## What is `2>/dev/null`?
 
Linux has three standard streams:
| Stream | Number | Purpose |
|--------|--------|---------|
| stdin  | 0 | Input |
| stdout | 1 | Normal output |
| stderr | 2 | Error messages |
 
`2>/dev/null` redirects **stderr** (stream 2) to `/dev/null` — a black hole that discards everything. Without it, the terminal floods with "Permission denied" for every protected directory.
 
---
 
## Key Takeaways
- Always use `2>/dev/null` when running `find /` to suppress permission errors
- `-user` and `-group` flags let you filter by file ownership
- System files can hold game data — think outside the home directory
---
 
## Commands Reference
 
| Command | Purpose |
|---------|---------|
| `find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null` | Search entire server for the file |
| `cat /var/lib/dpkg/info/bandit7.password` | Read the password |
 
---
