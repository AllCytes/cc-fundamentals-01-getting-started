# Claude Code Starter Template - Module 1

## Make It Your Own

After cloning, remove the original remote and create your own GitHub repository:

**Windows (PowerShell)**
```powershell
git remote remove origin
gh repo create cc-fundamentals-01-getting-started --public --source=. --remote=origin --push
```

**Mac / Linux**
```bash
git remote remove origin
gh repo create cc-fundamentals-01-getting-started --public --source=. --remote=origin --push
```

> **Prerequisite:** Install the [GitHub CLI](https://cli.github.com/) — `winget install GitHub.cli` (Windows) or `brew install gh` (Mac), then run `gh auth login` once.

---

Welcome to Claude Code! This template gives you the foundation for working with AI-powered development.

---

## Quick Start

1. **Install Claude Code** (if you haven't already):

   **Windows PowerShell:**
   ```powershell
   irm https://claude.ai/install.ps1 | iex
   ```

   **Mac/Linux:**
   ```bash
   curl -fsSL https://claude.ai/install.sh | bash
   ```

2. **Open this folder in Cursor IDE**

3. **Open terminal** (Ctrl+` or View → Terminal)

4. **Run Claude:**
   ```
   claude
   ```

5. **Verify it's working:**
   ```
   /doctor
   ```

6. **See all commands:**
   ```
   /help
   ```

---

## Project Structure

```
01-getting-started/
│
├── README.md              ← You are here! Start with this file.
├── .gitignore             ← Protects sensitive files from Git
├── .env.example           ← Template for API keys (copy to .env)
│
├── .claude/               ← Claude Code configuration
│   ├── CLAUDE.md          ← Project memory (Claude reads this first!)
│   ├── commands/          ← Your custom /commands go here (Module 2)
│   ├── hooks/             ← Security scripts (Module 7)
│   └── settings.json      ← Permissions and preferences
│
├── .mcp.json              ← MCP integrations (Module 4)
│
├── docs/                  ← Project documentation
│
├── specs/                 ← Planning workflow (Module 3)
│   ├── todo/              ← Plans waiting to be built
│   └── done/              ← Completed plans
│
└── src/                   ← Your application code goes here
```

### What Each Folder Is For

| Folder | Purpose |
|--------|---------|
| `.claude/` | Everything Claude Code needs to understand your project |
| `.claude/commands/` | Custom slash commands you create |
| `.claude/hooks/` | Scripts that protect you from dangerous operations |
| `docs/` | Documentation for your project |
| `specs/` | Planning and tracking workflow |
| `specs/todo/` | Specs waiting to be implemented |
| `specs/done/` | Completed specs (move here when finished) |
| `src/` | Your actual application code |

---

## Essential Claude Code Commands

These commands come **built-in** with Claude Code - no setup required!

### Must-Know Commands (Start Here)

| Command | What it Does | When to Use |
|---------|--------------|-------------|
| `/help` | Shows ALL available commands | First thing to run - see what's available |
| `/doctor` | Checks if Claude Code is working properly | If something seems broken |
| `/status` | Shows your account, model, and version info | Check which model you're using |
| `/clear` | Wipes conversation and starts fresh | Switching to a different task |
| `/context` | Shows how much "memory" you've used | Before context gets too full |

### Session Management

| Command | What it Does | When to Use |
|---------|--------------|-------------|
| `/compact` | Compresses conversation to save space | Long sessions, running low on context |
| `/model` | Switch between Claude models | Need faster (Haiku) or smarter (Opus) |
| `Esc Esc` | Undo Claude's last action | Made a mistake, want to try again |
| `/cost` | Shows token usage for this session | Curious about usage |

### Setup Commands

| Command | What it Does | When to Use |
|---------|--------------|-------------|
| `/init` | Creates a starter CLAUDE.md for your project | New project setup |
| `/config` | Opens settings panel | Change preferences |
| `/permissions` | Manage what Claude can/can't do | Adjust tool access |

### Troubleshooting

| Command | What it Does | When to Use |
|---------|--------------|-------------|
| `/doctor` | Health check for Claude Code | Installation problems |
| `/bug` | Report an issue to Anthropic | Found a bug |
| `/release-notes` | See what's new | After updates |

### Pro Tips

- **Type `/` and wait** - You'll see autocomplete suggestions
- **`/help` shows everything** - Both built-in AND your custom commands
- **`/clear` beats `/compact`** - For new tasks, fresh context = better results
- **`Esc Esc` is your undo** - Press Escape twice to rewind

---

## Understanding API Keys

### What is an API Key?

Think of an API key like a **password that lets programs talk to each other**.

When you want Claude Code to use other services (like generating images, searching the web, or accessing databases), those services need to know it's really you - that's what the API key does.

### Where API Keys Live

```
.env                 ← Your actual keys (NEVER share this file!)
.env.example         ← Template showing what keys you need (safe to share)
```

### Getting Your First API Key: Google Gemini (Free!)

Google's Gemini AI offers free API access - perfect for learning!

**Step-by-step:**

1. Go to: https://aistudio.google.com/apikey
2. Sign in with your Google account
3. Click **"Create API Key"**
4. Copy the key (starts with `AIza...`)
5. Create a `.env` file in this folder
6. Add your key:
   ```
   GOOGLE_API_KEY=AIzaSy...your-key-here
   ```

### Common API Keys You'll Encounter

| Service | What it's For | Free Tier? | Where to Get |
|---------|---------------|------------|--------------|
| `GOOGLE_API_KEY` | Gemini AI | Yes! | aistudio.google.com/apikey |
| `ANTHROPIC_API_KEY` | Claude API | Pay-per-use | console.anthropic.com |
| `OPENAI_API_KEY` | ChatGPT/GPT-4 | Pay-per-use | platform.openai.com/api-keys |
| `GITHUB_TOKEN` | GitHub automation | Yes | github.com/settings/tokens |
| `REPLICATE_API_TOKEN` | Image/Audio AI | Free credits | replicate.com/account |

### Golden Rules for API Keys

| Rule | Why |
|------|-----|
| **NEVER commit `.env` to Git** | Keys would be public! `.gitignore` protects you |
| **NEVER share keys publicly** | Treat like passwords |
| **DO share `.env.example`** | Shows structure without real values |
| **Rotate keys if exposed** | Get new ones immediately |

---

## Setting Up Your Environment

### Step 1: Copy the Environment Template

```bash
# Copy the example file to create your .env
cp .env.example .env
```

Or manually create a `.env` file and copy contents from `.env.example`.

### Step 2: Add Your API Keys

Open `.env` and fill in any keys you have:

```bash
# Required for some features
ANTHROPIC_API_KEY=sk-ant-...

# Optional - add as needed
GOOGLE_API_KEY=AIza...
OPENAI_API_KEY=sk-...
```

### Step 3: Verify .gitignore is Working

Your `.env` file should NOT appear when you run:
```bash
git status
```

If it does appear, check that `.gitignore` includes `.env`.

---

## The "Brilliant but Blind" Principle

Claude is incredibly smart, but it starts each session **knowing nothing about your project**.

Think of it like hiring a brilliant contractor who's never seen your house:
- They can do amazing work
- But they need you to show them around first
- They need context about what you want

**That's why we have:**
- `CLAUDE.md` - The "project tour" Claude reads first
- `specs/` - Detailed plans so Claude knows what to build
- `docs/` - Reference materials Claude can look up

The more context you provide, the better results you get!

---

## What's Next?

| Module | What You'll Learn |
|--------|-------------------|
| **Module 2** | Create your first custom /command |
| **Module 3** | The Plan → Build → Validate workflow |
| **Module 4** | Add superpowers with MCPs |
| **Module 5** | Build reusable Skills |
| **Module 6** | Delegate work with Subagents |
| **Module 7** | Security essentials and Hooks |
| **Module 8** | GitHub integration |
| **Module 9** | Validation and visual verification |
| **Module 10** | Tips, tricks, and putting it all together |

---

## Need Help?

| Resource | What it's For |
|----------|---------------|
| `/help` | See all available commands |
| `/doctor` | Troubleshoot installation issues |
| [code.claude.com/docs](https://code.claude.com/docs) | Official documentation |
| [cursor.sh](https://cursor.sh) | Download Cursor IDE |

---

*This is Module 1 of the Claude Code Fundamentals course.*
