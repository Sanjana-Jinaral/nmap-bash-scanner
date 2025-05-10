# Automated Network Reconnaissance using Nmap and Bash

## Introduction

This guide walks you through creating a simple, automated network reconnaissance tool using **Nmap** and **Bash scripting** on Linux. The goal is to help beginners learn how to perform basic network scans automatically and save results for review.

This step-by-step tutorial is ideal for live demos, presentations, or participation in cybersecurity hackathons.

---

## Prerequisites

Make sure you have:

- A Linux environment (e.g., Ubuntu, Debian, Kali Linux, or Windows Subsystem for Linux)
- An active internet connection
- Basic familiarity with terminal commands and Git

---

## Step 1: Install Required Tools

### 1.1 Install Nmap

Nmap is the network scanning tool.

Open your terminal and run:

```bash
sudo apt update
sudo apt install -y nmap

### Folder Structure

```
nmap-bash-scanner/
├── README.md
├── scan.sh
├── results/
│   └── [targetname]_scan.txt
└── LICENSE
```

## How It Works

1. User runs `scan.sh` and inputs a target IP or domain.
2. The script performs the following:
   - Ping scan to check if the host is up.
   - Port scan to find open ports.
   - OS detection and service version detection.
3. All outputs are saved in a text file inside the `results/` folder.

## Sample Bash Script (scan.sh)

```bash
#!/bin/bash

echo "Welcome to Simple Nmap Bash Scanner"

read -p "Enter the target IP or domain: " target

filename="results/${target}_scan.txt"

mkdir -p results

echo "Scanning host: $target"
echo "Results will be saved in $filename"

# Ping Scan
echo "Running Ping Scan..." | tee -a $filename
nmap -sn $target | tee -a $filename

# Port Scan
echo -e "\nRunning Port Scan..." | tee -a $filename
nmap -p- $target | tee -a $filename

# OS Detection
echo -e "\nRunning OS Detection and Service Version Scan..." | tee -a $filename
nmap -A $target | tee -a $filename

echo -e "\nScan completed. Check the file: $filename"
```

## Project Milestones

- [x] Setup Nmap and Bash environment
- [x] Write the core script (`scan.sh`)
- [x] Test on multiple IPs/domains
- [x] Upload to GitHub with README
- [ ] Add advanced features (like HTML reports or email alerts) – Optional

## GitHub Submission Guidelines

To submit your project to GitHub, follow these steps:

### Step 1: Create a GitHub Account
If you don’t have a GitHub account, go to [GitHub](https://github.com/) and sign up for a free account.

### Step 2: Install Git
Make sure you have Git installed on your machine. You can download it from [git-scm.com](https://git-scm.com/).

### Step 3: Create a New Repository
1. Log in to your GitHub account.
2. Click on the "+" icon in the top right corner and select "New repository."
3. Name your repository (e.g., `nmap-bash-scanner`).
4. Add a description (optional).
5. Choose "Public" for visibility.
6. Click "Create repository."

### Step 4: Clone the Repository
Open your terminal and run the following command to clone the repository to your local machine:

```bash
git clone https://github.com/yourusername/nmap-bash-scanner.git
```

Replace `yourusername` with your GitHub username.

### Step 5: Add Your Project Files
Navigate to the cloned repository folder:

```bash
cd nmap-bash-scanner
```

Copy your project files (`scan.sh`, `README.md`, `LICENSE`, etc.) into this folder.
