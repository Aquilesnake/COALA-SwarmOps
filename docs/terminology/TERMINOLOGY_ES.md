# COALA SwarmOps — Terminología y Glosario

> **Lenguaje estandarizado para el ecosistema COALA SwarmOps.**

---

## Estado

🚧 **BORRADOR** — Este documento está en construcción a medida que el ecosistema crece.  
Última actualización: 2026-05-26  
Meta de completitud: hito v7.0

---

## Cómo Usar Este Documento

Este glosario existe para prevenir:
- Confusión entre contribuidores
- Nomenclatura inconsistente en código y documentación
- Malentendidos de conceptos arquitectónicos
- Comunicación ambigua entre agentes

**Regla:** Al introducir un nuevo término en el codebase o docs, añádelo aquí primero.

---

## Conceptos Core

### Swarm (Enjambre)
> Un grupo coordinado de agentes de IA especializados que trabajan juntos para completar tareas complejas mediante orquestación.

**Contexto:** En COALA SwarmOps, un swarm no es una colección aleatoria de agentes. Es una jerarquía estructurada con roles definidos, caminos de escalación, y gates de validación.

**Relacionado:** Agente, MicroManager, Orquestación

---

### Agente
> Un trabajador de IA individual con un rol especializado, capacidades definidas, y asignación de tier específica.

**Contexto:** Los agentes no son de propósito general. Cada agente tiene una función primaria (ej., Code Expert, DevOps Inspector) y opera dentro de un tier de costo (T0-T3).

**Relacionado:** Swarm, Rol, Tier

---

### Tier (Nivel)
> Una clasificación de costo y capacidad para agentes y tareas.

| Tier | Nombre | Costo | Capacidad |
|------|--------|-------|-----------|
| T0 | Local / Gratis | $0 | Tareas rápidas, simples |
| T1 | Balanceado | ~$0.14 | Razonamiento moderado |
| T2 | Avanzado | ~$0.44-$3.00 | Razonamiento complejo |
| T3 | Cognitivo | ~$0.74-$3.49 | Decisiones estratégicas |

**Relacionado:** Escalación, Cost-Aware Routing, Agente

---

### Escalación
> El proceso de mover una tarea a un tier superior cuando el tier actual falla o carece de capacidad suficiente.

**Contexto:** La escalación es controlada y justificada, no automática. Ver [PHILOSOPHY_ES.md](../../PHILOSOPHY_ES.md) para principios de escalación.

**Relacionado:** Tier, Downgrade, Circuit Breaker

---

### Downgrade (Degradación)
> El proceso de intentar una tarea en un tier inferior tras establecer que el tipo de tarea es resoluble confiablemente en ese tier.

**Contexto:** El downgrade es el inverso de la escalación. Optimiza costos usando tiers más baratos para patrones de tareas conocidos.

**Relacionado:** Escalación, Tier, Cost-Aware Routing

---

## Términos de Arquitectura

### Orquestación
> La coordinación y gestión de múltiples agentes para ejecutar un flujo de trabajo en el orden correcto con validación apropiada.

**Relacionado:** MicroManager, Swarm, Pipeline

---

### MicroManager
> El agente T3 responsable de coordinar el pipeline completo de una feature, delegar tareas a agentes apropiados, y asegurar que los gates sean pasados.

**Relacionado:** Orquestación, Planner, Agente

---

### Planner (Planificador)
> El agente responsable de descomponer solicitudes de usuarios en tareas accionables y crear planes de ejecución.

**Relacionado:** Strategic Planner, MicroManager, Descomposición de Tareas

---

### Router (Enrutador)
> El componente que determina qué tier y qué agente debe manejar una tarea específica.

**Relacionado:** Smart Router, Tier, Escalación

---

### Smart Router (v7.0)
> Agente T0.5 planificado que clasifica automáticamente tareas y recomienda el tier óptimo con scoring de confianza.

**Relacionado:** Router, Tier, Escalación

---

### Circuit Breaker (Interruptor de Circuito)
> Un patrón que previene la ejecución repetida de tipos de tareas fallidas en un tier, escalando automáticamente tareas similares futuras.

**Relacionado:** Aprendizaje por Error, Escalación, Tier

---

## Términos de Memoria

### WM (Working Memory / Memoria de Trabajo)
> Contexto de corto plazo activo durante una sola sesión o tarea.

---

### EM (Episodic Memory / Memoria Episódica)
> Memoria de ejecuciones pasadas, incluyendo éxitos, fallas, y patrones aprendidos.

---

### SM (Semantic Memory / Memoria Semántica)
> Conocimiento estructurado sobre el proyecto, arquitectura, y dominio.

---

### PM (Procedural Memory / Memoria Procedural)
> Conocimiento de cómo ejecutar flujos de trabajo y procedimientos específicos.

**Relacionado:** Compresión de Memoria, Context Guardian

---

## Términos de Desarrollo

### SDD (Specification-Driven Development / Desarrollo Dirigido por Especificaciones)
> Un flujo de trabajo donde cada feature comienza con una especificación escrita antes de que se implemente cualquier código.

**Relacionado:** Spec, Red-Green-Refactor, PHILOSOPHY_ES.md

---

### Spec (Especificación)
> Un documento definiendo los requerimientos, diseño, tareas, y enfoque de testing para una feature.

**Relacionado:** SDD, Artifact Folder, FastForward Writer

---

### Artifact Folder (Carpeta de Artefactos)
> El directorio conteniendo los cuatro documentos de especificación: requirements.md, design.md, tasks.md, testing.md.

**Relacionado:** Spec, SDD, FastForward Writer

---

### Red-Green-Refactor (Rojo-Verde-Refactorizar)
> Un ciclo de TDD donde los tests se escriben primero (rojo), el código se implementa para pasar los tests (verde), y luego se optimiza (refactorizar).

**Relacionado:** TDD, Test Engineer, Code Expert

---

## Nombres de Componentes

### COALA Core
> El motor base de orquestación responsable de coordinación de swarm, routing, distribución de tareas, y flujo de ejecución.

**Relacionado:** Orquestación, Swarm, COALA Nexus

---

### Hermes
> La capa planificada de razonamiento cognitivo y orquestación responsable de razonamiento contextual, coordinación de memoria, y toma de decisiones adaptativa.

**Relacionado:** v8, Capa Cognitiva, Memoria

---

### GitNexus
> La capa planificada de inteligencia de repositorio responsable de inspección de repositorios, análisis de código, y comprensión de arquitectura.

**Relacionado:** v8, Inteligencia de Repositorio, Comprensión de Código

---

### COALA Nexus
> La capa planificada de orquestación enterprise con memoria avanzada, observabilidad, coordinación multi-nodo, y routing premium.

**Relacionado:** Enterprise, v9, Monetización

---

## Términos de Proceso

### Gate (Puerta/Validación)
> Un checkpoint de validación obligatorio que debe ser pasado antes de proceder a la siguiente fase.

**Ejemplos:** SPEC_VALID, ENRICH_APPROVED, TEST_PASS, EVIDENCE_CHECK

**Relacionado:** Validación, Pipeline, Fase

---

### Phase (Fase)
> Una etapa distinta en el pipeline de desarrollo de features (ej., FASE 0: Enriquecimiento, FASE 1: Especificación, FASE 3: Implementación).

**Relacionado:** Pipeline, Gate, Flujo de Trabajo

---

### Pipeline (Tubería/Flujo)
> La secuencia completa de fases, gates, y ejecuciones de agentes requeridas para entregar una feature.

**Relacionado:** Fase, Gate, MicroManager

---

## Términos de Costo

### Cost-Aware Routing (Routing Consciente de Costos)
> El principio arquitectónico de seleccionar el tier viable más barato para cada tarea.

**Relacionado:** Tier, Escalación, Downgrade, Cost Guardian

---

### Cost Guardian (Guardián de Costos)
> Agente T2 planificado que monitorea costos de features, alerta sobre sobrecostos, y sugiere degradaciones de tier.

**Relacionado:** Cost-Aware Routing, Tier, Presupuesto

---

## Términos de Error

### Error Taxonomy (Taxonomía de Errores)
> Un sistema de clasificación de errores que habilita reconocimiento de patrones y fixes automáticos.

**Relacionado:** Aprendizaje por Error, Self-Healing Playbook, Circuit Breaker

---

### Self-Healing Playbook (Playbook de Auto-Sanación)
> Una base de datos de errores conocidos con sus síntomas, causas, fixes, y los agentes que los aplican.

**Relacionado:** Taxonomía de Errores, Aprendizaje por Error, Circuit Breaker

---

## Contribuyendo

Para añadir un término:
1. Seguir el formato existente
2. Incluir definición, contexto, y términos relacionados
3. Actualizar el estado si esto cambia la completitud del documento
4. Enviar un PR con el cambio

---

*Este documento crecerá a medida que el ecosistema evoluciona. Los términos se añaden cuando se estabilizan, no cuando se proponen por primera vez.*