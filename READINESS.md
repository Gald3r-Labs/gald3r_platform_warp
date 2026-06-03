# gald3r Readiness Report — Warp

> An honest accounting of how much of the gald3r framework installs natively on this
> platform, what degrades to an approximation, and what has no native home yet.
> Generated from a live documentation crawl on 2026-06-02.

**Overall readiness: ✅ Full.** Warp is an AI terminal with a full agent platform (Oz).
gald3r's rules, agents, skills, and MCP layers all install natively; commands fit partially
through Workflows, and only the hook layer has no native host yet.

## C.R.A.S.H. capability grid

| | Capability | Native? | What gald3r gets here | The gap |
|---|---|:---:|---|---|
| **C** | Commands | ⚠️ | Parameterized Warp Drive Workflows (named, repo/user-scoped, with arguments) + Agent Prompts in the `/` menu | No user-defined `/my-command` syntax — gald3r's `@g-*` set maps to Workflows, not native slash commands (upstream request #6857 open) |
| **R** | Rules | ✅ | `AGENTS.md` (or legacy `WARP.md`) auto-applied from repo root + current dir; Global + Project scopes; Agent Memory for persistence | None — gald3r rules load as first-class Project Rules |
| **A** | Agents | ✅ | Named Agent Profiles (per-profile model, autonomy, tool/MCP allow-deny); Oz orchestrates parallel subagents (swarm, supervisor/worker, critic/verifier) | None — gald3r's `g-agnt-*` roles map to profiles and Oz subagent patterns |
| **S** | Skills | ✅ | Native `SKILL.md` engine (YAML frontmatter + markdown); discovers `.agents/skills/`, `.warp/skills/`, `.claude/skills/`, and more; cross-vendor interop explicit | None — gald3r skills install and invoke directly |
| **H** | Hooks | ❌ | — | No native lifecycle/event hooks; gald3r's `g-hk-*` session-start / pre-tool / pre-commit wiring can't fire (upstream requests #7834 / #6857 open, uncommitted) |

_Legend: ✅ native · ⚠️ partial / approximated · ❌ no native mechanism · ❓ unverified_

**Beyond C.R.A.S.H. — MCP: ✅** Native MCP servers configured in-app (Settings > Agents >
MCP servers); CLI (Command) and Streamable HTTP/SSE types, per-profile access rules, and
env-var/OAuth auth — shared as context across local and cloud (Oz) agents.

## Adoptable extras (non-C.R.A.S.H.)

Platform-native strengths gald3r can lean on, and which need wiring:

| Feature | Status | gald3r fit |
|---|:---:|---|
| Warp Drive Workflows (parameterized, repo/user-scoped commands) | ✅ present | Primary host for gald3r's `@g-*` commands; partially covers the custom-command gap |
| Oz cloud Triggers & Schedules (Slack/Linear/GitHub events, recurring runs) | ⚙️ needs customization | Event-automation surface adjacent to gald3r hooks; could drive scheduled gald3r workflows |
| Multi-harness orchestration (Warp Agent + Claude Code + Codex, shared Agent Memory) | ✅ present | Maps to gald3r's role-based, multi-agent handoff with shared cross-session memory |
| Agent API/SDK (programmatic agent invocation) | ✅ present | A real automation entry point for gald3r tooling |
| Warp Drive store (notebooks, prompts, env vars) · Codebase Context · Web search | ✅ present | Extra knowledge + input surfaces; no gald3r work required |

## The honest ceiling

gald3r adapts to this platform the way any third-party layer must — by mapping our commands, rules, agents, skills, and hooks onto whatever extension points the platform happens to expose. Where those points exist, the fit is clean. Where they don't, adaptation can only *approximate* the real thing — a stand-in that covers the common case but not the edges.

That isn't a knock on the platform. It's the ceiling of bolting *any* framework onto a surface that was never built to host it.

Full functional parity isn't something we can reach from the outside. It lives in the native build — **gald3r_agent**, running on the **gald3r throne** over the **gald3r_world_tree** — where commands, rules, agents, skills, and hooks aren't *adapted* to the platform, they *are* the platform.

> ### gald3r_agent — coming soon. 🌳

---

<sub>Capabilities verified against the platform's official documentation on 2026-06-02, and
re-verified each release via the gald3r platform-docs crawl. This report describes gald3r's
third-party adaptation surface; it is not an endorsement or critique of the platform itself.</sub>
