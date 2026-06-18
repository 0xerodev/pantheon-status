# PANTHEON AUTHORITY

> Canonical authority surface. Read this FIRST — before analysis, planning, coding, or blocker declaration.
> This file is authored/maintained. The state docs it points to are GENERATED (never hand-edit them).

## What Pantheon Is
Deterministic in-house cognition + generation runtime: own vGPU/wafer compute + 452M ConceptNet language
lattice + deterministic solvers + curated code emitter + IPU materialization. **NOT an LLM. Never a third-party
model.** In-house inference only; external models are TEST/BENCH only, never in the product path.

## Authority Surface (single source of continuity)
| Artifact | Role | Edit |
|---|---|---|
| `AUTHORITY.md` | this contract | authored |
| `docs/runtime/PANTHEON_SOURCE_OF_TRUTH.md/.json` | canonical state: what is, blockers, proven, target | GENERATED |
| `docs/runtime/PANTHEON_LIVE_STATUS.md/.json` | live runtime/repo/build/endpoint status | GENERATED |
| `docs/runtime/MISSION_CONTROL_STATE.json` | MC lock rules + conveyance | GENERATED |
| `docs/runtime/PROOF_INDEX.json` | index of proof artifacts | GENERATED |

Public mirror (ChatGPT-readable): `0xerodev/pantheon-status` →
`https://raw.githubusercontent.com/0xerodev/pantheon-status/main/PANTHEON_LIVE_STATUS.md`
`https://raw.githubusercontent.com/0xerodev/pantheon-status/main/PANTHEON_SOURCE_OF_TRUTH.md`

## Authority Path (no one acts as memory layer)
```
FOUNDER_INTENT
  -> CLAUDE (director: convey intent, judge, report — does not code unless granted)
  -> PANTHEON intent_inbox.jsonl
  -> pantheon-intent-realizer (2-min timer)
  -> MISSION_CONTROL autopilot
  -> WORKER (/v1/author: author -> compile -> test -> commit)
  -> PROOF (author_proof.v1, author_events.jsonl, HEAD moves)
  -> DIRECTOR_REPORT
```

## Mission Control Lock (ALWAYS ON)
BEFORE analysis / planning / coding / blocker-declaration, Mission Control and any agent MUST READ:
`AUTHORITY.md` + `PANTHEON_SOURCE_OF_TRUTH.json` + `PANTHEON_LIVE_STATUS.json`. No action from stale snapshots.

## Locks
- **MANUAL_EDIT_LOCK** — `PANTHEON_SOURCE_OF_TRUTH.md/.json` and `PANTHEON_LIVE_STATUS.md/.json` are GENERATED ONLY. Hand-edits are forbidden and CI-rejected.
- **CI_DRIFT_LOCK** — if regenerated authority != committed authority, the build FAILS.
- **DIRECTOR_LOCK** — Claude is director-only; direct file edits require a named, time-boxed founder grant (`~/.claude/runtime/director_mode_off`).

## Answer Contract (the product behavior)
Answer like a regular chatbot for everything, deterministically. BANNED: abstain / "I don't know" / "I can't
verify" / "not grounded" / canned non-answers. Only allowed fallback: *"I'm not quite sure about that. Let me
check on it for you."* — then actually resolve and return. Fallback budget ≤1/1000. Fallback triggers an Ising
resolver (params/values/spins) + web research + lattice retrieval; Ising-first.

## Generator
`scripts/generate_authority.py` — deterministic, replayable, valid JSON via `json.dump` (no heredoc bugs).
Run on pre-commit and in CI; CI pushes the public artifacts to `0xerodev/pantheon-status`.
