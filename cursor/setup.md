# Cursor Setup Guide

This guide will walk you through the complete setup process for Cursor, from installation to advanced configuration.

## 📋 Prerequisites

### System Requirements
- **Operating System**: Windows 10+, macOS 10.15+, or Linux
- **RAM**: Minimum 8GB, recommended 16GB+
- **Storage**: At least 2GB free space
- **Internet**: Stable connection for AI features
- **Git**: For version control integration

### Required Accounts
- **Cursor Account**: Free account at [cursor.sh](https://cursor.sh)
- **GitHub Account**: For Git integration (optional but recommended)
- **API Keys**: For advanced AI features (optional)

## 🚀 Installation

### Step 1: Download Cursor

1. **Visit the Official Site**: Go to [cursor.sh](https://cursor.sh)
2. **Choose Your Platform**: Click the download button for your OS
3. **Download**: Wait for the installer to download

### Step 2: Install Cursor

#### Windows
```powershell
# Download and run the installer
# Follow the installation wizard
# Cursor will be installed to Program Files
```

#### macOS
```bash
# Download the .dmg file
# Drag Cursor to Applications folder
# First launch may require security approval
```

#### Linux
```bash
# Download the .AppImage or .deb file
# For AppImage:
chmod +x cursor.AppImage
./cursor.AppImage

# For .deb:
sudo dpkg -i cursor.deb
sudo apt-get install -f  # Fix dependencies if needed
```

### Step 3: First Launch

1. **Open Cursor**: Launch the application
2. **Sign In**: Use your Cursor account credentials
3. **Welcome Screen**: Complete the initial setup wizard
4. **Extensions**: Install recommended extensions

## ⚙️ Configuration

### Essential Settings

Open Settings (`Ctrl/Cmd + ,`) and configure these essential options:

```json
{
  "editor.fontSize": 14,
  "editor.fontFamily": "'JetBrains Mono', 'Fira Code', Consolas, monospace",
  "editor.tabSize": 2,
  "editor.insertSpaces": true,
  "editor.detectIndentation": true,
  "editor.wordWrap": "on",
  "editor.minimap.enabled": true,
  "editor.suggestSelection": "first",
  "editor.acceptSuggestionOnCommitCharacter": false,
  "editor.acceptSuggestionOnEnter": "on",
  "editor.quickSuggestions": {
    "other": true,
    "comments": true,
    "strings": true
  },
  "files.autoSave": "afterDelay",
  "files.autoSaveDelay": 1000,
  "workbench.colorTheme": "Default Dark+",
  "workbench.iconTheme": "vs-seti"
}
```

### AI Configuration

#### Basic AI Settings
```json
{
  "cursor.ai.enabled": true,
  "cursor.ai.model": "gpt-4",
  "cursor.ai.maxTokens": 2048,
  "cursor.ai.temperature": 0.7,
  "cursor.ai.contextWindow": 8000
}
```

#### Advanced AI Settings
```json
{
  "cursor.ai.autoComplete": true,
  "cursor.ai.autoCompleteDelay": 100,
  "cursor.ai.chatHistory": true,
  "cursor.ai.codeActions": true,
  "cursor.ai.explanations": true,
  "cursor.ai.refactoring": true
}
```

### Git Configuration

```json
{
  "git.enabled": true,
  "git.autofetch": true,
  "git.confirmSync": false,
  "git.enableSmartCommit": true,
  "git.autofetchPeriod": 180,
  "git.autoStash": true
}
```

## 🔧 Extension Setup

### Essential Extensions

Install these recommended extensions for the best experience:

#### Language Support
- **JavaScript/TypeScript**: Built-in
- **Python**: Python extension
- **Go**: Go extension
- **Rust**: rust-analyzer
- **Java**: Extension Pack for Java

#### Development Tools
- **GitLens**: Enhanced Git capabilities
- **Prettier**: Code formatting
- **ESLint**: JavaScript linting
- **Auto Rename Tag**: HTML/XML tag renaming
- **Bracket Pair Colorizer**: Visual bracket matching

#### AI Enhancements
- **GitHub Copilot**: Additional AI assistance
- **Tabnine**: Alternative AI completion
- **Kite**: Python AI completion

### Extension Configuration

```json
{
  "prettier.singleQuote": true,
  "prettier.tabWidth": 2,
  "prettier.semi": true,
  "eslint.autoFixOnSave": true,
  "gitlens.codeLens.enabled": true,
  "gitlens.currentLine.enabled": true
}
```

## 🔑 API Keys Setup

### OpenAI API Key (Optional)

For enhanced AI features, you can configure your own OpenAI API key:

1. **Get API Key**: Visit [OpenAI Platform](https://platform.openai.com/api-keys)
2. **Create Key**: Generate a new API key
3. **Configure in Cursor**: 
   - Open Settings
   - Search for "OpenAI"
   - Enter your API key

### GitHub Copilot (Optional)

1. **Install Copilot**: Install GitHub Copilot extension
2. **Sign In**: Authenticate with GitHub
3. **Enable**: Activate Copilot in your account

## 🎨 Theme and Appearance

### Recommended Themes
- **Dark Themes**: One Dark Pro, Dracula, Material Theme
- **Light Themes**: GitHub Light, Solarized Light
- **High Contrast**: High Contrast themes for accessibility

### Font Configuration
```json
{
  "editor.fontFamily": "'JetBrains Mono', 'Fira Code', Consolas, monospace",
  "editor.fontSize": 14,
  "editor.fontLigatures": true,
  "editor.fontWeight": "normal"
}
```

## 🔍 Troubleshooting

### Common Issues

#### AI Features Not Working
1. **Check Internet**: Ensure stable internet connection
2. **Verify Account**: Make sure you're signed in to Cursor
3. **Check API Keys**: Verify OpenAI API key if using custom key
4. **Restart Cursor**: Close and reopen the application

#### Performance Issues
1. **Close Unused Tabs**: Too many open files can slow down performance
2. **Disable Heavy Extensions**: Some extensions can impact performance
3. **Check System Resources**: Ensure adequate RAM and CPU
4. **Update Cursor**: Keep to the latest version

#### Git Integration Problems
1. **Verify Git Installation**: Ensure Git is installed and in PATH
2. **Check Repository**: Make sure you're in a Git repository
3. **Configure Git**: Set up user name and email
4. **Check Permissions**: Ensure proper file permissions

### Performance Optimization

#### Memory Usage
```json
{
  "files.watcherExclude": {
    "**/node_modules/**": true,
    "**/dist/**": true,
    "**/build/**": true
  },
  "search.exclude": {
    "**/node_modules": true,
    "**/bower_components": true,
    "**/*.code-search": true
  }
}
```

#### Editor Performance
```json
{
  "editor.renderWhitespace": "none",
  "editor.renderControlCharacters": false,
  "editor.renderLineHighlight": "line",
  "editor.minimap.enabled": false
}
```

## ✅ Verification

After setup, verify everything is working:

1. **AI Chat**: Press `Ctrl/Cmd + K` and ask a question
2. **Code Completion**: Start typing in a supported language
3. **Git Integration**: Check Git panel for repository info
4. **Extensions**: Verify all extensions are loaded
5. **Settings**: Confirm all settings are applied

## 📚 Next Steps

After completing setup:

1. **Read the Workflows Guide**: Learn best practices for using Cursor
2. **Explore Tips & Tricks**: Discover advanced features
3. **Join the Community**: Connect with other Cursor users
4. **Customize Further**: Adjust settings to match your preferences

---

*For additional help, check the [Cursor Documentation](https://cursor.sh/docs) or join the [Cursor Discord](https://discord.gg/cursor).* 