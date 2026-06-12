<!-- Sync Impact Report
Version change: 0.0.0 (uninitialized) → 1.0.0 (MAJOR — initial ratification)
Modified principles: N/A (first version)
Added sections:
  - Principle I: Best Practice Implementation
  - Principle II: Code Quality First
  - Principle III: Test Coverage Standards
  - Principle IV: Commit Standards
  - Principle V: Simple & Maintainable
  - Principle VI: No Deprecated Dependencies
  - Development Workflow
  - Governance
Removed sections: None
Templates requiring updates:
  - .specify/templates/plan-template.md ✅ no changes needed (Constitution Check section is generic)
  - .specify/templates/spec-template.md ✅ no changes needed (no constitution-specific references)
  - .specify/templates/tasks-template.md ✅ no changes needed (task structure compatible)
Follow-up TODOs: None
-->

# VDrawer Constitution

## Core Principles

### I. Best Practice Implementation

All features MUST follow Web/frontend development best practices or
widely recognized architectural patterns. This includes but is not
limited to: responsive design, accessibility standards, semantic
markup, proper separation of concerns, and framework-recommended
patterns. Deviation from established best practices MUST be
justified in the implementation plan's Complexity Tracking section.

### II. Code Quality First

All code MUST pass quality gates before being committed. Quality
gates include:

- **Logic error checks**: No known logic defects in committed code
- **Performance optimization**: No unnecessary re-renders, redundant
  computations, or memory leaks
- **Memory leak detection**: Event listeners, timers, and
  subscriptions MUST be properly cleaned up
- **Static analysis**: Linting and type checking MUST pass with
  zero errors

Each commit MUST demonstrate that these checks have passed.

### III. Test Coverage Standards

Testing requirements by category:

- **Core business logic** (voice instruction parsing, drawing
  execution engine, state management): MUST achieve ≥80% unit test
  coverage. Critical paths MUST achieve 100% coverage.
- **Functional modules** (instruction decomposition, voice-to-
  drawing mapping): MUST have unit tests written.
- **UI tests**: MUST cover primary user flows to ensure pure-voice
  operation interactions are reliable.

### IV. Commit Standards

All Git commits MUST follow Conventional Commits specification:

- `feat:` — New features (e.g., new voice instruction parsing)
- `fix:` — Bug fixes
- `docs:` — Documentation updates (design docs, instruction
  support notes)
- `test:` — Test-related changes

Co-author metadata (e.g., `Co-Authored-By` trailers) MUST NOT be
included in commit messages.

### V. Simple & Maintainable

Functional modules MUST follow single responsibility:

- **Voice recognition**, **instruction parsing**, and **drawing
  execution** modules MUST be separated.
- Prefer composition, event-driven design, or modular patterns
  over complex inheritance or deep nesting.
- Apply YAGNI principle: implement only currently required
  instruction features. Avoid over-engineering.

### VI. No Deprecated Dependencies

All APIs, libraries, and language features used MUST be actively
maintained and not deprecated. Before adding a dependency, verify
its maintenance status and deprecation timeline.

## Development Workflow

### Quality Gate Sequence

1. Lint and type-check pass
2. Unit tests pass with required coverage
3. Integration/UI tests pass for affected user flows
4. Manual verification of voice interaction paths (when applicable)

### Module Boundaries

Voice recognition, instruction parsing, and drawing execution
modules MUST communicate through well-defined interfaces. Direct
cross-module state mutation is prohibited.

## Governance

This constitution supersedes all other development practices for
the VDrawer project. Amendments MUST:

1. Be documented with rationale
2. Update the version number following semantic versioning:
   - MAJOR: Backward-incompatible governance/principle removals
     or redefinitions
   - MINOR: New principle/section added or materially expanded
   - PATCH: Clarifications, wording, typo fixes
3. Propagate changes to dependent templates (plan, spec, tasks)
4. Include a Sync Impact Report as an HTML comment at the top
   of this file

Compliance reviews MUST occur during plan Constitution Check
gates and during code review.

**Version**: 1.0.0 | **Ratified**: 2026-06-12 | **Last Amended**: 2026-06-12
