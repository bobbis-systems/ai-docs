# Complete Setup Guide from Scratch

This guide documents the exact process used to set up the AI documentation repository development environment from zero. Follow this guide to recreate the same setup process.

## 🎯 Overview

This guide will walk you through setting up a complete development environment for the AI documentation repository, including all tools, configurations, and folder structures needed.

## 📋 Prerequisites

### System Requirements
- **Operating System**: Windows 10/11
- **RAM**: Minimum 8GB, recommended 16GB+
- **Storage**: At least 5GB free space
- **Internet**: Stable connection for downloads and Git operations
- **Administrator Access**: Required for some installations

### Accounts Needed
- **GitHub Account**: For repository hosting and collaboration
- **Cursor Account**: For AI-powered code editing
- **Email Account**: For GitHub verification

## 🚀 Step-by-Step Setup Process

### Step 1: Install Git

**Download Git:**
1. Open browser and go to [git-scm.com](https://git-scm.com/download/win)
2. Click "Click here to download" for Windows
3. Save the installer to Downloads folder

**Install Git:**
1. Navigate to Downloads folder
2. Right-click on Git installer and "Run as administrator"
3. Click "Next" through all prompts with default settings
4. Click "Install"
5. Click "Finish" when complete

**Verify Git Installation:**
```powershell
# Open PowerShell as Administrator
# Press Win + X, then "Windows PowerShell (Admin)"

# Check Git version
git --version
# Expected output: git version 2.x.x.windows.x
```

**Configure Git:**
```powershell
# Set your identity
git config --global user.name "Your Full Name"
git config --global user.email "your.email@example.com"

# Set default branch name
git config --global init.defaultBranch main

# Configure line endings for Windows
git config --global core.autocrlf true

# Verify configuration
git config --list
```

### Step 2: GitHub Account Setup

**Create GitHub Account:**
1. Go to [github.com](https://github.com)
2. Click "Sign up"
3. Enter your email, create password, and username
4. Complete the verification process
5. Verify your email address

**Logout of Existing Accounts (if any):**
```powershell
# Check if GitHub CLI is installed
gh --version

# If installed, logout first
gh auth logout

# Clear Windows Credential Manager for GitHub
# Press Win + R, type "control keymgr.dll"
# Look for any GitHub entries and remove them
```

**Install GitHub CLI:**
```powershell
# Install using winget (Windows Package Manager)
winget install GitHub.cli

# Or download manually from: https://cli.github.com/
# Download the Windows installer and run as administrator

# Verify installation
gh --version
```

**Authenticate with GitHub:**
```powershell
# Login to GitHub
gh auth login

# Follow these exact prompts:
# 1. What account do you want to log into? → GitHub.com
# 2. What is your preferred protocol for Git operations? → HTTPS
# 3. Authenticate Git with your GitHub credentials? → Yes
# 4. How would you like to authenticate GitHub CLI? → Login with a web browser
# 5. Copy the one-time code shown
# 6. Open browser and paste the code
# 7. Authorize GitHub CLI

# Verify authentication
gh auth status
```

### Step 3: Create Development Folder Structure

**Create Base Directory Structure:**
```powershell
# Create the main development folder
mkdir C:\Git
cd C:\Git

# Create organization folder
mkdir bobbis-systems
cd bobbis-systems

# Create project folder
mkdir ai-docs
cd ai-docs

# Verify current location
pwd
# Should show: C:\Git\bobbis-systems\ai-docs
```

**Verify Folder Structure:**
```powershell
# Check the complete structure
tree C:\Git /F
# Should show:
# C:\GIT
# └───bobbis-systems
#     └───ai-docs
```

### Step 4: Initialize Git Repository

**Create Local Repository:**
```powershell
# Initialize git repository
git init

# Create initial README file
@"
# AI Documentation Repository

Welcome to the comprehensive documentation repository for AI assistance tools and technologies.

## Getting Started

This repository contains documentation for various AI tools and frameworks used in development workflows.

## Structure

- `cursor/` - Cursor editor documentation
- `copilot/` - GitHub Copilot documentation (planned)
- `chatgpt/` - ChatGPT/Claude documentation (planned)
- `frameworks/` - AI framework documentation (planned)

## Contributing

Please read our contributing guidelines before submitting changes.
"@ | Out-File -FilePath "README.md" -Encoding UTF8

# Add and commit initial file
git add README.md
git commit -m "Initial commit: Add README"
```

**Create GitHub Repository:**
```powershell
# Create repository on GitHub
gh repo create ai-docs --public --description "AI assistance tools and technologies documentation"

# Add remote origin
git remote add origin https://github.com/bobbis-systems/ai-docs.git

# Push to GitHub
git branch -M main
git push -u origin main

# Verify remote
git remote -v
```

### Step 5: Install Cursor Editor

**Download Cursor:**
1. Go to [cursor.sh](https://cursor.sh)
2. Click "Download for Windows"
3. Save the installer to Downloads folder

**Install Cursor:**
1. Navigate to Downloads folder
2. Right-click on Cursor installer and "Run as administrator"
3. Follow the installation wizard
4. Click "Finish" when complete

**First Launch Setup:**
1. Open Cursor from Start Menu
2. Click "Sign in" or create a new account
3. Complete the sign-in process
4. Install recommended extensions when prompted
5. Configure your preferences

**Verify Cursor Installation:**
```powershell
# Check if Cursor is in PATH
cursor --version

# If not in PATH, add it manually:
# 1. Find Cursor installation path (usually C:\Users\[Username]\AppData\Local\Programs\cursor\Cursor.exe)
# 2. Add to PATH environment variable
```

**Open Project in Cursor:**
```powershell
# Navigate to your project
cd C:\Git\bobbis-systems\ai-docs

# Open in Cursor
cursor .

# Or open Cursor and use File → Open Folder
```



### Step 6: Install Essential Extensions

**Open Cursor and Install Extensions:**

1. **Git & GitHub Extensions:**
   - GitLens (by Eric Amodio)
   - GitHub Pull Requests and Issues (by GitHub)

2. **Code Quality Extensions:**
   - Prettier - Code formatter (by Prettier)
   - ESLint (by Microsoft)
   - Auto Rename Tag (by Jun Han)

3. **AI & Productivity Extensions:**
   - GitHub Copilot (if you have access)
   - Tabnine (by Tabnine)
   - IntelliCode (by Microsoft)

4. **Language Support:**
   - Python (by Microsoft)
   - JavaScript and TypeScript (built-in)
   - Go (by Google)
   - Rust (by rust-lang)

**Install Extensions via Command Line:**
```powershell
# If you prefer command line installation
cursor --install-extension ms-vscode.vscode-json-language-features
cursor --install-extension ms-vscode.vscode-typescript-next
cursor --install-extension eamodio.gitlens
cursor --install-extension GitHub.vscode-pull-request-github
cursor --install-extension esbenp.prettier-vscode
cursor --install-extension ms-vscode.vscode-eslint
cursor --install-extension formulahendry.auto-rename-tag
```

### Step 7: Configure Development Environment

**Create Workspace Settings:**
```powershell
# Create .vscode folder
mkdir .vscode

# Create settings.json
@"
{
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "files.autoSave": "afterDelay",
  "files.autoSaveDelay": 1000,
  "git.autofetch": true,
  "git.confirmSync": false,
  "editor.tabSize": 2,
  "editor.insertSpaces": true,
  "editor.detectIndentation": true,
  "editor.wordWrap": "on",
  "workbench.colorTheme": "Default Dark+",
  "workbench.iconTheme": "vs-seti"
}
"@ | Out-File -FilePath ".vscode\settings.json" -Encoding UTF8
```

**Create .gitignore:**
```powershell
@"
# Dependencies
node_modules/
npm-debug.log*
yarn-debug.log*
yarn-error.log*

# Build outputs
dist/
build/
*.tsbuildinfo

# Environment variables
.env
.env.local
.env.development.local
.env.test.local
.env.production.local

# IDE files
.vscode/settings.json
.idea/
*.swp
*.swo

# OS files
.DS_Store
Thumbs.db

# Logs
logs
*.log

# Runtime data
pids
*.pid
*.seed
*.pid.lock

# Coverage directory used by tools like istanbul
coverage/

# nyc test coverage
.nyc_output

# Dependency directories
jspm_packages/

# Optional npm cache directory
.npm

# Optional REPL history
.node_repl_history

# Output of 'npm pack'
*.tgz

# Yarn Integrity file
.yarn-integrity

# dotenv environment variables file
.env
"@ | Out-File -FilePath ".gitignore" -Encoding UTF8
```

**Create Launch Configuration:**
```powershell
# Create launch.json for debugging
@"
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Launch Program",
      "type": "node",
      "request": "launch",
      "program": "\${workspaceFolder}/index.js",
      "skipFiles": [
        "<node_internals>/**"
      ]
    }
  ]
}
"@ | Out-File -FilePath ".vscode\launch.json" -Encoding UTF8
```

### Step 8: Verify Complete Setup

**Test All Components:**
```powershell
# Test Git
git --version
git status

# Test GitHub CLI
gh --version
gh auth status

# Test Cursor
cursor --version



# Test repository access
gh repo view

# Test workspace
pwd
# Should show: C:\Git\bobbis-systems\ai-docs
```

**Verify Repository Structure:**
```powershell
# Check current structure
tree /F

# Should show:
# .
# ├── .git/
# ├── .gitignore
# ├── .vscode/
# │   ├── launch.json
# │   └── settings.json
# └── README.md
```

### Step 9: Initial Commit and Push

**Commit All Changes:**
```powershell
# Add all files
git add .

# Commit with descriptive message
git commit -m "Complete initial setup: Add workspace configuration and documentation structure"

# Push to GitHub
git push origin main

# Verify on GitHub
gh repo view --web
```

## 🎯 Quick Reference Commands

### Daily Workflow Commands
```powershell
# Open project in Cursor
cd C:\Git\bobbis-systems\ai-docs
cursor .

# Check status
git status

# Make changes and commit
git add .
git commit -m "Update documentation"
git push

# Create new documentation section
mkdir new-tool-name
# Add files...
git add .
git commit -m "Add new tool documentation"
git push
```

### Troubleshooting Commands
```powershell
# Reset Git credentials
git config --global --unset credential.helper
gh auth logout
gh auth login

# Reinstall GitHub CLI
winget uninstall GitHub.cli
winget install GitHub.cli

# Check PATH
echo $env:PATH

# Verify all installations
git --version
gh --version
cursor --version
```

## 🔧 Troubleshooting Common Issues

### Git Authentication Problems
```powershell
# Clear existing credentials
git config --global --unset credential.helper

# Clear Windows Credential Manager
# Press Win + R, type "control keymgr.dll"
# Remove any GitHub entries

# Re-authenticate
gh auth logout
gh auth login
```

### Cursor Not Opening
```powershell
# Check if Cursor is in PATH
where cursor

# If not found, add to PATH manually:
# 1. Find Cursor installation: C:\Users\[Username]\AppData\Local\Programs\cursor\
# 2. Add to PATH environment variable
# 3. Restart PowerShell

# Or run directly:
& "C:\Users\$env:USERNAME\AppData\Local\Programs\cursor\Cursor.exe" .
```

### Permission Issues
```powershell
# Run PowerShell as Administrator
# Press Win + X, then "Windows PowerShell (Admin)"

# Check folder permissions
icacls C:\Git

# Grant full control if needed
icacls C:\Git /grant "$env:USERNAME:(OI)(CI)F"
```

### GitHub CLI Issues
```powershell
# Reinstall GitHub CLI
winget uninstall GitHub.cli
winget install GitHub.cli

# Clear cache
gh auth logout
gh auth login

# Check authentication
gh auth status
```

## 📋 Final Verification Checklist

- [ ] Git installed and configured
- [ ] GitHub account created and verified
- [ ] GitHub CLI installed and authenticated
- [ ] Cursor installed and configured

- [ ] Essential extensions installed
- [ ] Development folder structure created
- [ ] Git repository initialized and pushed to GitHub
- [ ] Workspace settings configured
- [ ] All tools working correctly

## 🎉 Setup Complete!

Your development environment is now ready for creating and maintaining AI documentation. You can:

1. **Start Documenting**: Begin adding documentation for AI tools
2. **Collaborate**: Share the repository with team members
3. **Expand**: Add more tools and frameworks to the documentation
4. **Maintain**: Keep the documentation up-to-date as tools evolve

---

*This setup guide documents the exact process used to create this development environment. Follow these steps to recreate the same setup on any Windows machine.* 