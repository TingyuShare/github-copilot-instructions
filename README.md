# Operations Logger - GitHub Copilot Instructions

Automatically log key operations and commands to `operations.md` after each GitHub Copilot session.

## How It Works

This repository contains a `.github/copilot-instructions.md` file that tells GitHub Copilot to:

1. Track significant operations during each session
2. Append structured entries to `operations.md` after task completion
3. Record **key commands, file changes, and decisions** — skip trivial logs

## Usage

### Option 1: Clone & Use (Recommended)

Clone this repo and open it in VS Code:

```bash
git clone <this-repo-url> your-project
code your-project
```

GitHub Copilot will automatically read `.github/copilot-instructions.md` and apply the logging rule.

### Option 2: Add to an Existing Project

Copy `.github/copilot-instructions.md` into your existing project:

```bash
cp .github/copilot-instructions.md your-project/.github/
```

### Option 3: VS Code Global Settings

Set this in your VS Code `settings.json` to apply globally:

```json
"github.copilot.chat.customInstructions": [
  {
    "url": "https://raw.githubusercontent.com/<owner>/<repo>/main/.github/copilot-instructions.md"
  }
]
```

Or copy the file to your VS Code prompts folder:

```bash
# Linux / macOS
cp .github/copilot-instructions.md ~/.vscode-server/data/User/prompts/operations-logging.md

# Windows
# Copy to %APPDATA%\Code\User\prompts\operations-logging.md
```

## What Gets Logged

After each resolved task, Copilot appends to `operations.md`:

```
## [2025-01-15 14:30] - Project Setup

**Summary:** Initialized React project with TypeScript and ESLint.

**Commands:**
```bash
npm create vite@latest . -- --template react-ts
npm install
```

**Files:** `src/App.tsx`, `vite.config.ts`, `package.json`

**Notes:** Using Vite for fast builds.
```

## What Gets Skipped

- ❌ Trivial steps ("opened a file", "read a function")
- ❌ Debug logs and error messages (unless critical)
- ❌ Intermediate dead ends or failed attempts
- ❌ Exploratory searches that led nowhere

## File Structure

```
.
├── .github/
│   └── copilot-instructions.md   # The rule file (auto-detected by Copilot)
├── README.md                     # This file
└── operations.md                 # Generated automatically by Copilot
```

## License

MIT
