# AGENTS.md — Project AI Assistant Guide

This file provides instructions for AI agents assisting developers on this project.

## Project Overview

- **Project Name:** RWD.Poker.Clock
- **Description:** A cross-platform Texas Hold’em tournament clock application that tracks tournament time, blind levels, breaks, and chip denominations, providing clear, real-time information for players and tournament organizers. Designed for reliable offline and cross-platform operation across mobile, tablet, and laptop devices.
- **Technology Stack:** Under active design and planning. Web-first, cross-platform UI with Progressive Web App (PWA) capabilities and client-side persistence. React / TypeScript is under evaluation as the primary UI framework candidate.
- **Source & Directory Layout:** To be finalized during architectural planning prior to code scaffolding.

---

## Agent Responsibilities

1. **High Quality Code:** Write clean, maintainable, well-tested code following project conventions.
2. **Read Before Writing:** Inspect existing code, architecture, and documentation before modifying files.
3. **Preserve Conventions:** Follow existing project patterns, naming conventions, and file organization.
4. **Documentation Sync:** Keep project documentation updated whenever code implementation changes.

---

## Working Rules & Project Standards

All AI assistants must adhere to the mandatory standards in `.agents/standards/`:

- **Coding Standards:** Follow [.agents/standards/coding-standards.md](file:///.agents/standards/coding-standards.md) for clean architecture, separation of concerns, defensive programming, and pre-commit hygiene.
- **Documentation Standards:** Follow [.agents/standards/documentation-standards.md](file:///.agents/standards/documentation-standards.md) for README maintenance and documentation synchronization.
- **Code Documentation & Comments:** Follow [.agents/standards/code-documentation-standards.md](file:///.agents/standards/code-documentation-standards.md). Plain-language comments are required: short statements anyone can follow, one idea per sentence, no jargon, short words over long words, explaining intent (why) rather than restating code.
- **Workflow Standards:** Follow [.agents/standards/workflow-standards.md](file:///.agents/standards/workflow-standards.md) for the 5-phase SDLC (`Orient` -> `Plan` -> `Implement` -> `Verify` -> `Hand Off`).
- **Memory Management:** Follow [.agents/standards/memory-policy.md](file:///.agents/standards/memory-policy.md) to maintain long-term memory in `.agents/memory/PROJECT_CONTEXT.md` and active session tracking in `.agents/memory/AI_HANDOFF.md`.
- **Questions Are Inquiries, Not Edits:** Answer questions and propose actions before making changes; do not execute edits on questions alone.
- **Strict Scope Control:** Do not refactor code outside the defined scope of the instruction without explicit user permission.
- **Selective Verification:** Verify changes with tests or build checks when making functional updates. If writing comments or documentation only, running builds and unit tests is not required.
- **Clear Communication:** Provide concise summaries of work completed and highlight any open questions.
