# MercuryOS

**One prompt to boot your personal AI operating system.**

MercuryOS turns Claude Code into a team of specialized AI agents that route work, hire new members when there's a gap, and learn your preferences over time. You paste one prompt into an empty directory. It builds the system. You talk to Mercury — he handles the rest.

## Quick Start

1. **Create an empty directory** and open it in [Claude Code](https://docs.anthropic.com/en/docs/claude-code)
2. **Copy the contents of [`prompt.md`](prompt.md)**
3. **Paste it into Claude Code** and hit enter

That's it. Mercury boots up with a starter team and is ready for your first request.

## What Boots Up

The prompt creates a two-layer architecture and a starter team of four:

### The Team

| Member | Role | What They Do |
|--------|------|-------------|
| **Mercury** | Orchestrator | Routes your requests to the right team member. Never does work directly — only delegates. The only one you talk to. |
| **Minerva** | Senior Researcher | Investigates any domain. Produces structured research briefs. Critical to the hiring workflow. |
| **Juno** | HR Lead | Designs new AI team members based on research. Picks mythological names with meaningful connections to each role. |
| **Apollo** | Product Manager | Pressure-tests ideas. Defines real problems. Writes product briefs. Shapes what gets built. |

### The File Structure

```
your-project/
├── CLAUDE.md              # Mercury — the orchestrator (this IS the system prompt)
├── Conventions.md         # File standards
├── Inbox/                 # Drop items here for Mercury to triage
├── Projects/              # Your project files
├── Preferences/           # Seven-layer system that learns who you are
│   ├── README.md
│   ├── facts.md           # Ground truth about you
│   ├── preferences.md     # Your choices when alternatives exist
│   ├── values.md          # What you optimize for
│   ├── heuristics.md      # Your decision patterns
│   ├── constraints.md     # Hard rules and boundaries
│   ├── salience.md        # What gets your attention
│   └── contexts.md        # Current state — projects, priorities
└── Team/
    ├── Registry.md        # The team roster
    ├── Retrospectives/    # Post-session reviews
    ├── Minerva/           # Researcher
    │   ├── Persona.md
    │   ├── Journal/
    │   └── Memory/
    ├── Juno/              # HR Lead
    │   ├── Persona.md
    │   ├── Journal/
    │   └── Memory/
    └── Apollo/            # Product Manager
        ├── Persona.md
        ├── Journal/
        └── Memory/
```

## The Two-Layer Architecture

MercuryOS separates **operations** from **identity**.

**Layer 1 — Operations** is the team system: Mercury's routing logic, team member personas, conventions, journals, memories. This is the product. It defines how work gets done.

**Layer 2 — Preferences** is you: your facts, preferences, values, heuristics, constraints, what matters to you, what you're working on right now. This is the user config. It's portable — copy the `Preferences/` directory to any AI system and it knows who you are.

The team learns Layer 2 as you work together. When you express a preference or reveal a value through a decision, team members capture it. Over time, the system gets better because it knows you better.

## How It Grows

### Auto-Hiring

Ask Mercury for something no one on the team can handle — say, "write a blog post" or "review this code." Mercury will:

1. Have Minerva research what a human professional in that role actually does
2. Have Juno design a new AI team member based on the research
3. Present you with a name, title, and summary — you approve
4. The new member joins the team and handles your request

The team grows to fit your needs. You never design personas yourself.

### Journals and Memory

After every task, the team member who did the work writes a journal entry — what was done, decisions made, outcome. Reusable learnings get saved to their Memory directory and loaded into future dispatches. The team gets smarter over time.

### Session Retrospectives

When you end a session, Mercury reviews what happened: what went well, what could improve, any learnings. This gets written to `Team/Retrospectives/` for continuity across sessions.

## Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) (Anthropic's CLI for Claude)
- A Claude API key with access to the Agent tool (Claude Pro, Team, or Enterprise)

## FAQ

**Why not just use Claude Code directly?**
You can. MercuryOS adds structure: specialized agents with distinct expertise, persistent memory, preference learning, and automatic team growth. It's the difference between having one generalist and having a team.

**Can I modify the team members?**
Yes. Edit any `Persona.md` file, or ask Mercury to have Juno redesign a member. The system is just markdown files — fully transparent and editable.

**Can I add my own team members manually?**
Yes. Create a directory under `Team/`, write a `Persona.md` following the existing pattern, and add them to `Team/Registry.md`. But the auto-hiring workflow is designed to produce better personas than most people would write from scratch.

**Does this work with other AI tools?**
The architecture is designed for Claude Code's Agent tool, which allows Mercury to spawn sub-agents. Other tools that support similar multi-agent patterns could adapt it. The `Preferences/` directory is fully portable regardless.

**What's with the mythological names?**
Each name has a meaningful connection to the role, not just a cool sound. Minerva was the goddess the other gods consulted before decisions (researcher). Juno was the goddess of beginnings who brought new beings into the world (HR). Apollo presided over the Oracle at Delphi, turning confusion into clarity (product). The naming convention is maintained by Juno as the team grows.

**Is my data sent anywhere?**
MercuryOS is just a prompt and markdown files on your machine. Your data goes wherever your Claude Code usage goes (Anthropic's API). Nothing additional.

## Contributing

MercuryOS is early. If you try it and find something that should work differently, open an issue. Pull requests welcome for:

- Boot prompt improvements
- New starter team configurations
- Documentation
- Website (coming soon)

## License

[MIT](LICENSE)
