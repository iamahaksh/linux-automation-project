# linux-automation-project
Linux automation using Bash
Added automation script

# 🐧 Linux Automation Project

## 📌 Project Overview

This project demonstrates basic Linux automation using a Bash script.
The script performs common system administration tasks automatically.

---

## 🎯 Objective

Automate daily Linux tasks such as:

* User creation
* Deleting old files
* Checking disk usage

---

## 🛠️ Technologies Used

* Bash Scripting
* Linux Commands

---

## 📂 Project Structure

```
linux-automation-project/
│
├── automation.sh
└── README.md
```

---

## ⚙️ Step-by-Step Implementation

---

### 🔹 Step 1: Create Project Directory

```bash
mkdir myproject
cd myproject
```

---

### 🔹 Step 2: Create Script File

```bash
nano automation.sh
```

---

### 🔹 Step 3: Add Script Code

```
#!/bin/bash

# Log file
LOG_FILE="/var/log/automation.log"

echo "========== Automation Started ==========" | tee -a $LOG_FILE
DATE=$(date)
echo "Date: $DATE" | tee -a $LOG_FILE

# -------------------------------
# 1. Create User (Safe Way)
# -------------------------------

USERNAME="testuser"

if id "$USERNAME" &>/dev/null
then
    echo "User '$USERNAME' already exists" | tee -a $LOG_FILE
else
    sudo useradd "$USERNAME"
    if [ $? -eq 0 ]; then
        echo "User '$USERNAME' created successfully" | tee -a $LOG_FILE
    else
        echo "Failed to create user '$USERNAME'" | tee -a $LOG_FILE
    fi
fi

# -------------------------------
# 2. Delete Old Files
# -------------------------------

echo "Cleaning old files from /tmp..." | tee -a $LOG_FILE

DELETED_FILES=$(find /tmp -type f -mtime +7 2>/dev/null)

if [ -z "$DELETED_FILES" ]; then
    echo "No old files found" | tee -a $LOG_FILE
else
    find /tmp -type f -mtime +7 -delete
    echo "Old files deleted successfully" | tee -a $LOG_FILE
fi

# -------------------------------
# 3. Check Disk Usage
# -------------------------------

echo "Disk Usage:" | tee -a $LOG_FILE
df -h | tee -a $LOG_FILE

# -------------------------------
# 4. Memory Usage (NEW FEATURE)
# -------------------------------

echo "Memory Usage:" | tee -a $LOG_FILE
free -h | tee -a $LOG_FILE

# -------------------------------
# 5. System Uptime (NEW FEATURE)
# -------------------------------

echo "System Uptime:" | tee -a $LOG_FILE
uptime | tee -a $LOG_FILE

echo "========== Automation Completed ==========" | tee -a $LOG_FILE

### 🔹 Step 4: Give Permission

```bash
chmod +x automation.sh
```

---

### 🔹 Step 5: Run Script

```bash
./automation.sh
```

---

## ✅ Output

* User `testuser` will be created
* Old files in `/tmp` will be deleted
* Disk usage information will be displayed

---


