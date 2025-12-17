# My Skills Plugin

A Claude Code plugin containing workflow skills for task management and automation.

## Installation

### Option 1: Add as Local Marketplace

```bash
# In Claude Code, add this directory as a marketplace
claude /plugin marketplace add /home/gb/Work/projects/Productivity/my_skills

# Install the plugin
claude /plugin install my-skills@gb-skills-marketplace
```

### Option 2: Interactive Installation

```bash
# Start Claude Code
claude

# Then use the plugin command
/plugin
# Select "Browse Plugins" and choose my-skills
```

## Available Skills

### legalizacao

Specialized workflow for Brazilian company legalizations:
- **ABERTURA** - Opening a new company
- **ALTERACAO** - Modifying an existing company
- **BAIXA** - Closing a company

Integrates with Trello for task tracking and progress management.

**Trigger phrases:** "legalizacao", "company opening", "abertura", "alteracao", "baixa"

## Adding New Skills

To add a new skill:

1. Create a directory under `skills/`:
   ```
   skills/
   └── your-new-skill/
       ├── SKILL.md        # Required - skill definition
       ├── reference.md    # Optional - additional docs
       └── scripts/        # Optional - utilities
   ```

2. Create `SKILL.md` with frontmatter:
   ```markdown
   ---
   name: your-skill-name
   description: What the skill does and when to use it
   ---

   # Skill Title

   Instructions for Claude on how to use this skill...
   ```

3. Reinstall the plugin to pick up changes:
   ```bash
   /plugin uninstall my-skills@gb-skills-marketplace
   /plugin install my-skills@gb-skills-marketplace
   ```

## Directory Structure

```
my_skills/
├── .claude-plugin/
│   └── plugin.json          # Plugin manifest
├── skills/
│   └── legalizacao/
│       ├── SKILL.md         # Skill instructions
│       └── scripts/         # Node.js CLI tools
├── marketplace.json         # For local installation
└── README.md
```

## Requirements

For the legalizacao skill:
- Node.js >= 18.0.0
- Trello API credentials (TRELLO_API_KEY, TRELLO_TOKEN)

## License

MIT
