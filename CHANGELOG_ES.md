# Registro de Cambios

Todos los cambios notables de COALA SwarmOps se documentan en este archivo.

El formato sigue [Keep a Changelog](https://keepachangelog.com/es-ES/1.1.0/),
y este proyecto adhiere a [Versionado Semántico](https://semver.org/lang/es/).

---

## [Sin Publicar]

### Agregado (2026-05-27 — Fase de Fundación)
- `FOUNDATION.md` — El Covenant v6.2: historia, arquitectura, evolución, score card base (78/100)
- `FOUNDATION_ES.md` — Traducción al español
- `STRATEGY.md` — Visión de mercado, posicionamiento competitivo, modelo open-core, estrategia de releases
- `STRATEGY_ES.md` — Traducción al español
- `PHILOSOPHY.md` — Principios de diseño, anti-patrones, filosofía operacional
- `PHILOSOPHY_ES.md` — Traducción al español
- `CONTEXT.md` — Documento maestro de continuidad del ecosistema swarm
- `CONTRIBUTING.md` — Guía de contribución: flujo SDD, estándares de código, proceso de PR
- `CONTRIBUTING_ES.md` — Traducción al español
- `next_steps_evolution.md` — Plan de expansión del ecosistema: evolución dual, estructura proyectada
- `next_steps_evolution_ES.md` — Traducción al español
- `docs/ECOSYSTEM_CONTEXT.md` — Mapa del ecosistema de 4 repos
- `docs/COST_TRACKER.md` — Sistema de trazabilidad de costos por feature
- `docs/HERMES_NEXUS_ROADMAP.md` — Hoja de ruta Hermes + GitNexus + Nexus (Q3 2026 → Q2 2027)
- `docs/INSTALL.md` — Guía de instalación rápida (Windows, Linux, macOS)
- `docs/PRICES.md` — Fuente de verdad de precios de APIs
- `docs/USER_GUIDE.md` — Manual paso a paso para clientes
- `docs/architecture/ARCHITECTURE.md` — Decisiones de arquitectura técnica (EN+ES)
- `docs/terminology/TERMINOLOGY.md` — Glosario del swarm (EN+ES)
- `docs/custom_modes/custom_modes_v6.0.yaml` — Starter Swarm gratuito (14 workers)
- `docs/custom_modes/README_VERSIONS.md` — Catálogo de versiones y precios (EN+ES)
- `docs/SWARM_v6.5_SCORE_CARD.md` — Scorecard formal 78/100 + roadmap a 100
- `img/score_claude.png` — Evidencia de benchmark Claude
- `models/` — Modelfiles de Ollama (ejecutor, qwen, qwencoder)
- `LICENSE` — Licencia MIT
- `.gitignore` — Reglas de ignorado completas
- `SECURITY.md` + `SECURITY_ES.md` — Política de seguridad
- `.github/FUNDING.yml` — Configuración de GitHub Sponsors
- `.github/ISSUE_TEMPLATE/` — Templates de bug report y feature request
- `.github/PULL_REQUEST_TEMPLATE.md` — Checklist de PR alineado con pipeline SDD
- `CODEOWNERS` — Reglas de propiedad del repositorio
- `CHANGELOG.md` + `CHANGELOG_ES.md` — Este archivo

### Modificado
- `README.md` — Actualizado con contexto de ecosistema, instalación rápida, tabla de documentación

---

## [v6.2] — 2025-2026 — Swarm Operativo Estable

### Fundación
- 18 agentes definidos en 4 tiers (T0-T3)
- Enrutamiento consciente de costos: T0 ($0 local) → T3 (~$3.49 cloud)
- Patrón Circuit Breaker para aprendizaje de errores
- Escalación 1-fallo (T0 falla → T1 inmediato)
- Flujo de trabajo SDD (Specification-Driven Development)

### Soporte Nativo Windows
- Port de mhito/ai a Windows 10 nativo
- Capa de compatibilidad Git Bash
- 87/96 tests pasando en Windows
- Integración con Ollama, Groq, DeepSeek

### Ecosistema
- Plataforma ecommerce TanCerca.cl
- Infraestructura Dockerizada img.bodegamk.cl
- Orquestación DevOps multi-proyecto

---

## [v1-v5] — 2024-2025 — Experimental

- Flujos de orquestación manual
- Prototipos de agentes fragmentados
- Experimentación de infraestructura
- Conceptos pre-swarm operacionales

---

*Registro mantenido por COALA SwarmOps / context-guardian.*
