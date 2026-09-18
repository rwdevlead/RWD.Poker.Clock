# PROJECT_CONTEXT.md — Long-Term Project Context

## 1. Project Overview

- **Project Name:** RWD.Poker.Clock

- **Purpose:**  
  A cross-platform Texas Hold'em poker tournament clock that tracks tournament time, blind levels, betting-related information, and chip denominations. The application provides players with a clear, easy-to-read display showing the current level, remaining time, current and upcoming blinds, and the values of the colored chips in use.

- **Primary Goals:**
  - Provide a simple, reliable poker tournament clock.
  - Run on mobile devices, tablets, and laptops.
  - Function fully without an internet connection after installation.
  - Clearly display the current blind level and time remaining.
  - Clearly indicate upcoming blind levels and changes.
  - Provide a configurable chip-value legend based on the chips being used.
  - Support common Texas Hold'em tournament structures.
  - Make tournament configuration quick and straightforward.
  - Preserve tournament state if the application is temporarily closed or the device is interrupted.
  - Provide a responsive interface suitable for both small mobile screens and larger laptop displays.
  - Minimize dependencies on external services or network connectivity.

## 2. Technical Stack & Dependencies

- **Core Languages & Frameworks:**
  - TypeScript / JavaScript
  - React (under evaluation as primary front-end framework)
  - HTML5 / CSS
  - Progressive Web App (PWA) standards (Service Workers, Web App Manifest)
  - Runtime / Build tooling: Vite or comparable modern bundler (to be finalized)

- **Database & Storage:**
  - Browser-local persistent storage for tournament configuration and runtime state.
  - IndexedDB preferred for structured client-side application data (e.g., via Dexie.js or native IDB).
  - LocalStorage / SessionStorage for light preferences.
  - No server-side database required for the core application.

- **Key Libraries / Infrastructure:**
  - PWA service worker and web manifest for offline-first capability.
  - Browser APIs for persistent storage, wake lock (prevent screen sleep during tournament), audio/beeps for level changes.
  - Test framework (e.g. Vitest, React Testing Library).
  - Avoid unnecessary external dependencies; prioritize local, reliable offline execution.

## 3. Architecture & Core Patterns

- **Architecture Pattern:**
  - Offline-first Progressive Web Application.
  - Client-side application architecture with clear separation between UI, tournament engine/application logic, domain models, and persistence.
  - Core tournament timing, rule enforcement, and state transitions must remain pure/deterministic and testable independently of React components.

- **Directory Layout:**
  - To be determined during architectural design and planning.

- **Canonical Design Decisions:**
  - The application is **offline-first**; an internet connection is not required during normal tournament operation.
  - Tournament state belongs to the client and should persist locally.
  - Core tournament rules and timing calculations must not depend on UI components.
  - The timer must be based on elapsed time rather than UI refresh intervals so that display refreshes do not affect tournament timing.
  - The application should use a single authoritative tournament state rather than allowing individual UI components to maintain independent copies of tournament state.
  - Configuration and runtime tournament state should be modeled separately.
  - External services and APIs are not required for the core poker-clock functionality.
  - The architecture should leave room for future synchronization, sharing, or remote-control functionality without making those capabilities prerequisites for the initial application.

## 4. Domain & Data Concepts

- **Core Domain Entities:**
  - Tournament
  - Tournament Configuration
  - Blind Level
  - Blind Structure
  - Tournament Timer
  - Break
  - Chip Denomination
  - Chip Set / Chip Configuration
  - Tournament State

- **Business Rules:**
  - A tournament consists of an ordered sequence of blind levels and optional breaks.
  - Each blind level has a defined duration.
  - Each blind level defines the small blind and big blind values.
  - The application identifies the current blind level based on tournament elapsed time.
  - The application identifies the next blind level and its effective time.
  - The timer must accurately track elapsed and remaining tournament time.
  - Pausing the tournament must stop the tournament clock without losing the current tournament position.
  - Resuming the tournament continues from the paused position.
  - Advancing to the next level must update the displayed blind information.
  - Breaks are represented as scheduled periods within the tournament structure.
  - Chip denominations are configurable and independent of the blind structure.
  - Each chip denomination has a color and monetary/value amount.
  - The chip legend displays the configured chip colors and values.
  - Tournament state must survive normal browser/application closure and reopening.
  - Invalid tournament configurations should be rejected before a tournament is started.
  - The system should prevent ambiguous or contradictory tournament states.

## 5. Constraints & Non-Goals

- **Hard Constraints:**
  - Must run on mobile devices and laptops.
  - Must support modern browsers.
  - Must operate without an internet connection after the application has been installed/cached.
  - Must be usable in a live poker environment where information needs to be immediately visible.
  - Timer accuracy must not depend on browser rendering frequency.
  - The UI must be responsive across substantially different screen sizes.
  - Tournament configuration must be stored locally.
  - The application should not require user accounts for core functionality.
  - The initial application should not require a server, external API, or cloud database to conduct a tournament.
  - The application should remain functional when network connectivity is unavailable.

- **Explicit Non-Goals:**
  - Managing individual player accounts.
  - Tracking individual player chip counts.
  - Processing or managing monetary transactions.
  - Online poker gameplay.
  - Providing a poker game engine.
  - Tracking individual hands or cards.
  - Providing player statistics or rankings.
  - Requiring cloud synchronization for normal operation.
  - Requiring an internet connection to run a tournament.
  - Becoming a general-purpose poker management platform in the initial release.

## 6. Architecture & Milestone Log

- `2026-09-18`: Initialized project context from RWD.Ai.Stack starter kit.
- `2026-09-18`: Established initial requirements for an offline-first Texas Hold'em poker tournament clock.
- `2026-09-18`: Dropped Blazor from technology considerations per architectural guidance. Shifted focus to design and planning with React / TypeScript PWA as primary candidate.
