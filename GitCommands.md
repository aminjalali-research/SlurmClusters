# Uploading a VS Code Project to GitHub

This guide walks you through the **complete steps** to upload a local VS Code project to GitHub, including best practices.

```
 your-project/
│
├── src/                   # Source code files
│   └── main.py
│
├── data/                  # Datasets (excluded via .gitignore)
│   └── raw/
│
├── results/               # Output results, logs, plots, etc.
│   └── output.txt
│
├── .gitignore             # Ignore rules
├── README.md              # Project overview
├── requirements.txt       # Python dependencies
└── LICENSE                # License info (optional)
```


---
- Install Git from **git-scm.com**. For example for Ubuntu: # sudo apt-get install git
- Verify: Run **git --version** in the VS Code terminal.

## Step 1: Configure Git (One-Time Setup)
This sets your identity globally:
```bash
git config --global user.name "Your Name"
git config --global user.email "youremail@example.com"
git config --global --list  # Check your configuration

```

## Step 2: Open VS Code Terminal and Initialize Git in your Project
Open terminal (Ctrl + backtick)
```bash
git init
git add .
git commit -m "Initial commit"
```

## Step 3: Create a GitHub Repository
Go to https://github.com and click New repository
Set Repository name
Visibility (Public or Private)
❌ DO NOT initialize with README, .gitignore, or license
Click Create repository
You’ll receive a repository URL like:
```bash
https://github.com/yourusername/your-repo-name.git
```

## Step 4: Link Local Repo to GitHub
```bash
git remote add origin https://github.com/yourusername/your-repo-name.git
git branch -M main  # Ensures default branch is 'main'
```

## Step 5: Push Code to GitHub
```bash
git push -u origin main
```

## Best Practices for Future Updates
```bash
git status

git add .
git commit -m "Descriptive commit message"
git push
git pull origin main  # Pull updates from GitHub:
```










