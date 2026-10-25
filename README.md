# roblox-game — Antigravity Skill & Plugin

The ultimate Roblox game development companion for Google Antigravity. A self-contained, full-lifecycle development companion that serves all skill levels with deep Luau expertise, autonomous game building via Roblox Studio MCP integration, active guardrails, and comprehensive knowledge of game design, monetization, security, and performance optimization.

## Stats

- **31 skill files** | **30,768 lines** | **1.0 MB**
- 120-line `SKILL.md` router with lazy-loaded references
- Native Antigravity Plugin manifest (`plugin.json`) + Active Rules (`rules/AGENTS.md`)
- 4-mode Roblox Studio MCP integration (Antigravity StudioMCP / Community / Legacy / Offline)
- 100% verified with `agy plugin validate`

## Architecture

**Router + Reference Library Plugin** — lightweight `SKILL.md` dispatcher with lazy-loaded deep knowledge and active Antigravity rules.

```
roblox-game/
├── plugin.json                 # Antigravity plugin manifest
├── rules/
│   └── AGENTS.md               # Active rules (security, persistence, MCP safety)
├── skills/
│   └── roblox-game/
│       ├── SKILL.md            # Router (120 lines, 18 routing paths)
│       ├── references/         # 16 deep reference files
│       │   ├── animation-vfx.md
│       │   ├── architecture-patterns.md
│       │   ├── combat-systems.md
│       │   ├── datastore-persistence.md
│       │   ├── game-design-roblox.md
│       │   ├── gui-systems.md
│       │   ├── inventory-systems.md
│       │   ├── luau-mastery.md
│       │   ├── mcp-orchestration.md
│       │   ├── monetization-systems.md
│       │   ├── multiplayer-networking.md
│       │   ├── performance-optimization.md
│       │   ├── security-hardening.md
│       │   ├── sharp-edges.md
│       │   ├── testing-patterns.md
│       │   └── tooling-ecosystem.md
│       ├── templates/          # 7 game templates
│       │   ├── game-scaffold.md        # Universal base (any genre)
│       │   ├── genre-simulator.md      # Pet Simulator style
│       │   ├── genre-tycoon.md         # Retail Tycoon style
│       │   ├── genre-obby.md           # Tower of Hell style
│       │   ├── genre-rpg.md            # Blox Fruits style
│       │   ├── genre-horror.md         # Doors style
│       │   └── genre-battle-royale.md  # Battle royale style
│       └── workflows/          # 7 guided workflows
│           ├── new-game.md             # Build a game from scratch
│           ├── debug-loop.md           # Iterative MCP debugging
│           ├── performance-audit.md    # Performance profiling
│           ├── security-audit.md       # Security review
│           ├── publish-checklist.md    # Pre-publish verification
│           ├── monetization-audit.md   # Revenue optimization
│           └── code-review.md          # Code quality review
└── docs/plans/                 # Design specifications & task plans
```

## Features

### MCP Studio Integration (4 Modes)

| Mode | Server | Tools | Capabilities |
|------|--------|:-----:|-------------|
| **Antigravity StudioMCP** | Roblox Official (`StudioMCP.exe`) | 28 | Live Luau execution, hierarchy inspection, script search & grep, playtest control, console reading, Creator Store insertion, AI 3D/texture generation |
| **Community** | `boshyxd/robloxstudio-mcp` | 39 | Project exploration, autonomous building, iterative debugging, bulk operations, Creator Store |
| **Legacy Official** | `Roblox/studio-rust-mcp-server` | 6 | Code execution, model insertion, console reading, play mode control |
| **Offline** | None | 0 | Pure Luau code generation with target service placement instructions |

Auto-detects which server is available in Antigravity and adapts all workflows accordingly.

### Active Rules (`rules/AGENTS.md`)

Pre-loaded rules that safeguard your game in every Antigravity interaction:
- **Never trust the client**: Strict server authority and remote payload verification.
- **DataStore safety**: Enforces session locking (ProfileService) and prevents data loss.
- **Studio MCP guardrails**: Mandates `task.wait()` batching for unyielding operations and Edit/Play mode checks.

### Genre Templates

Each template includes complete, production-ready Luau code for every core system:

- **Simulator** — Collection, pet system (hatching + rarity), zones, upgrades, prestige/rebirth
- **Tycoon** — Plot claiming, droppers/collectors, button pad purchasing, income, tiers
- **Obby** — Checkpoints, 5 obstacle types, timer/speedrun, leaderboards
- **RPG** — Character stats + leveling, quest system, NPC AI, dialog trees, zones
- **Horror** — Atmosphere control, monster AI (5-state FSM), event sequencer, jumpscares, flashlight
- **Battle Royale** — Match lifecycle, shrinking storm, loot spawning, elimination tracking, spectator

### Guided Workflows

- **New Game** — Build a complete game from a description in 8 steps
- **Debug Loop** — Iterative error detection and fixing (max 5 attempts)
- **Performance Audit** — Part count, script, memory, and network analysis
- **Security Audit** — RemoteEvent validation, client trust, data exposure review
- **Publish Checklist** — 60+ item pre-launch verification across 10 categories
- **Monetization Audit** — GamePass, DevProduct, Premium, and Ad optimization
- **Code Review** — A-F quality rating with specific fixes

### Deep References

16 reference files covering every aspect of Roblox development:
- Luau language mastery with type system and OOP patterns
- Game architecture (services, client-server, modules, frameworks)
- Security hardening (never trust client, validation, rate limiting)
- DataStore persistence (ProfileService, session locking, migration)
- MCP orchestration and live Studio automation
- And 11 more specialized topics

### Sharp Edges

12 severity-rated gotchas that save you from disaster (Critical → Low):
- DataStore data loss, client-side currency manipulation, ProcessReceipt bugs
- Memory leaks, RemoteEvent flooding, BindToClose timeout
- And 6 more common pitfalls with complete Luau code fixes

---

## Antigravity Studio MCP Setup

To enable live interaction with Roblox Studio in Antigravity:

1. In Roblox Studio, enable **Allow Third Party Integrations** in Game Settings.
2. Add the `Roblox_Studio` MCP server to `~/.gemini/config/mcp_config.json`:

```json
{
  "mcpServers": {
    "Roblox_Studio": {
      "command": "cmd.exe",
      "args": [
        "/c",
        "%LOCALAPPDATA%\\Roblox\\mcp.bat"
      ]
    }
  }
}
```

Antigravity will automatically detect `Roblox_Studio` and connect via the official `StudioMCP.exe`.

---

## Usage

The skill is automatically invoked by Antigravity whenever you mention Roblox, Luau, game development, or related topics.

**Example prompts:**
- "Build me a pet simulator with 3 zones and pet hatching"
- "Audit my Roblox game security and RemoteEvents"
- "Connect to Roblox Studio and inspect the Workspace tree"
- "How do I implement session locking with ProfileService?"
- "Optimize this game for low-end mobile devices"
- "Add a shop system with GamePasses and developer products"

---

## Installation

### Method 1: Global Antigravity Plugin (Recommended)

Install globally so the skill and rules are active across all workspaces:

```bash
git clone https://github.com/ikarisz/roblox-game-skill.git ~/.gemini/config/plugins/roblox-game
agy plugin enable roblox-game
```

Validate the installation:
```bash
agy plugin validate ~/.gemini/config/plugins/roblox-game
```

### Method 2: Workspace Plugin

Install specifically for a single project:

```bash
git clone https://github.com/ikarisz/roblox-game-skill.git .agents/plugins/roblox-game
```

### Method 3: Workspace Skill (`skills.json`)

If managing skills via custom path:

```json
{
  "entries": [
    { "path": "path/to/roblox-game/skills" }
  ]
}
```

---

## Design Documents

See `docs/plans/` for the original architectural design documents and implementation task specifications.
