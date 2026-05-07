# Assignments — Linux and DevOps Basics

## Assignment — Linux and SSH Setup

1. Launch an Amazon Linux 2023 EC2 instance in HYD region. Generate an SSH key pair. What is the difference between the two files created?

2. Connect to your EC2 instance using SSH. Confirm you are connected by checking the hostname, current directory, and logged-in username.

3. Your Security Group currently allows SSH from anywhere. Restrict it to your own IP only.

4. Find out which Linux distribution and version is running on the instance.

5. Delete the instance, Security Group, and key pair.

---

## Assignment — Linux File Operations

1. Create the following directory structure using a single command:
   ```
   devops/
   └── projects/
       └── batch-90s/
   ```

2. Inside `batch-90s/`, create a file called `notes.txt`. Write three lines into it, then append two more. Read it to verify.

3. Copy `notes.txt` to `projects/` and rename the copy to `backup.txt`. Verify both exist.

4. Move `backup.txt` to `/tmp/`. What happens to files there when the server restarts?

5. Delete the `devops/` directory and everything inside it.

6. List the contents of `/var/log/` sorted by time. What do you notice? Why would a DevOps engineer check this directory?

---

## Assignment — Linux Text Processing

Create a file with this content:
```
web-server-01 192.168.1.10 running
web-server-02 192.168.1.11 stopped
db-server-01  192.168.1.20 running
db-server-02  192.168.1.21 running
cache-server  192.168.1.30 stopped
```

Write a command for each:

1. Show only lines where the server is `running`.

2. Show only lines where the server is NOT `running`.

3. Count how many servers are `running`.

4. Show the first 3 lines. Then show the last 2.

5. Extract only the IP addresses.

6. Extract only the server names.

7. Show only the names of `stopped` servers — in one command.

---

## Assignment — wget, curl, and Pipes

1. Download the following file to your EC2 instance and save it as `session-notes.txt`:
   ```
   https://raw.githubusercontent.com/daws-90s/notes/refs/heads/main/session-02.txt
   ```

2. Fetch the same file using `curl` and count its lines — without saving it to disk.

3. Fetch the file and print only lines containing `Linux` — in one command.

4. Run this and explain what `$NF` means:
   ```bash
   echo "https://raw.githubusercontent.com/daws-90s/notes/refs/heads/main/session-02.txt" | awk -F "/" '{print $NF}'
   ```

5. Fetch the file, filter lines containing `ssh`, then count how many matched — using two pipes.

---

## Assignment — /etc/passwd Deep Dive

1. How many user accounts exist on the system?

2. Extract only the usernames.

3. Show only users with UID greater than 999.

4. Find the entry for `ec2-user`. What is their home directory?

5. List all unique login shells assigned to users on the system.

---

## Assignment — Vim Editor

1. Create `practice.txt` using vim. Add 10 lines of content, save and exit.

2. Open the file. Turn on line numbers, jump to line 7, delete line 3, save and exit.

3. Open the file. Search for a word, move through its occurrences, then clear the highlight.

4. Replace every occurrence of one word in the file with another — in one command.

5. Go to the bottom of the file, add 3 lines, then undo the last one. Save.

6. Copy one line and paste it 5 times in a single step. What is the command?

---

## Assignment — Linux User Management

1. Create a user `alice`. What primary group was automatically created for her?

2. Set a password for `alice`. Configure the server to allow password-based SSH and connect as `alice`.

3. Create a group `devops-team`. Add `alice` as a secondary member. Verify.

4. Create a user `bob`. Add both `alice` and `bob` to `devops-team`.

5. Give `alice` sudo access. Verify she can run commands as root.

6. Remove `alice`'s sudo access. Confirm she can no longer run sudo commands.

7. Add a rule to `/etc/sudoers` that allows only `devops-team` to run `useradd` and `usermod` — nothing else.

---

## Assignment — File Permissions and Ownership

1. Create `secret.txt` with some content. Who can read it by default?

2. Restrict it so only the owner can read and write. Switch to another user and try to read it — what happens?

3. Create `deploy.sh` with one line of content. Make it executable by the owner only. What numeric value represents owner read+write+execute?

4. Create `shared/`. Owner has full access, group can read and execute, others have none — set this in numeric form.

5. Change the owner of `secret.txt` to `alice` and the group to `devops-team`.

6. Create `project/` with 3 files inside. Change ownership of everything in it to `alice:devops-team` in one command.

7. Check the permissions on `/etc/shadow`. Why is it set that way?

---

## Assignment — Key-Based SSH for a New User

1. Create a user `deploy` with no password.

2. Generate a new SSH key pair for this user on your local machine.

3. Set up `.ssh/` and `authorized_keys` on the server for `deploy` with the correct permissions and ownership.

4. Connect to the server as `deploy` using the private key.

5. Try connecting without specifying the key. What happens and why?

6. Disable password authentication on the server. Verify that a password login is rejected. Why does this matter for production?

---

> If a command fails, read the error carefully — it usually tells you what is wrong. Search if needed. Bring questions to the Q&A session.
