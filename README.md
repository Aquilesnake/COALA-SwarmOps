# COALA SwarmOps

Operational swarm orchestration platform evolved from real-world DevOps and engineering workflows.

Self-hosted engineering swarm orchestration platform focused on low-cost intelligent execution, modular agent collaboration, DevOps automation, and adaptive multi-tier reasoning.

> Smarter agents. Lower costs. Better systems.

---

## Overview

COALA SwarmOps is a modular multi-agent orchestration platform designed for real-world engineering, DevOps automation, software architecture, and intelligent system execution.

Built around adaptive tier escalation and cost-aware routing, COALA enables local and cloud-based AI agents to collaborate efficiently while maintaining control over performance, hallucinations, and operational costs.

The platform was originally evolved from real engineering workflows and production-oriented orchestration systems focused on practical infrastructure and software development challenges.

---

## Core Features

- Multi-agent swarm orchestration
- Adaptive tier escalation
- Cost-aware AI routing
- Self-hosted first architecture
- Local + cloud model support
- Windows and Linux compatibility
- Modular agent system
- Specification-driven development (SDD)
- DevOps-native workflows
- Intelligent fallback switching
- Repository analysis and inspection
- Distributed execution support
- Extensible architecture

---

## Architecture

COALA SwarmOps follows a hierarchical orchestration model:

User Request
    ↓
Planner Agent
    ↓
Task Decomposition
    ↓
Manager / Router
    ↓
Tier Selection
    ↓
Specialized Agents
    ↓
Validation & Review
    ↓
Final Execution

---

## Core Components

### COALA Core
Base orchestration engine responsible for:
- swarm coordination
- routing
- task distribution
- execution flow
- fallback handling

### Hermes
Cognitive reasoning and orchestration layer responsible for:
- contextual reasoning
- memory coordination
- adaptive decision making
- semantic planning

### GitNexus
Repository intelligence layer responsible for:
- repository inspection
- contextual code analysis
- architecture understanding
- swarm-assisted repository operations

### COALA Nexus
Enterprise and premium orchestration layer including:
- advanced memory systems
- enterprise orchestration
- distributed swarm coordination
- observability
- advanced routing systems

---

## Supported Workflows

- DevOps automation
- Infrastructure planning
- Software architecture
- Code inspection
- Repository analysis
- CI/CD orchestration
- Windows installer generation
- Self-hosted AI execution
- Multi-agent collaboration
- Intelligent code generation

---

## Supported Models

Local Models:
- DeepSeek
- Qwen
- Kimi
- Hermes
- Llama

Cloud Models:
- OpenAI
- Anthropic
- Groq
- OpenRouter-compatible providers

---

## Why COALA SwarmOps?

Modern AI development systems often suffer from:
- high operational costs
- hallucination-heavy execution
- lack of orchestration
- cloud dependency
- poor modularity
- limited observability

COALA SwarmOps focuses on:
- controlled execution
- adaptive model escalation
- cost optimization
- modular orchestration
- engineering-oriented workflows
- self-hosted infrastructure

---

## Real-World Use Cases

### Native Windows Integration
COALA SwarmOps evolved with practical Windows-native orchestration and installation workflows.

### TanCerca.cl
Real-world swarm-assisted architecture and orchestration experimentation platform.

### Self-Improving Swarm Systems
COALA can analyze and improve parts of its own orchestration logic through controlled multi-agent execution.

---

## Roadmap

### V1
- Core orchestration
- Tier routing
- Windows support
- Docker deployment
- Basic SDD workflows

### V2
- Hermes cognitive layer
- GitNexus integration
- Persistent memory
- Enhanced orchestration

### V3
- Distributed swarm execution
- Advanced semantic planning
- Multi-node orchestration
- Enterprise observability

### V4
- COALA Nexus
- Marketplace
- Kubernetes orchestration
- Enterprise deployment systems

---

## Documentation

| Documento | Descripción |
|-----------|-------------|
| [`docs/INSTALL.md`](docs/INSTALL.md) | Guía de instalación rápida (Windows, Linux, macOS) |
| [`docs/USER_GUIDE.md`](docs/USER_GUIDE.md) | Manual paso a paso para usar el servicio |
| [`docs/ECOSYSTEM_CONTEXT.md`](docs/ECOSYSTEM_CONTEXT.md) | Mapa de repositorios: tancerca, fuente-de-datos, imp.bodegamk |
| [`docs/COST_TRACKER.md`](docs/COST_TRACKER.md) | Mecanismo de trazabilidad de costos por feature |
| [`docs/PRICES.md`](docs/PRICES.md) | Fuente de verdad de precios de APIs (actualizar cada 30 días) |
| [`docs/HERMES_NEXUS_ROADMAP.md`](docs/HERMES_NEXUS_ROADMAP.md) | Hoja de ruta de Hermes + GitNexus + Nexus |
| [`docs/BUSINESS_STRATEGY.md`](docs/BUSINESS_STRATEGY.md) | Estrategia de posicionamiento top 10 mundial |
| [`docs/architecture/`](docs/architecture/) | Decisiones de arquitectura |
| [`docs/terminology/`](docs/terminology/) | Glosario de términos del swarm |

## Ecosistema

COALA-SwarmOps es la cabeza cognitiva de un ecosistema de 4 repositorios:

```
COALA-SwarmOps → tancerca (ecommerce) → fuente-de-datos (RAG) → imp.bodegamk (logística)
```

Ver [`docs/ECOSYSTEM_CONTEXT.md`](docs/ECOSYSTEM_CONTEXT.md) para el mapa completo.

## Instalación Rápida

```bash
# 1. Instalar Ollama y modelos T0 locales
ollama pull ejecutor-qwen2.5:latest
ollama pull qwen3.5:9b-opt
ollama pull granite3.2:8b

# 2. Copiar custom_modes.yaml a RooCode
# Windows:
copy docs\custom_modes\custom_modes_v6.7.yaml %USERPROFILE%\.vscode\extensions\roo-code\.roo\custom_modes.yaml
# Linux / macOS:
cp docs/custom_modes/custom_modes_v6.7.yaml ~/.vscode/extensions/roo-code/.roo/custom_modes.yaml

# 3. Configurar API key (DeepSeek directo o Moonshot directo)
# Ver docs/INSTALL.md para instrucciones detalladas

# 4. Tu primera feature:
/enrich_us "Como usuario quiero filtrar productos por precio"
```

Guía completa en [`docs/INSTALL.md`](docs/INSTALL.md).

## Contributing

COALA SwarmOps is designed as an evolving open-source engineering orchestration ecosystem.

Contributions, ideas, testing, architectural feedback, and swarm experimentation are welcome.

---

## Vision

To bring adaptive swarm intelligence into real-world engineering, DevOps, automation, and software development workflows through accessible, modular, and self-hosted AI orchestration.

---

## License

License definition coming soon.
