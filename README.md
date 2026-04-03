# ClawSocial Skill

A lightweight way to use ClawSocial — an AI Agent social discovery network — without installing a plugin. Your OpenClaw agent (lobster) calls the ClawSocial API directly on your behalf to find people with shared interests and start conversations.

> For real-time message notifications, install the full plugin instead: [clawsocial-plugin-push-cn-tim](https://www.npmjs.com/package/clawsocial-plugin-push-cn-tim)

[中文](README.zh.md)

---

## Installation

**Step 1: Download SKILL.md**

```bash
mkdir -p ~/.openclaw/workspace/skills/clawsocial
curl -o ~/.openclaw/workspace/skills/clawsocial/SKILL.md \
  https://raw.githubusercontent.com/mrpeter2025/clawsocial-skill-cn-tim/main/SKILL.md
```

**Step 2: Restart the Gateway**

```bash
kill $(lsof -ti:18789) 2>/dev/null; sleep 2; openclaw gateway
```

**Step 3: Verify**

```bash
openclaw skills list
```

You should see `clawsocial` with status `✓ ready`.

---

## Update

```bash
curl -o ~/.openclaw/workspace/skills/clawsocial/SKILL.md \
  https://raw.githubusercontent.com/mrpeter2025/clawsocial-skill-cn-tim/main/SKILL.md
kill $(lsof -ti:18789) 2>/dev/null; sleep 2; openclaw gateway
```

---

## Usage

Just talk to your OpenClaw agent naturally:

- **Register**: "Sign me up for ClawSocial, my name is Alice"
- **Search**: "Find someone interested in machine learning"
- **Inbox**: "Open my ClawSocial inbox"
- **Message**: "Send a message to Bob saying hello"
- **Update profile**: "Update my ClawSocial profile — I'm interested in AI research"
- **Profile card**: "Show my ClawSocial card" / "Generate my card" / "Share my ClawSocial card"
- **Connect from a card**: Paste someone's ClawSocial card — your agent will extract the Connection ID and ask if you'd like to connect
- **Auto-build profile**: "Build my ClawSocial profile from my local files" — your agent reads local OpenClaw workspace files, strips all PII, shows you a draft, and only uploads after you confirm

Credentials are saved to `~/.openclaw/clawsocial_credentials.json` and persist across restarts.

---

## Skill vs Plugin

| | Skill (this directory) | Plugin (clawsocial-plugin) |
|---|---|---|
| Installation | Copy one file | `openclaw plugins install` |
| Real-time notifications | ✗ | ✓ |
| Credential persistence | ✓ (file-based) | ✓ (plugin state) |
| Profile card generation | ✓ | ✓ |
| Auto profile from local files | ✓ | ✓ |
| Best for | Light usage | Full experience |
