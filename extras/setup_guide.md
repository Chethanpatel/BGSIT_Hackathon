# 🛠️ BGSIT Hackathon - Complete Setup Guide

## 📋 Table of Contents
1. [WSL Installation and Setup](#wsl-installation-and-setup)
2. [Git Installation and Configuration](#git-installation-and-configuration)
3. [Python and Jupyter Setup](#python-and-jupyter-setup)
4. [Repository Fork and Clone](#repository-fork-and-clone)
5. [Troubleshooting](#troubleshooting)

---

## 🐧 WSL Installation and Setup

### What is WSL?
Windows Subsystem for Linux (WSL) allows you to run a Linux environment directly on Windows without the overhead of a traditional virtual machine.

### Step 1: Enable WSL Feature

1. **Open PowerShell as Administrator**
   - Press `Win + X` and select "Windows PowerShell (Admin)" or "Terminal (Admin)"

2. **Run the following command:**
   ```powershell
   wsl --install
   ```

3. **If the above doesn't work, try manual installation:**
   ```powershell
   dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
   dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
   ```

4. **Restart your computer**

### Step 2: Install Ubuntu 22.04 LTS

1. **Open Microsoft Store**
2. **Search for "Ubuntu 22.04.3 LTS"**
3. **Click "Install"**
4. **Wait for installation to complete**

### Step 3: Initial Ubuntu Setup

1. **Launch Ubuntu from Start Menu**
2. **Create a username and password when prompted**
   ```bash
   # You'll see something like this:
   Installing, this may take a few minutes...
   Please create a default UNIX user account. The username does not need to match your Windows username.
   For more information visit: https://aka.ms/wslusers
   Enter new UNIX username: your_username
   New password: 
   Retype new password:
   ```

3. **Update the system:**
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```

### Step 4: WSL Configuration

1. **Set WSL 2 as default (if not already):**
   ```powershell
   # Run this in PowerShell (as Admin)
   wsl --set-default-version 2
   ```

2. **Verify WSL installation:**
   ```bash
   # In Ubuntu terminal
   lsb_release -a
   ```

---

## 🔧 Git Installation and Configuration

### Step 1: Install Git in WSL

```bash
# Update package list
sudo apt update

# Install Git
sudo apt install git -y

# Verify installation
git --version
```

### Step 2: Configure Git

```bash
# Set your name (use your real name)
git config --global user.name "Your Full Name"

# Set your email (use your GitHub email)
git config --global user.email "your.email@example.com"

# Set default branch name
git config --global init.defaultBranch main

# Verify configuration
git config --list
```

### Step 3: Generate SSH Key (Optional but Recommended)

```bash
# Generate SSH key
ssh-keygen -t ed25519 -C "your.email@example.com"

# Press Enter to accept default file location
# Enter a passphrase (optional)

# Start SSH agent
eval "$(ssh-agent -s)"

# Add SSH key to agent
ssh-add ~/.ssh/id_ed25519

# Display public key to copy
cat ~/.ssh/id_ed25519.pub
```

### Step 4: Add SSH Key to GitHub

1. **Copy the SSH key output from the previous step**
2. **Go to GitHub.com → Settings → SSH and GPG keys**
3. **Click "New SSH key"**
4. **Paste your public key and save**

---

## 🐍 Python and Jupyter Setup

### Step 1: Install Python

```bash
# Install Python 3 and pip
sudo apt install python3 python3-pip -y

# Install python-venv for virtual environments
sudo apt install python3-venv -y

# Verify installation
python3 --version
pip3 --version
```

### Step 2: Create Virtual Environment

```bash
# Navigate to your project directory
cd ~

# Create virtual environment
python3 -m venv hackathon_env

# Activate virtual environment
source hackathon_env/bin/activate

# Your prompt should now show (hackathon_env)
```

### Step 3: Install Required Packages

```bash
# Make sure virtual environment is activated
source hackathon_env/bin/activate

# Install essential packages
pip install --upgrade pip
pip install jupyter pandas numpy matplotlib seaborn scikit-learn

# Install additional ML libraries
pip install xgboost lightgbm plotly

# Install other useful packages
pip install ipykernel ipywidgets

# Verify Jupyter installation
jupyter --version
```

### Step 4: Configure Jupyter

```bash
# Add virtual environment to Jupyter
python -m ipykernel install --user --name=hackathon_env --display-name="Python (Hackathon)"

# Generate Jupyter config (optional)
jupyter notebook --generate-config
```

---

## 🍴 Repository Fork and Clone

### Step 1: Fork the Repository

1. **Go to the main repository:**
   ```
   https://github.com/Chethanpatel/BGSIT_Hackathon
   ```

2. **Click the "Fork" button** in the top-right corner

3. **Select your GitHub account** as the destination

4. **Wait for the fork to complete**

### Step 2: Clone Your Fork

```bash
# Navigate to your desired directory
cd ~

# Clone your forked repository (replace YOUR_USERNAME)
git clone https://github.com/YOUR_USERNAME/BGSIT_Hackathon.git

# Navigate into the repository
cd BGSIT_Hackathon

# Verify the clone
ls -la
```

### Step 3: Set Up Remote Upstream

```bash
# Add the original repository as upstream
git remote add upstream https://github.com/Chethanpatel/BGSIT_Hackathon.git

# Verify remotes
git remote -v
```

### Step 4: Start Working

```bash
# Activate your virtual environment
source ~/hackathon_env/bin/activate

# Start Jupyter Notebook
jupyter notebook

# Your browser should open with Jupyter interface
```

---

## 🔍 Troubleshooting

### Common WSL Issues

**Issue: WSL command not found**
```powershell
# Enable WSL feature manually
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

**Issue: Ubuntu won't start**
```powershell
# Reset WSL
wsl --shutdown
wsl --unregister Ubuntu-22.04
# Reinstall Ubuntu from Microsoft Store
```

**Issue: File permission problems**
```bash
# Fix file permissions
sudo chown -R $USER:$USER /path/to/your/files
```

### Common Git Issues

**Issue: Permission denied (publickey)**
```bash
# Check SSH connection
ssh -T git@github.com

# If fails, add SSH key to agent
ssh-add ~/.ssh/id_ed25519
```

**Issue: Git credentials**
```bash
# Cache credentials for HTTPS
git config --global credential.helper cache

# Or use SSH instead of HTTPS
git remote set-url origin git@github.com:YOUR_USERNAME/BGSIT_Hackathon.git
```

### Common Python Issues

**Issue: pip install fails**
```bash
# Update pip
python -m pip install --upgrade pip

# Install with user flag
pip install --user package_name
```

**Issue: Jupyter not starting**
```bash
# Check if installed in virtual environment
which jupyter

# Reinstall if needed
pip install --force-reinstall jupyter
```

**Issue: Module not found in Jupyter**
```bash
# Make sure you're using the correct kernel
# In Jupyter: Kernel → Change Kernel → Python (Hackathon)

# Or reinstall kernel
python -m ipykernel install --user --name=hackathon_env --display-name="Python (Hackathon)"
```

---

## 📺 Video Tutorials

### WSL Installation
- [Microsoft Official WSL Guide](https://docs.microsoft.com/en-us/windows/wsl/install)
- [WSL 2 Installation Tutorial](https://www.youtube.com/results?search_query=wsl+2+installation+windows+11)

### Git Setup
- [Git Basics Tutorial](https://www.youtube.com/results?search_query=git+tutorial+for+beginners)
- [GitHub SSH Setup](https://www.youtube.com/results?search_query=github+ssh+key+setup)

### Python & Jupyter
- [Python Virtual Environment](https://www.youtube.com/results?search_query=python+virtual+environment+tutorial)
- [Jupyter Notebook Basics](https://www.youtube.com/results?search_query=jupyter+notebook+tutorial)

---

## ✅ Quick Verification Checklist

Before the hackathon, make sure you can:

- [ ] Open WSL Ubuntu terminal
- [ ] Run `git --version` successfully
- [ ] Run `python3 --version` successfully
- [ ] Activate virtual environment
- [ ] Start Jupyter Notebook
- [ ] Access your forked repository
- [ ] Create and run a simple Python cell in Jupyter

---

## 🆘 Getting Help

If you encounter issues:

1. **Search for error messages** online
2. **Check Stack Overflow** for similar problems
3. **Ask on GitHub Discussions** in your forked repository
4. **Contact the organizing team** for hackathon-specific issues

---

## 🎯 You're Ready!

Once you've completed this setup, you should have:
- ✅ WSL with Ubuntu 22.04 LTS running
- ✅ Git installed and configured
- ✅ Python environment set up
- ✅ Jupyter Notebook working
- ✅ Your forked repository cloned and ready

**Good luck with the BGSIT Hackathon! 🚀**

---

*Last Updated: October 24, 2025*
*For BGSIT CodeFest Machine Learning Challenge 2025*