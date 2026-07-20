# Personal Chief of Staff

A template for running your life with an AI Chief of Staff built on [Claude Code](https://claude.com/claude-code).

Not a scheduling app. A system with four parts:

1. **A constitution** (`CLAUDE.md`) — who your COS is, what zones of your life it runs, what it may do autonomously, and what it must never do.
2. **Memory** (`memory/`) — who you are, open loops, how long your tasks *actually* take, and a log of every session. This is how it learns your behaviors instead of resetting every morning.
3. **Tools** (`Tools/`) — scripts your COS writes for itself and reuses.
4. **A heartbeat** — a scheduled job that wakes it every morning to plan your day unattended, with a hard safety rule: the unattended run has **no send-message capabilities**. It can prepare drafts; it can never speak as you.

## File map

```
personal-chief-of-staff/
├── CLAUDE.md                    # the constitution — edit every [PLACEHOLDER]
├── memory/
│   ├── memory.md                # stable facts: who you are, preferences, key people
│   ├── context.txt              # open loops — updated every session
│   ├── task_durations.md        # learned time-calibration table
│   └── conversations/           # one log per day, written automatically
└── Tools/
    └── morning_briefing.sh      # the 7:30 AM heartbeat script
```

## Setup

1. **Install Claude Code** and sign in.
2. **Clone this repo** somewhere permanent (e.g. `~/PersonalChiefOfStaff`).
3. **Fill in `CLAUDE.md`** — every `[PLACEHOLDER]`. Define your own focus zones (mine are Social & Travel, Career, Personal Projects, Health & Fitness, Admin — yours will differ). For each zone: its tasks, its autonomous agents, its guardrails.
4. **Connect your systems** — add the MCP connectors your COS should use (calendar, tasks/Notion, email read-only). Task source of truth + writable calendar are the minimum.
5. **Run one day manually.** Open Claude Code in the folder and say "run the daily routine." Correct everything it gets wrong — *those corrections are the training data.* Tell it to save each correction as a dated rule in `CLAUDE.md` or `memory/`.
6. **Automate the heartbeat.** Edit the paths in `Tools/morning_briefing.sh`, then register it (macOS: `launchd`; Linux: cron). Keep the allowlist restriction — the unattended run must not have email/message tools.

## The learning loop (the part that matters)

Your COS gets good the same way a human chief of staff does: feedback becomes standing rules.

- "The workout should be evenings, midday is too hot" → it rewrites the rule, stamps the date.
- A task took 2× the blocked time → `task_durations.md` gets a new learned estimate.
- "Ignore most of what you find — only surface what truly fits me" → selectivity becomes policy.

Correct it out loud, make it write the correction down, and within weeks the calendar it builds stops feeling like a robot's and starts feeling like yours.

## Safety defaults

- Unattended runs: read + schedule only. **No send.**
- Outbound anything (email, message, money, commitments): draft & confirm, always.
- Meetings with real people are immovable by default.

---

Built by [DCZ](https://dcz.me) — the original write-up lives at [dcz.me/#/chief-of-staff](https://dcz.me/#/chief-of-staff).
