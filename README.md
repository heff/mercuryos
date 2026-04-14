# MercuryOS

**One prompt to boot your personal AI operating system.**

One prompt, one folder. An AI-independent orchestration layer that works with any tool with filesystem access and sub-agent capability. Paste a single prompt into a directory. It builds the rest. Your preferences are the gold — details about you that accumulate over time and may be the only part worth bringing to the next version. You talk to Mercury — Mercury talks to the team.

## Quick Start

1. Create a directory (empty or with an existing MercuryOS installation)
2. Open it in your AI tool of choice
3. Paste the contents of [`prompt.md`](prompt.md) and run it

Mercury boots with a starter team of three and is ready for your first request.

### Platform Notes

**Claude Code** — Open the directory, paste the prompt. The Agent tool provides sub-agent capability out of the box. Set your `CLAUDE.md` as the system prompt.

**Codex** — Use the prompt as your system instructions. Codex supports file creation and sub-agent dispatch. Point it at the directory and paste the prompt as your first message.

**Other tools** — Any AI tool that can (a) read and write files and (b) spawn sub-agents or equivalent can run MercuryOS. Adapt the dispatch mechanism to your tool's agent/function-calling pattern.

## What You Get

- **Mercury** — the orchestrator. Routes requests, never does work directly. The only agent you talk to. Renameable during boot.
- **Three starter roles** — a researcher, an HR lead, and a product manager. Named during boot using your chosen naming convention (default: Roman gods, each name meaningful to the role). The PM leads as the OS's own product manager — designs new capabilities when tasks aren't supported, asks the right questions to understand goals, and secondarily serves as PM for other products.
- **Three-layer architecture** — preferences (the gold), decisions, and operations, separated by durability.
- **For Team / For Me** — exchange folders for communication between you and the team. Drop items in For Team, get results back in For Me.
- **Task + decision logging** — a capability map of what the system has done, used to inform rebuilds.
- **Retrospective** — automatic session review that surfaces learnings, captures preferences, and improves the system over time.

## The Three-Layer Architecture

MercuryOS separates your data into three layers based on how long they last.

**Preferences (most durable)** — Who you are. Facts, preferences, values, heuristics, constraints, salience, current contexts. Organized by cognitive primitive type. This is the gold of the system — details about you that accumulate over time as you work with your team. With AI capabilities changing rapidly, preferences may be the only part worth bringing to the next version. Fully portable: copy them to any AI system and it knows you.

**Decisions (medium durable)** — Choices made while building and operating the system. Each entry logs what was decided, why, what alternatives were considered, and which task prompted it. On a rebuild, the new system reads these as guidance rather than gospel — it can make different choices with better reasoning.

**Operations (least durable)** — The OS itself: team roster, routing logic, personas, conventions, workflows. This is the layer that gets rebuilt when you upgrade. It is a product of the prompt plus your preferences and decisions, not a thing you preserve.

The key insight: when you separate identity from machinery, you can replace the machinery without losing yourself.

## How It Grows

**Auto-hiring.** Ask for something no one on the team handles. Mercury has the researcher investigate the role, the HR lead design a new team member, and presents you with a name and summary. You approve, they join the team. The team grows to match your usage.

**Task logging.** Every request is recorded. Over time this builds a capability map — what you actually use the system for. Rebuilds can read this to prioritize which roles to recreate first.

**Decision logging.** When the system makes a structural choice (naming convention, file organization, workflow design), it logs the decision with context. Future versions inherit your decisions without inheriting your implementation.

**Preference capture.** As you work, team members watch for signals — facts, preferences, values, patterns — and write them to the appropriate preference file. The system gets better because it knows you better.

**Retrospective.** At session end, the system reviews what happened — what was accomplished, what went well, what could improve. It surfaces learnings, captures new preferences, and writes meta-insights to memory. Can hook into platform session-end events for automatic triggering.

## Upgrades and Rebuilds

This is the core design bet. When a better AI model ships, paste the prompt into your directory and run it.

The boot sequence detects what's already there. If it finds an existing MercuryOS installation in the current folder, it offers a rebuild — reading your preferences, decision log, and task history, then reconstructing operations from scratch. If the folder is empty, it asks whether you have a prior installation at another path so it can import your preferences and decisions before building fresh.

The prompt is a seed, not a blueprint. Each rebuild produces a system shaped by your actual usage, not by the assumptions of the original author. Preferences persist. Decisions provide guidance. Operations get rebuilt better.

You never migrate. You replant.

## Environment System

`~/.mercuryos/` stores machine-specific configuration that doesn't belong in the OS directory and shouldn't sync across machines.

- **`environment.md`** — discovered capabilities: which CLIs are installed, what integrations are available, platform details. Written during boot, updated as new tools are detected.
- **`.env`** — secrets and API keys. Never committed, never synced.

Purpose: multi-machine support. Run MercuryOS on your laptop and your desktop — each has its own environment file describing what's available locally. When a new OS version boots, it reads `~/.mercuryos/` immediately and knows what it can work with.

## Requirements

- Any AI tool with filesystem read/write access
- Sub-agent or equivalent dispatch capability (the tool can spawn scoped sub-tasks)
- No specific vendor, model, or platform dependency

## FAQ

**Why not just use my AI tool directly?**
You can. MercuryOS adds specialization, persistent memory, preference learning, and automatic team growth. One generalist vs. a team that knows you.

**Is this tied to a specific AI platform?**
No. It requires filesystem access and sub-agent capability. Any tool with those features works. The `Preferences/` layer is portable to anything, including tools that don't run MercuryOS.

**What are the three layers again?**
Preferences (who you are, most durable), decisions (choices made, medium durable), operations (the system itself, least durable). Preferences are the gold — they survive everything. Operations get rebuilt on upgrade.

**Can I rename Mercury?**
Yes. During boot, you're asked for a naming convention and Mercury itself can be renamed to fit. The orchestrator role stays the same regardless of what you call it.

**What's the environment directory?**
`~/.mercuryos/` stores machine-specific config — discovered capabilities, secrets, platform details. It lives outside the OS directory so it doesn't sync and each machine can describe its own environment.

**Can I modify team members?**
Yes. Edit any persona file, or ask Mercury to redesign a member through the HR lead. Everything is markdown.

**What's with the mythological names?**
The default naming convention uses Roman gods, each chosen for a meaningful connection to the role. The convention is configurable — you can use any naming scheme. The HR lead maintains consistency.

**How is this different from a fixed agent framework?**
No predefined file structure. No hardcoded team. The prompt creates an orchestrator and three starter roles. Everything else emerges from use. The system builds its own structure organically.

**What happens during a rebuild?**
The boot sequence detects an existing installation and offers to rebuild. It reads your preferences (preserved as-is), decision log (used as guidance), and task history (used to prioritize). Operations are reconstructed from scratch using the current model's capabilities. Your team may come back with the same names and better skills, or the system may propose structural changes based on what it learned.

## Contributing

MercuryOS is early. If you try it and find something that should work differently, open an issue. Pull requests welcome for:

- Boot prompt improvements
- Platform-specific setup guides
- Documentation

## License

[MIT](LICENSE)
