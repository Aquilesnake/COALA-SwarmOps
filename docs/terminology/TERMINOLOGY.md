# COALA SwarmOps — Terminology & Glossary

> **Standardized language for the COALA SwarmOps ecosystem.**

---

## Status

🚧 **DRAFT** — This document is under construction as the ecosystem grows.  
Last updated: 2026-05-26  
Target completion: v7.0 milestone

---

## How to Use This Document

This glossary exists to prevent:
- Confusion between contributors
- Inconsistent naming in code and documentation
- Misunderstanding of architectural concepts
- Ambiguous communication between agents

**Rule:** When introducing a new term to the codebase or docs, add it here first.

---

## Core Concepts

### Swarm
> A coordinated group of specialized AI agents working together to complete complex tasks through orchestration.

**Context:** In COALA SwarmOps, a swarm is not a random collection of agents. It is a structured hierarchy with defined roles, escalation paths, and validation gates.

**Related:** Agent, MicroManager, Orchestration

---

### Agent
> An individual AI worker with a specialized role, defined capabilities, and specific tier assignment.

**Context:** Agents are not general-purpose. Each agent has a primary function (e.g., Code Expert, DevOps Inspector) and operates within a cost tier (T0-T3).

**Related:** Swarm, Role, Tier

---

### Tier
> A cost and capability classification for agents and tasks.

| Tier | Name | Cost | Capability |
|------|------|------|------------|
| T0 | Local / Free | $0 | Fast, simple tasks |
| T1 | Balanced | ~$0.14 | Moderate reasoning |
| T2 | Advanced | ~$0.44-$3.00 | Complex reasoning |
| T3 | Cognitive | ~$0.74-$3.49 | Strategic decisions |

**Related:** Escalation, Cost-Aware Routing, Agent

---

### Escalation
> The process of moving a task to a higher tier when the current tier fails or lacks sufficient capability.

**Context:** Escalation is controlled and justified, not automatic. See [PHILOSOPHY.md](../../PHILOSOPHY.md) for escalation principles.

**Related:** Tier, Downgrade, Circuit Breaker

---

### Downgrade
> The process of attempting a task at a lower tier after establishing that the task type is reliably solvable at that tier.

**Context:** Downgrade is the inverse of escalation. It optimizes costs by using cheaper tiers for known task patterns.

**Related:** Escalation, Tier, Cost-Aware Routing

---

## Architecture Terms

### Orchestration
> The coordination and management of multiple agents to execute a workflow in the correct order with proper validation.

**Related:** MicroManager, Swarm, Pipeline

---

### MicroManager
> The T3 agent responsible for coordinating the entire feature pipeline, delegating tasks to appropriate agents, and ensuring gates are passed.

**Related:** Orchestration, Planner, Agent

---

### Planner
> The agent responsible for decomposing user requests into actionable tasks and creating execution plans.

**Related:** Strategic Planner, MicroManager, Task Decomposition

---

### Router
> The component that determines which tier and which agent should handle a specific task.

**Related:** Smart Router, Tier, Escalation

---

### Smart Router (v7.0)
> Planned T0.5 agent that automatically classifies tasks and recommends the optimal tier with confidence scoring.

**Related:** Router, Tier, Escalation

---

### Circuit Breaker
> A pattern that prevents repeated execution of failing task types at a tier, automatically escalating future similar tasks.

**Related:** Error Learning, Escalation, Tier

---

## Memory Terms

### WM (Working Memory)
> Short-term context active during a single session or task.

---

### EM (Episodic Memory)
> Memory of past executions, including successes, failures, and learned patterns.

---

### SM (Semantic Memory)
> Structured knowledge about the project, architecture, and domain.

---

### PM (Procedural Memory)
> Knowledge of how to execute specific workflows and procedures.

**Related:** Memory Compression, Context Guardian

---

## Development Terms

### SDD (Specification-Driven Development)
> A workflow where every feature begins with a written specification before any code is implemented.

**Related:** Spec, Red-Green-Refactor, PHILOSOPHY.md

---

### Spec
> A document defining the requirements, design, tasks, and testing approach for a feature.

**Related:** SDD, Artifact Folder, FastForward Writer

---

### Artifact Folder
> The directory containing the four specification documents: requirements.md, design.md, tasks.md, testing.md.

**Related:** Spec, SDD, FastForward Writer

---

### Red-Green-Refactor
> A TDD cycle where tests are written first (red), code is implemented to pass tests (green), and then optimized (refactor).

**Related:** TDD, Test Engineer, Code Expert

---

## Component Names

### COALA Core
> The base orchestration engine responsible for swarm coordination, routing, task distribution, and execution flow.

**Related:** Orchestration, Swarm, COALA Nexus

---

### Hermes
> The planned cognitive reasoning and orchestration layer responsible for contextual reasoning, memory coordination, and adaptive decision making.

**Related:** v8, Cognitive Layer, Memory

---

### GitNexus
> The planned repository intelligence layer responsible for repository inspection, code analysis, and architecture understanding.

**Related:** v8, Repository Intelligence, Code Understanding

---

### COALA Nexus
> The planned enterprise orchestration layer with advanced memory, observability, multi-node coordination, and premium routing.

**Related:** Enterprise, v9, Monetization

---

## Process Terms

### Gate
> A mandatory validation checkpoint that must be passed before proceeding to the next phase.

**Examples:** SPEC_VALID, ENRICH_APPROVED, TEST_PASS, EVIDENCE_CHECK

**Related:** Validation, Pipeline, Phase

---

### Phase
> A distinct stage in the feature development pipeline (e.g., FASE 0: Enrichment, FASE 1: Specification, FASE 3: Implementation).

**Related:** Pipeline, Gate, Workflow

---

### Pipeline
> The complete sequence of phases, gates, and agent executions required to deliver a feature.

**Related:** Phase, Gate, MicroManager

---

## Cost Terms

### Cost-Aware Routing
> The architectural principle of selecting the cheapest viable tier for each task.

**Related:** Tier, Escalation, Downgrade, Cost Guardian

---

### Cost Guardian
> Planned T2 agent that monitors feature costs, alerts on overruns, and suggests tier downgrades.

**Related:** Cost-Aware Routing, Tier, Budget

---

## Error Terms

### Error Taxonomy
> A classification system for errors that enables pattern recognition and automatic fixes.

**Related:** Error Learning, Self-Healing Playbook, Circuit Breaker

---

### Self-Healing Playbook
> A database of known errors with their symptoms, causes, fixes, and the agents that apply them.

**Related:** Error Taxonomy, Error Learning, Circuit Breaker

---

## Contributing

To add a term:
1. Follow the existing format
2. Include definition, context, and related terms
3. Update the status if this changes document completeness
4. Submit a PR with the change

---

*This document will grow as the ecosystem evolves. Terms are added when they stabilize, not when they are first proposed.*