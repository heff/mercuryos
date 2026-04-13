# MercuryOS

**One prompt to boot your personal AI operating system.**

An AI-independent orchestration layer that works with any tool that has filesystem access and sub-agent capability. Paste a single prompt into an empty directory. It builds the rest. You talk to Mercury — Mercury talks to the team.

## Quick Start

1. Create an empty directory
2. Open it in your AI tool of choice
3. Paste the contents of [`prompt.md`](prompt.md) and run it

Mercury boots with a starter team of three and is ready for your first request.

### Platform Notes

**Claude Code** — Open the directory, paste the prompt. The Agent tool provides sub-agent capability out of the box. Set your `CLAUDE.md` as the system prompt.

**Codex** — Use the prompt as your system instructions. Codex supports file creation and sub-agent dispatch. Point it at the directory and paste the prompt as your first message.

**Other tools** — Any AI tool that can (a) read and write files and (b) spawn sub-agents or equivalent can run MercuryOS. Adapt the dispatch mechanism to your tool's agent/function-calling pattern.

## What You Get

- **Mercury** — the orchestrator. Routes requests, never does work directly. The only agent you talk to.
- **Three starter roles** — a researcher, an HR lead, and a product manager. They get named during boot using your chosen naming convention (default: Roman gods, each name meaningful to the role).
- **Three-layer architecture** — preferences, decisions, and operations, separated by durability.
- **Task and decision logging** — a record of what was asked and what choices were made, used for rebuilds.

## The Three-Layer Architecture

MercuryOS separates your data into three layers based on how long they last.

**Preferences (most durable)** — Who you are. Facts, preferences, values, heuristics, constraints, salience, current contexts. Organized by cognitive primitive type. This layer is fully portable: copy it to any AI system and it knows you. Survives complete rebuilds.

**Decisions (medium durable)** — Choices made while building and operating the system. Each entry logs what was decided, why, what alternatives were considered, and which task prompted it. On a rebuild, the new system reads these as guidance rather than gospel — it can make different choices with better reasoning.

**Operations (least durable)** — The OS itself: team roster, routing logic, personas, conventions, workflows. This is the layer that gets rebuilt when you upgrade. It is a product of the prompt plus your preferences and decisions, not a thing you preserve.

The key insight: when you separate identity from machinery, you can replace the machinery without losing yourself.

## How It Grows

**Auto-hiring.** Ask for something no one on the team handles. Mercury has the researcher investigate the role, the HR lead design a new team member, and presents you with a name and summary. You approve, they join the team. The team grows to match your usage.

**Task logging.** Every request is recorded. Over time this builds a capability map — what you actually use the system for. Rebuilds can read this to prioritize which roles to recreate first.

**Decision logging.** When the system makes a structural choice (naming convention, file organization, workflow design), it logs the decision with context. Future versions inherit your decisions without inheriting your implementation.

**Preference capture.** As you work, team members watch for signals — facts, preferences, values, patterns — and write them to the appropriate preference file. The system gets better because it knows you better.

## Upgrades and Rebuilds

This is the core design bet. When a better AI model ships:

1. Start a fresh session with the original prompt
2. Point it at your existing MercuryOS directory
3. It reads your preferences, decision log, and task history
4. It rebuilds operations from scratch — new personas, new workflows, informed by everything that came before

The prompt is a seed, not a blueprint. Each rebuild produces a system shaped by your actual usage, not by the assumptions of the original author. Preferences persist. Decisions provide guidance. Operations get rebuilt better.

You never migrate. You replant.

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
Preferences (who you are, most durable), decisions (choices made, medium durable), operations (the system itself, least durable). Preferences survive everything. Operations get rebuilt on upgrade.

**Can I modify team members?**
Yes. Edit any persona file, or ask Mercury to redesign a member through the HR lead. Everything is markdown.

**What's with the mythological names?**
The default naming convention uses Roman gods, each chosen for a meaningful connection to the role. The convention is configurable — you can use any naming scheme. The HR lead maintains consistency.

**How is this different from a fixed agent framework?**
No predefined file structure. No hardcoded team. The prompt creates an orchestrator and three starter roles. Everything else emerges from use. The system builds its own structure organically.

**Does a rebuild lose my team?**
It rebuilds your team. The decision log records why each member was created and how they were designed. A rebuild reads that history and recreates what you need — potentially better, since the new model may be more capable.

## Contributing

MercuryOS is early. If you try it and find something that should work differently, open an issue. Pull requests welcome for:

- Boot prompt improvements
- Platform-specific setup guides
- Documentation

## License

[MIT](LICENSE)
