# Shell Scripting Assignments

> Based on Session 14 & Session 15 notes.
> Every script must start with `#!/bin/bash` and be pushed to the shell-practice repo.

---

## Assignment 1 — Hello World & Shebang

Write a script `01-hello.sh` that:

1. Prints `Hello, World!`
2. Prints the current date and time
3. Prints the name of the user running the script
4. Prints the directory the script is running from

**Expected output:**
```
Hello, World!
Today is: Fri May 23 10:30:00 IST 2026
Running as: ec2-user
Current directory: /home/ec2-user/scripts
```

---

## Assignment 2 — Variables & DRY Principle

Write a script `02-variables.sh` that:

1. Store your name, age, and city in variables
2. Print a sentence using all three variables
3. Calculate and print how many years until you turn 60
4. Change the name variable to a different name and verify only **one line** needs to change

**Expected output:**
```
My name is Siva, I am 28 years old and I live in Hyderabad.
Years until 60: 32
```

---

## Assignment 3 — Command Line Arguments

Write a script `03-args.sh` that accepts two arguments: a **username** and a **country**.

1. Print: `User <username> is from <country>`
2. Print total number of arguments passed
3. Print all arguments passed
4. Print the script name

Run it as: `sh 03-args.sh Siva India`

**Expected output:**
```
User Siva is from India
Number of arguments: 2
All arguments: Siva India
Script name: 03-args.sh
```

---

## Assignment 4 — Special Variables

Write a script `04-special-vars.sh` that demonstrates all special variables:

1. Print who is running the script
2. Print the current directory
3. Print the home directory
4. Print the PID of the script
5. Run `sleep 10` in the **background** and print its PID
6. Print a random number between 1–100
7. At the end, print how many seconds the script took to run

**Expected output:**
```
Running as     : ec2-user
Directory      : /home/ec2-user
Home           : /home/ec2-user
Script PID     : 12345
Background PID : 12346
Random number  : 73
Script ran in 0 seconds
```

---

## Assignment 5 — Exit Codes

Write a script `05-exit-code.sh` that:

1. Runs `ls /tmp` and checks if it succeeded — print `SUCCESS` or `FAILURE`
2. Runs `ls /fakedir` and checks — print `SUCCESS` or `FAILURE`
3. Runs `ping -c1 google.com` and checks — print `Host reachable` or `Host not reachable`
4. At the end, exit the script with code `0` if all commands succeeded, or `1` if any failed

---

## Assignment 6 — Conditions: Even or Odd

Write a script `06-even-odd.sh` that:

1. Accepts a number as a command line argument
2. Checks if the number is even or odd using the modulo operator
3. Prints the result

Run as: `sh 06-even-odd.sh 11`

**Expected output:**
```
11 is odd
```

---

## Assignment 7 — Conditions: Prime Number or Not

Write a script `07-prime.sh` that:

1. Accepts a number as a command line argument
2. Validates that the argument is provided — exit with an error if missing
3. Checks whether the number is a **prime number** or not
4. Prints the result

A prime number is a number greater than 1 that has no divisors other than 1 and itself.

Run as: `sh 07-prime.sh 17`

**Expected output:**
```
17 is a prime number
```

```
sh 07-prime.sh 12
12 is not a prime number
```

---

## Assignment 8 — Conditions: Day Check

Write a script `08-day-check.sh` that:

1. Gets today's day automatically
2. If it is **Saturday or Sunday**, print `Weekend! Enjoy your holiday.`
3. If it is **Monday**, print `Start of the week. Let's go!`
4. For any other day, print `Weekday. Go to school/work.`

---

## Assignment 9 — Conditions: Package Installer

Write a script `09-install.sh` that:

1. Checks if the script is run as **root** — if not, print an error and exit with code `1`
2. Accepts a package name as argument (e.g., `nginx`)
3. Checks if the package is **already installed** — if yes, print `nginx is already installed` and exit
4. If not installed, installs it using `dnf install -y`
5. Checks the exit status after install — prints `nginx installed successfully` or `nginx installation failed`

Run as: `sudo sh 09-install.sh nginx`

---

## Assignment 10 — Functions

Write a script `10-functions.sh` that defines the following functions:

1. `print_header` — prints a separator line and a heading passed as argument
2. `check_status` — accepts an exit code and a message; prints `SUCCESS: <message>` or `FAILURE: <message>`
3. `install_package` — accepts a package name; checks if installed, installs if not, uses `check_status` to report

Call `install_package` for: `git`, `wget`, `curl`

**Expected output:**
```
==========================================
Installing packages
==========================================
git is already installed
SUCCESS: wget installed
FAILURE: curl installation failed
```

---

## Assignment 11 — Redirections & Logging

Write a script `11-log.sh` that:

1. Creates a log file at `/tmp/script.log`
2. Redirects all **success output** to the log file
3. Redirects all **error output** to `/tmp/script-errors.log`
4. Runs three commands: `ls /tmp`, `ls /fakedir`, `date`
5. At the end, prints the contents of both log files

---

## Assignment 12 — Putting It All Together

Write a script `12-system-info.sh` that:

1. Accepts one argument: a **server name** (label only)
2. Validates that the argument is provided — exit with error if missing
3. Defines a function `section` that prints a heading separator
4. Collects and prints:
   - Script start time and PID
   - Server label (from argument)
   - Current user and home directory
   - OS information (`cat /etc/os-release | grep PRETTY`)
   - Disk usage (`df -h /`)
   - Memory usage (`free -h`)
   - Uptime
5. Logs everything to `/tmp/system-info.log`
6. Prints total script execution time at the end

**Expected output (abbreviated):**
```
========================================
System Info Report — webserver-01
========================================
Script PID    : 9821
Started at    : 2026-05-23 10:30:00
User          : ec2-user
OS            : Red Hat Enterprise Linux 9.x
Disk (/)      : 15G used of 50G
Memory        : 2.1G used of 4.0G
Uptime        : up 3 days, 4:12
========================================
Script completed in 2 seconds
```

---
