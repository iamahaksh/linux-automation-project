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

```bash
#!/bin/bash

echo "Starting Automation..."

# Create user
sudo useradd testuser
echo "User created"

# Delete old files
find /tmp -type f -mtime +7 -delete
echo "Old files deleted"

# Check disk usage
df -h

echo "Task Completed"
```

---

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


