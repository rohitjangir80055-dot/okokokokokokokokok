# MASTER PROMPT — Google AI Studio

You are rebuilding a NEW, independent desktop application based on the supplied
Munder Difflin reference source.

IMPORTANT:
- Do NOT merely rename the original app.
- Do NOT delete functionality to simplify the project.
- First inspect ALL supplied source, specifications, assets, package configuration,
  tests and documentation.
- Build an independent implementation with the same observable product behavior,
  architecture concepts, workflows and major UI/UX.
- Preserve attribution/license requirements for any supplied third-party artwork.
- Never copy secrets or credentials.
- Do not include node_modules or generated build output in the project.

## PRODUCT TARGET

Create a polished multi-agent AI software company/office desktop application.

The user should be able to:
1. create/manage AI agents;
2. run real CLI agents in terminals;
3. assign work to agents;
4. let a supervisor/orchestrator route work;
5. allow agents to communicate through a persistent coordination system;
6. watch agents live in a pixel-art office;
7. inspect tasks, memory, files, code and Git changes;
8. configure AI providers;
9. use schedules, webhooks and integrations;
10. recover from failed/stopped agents safely.

## REQUIRED ARCHITECTURE

Electron desktop application:
- Main process: privileged operations and orchestration
- Preload: typed/safe IPC bridge
- Renderer: React UI
- Shared: types/contracts/provider abstractions

Core systems:
- PTY manager
- xterm.js terminal
- agent/provider abstraction
- Hive coordination
- SQLite persistence
- Git integration
- memory and knowledge graph
- supervisor/GOD/Michael orchestration
- Pixi.js office
- task/Kanban system
- IDE/editor
- integrations
- schedules/triggers
- telemetry/cost/budget controls
- recovery/circuit breaker

## HIVE COORDINATION

Implement the supplied HIVE specification faithfully.

Conceptual structure:

hive/
  PROTOCOL.md
  registry.json
  board.md
  tasks.json
  log.jsonl
  agents/<agent-id>/
    identity.md
    memory.md
    inbox/
    inbox/.done/
    outbox/
    cursor.json

Rules:
- Main process is the single committer for coordination Git.
- Each agent writes only to its own directory.
- Cross-agent messages are delivered by the router.
- Messages are atomic.
- log.jsonl is append-only.
- Consumers maintain cursors.
- Message IDs are idempotent.
- Use hop limits and escalate unresolved chains.

Message fields:
id, conversation, in_reply_to, from, to, act, subject, body,
hops, requires_reply, needs_human, created_at

Acts:
request, inform, propose, query, agree, refuse, done

## SUPERVISOR / MICHAEL

Create an always-on supervisor agent called Michael/GOD.

Michael must:
- understand roster and capabilities;
- route tasks to specialists;
- coordinate multi-agent work;
- maintain the task ledger/blackboard;
- request clarification when necessary;
- retry/recover work;
- escalate destructive, costly, ambiguous or permission-sensitive actions;
- monitor agent health;
- use tools/IPC rather than hard-coded fake behavior.

Do not make Michael a static mock chatbot. It must be connected to actual agent state.

## REAL AGENTS

Use a provider adapter architecture supporting the providers represented
in the reference project, including:
- OpenAI Codex
- Claude Code
- Gemini/Antigravity
- Grok
- Kimi
- Qwen
- OpenCode
- Crush
- pi
- GitHub Copilot CLI
- custom commands

Provider-specific command construction belongs in adapters.

The generic lifecycle must support:
spawn → terminal stream → tool/event parsing → Hive context →
work → Stop/hook checks → inbox/outbox delivery → persistence → recovery.

## OFFICE UI

Reproduce the reference product's distinctive pixel-art office concept:
- tiled office maps;
- desks/seats;
- agent character sprites;
- movement/pathfinding;
- camera;
- office themes;
- thought/tool/message bubbles;
- message envelopes;
- live state animations.

Office state must be driven by actual agent events, not only decorative animation.

## COMMAND CENTER

Include:
- agent strip/cards;
- command center;
- tasks/Kanban;
- activity;
- agent detail;
- terminal;
- files;
- IDE;
- Git changes/history/compare;
- memory;
- memory graph;
- skills;
- triggers;
- schedules;
- webhooks;
- integrations;
- AI/provider settings;
- onboarding;
- setup/prerequisite checks;
- budget/cost information;
- blocked/recovery banners.

## IDE + GIT

Provide:
- file tree;
- editor;
- image preview where appropriate;
- changes;
- diff;
- history;
- commit graph;
- guarded branch/checkout operations.

## SAFETY

Never expose API keys to renderer or logs.

Implement:
- permission gates;
- budget/spend limits;
- circuit breaker;
- process recovery;
- terminal recovery;
- path validation;
- idempotency;
- stale-state recovery;
- telemetry controls;
- durable usage/cost ledger.

## DEVELOPMENT ORDER

Do not try to implement everything in one giant step.

Phase 0:
- inspect all supplied files;
- produce architecture map;
- identify dependencies;
- identify missing/broken imports;
- identify platform-specific code;
- produce implementation checklist.

Phase 1:
- Electron + React + TypeScript shell;
- main/preload/renderer;
- typed IPC.

Phase 2:
- PTY + xterm;
- one real provider;
- spawn/write/resize/kill/recovery.

Phase 3:
- Hive registry/memory/inbox/outbox/tasks/board/log;
- router;
- persistence;
- tests.

Phase 4:
- Michael/GOD orchestration;
- real task dispatch;
- escalation/retry.

Phase 5:
- Pixi office;
- maps/assets;
- seats;
- avatars;
- movement;
- live event state.

Phase 6:
- Command Center;
- Kanban;
- memory;
- skills;
- schedules/triggers.

Phase 7:
- IDE/Git.

Phase 8:
- provider expansion;
- Slack/webhooks;
- voice/realtime;
- BYOK/local model configuration.

Phase 9:
- tests;
- security;
- recovery;
- packaging.

## VALIDATION

Before calling the project complete:
- run typecheck;
- run unit/integration tests;
- verify imports;
- verify IPC contracts;
- verify agent spawn;
- verify terminal interaction;
- verify two-agent messaging;
- verify Michael routing;
- verify Hive persistence;
- verify office reflects agent state;
- verify task creation/completion;
- verify Git diff/history;
- verify recovery after process failure.

## FIRST ACTION

Do NOT immediately start writing random UI.

First:
1. inspect the entire supplied repository;
2. read README.md, SPEC.md, HIVE.md, DESIGN.md,
   MEMORY_GRAPH_SPEC.md, SECURITY.md and TELEMETRY.md;
3. map all source directories and major components;
4. inspect package.json and scripts;
5. detect missing imports/dependencies;
6. create a `REBUILD_PLAN.md`;
7. only then start implementation.

The final result must be a genuinely working independent project,
not a static mockup.
