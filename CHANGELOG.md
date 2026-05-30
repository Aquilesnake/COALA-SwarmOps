# Changelog

All notable changes to COALA SwarmOps will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [Unreleased]

### Added (2026-05-27 — Foundation Phase)
- `FOUNDATION.md` — The v6.2 Covenant: origin story, architecture snapshot, evolution path, score card baseline (78/100)
- `FOUNDATION_ES.md` — Spanish translation
- `STRATEGY.md` — Market vision, competitive positioning, open-core model, release strategy, risk mitigation
- `STRATEGY_ES.md` — Spanish translation
- `PHILOSOPHY.md` — Design principles, anti-patterns, operational philosophy
- `PHILOSOPHY_ES.md` — Spanish translation
- `CONTEXT.md` — Master continuity document preserving full project history across conversations
- `CONTRIBUTING.md` — Contributor guide: SDD workflow, code standards, PR process
- `CONTRIBUTING_ES.md` — Spanish translation
- `next_steps_evolution.md` — Ecosystem expansion plan: dual-layer evolution, projected repo structure
- `next_steps_evolution_ES.md` — Spanish translation
- `docs/ECOSYSTEM_CONTEXT.md` — 4-repo ecosystem map (COALA → tancerca → fuente-de-datos → imp.bodegamk)
- `docs/BUSINESS_STRATEGY.md` — Positioning strategy for top 10 worldwide, monetization model ($1M ARR target)
- `docs/COST_TRACKER.md` — Per-feature cost traceability system
- `docs/HERMES_NEXUS_ROADMAP.md` — Hermes + GitNexus + Nexus 4-phase roadmap (Q3 2026 → Q2 2027)
- `docs/INSTALL.md` — Quick install guide for Windows, Linux, macOS
- `docs/PRICES.md` — API pricing truth source (updated every 30 days)
- `docs/USER_GUIDE.md` — Step-by-step manual for clients
- `docs/architecture/ARCHITECTURE.md` — Technical architecture decisions (EN+ES)
- `docs/terminology/TERMINOLOGY.md` — Swarm glossary (EN+ES)
- `img/score_claude.png` — Claude benchmark evidence
- `LICENSE` — MIT License
- `.gitignore` — Comprehensive ignore rules
- `.github/FUNDING.yml` — GitHub Sponsors configuration
- `.github/ISSUE_TEMPLATE/` — Bug report and feature request templates
- `.github/PULL_REQUEST_TEMPLATE.md` — PR checklist aligned with SDD pipeline
- `SECURITY.md` — Vulnerability reporting and security architecture
- `CODEOWNERS` — Repository ownership rules
- `CHANGELOG.md` — This file

### Changed
- `README.md` — Updated with ecosystem context, quick install, documentation table, contributing section

---

## [v6.2] — 2025-2026 — Operational Stable Swarm

### Foundation
- 18 agents defined across 4 tiers (T0-T3)
- Cost-aware routing: T0 ($0 local) → T3 (~$3.49 cloud)
- Circuit breaker pattern for error learning
- 1-fail escalation (T0 fail → immediate T1)
- Specification-Driven Development (SDD) workflow

### Windows-Native Support
- Port of mhito/ai to native Windows 10
- Git Bash compatibility layer
- 87/96 tests passing on Windows
- Ollama, Groq, DeepSeek integration

### Ecosystem
- TanCerca.cl ecommerce platform
- img.bodegamk.cl Dockerized infrastructure
- Multi-project DevOps orchestration

---

## [v1-v5] — 2024-2025 — Experimental

- Manual orchestration workflows
- Fragmented agent prototypes
- Infrastructure experimentation
- Pre-swarm operational concepts

---

*Changelog maintained by COALA SwarmOps / context-guardian.*
