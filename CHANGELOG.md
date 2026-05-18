# Changelog

All notable changes to the AIS Spec framework are documented here.

This project follows Semantic Versioning. Releases are created automatically
from merged pull requests.

## [0.15.1] - 2026-05-14

### Changed

- chore: remove .github/copilot-instructions.md and .cursorrules from generated outputs ([#141](https://github.com/ais-internal/ais-spec/pull/141))

Removed `.github/copilot-instructions.md` and `.cursorrules` from generated outputs. `AGENTS.md` is the canonical instructions file for Copilot; Cursor uses `.cursor/skills/`.

Fixes #140

Coded with [AIS-spec](https://github.com/ais-internal/ais-spec)

## [0.15.0] - 2026-05-13

### Added

- Add AIS Spec upgrade guide and skill ([#135](https://github.com/ais-internal/ais-spec/pull/135))

Adds an AIS Spec upgrade guide and `ais-spec-upgrade` Agent Skill for changelog-driven, drift-aware project framework upgrades.

## [0.14.0] - 2026-05-13

### Added

- Add AIS brainstorming, implementation gates, and debug command ([#133](https://github.com/ais-internal/ais-spec/pull/133))

Add optional `/ais.spec.brainstorm`, add `/ais.maintain.debug`, and strengthen AIS implementation execution with review gates, evidence-before-completion, optional worktree isolation, root-cause recovery handoff, and enhanced implementation-plan standards.

## [0.13.0] - 2026-05-12

### Added

- [SPEC]: Add project retrospective reporting command ([#131](https://github.com/ais-internal/ais-spec/pull/131))

Add `/ais.report.retrospective`, an internal report command for start/stop/continue project retrospectives focused on spec-driven delivery adoption, qualitative drift, delegation, and AIS Specify improvement opportunities.

## [0.12.0] - 2026-05-12

### Added

- [SPEC] Add proposal redline DOCX skill ([#127](https://github.com/ais-internal/ais-spec/pull/127))

Adds an AIS proposal redline DOCX skill for preserving reviewed pink drafts while applying tracked red-draft revisions and comment responses.

Closes #126

## [0.11.0] - 2026-05-12

### Added

- [SPEC] Implement AIS metrics reporting ([#130](https://github.com/ais-internal/ais-spec/pull/130))

release:minor: Adds the `/ais.report.metrics` outcome metrics reporting command, metrics report template, automated metrics workflow, and compact metrics rollups for project and status reports.

## [0.10.0] - 2026-05-05

### Added

- feat: Add ais-branding-docx Agent Skill ([#125](https://github.com/ais-internal/ais-spec/pull/125))

Adds `ais-branding-docx` Agent Skill for generating AIS-branded Word documents (.docx) from structured JSON input. Supports 13 content block types (headings, body text, bullets, numbered lists, tables, code blocks, and more), real TOC field codes, inline formatting (bold, italic, code), nested list levels 0–3, and 8-point OOXML validation. Includes JSON Schema, AIS-branded template, example inputs, and pre-generated outputs for visual review.

## [0.9.0] - 2026-05-04

### Added

- feat: add ais-branding-pptx implicit skill ([#123](https://github.com/ais-internal/ais-spec/pull/123))

Adds `ais-branding-pptx` implicit Agent Skill for enforcing AIS brand identity across PowerPoint and Word outputs. Includes color palette, typography, logo usage, layout system, design principles, and quality checklist. Also adds `Skills/` directory with README linking to the [Agent Skills specification](https://agentskills.io/specification).

## [0.8.0] - 2026-05-04

### Added

- feat: add ais-proposal-docx skill and Skills directory ([#121](https://github.com/ais-internal/ais-spec/pull/121))

Adds `Skills/` directory and the first Agent Skill (`ais-proposal-docx`) for generating AIS-branded proposal Word documents from structured JSON input. Skills follow the open [Agent Skills specification](https://agentskills.io/specification). The generator includes built-in OOXML validation to catch common Word errors before submission.

## [0.7.0] - 2026-05-01

### Added

- feat: proposal evaluation strategy — outline, win themes, page budgets, eval-criteria mapping ([#119](https://github.com/ais-internal/ais-spec/pull/119))

Adds proposal evaluation strategy to the pre-sales workflow: evaluation-criteria extraction from solicitations, human-reviewed proposal outlines with page budgets, win themes as a first-class concept, and evaluation response cross-reference matrices. All features activate conditionally when source material contains published evaluation criteria.

## [0.6.3] - 2026-04-28

### Changed

- chore: bump actions/checkout from 4 to 6 ([#112](https://github.com/ais-internal/ais-spec/pull/112))

Updates actions/checkout from 4 to 6.

## [0.6.2] - 2026-04-28

### Changed

- fix: keep release changelog markdown clean ([#114](https://github.com/ais-internal/ais-spec/pull/114))

Keeps generated release changelog entries markdown-clean and supports Dependabot patch release notes.

## [0.6.1] - 2026-04-28

### Changed

- chore: bump DavidAnson/markdownlint-cli2-action from 19 to 23 ([#111](https://github.com/ais-internal/ais-spec/pull/111))

Updates DavidAnson/markdownlint-cli2-action from 19 to 23.

## [0.6.0] - 2026-04-28

### Added

- chore: harden repository CI and docs ([#110](https://github.com/ais-internal/ais-spec/pull/110))

Hardens repository CI, release app configuration, dependency update policy, and maintainer documentation.

## [0.5.0] - 2026-04-27

### Added

- Define pre-sales scoping, estimation, and replanning model ([#107](https://github.com/ais-internal/ais-spec/pull/107))

release:minor: Adds pre-sales SOW template routing for Microsoft End Customer Investment Funds (ECIF) and client SOWs, plus draft commercial-model templates for FFP, outcome-driven, managed capacity, and time-and-materials engagements.

## [0.4.2] - 2026-04-27

### Changed

- Add release PR lookup fallback ([#109](https://github.com/ais-internal/ais-spec/pull/109))

release:patch: Makes release PR metadata lookup reliable for squash merge commits when the commit-to-PR API returns no results.

## [0.4.1] - 2026-04-27

### Changed

- Repair semantic release automation ([#108](https://github.com/ais-internal/ais-spec/pull/108)).

release:patch: Fixes semantic release automation so release commits can be
pushed by the dedicated release GitHub App and missed releases are backfilled.

## [0.4.0] - 2026-04-27

### Added

- Add Azure discovery to custom app playbook ([#105](https://github.com/ais-internal/ais-spec/pull/105)).

Adds Azure environment and deployment discovery guidance to the custom
application playbook, including prerequisites, access, governance, networking,
ownership, quota, approval, and deployment-hand-off concerns.

## [0.3.0] - 2026-04-27

### Added

- Add PR-driven semantic release automation ([#106](https://github.com/ais-internal/ais-spec/pull/106)).

Adds automated semantic release enforcement for every pull request.

## [0.2.0] - 2026-04-22

### Added

- Added the Copilot Readiness playbook for Microsoft 365 Copilot, Data Security, and AI Readiness engagements ([#101](https://github.com/ais-internal/ais-spec/pull/101)).
- Added the AIS-spec improvement loop guide for routing delivered-project lessons back into framework improvements ([#94](https://github.com/ais-internal/ais-spec/pull/94)).
- Added `implementation-plan.md` as an optional first-class artifact for larger or riskier specs ([#93](https://github.com/ais-internal/ais-spec/pull/93)).

### Changed

- Disabled the scheduled daily standup report while preserving manual and reusable workflow entry points ([#92](https://github.com/ais-internal/ais-spec/pull/92)).

## [0.1.0] - 2026-04-19

### Added

- Established the AIS Spec framework baseline before the week of April 20, 2026.
