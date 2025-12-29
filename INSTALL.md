# Install managing-skills

## Step 1: Detect your environment

```bash
# Check what exists
ls -la ~/.claude/skills 2>/dev/null && echo "Claude Code skills found"
ls -la ~/.config/opencode/skill 2>/dev/null && echo "OpenCode skills found"
```

## Step 2: Install

Clone to your tool's skill directory:

| Tool | Command |
|------|---------|
| Claude Code | `mkdir -p ~/.claude/skills && git clone https://github.com/mikekelly/managing-skills ~/.claude/skills/managing-skills` |
| OpenCode | `mkdir -p ~/.config/opencode/skill && git clone https://github.com/mikekelly/managing-skills ~/.config/opencode/skill/managing-skills` |

If neither directory exists, use the one matching your current tool.

## Step 3: Set up interop (if both tools are in use)

If the user has both Claude Code and OpenCode, share skills via symlink. The directory you just installed to becomes the primary; symlink the other to it.

**Installed to Claude Code, want OpenCode access:**
```bash
[ -d ~/.config/opencode/skill ] && echo "Warning: OpenCode skills exist - confirm before replacing"
rm -rf ~/.config/opencode/skill
mkdir -p ~/.config/opencode
ln -s ~/.claude/skills ~/.config/opencode/skill
```

**Installed to OpenCode, want Claude Code access:**
```bash
[ -d ~/.claude/skills ] && echo "Warning: Claude skills exist - confirm before replacing"
rm -rf ~/.claude/skills
mkdir -p ~/.claude
ln -s ~/.config/opencode/skill ~/.claude/skills
```

## Verify

```bash
ls -la ~/.claude/skills/managing-skills/SKILL.md ~/.config/opencode/skill/managing-skills/SKILL.md 2>/dev/null
```

Both paths should resolve (one real, one symlink).
