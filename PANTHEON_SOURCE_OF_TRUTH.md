# Pantheon Source of Truth

> GENERATED — do not hand-edit. Generated: 2026-06-18T18:17:45Z

## What Pantheon Is
Deterministic in-house cognition+generation runtime (own vGPU/wafer compute + 452M ConceptNet language lattice + deterministic solvers + curated code emitter + IPU materialization). NOT an LLM, never a third-party model.

## Current Highest Blocker
LIVE_CHAT_CAPABILITY_GAP

## Answer Contract
- RULE: answer like a regular chatbot for everything, deterministic
- BANNED: abstain, I don't know, I can't verify, not grounded, canned non-answer
- ALLOWED FALLBACK: I'm not quite sure about that. Let me check on it for you. (then resolve + return)
- FALLBACK BUDGET: <=1/1000
- FALLBACK MECHANISM: trigger Ising model (params/values/spins) + web research + lattice retrieval; Ising-first

## Conveyance Path
FOUNDER_INTENT -> CLAUDE(director) -> PANTHEON intent_inbox.jsonl -> pantheon-intent-realizer -> MISSION_CONTROL -> WORKER (/v1/author) -> PROOF -> DIRECTOR_REPORT

## Open Blockers
- [BLOCKER] LIVE_CHAT_CAPABILITY_GAP: /v1/chat: facts+reasoning pass; 321 abstain matches; coding gen + open-domain synthesis fail/abstain
- [MAJOR] USER_CAN_PAY: Stripe creds present; end-to-end pay flow unproven

## Proven
- PHASE_1 AUTHOR_ENGINE_V1: create_test_file + create_function lanes author real files, cargo-check + cargo-test, real live HEAD move (VERIFY_1/2/3 pass)
- PHASE_2 FALSE_COMMIT_PROOF closed: committed gated on live HEAD advance (create lanes)
- routing: build-class intents reach /v1/author
- intent conveyance: founder intent -> intent_inbox -> realizer -> MC autopilot
- 452M lattice live (:7878), graph synthesis live
- live /v1/chat: facts (Paris), reasoning (syllogism), science (Rayleigh), comparison pass
- authority externalized -> public mirror 0xerodev/pantheon-status (ChatGPT-readable, auto-published)

## Go-Live Target
- SCOPE: whole 847-component atlas
- BAR: frontier or above
- PRIORITY_1: conversational + coding general understanding + replies
- 90-day sim: REMOVED 2026-06-18
- Stripe: set up by founder
