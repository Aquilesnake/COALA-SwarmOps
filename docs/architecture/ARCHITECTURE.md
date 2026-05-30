# COALA SwarmOps — Architecture Document

> **Technical architecture, component interactions, and system design.**

---

## Status

🚧 **DRAFT** — This document is under construction.  
Last updated: 2026-05-26  
Target completion: v7.0 milestone

---

## Purpose

This document provides the technical reference for COALA SwarmOps architecture including:
- Component diagrams and interactions
- Data flow patterns
- API contracts between agents
- Infrastructure requirements
- Deployment models

---

## High-Level Architecture

```mermaid
flowchart TD
    subgraph UserLayer["User Layer"]
        User[User Request]
        CLI[CLI Interface]
        UI[Web UI - Future]
    end

    subgraph OrchestrationLayer["Orchestration Layer"]
        Core[COALA Core]
        Planner[Planner Agent]
        Router[Router / MicroManager]
        Validator[Validation Engine]
    end

    subgraph AgentLayer["Agent Layer"]
        T0[T0 Agents<br>Intern, Junior, Researcher]
        T1[T1 Agents<br>Senior, Code Expert, DevOps]
        T2[T2 Agents<br>DS Experts, Architects]
        T3[T3 Agents<br>Strategic Planner, MicroManager]
    end

    subgraph ProviderLayer["Provider Layer"]
        Ollama[Ollama<br>Local Models]
        Groq[Groq<br>Fast Cloud]
        OpenAI[OpenAI<br>GPT Models]
        Anthropic[Anthropic<br>Claude Models]
    end

    subgraph MemoryLayer["Memory Layer"]
        WM[Working Memory]
        EM[Episodic Memory]
        SM[Semantic Memory]
        PM[Procedural Memory]
    end

    User --> CLI
    CLI --> Core
    Core --> Planner
    Planner --> Router
    Router --> T0
    Router --> T1
    Router --> T2
    Router --> T3
    T0 --> Validator
    T1 --> Validator
    T2 --> Validator
    T3 --> Validator
    Validator --> Core
    Core --> User

    T0 --> Ollama
    T1 --> Groq
    T2 --> Groq
    T3 --> OpenAI
    T3 --> Anthropic

    Core --> WM
    Core --> EM
    Core --> SM
    Core --> PM
```

---

## Component Details

### COALA Core

**Responsibilities:**
- Swarm coordination
- Task routing
- Execution flow management
- Fallback handling
- Gate enforcement

**Interfaces:**
- Input: User requests, spec documents
- Output: Execution plans, task assignments, validation results

---

### Planner Agent

**Responsibilities:**
- Request decomposition
- Task identification
- Dependency mapping
- Execution plan creation

---

### Router / MicroManager

**Responsibilities:**
- Tier selection
- Agent assignment
- Pipeline orchestration
- Gate management

---

### Validation Engine

**Responsibilities:**
- Output verification
- Gate checking
- Evidence validation
- Quality metrics

---

## Data Flow

### Feature Pipeline Flow

```mermaid
sequenceDiagram
    participant User
    participant Planner
    participant MicroManager
    participant Agent
    participant Validator
    participant Memory

    User->>Planner: Feature request
    Planner->>Memory: Retrieve context
    Memory-->>Planner: Project context
    Planner->>Planner: Decompose tasks
    Planner->>MicroManager: Execution plan
    MicroManager->>MicroManager: Select tier
    MicroManager->>Agent: Assign task
    Agent->>Memory: Read working memory
    Agent->>Agent: Execute task
    Agent->>Memory: Write results
    Agent->>Validator: Submit output
    Validator->>Validator: Check quality
    Validator->>MicroManager: Pass/Fail
    alt Pass
        MicroManager->>User: Complete
    else Fail
        MicroManager->>MicroManager: Escalate tier
        MicroManager->>Agent: Reassign
    end
```

---

## Deployment Models

### Single-Node (Current)

```
[Windows/Linux Host]
  ├── Docker Engine
  │   ├── COALA Core Container
  │   ├── Ollama Container
  │   └── Supporting Services
  ├── Git Repository
  └── Local File System
```

### Multi-Node (Future — COALA Nexus)

```
[Control Plane]
  ├── COALA Nexus
  ├── Global Memory
  └── Observability

[Worker Nodes]
  ├── Worker 1: T0/T1 Tasks
  ├── Worker 2: T2/T3 Tasks
  └── Worker N: Scalable
```

---

## API Contracts

### Agent Communication

```yaml
agent_message:
  version: "1.0"
  from: "agent_slug"
  to: "agent_slug_or_manager"
  task_id: "uuid"
  phase: "fase_number"
  content:
    type: "code|text|command|validation"
    data: "..."
  metadata:
    tier: "T0|T1|T2|T3"
    cost_estimate: "0.00"
    timestamp: "ISO8601"
```

### Gate Check

```yaml
gate_result:
  gate_name: "SPEC_VALID|ENRICH_APPROVED|TEST_PASS"
  status: "PASSED|BLOCKED|CONDITIONAL"
  evidence:
    - "reference_to_document"
    - "test_results"
  reviewer: "agent_slug"
  timestamp: "ISO8601"
```

---

## Infrastructure Requirements

### Minimum (Single Developer)

| Resource | Requirement |
|----------|-------------|
| OS | Windows 10+ or Linux |
| CPU | 4 cores |
| RAM | 8 GB |
| Storage | 20 GB |
| Docker | Docker Desktop |
| Git | Latest |

### Recommended (Team)

| Resource | Requirement |
|----------|-------------|
| OS | Windows Server 2019+ or Ubuntu 22.04+ |
| CPU | 8+ cores |
| RAM | 32 GB |
| Storage | 100 GB SSD |
| GPU | Optional, for local model acceleration |

---

## Security Architecture

### Current (v6.2)

- OWASP Top 10 baseline
- PCI-DSS awareness for payment-adjacent operations
- No secrets in code
- Local execution privacy by default

### Planned (v7.0+)

- SAST automated scanning
- Dependency vulnerability scanning
- Audit logging
- Role-based access control for multi-user deployments

---

## Migration Path

### v6.2 → v7.0

- Add Smart Router component
- Enhance Memory Layer with compression
- Introduce Cost Guardian
- No breaking changes to existing agents

### v7.0 → v8.0

- Add Hermes cognitive layer
- Add GitNexus repository intelligence
- Expand validation gates
- Maintain backward compatibility

---

*This document will be expanded as architecture decisions are finalized.*