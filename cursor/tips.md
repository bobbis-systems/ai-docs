# Cursor Tips & Tricks

Master Cursor with these advanced techniques, keyboard shortcuts, and productivity hacks to supercharge your development workflow.

## ⌨️ Essential Keyboard Shortcuts

### AI Commands
| Shortcut | Action | Description |
|----------|--------|-------------|
| `Ctrl/Cmd + K` | Open AI Chat | Quick access to AI assistant |
| `Ctrl/Cmd + L` | AI Line Edit | Edit current line with AI |
| `Ctrl/Cmd + I` | AI Inline Edit | Inline AI code generation |
| `Ctrl/Cmd + Shift + L` | AI Selection Edit | Edit selected code with AI |
| `Ctrl/Cmd + Enter` | Accept AI Suggestion | Accept current AI suggestion |
| `Esc` | Cancel AI Suggestion | Cancel current AI operation |

### Navigation
| Shortcut | Action | Description |
|----------|--------|-------------|
| `Ctrl/Cmd + P` | Quick Open | Find and open files quickly |
| `Ctrl/Cmd + Shift + P` | Command Palette | Access all commands |
| `Ctrl/Cmd + Shift + O` | Go to Symbol | Navigate to functions/classes |
| `Ctrl/Cmd + G` | Go to Line | Jump to specific line number |
| `Ctrl/Cmd + T` | Go to Symbol in Workspace | Find symbols across workspace |
| `F12` | Go to Definition | Jump to function/class definition |
| `Alt + F12` | Peek Definition | Preview definition without leaving |

### Editing
| Shortcut | Action | Description |
|----------|--------|-------------|
| `Ctrl/Cmd + D` | Select Next Occurrence | Multi-cursor editing |
| `Ctrl/Cmd + Shift + L` | Select All Occurrences | Select all matches |
| `Alt + Click` | Add Cursor | Add cursor at click position |
| `Ctrl/Cmd + U` | Undo Last Cursor Operation | Undo multi-cursor action |
| `Ctrl/Cmd + /` | Toggle Comment | Comment/uncomment lines |
| `Alt + Shift + A` | Toggle Block Comment | Block comment selection |
| `Ctrl/Cmd + Shift + K` | Delete Line | Delete current line |
| `Alt + Up/Down` | Move Line | Move line up or down |

### Git Operations
| Shortcut | Action | Description |
|----------|--------|-------------|
| `Ctrl/Cmd + Shift + G` | Open Git Panel | Access Git operations |
| `Ctrl/Cmd + Enter` | Commit | Commit staged changes |
| `Ctrl/Cmd + Shift + Enter` | Commit All | Commit all changes |

## 🚀 Advanced AI Techniques

### 1. Context-Aware Prompts

#### Better Code Generation
```typescript
// Instead of: "Create a function"
// Use: "Create a TypeScript function that validates email addresses with proper error handling"

function validateEmail(email: string): { isValid: boolean; error?: string } {
  if (!email) {
    return { isValid: false, error: 'Email is required' };
  }
  
  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  const isValid = emailRegex.test(email);
  
  return {
    isValid,
    error: isValid ? undefined : 'Invalid email format'
  };
}
```

#### Smart Refactoring
```typescript
// Instead of: "Refactor this code"
// Use: "Refactor this code to use modern JavaScript features and improve performance"

// Before
function processUsers(users) {
  const result = [];
  for (let i = 0; i < users.length; i++) {
    if (users[i].active) {
      result.push({
        id: users[i].id,
        name: users[i].name.toUpperCase()
      });
    }
  }
  return result;
}

// After AI refactoring
const processUsers = (users: User[]): ProcessedUser[] =>
  users
    .filter(user => user.active)
    .map(user => ({
      id: user.id,
      name: user.name.toUpperCase()
    }));
```

### 2. AI Chat Strategies

#### Problem-Solving Workflow
1. **Describe the Problem**: "I'm getting a TypeScript error when trying to..."
2. **Show the Error**: Paste the error message
3. **Provide Context**: Include relevant code snippets
4. **Ask for Solution**: "How can I fix this?"

#### Code Review with AI
```typescript
// Ask AI: "Review this code for potential issues, security vulnerabilities, and performance improvements"

function processUserData(userData) {
  const result = {};
  for (const key in userData) {
    result[key] = userData[key];
  }
  return result;
}

// AI will suggest improvements like:
// - Use Object.assign() or spread operator
// - Add type safety with TypeScript
// - Consider edge cases (null/undefined)
// - Add input validation
```

### 3. Custom AI Prompts

#### Template Prompts
```typescript
// Function Documentation Template
"Add comprehensive JSDoc documentation to this function, including:
- Parameter descriptions with types
- Return value description
- Usage examples
- Edge cases and error handling"

// Test Generation Template
"Generate comprehensive unit tests for this function, including:
- Happy path scenarios
- Edge cases
- Error conditions
- Performance tests if applicable"

// Code Review Template
"Review this code for:
- Potential bugs
- Performance issues
- Security vulnerabilities
- Code style and best practices
- Maintainability concerns"
```

## 🎯 Productivity Hacks

### 1. Snippets and Templates

#### Custom Snippets
```json
{
  "React Component": {
    "prefix": "rfc",
    "body": [
      "import React from 'react';",
      "",
      "interface ${1:ComponentName}Props {",
      "  $2",
      "}",
      "",
      "const ${1:ComponentName}: React.FC<${1:ComponentName}Props> = ({ $3 }) => {",
      "  return (",
      "    <div>",
      "      $0",
      "    </div>",
      "  );",
      "};",
      "",
      "export default ${1:ComponentName};"
    ],
    "description": "Create a React functional component with TypeScript"
  }
}
```

#### AI-Generated Templates
```typescript
// Ask AI: "Create a template for a React component with TypeScript, styled-components, and proper error handling"

import React, { useState, useEffect } from 'react';
import styled from 'styled-components';

interface ComponentProps {
  title: string;
  onAction?: () => void;
}

const StyledComponent = styled.div`
  padding: 1rem;
  border: 1px solid #ccc;
  border-radius: 4px;
`;

const Component: React.FC<ComponentProps> = ({ title, onAction }) => {
  const [isLoading, setIsLoading] = useState(false);
  const [error, setError] = useState<string | null>(null);

  const handleAction = async () => {
    try {
      setIsLoading(true);
      setError(null);
      await onAction?.();
    } catch (err) {
      setError(err instanceof Error ? err.message : 'An error occurred');
    } finally {
      setIsLoading(false);
    }
  };

  return (
    <StyledComponent>
      <h2>{title}</h2>
      {error && <div style={{ color: 'red' }}>{error}</div>}
      <button onClick={handleAction} disabled={isLoading}>
        {isLoading ? 'Loading...' : 'Action'}
      </button>
    </StyledComponent>
  );
};

export default Component;
```

### 2. Multi-Cursor Magic

#### Simultaneous Editing
```typescript
// Select multiple lines and edit them simultaneously
const user1 = { name: 'John', age: 30 };
const user2 = { name: 'Jane', age: 25 };
const user3 = { name: 'Bob', age: 35 };

// Use Ctrl/Cmd + D to select each 'name' and change them all at once
const user1 = { firstName: 'John', age: 30 };
const user2 = { firstName: 'Jane', age: 25 };
const user3 = { firstName: 'Bob', age: 35 };
```

#### Column Selection
```typescript
// Hold Alt + Shift and drag to select columns
// Useful for editing aligned data

// Before
name: 'John',
age: 30,
email: 'john@example.com'

// After column selection and editing
firstName: 'John',
userAge: 30,
userEmail: 'john@example.com'
```

### 3. Advanced Search and Replace

#### Regex Replacements
```typescript
// Find: function (\w+)\(
// Replace: const $1 = (
// This converts function declarations to arrow functions

// Before
function processData(data) {
  return data.map(item => item.id);
}

// After
const processData = (data) => {
  return data.map(item => item.id);
};
```

#### Multi-file Refactoring
```typescript
// Use Ctrl/Cmd + Shift + H for find and replace across files
// Find: oldFunctionName
// Replace: newFunctionName
// Files to include: *.ts, *.tsx
```

## 🔧 Customization Tips

### 1. Settings Optimization

#### Performance Settings
```json
{
  "files.watcherExclude": {
    "**/node_modules/**": true,
    "**/dist/**": true,
    "**/build/**": true,
    "**/.git/**": true
  },
  "search.exclude": {
    "**/node_modules": true,
    "**/bower_components": true,
    "**/*.code-search": true
  },
  "editor.renderWhitespace": "none",
  "editor.renderControlCharacters": false,
  "editor.minimap.enabled": false
}
```

#### AI Settings
```json
{
  "cursor.ai.enabled": true,
  "cursor.ai.model": "gpt-4",
  "cursor.ai.maxTokens": 2048,
  "cursor.ai.temperature": 0.7,
  "cursor.ai.contextWindow": 8000,
  "cursor.ai.autoComplete": true,
  "cursor.ai.autoCompleteDelay": 100
}
```

### 2. Extension Recommendations

#### Essential Extensions
- **GitLens**: Enhanced Git capabilities
- **Prettier**: Code formatting
- **ESLint**: JavaScript linting
- **Auto Rename Tag**: HTML/XML tag renaming
- **Bracket Pair Colorizer**: Visual bracket matching
- **Path Intellisense**: File path autocomplete
- **Import Cost**: Show package sizes
- **Thunder Client**: API testing

#### AI-Enhanced Extensions
- **GitHub Copilot**: Additional AI assistance
- **Tabnine**: Alternative AI completion
- **Kite**: Python AI completion
- **IntelliCode**: Microsoft's AI completion

### 3. Theme and Font Optimization

#### Recommended Fonts
```json
{
  "editor.fontFamily": "'JetBrains Mono', 'Fira Code', 'Cascadia Code', Consolas, monospace",
  "editor.fontSize": 14,
  "editor.fontLigatures": true,
  "editor.fontWeight": "normal",
  "editor.letterSpacing": 0.5
}
```

#### Dark Theme Settings
```json
{
  "workbench.colorTheme": "One Dark Pro",
  "workbench.iconTheme": "material-icon-theme",
  "editor.tokenColorCustomizations": {
    "textMateRules": [
      {
        "scope": "comment",
        "settings": {
          "fontStyle": "italic"
        }
      }
    ]
  }
}
```

## 🎨 Advanced Features

### 1. Custom Keybindings

#### Personal Shortcuts
```json
{
  "key": "ctrl+shift+r",
  "command": "cursor.ai.refactor",
  "when": "editorTextFocus"
},
{
  "key": "ctrl+shift+d",
  "command": "cursor.ai.document",
  "when": "editorTextFocus"
},
{
  "key": "ctrl+shift+t",
  "command": "cursor.ai.test",
  "when": "editorTextFocus"
}
```

### 2. Workspace-Specific Settings

#### Project-Specific Configuration
```json
// .vscode/settings.json
{
  "typescript.preferences.importModuleSpecifier": "relative",
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "files.associations": {
    "*.css": "tailwindcss"
  }
}
```

### 3. Task Automation

#### Custom Tasks
```json
// .vscode/tasks.json
{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "Start Development Server",
      "type": "shell",
      "command": "npm run dev",
      "group": "build",
      "presentation": {
        "echo": true,
        "reveal": "always",
        "focus": false,
        "panel": "new"
      }
    },
    {
      "label": "Run Tests",
      "type": "shell",
      "command": "npm test",
      "group": "test"
    }
  ]
}
```

## 🚀 Performance Tips

### 1. Memory Management
- **Close Unused Tabs**: Too many open files consume memory
- **Disable Heavy Extensions**: Some extensions can slow down performance
- **Use Workspace Folders**: Organize projects into workspace folders
- **Clear Cache**: Restart Cursor periodically

### 2. AI Performance
- **Limit Context Window**: Don't include unnecessary files in AI context
- **Use Specific Prompts**: More specific prompts get better results
- **Batch AI Requests**: Group related questions together
- **Cache AI Responses**: Save useful AI responses for future reference

### 3. Git Performance
- **Exclude Large Files**: Add large files to .gitignore
- **Use Git LFS**: For binary files and large assets
- **Limit Git History**: Consider shallow clones for large repositories
- **Optimize Git Settings**: Configure Git for better performance

## 🎯 Workflow Optimization

### 1. Daily Routine
1. **Morning Setup**: Open Cursor, check Git status, review yesterday's work
2. **Task Planning**: Use AI to help prioritize and plan tasks
3. **Development**: Use AI-assisted coding for faster development
4. **Review**: Self-review code using AI before committing
5. **Documentation**: Update documentation with AI assistance

### 2. Project Management
- **Use AI for Estimation**: Get AI help with time estimates
- **Generate Documentation**: Use AI to create project documentation
- **Code Reviews**: Use AI to assist with code reviews
- **Bug Tracking**: Use AI to help debug and fix issues

### 3. Team Collaboration
- **Share Snippets**: Create and share useful code snippets
- **Document Workflows**: Use AI to document team workflows
- **Code Standards**: Use AI to help maintain code standards
- **Knowledge Sharing**: Use AI to help create team documentation

---

*These tips and tricks will help you become a Cursor power user. Remember to adapt these techniques to your specific workflow and project needs.* 