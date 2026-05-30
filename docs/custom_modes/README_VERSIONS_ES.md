# COALA SwarmOps — Versiones de Custom Modes

## Tier Gratuito: v6.0 Starter Swarm

**Incluido en este repositorio.** Copia `custom_modes_v6.0.yaml` a tu carpeta de custom modes de RooCode para comenzar en 15 minutos.

### Qué Recibes (Gratis)

| Funcionalidad | v6.0 |
|---------------|------|
| **Agentes** | Equipo inicial core (ejecutores T1 + locales T0 + planificadores T3) |
| **Pipeline** | SDD básico: Requerimientos → Especificación → Coordinación |
| **Tiers** | T0 (local $0) + T1 (cloud) + T3 (estratégico) |
| **Gates** | Ninguno — ejecución directa |
| **Anti-duplicado** | No |
| **Human gate** | No |
| **Memoria CoALA** | No |
| **CLI Agnóstica** | No |
| **Circuit breaker** | No |
| **Puntaje** | Línea base inicial |

### Ideal Para
- Probar el concepto del swarm
- Proyectos personales pequeños
- Aprender cómo funciona la orquestación multi-agente
- Evaluar antes de actualizar

---

## Tiers Premium

Actualiza para desbloquear swarms de grado producción con más agentes, gates de validación, optimización de costos y razonamiento avanzado.

| Tier | Versión | Precio | Agentes | Destacados |
|------|---------|--------|---------|------------|
| 🥉 **Starter** | v6.1 | $7.99 pago único | Expandido | Anti-duplicado, human gate, escalación T2 básica |
| 🥈 **Production** | v6.2 | $19.99 pago único | Equipo completo | 3 gates de validación, memoria CoALA, escalación T2 completa. **+ Template docker-compose de sistema POS/Inventario** |
| 🥇 **Docker & Ecommerce** | v6.3 | $14.99 pago único | Equipo completo + | Bucle CoALA, CLI Agnóstica, RAG expandido. **+ Template docker-compose de ecommerce** |
| 💰 **Pro** | v6.5 | $49/mes | Expandido | Agentes T0 locales (costo $0), circuit breaker, aprendizaje de errores, actualizaciones mensuales |
| 🏢 **Enterprise** | v6.7 | $299/mes | Máximo | Agentes cloud por tiers, agentes locales mejorados, gates de validación completos, todos los templates starter, soporte prioritario, voto en roadmap |

### Cómo Actualizar

1. **Compras únicas (v6.1, v6.2, v6.3):** [Buy Me a Coffee](https://buymeacoffee.com/coalaswarmops)
2. **Suscripciones (v6.5, v6.7):** [GitHub Sponsors](https://github.com/sponsors/Aquilesnake)

Después de la compra, recibirás:
- El archivo YAML de tu versión
- Templates docker-compose (donde corresponda)
- Instrucciones de instalación

---

## Comparativa de Versiones (Dimensiones de Puntaje)

| Dimensión | v6.0 (Gratis) | v6.2 (Production) | v6.7 (Enterprise) |
|-----------|---------------|-------------------|-------------------|
| Arquitectura T0-T3 | Línea base | Buena | Excelente |
| Manejo de Errores | Línea base | Buena | Excelente |
| Cobertura de Roles | Línea base | Buena | Excelente |
| Gates de Validación | Mínimo | Bueno | Excelente |
| Seguridad | Línea base | Buena | Excelente |
| Escalabilidad de Costos | Línea base | Buena | Excelente |
| TDD y Calidad | Línea base | Buena | Excelente |
| **Total** | **~33** | **~82** | **~92** |

---

## Instalación (Todas las Versiones)

```bash
# 1. Copiar el YAML a custom modes de RooCode
# Windows:
copy custom_modes_v6.X.yaml %USERPROFILE%\.vscode\extensions\roo-code\.roo\custom_modes.yaml

# Linux / macOS:
cp custom_modes_v6.X.yaml ~/.vscode/extensions/roo-code/.roo/custom_modes.yaml

# 2. Reiniciar VS Code
# 3. Abrir Paleta de Comandos → "Roo Code: Switch Mode"
```

Guía completa: [`docs/INSTALL.md`](../INSTALL.md)

---

## Preguntas Frecuentes

**P: ¿Puedo quedarme con el YAML después de cancelar una suscripción?**
R: Sí. Patrocinas 1 mes, descargas tu YAML, y es tuyo. Cancela cuando quieras.

**P: ¿Cuál es la diferencia entre pago único y suscripción?**
R: Pago único (v6.1-v6.3) = recibes el YAML tal cual. Suscripción (v6.5, v6.7) = recibes actualizaciones, nuevas versiones y soporte.

**P: ¿v6.0 es suficiente para producción?**
R: v6.0 es para aprendizaje y proyectos pequeños. Equipos de producción deberían usar v6.2+ por los gates de validación y memoria CoALA.

**P: ¿Ofrecen swarms personalizados para mi stack tecnológico?**
R: El tier Enterprise incluye voto en roadmap — si suficientes clientes piden un stack, lo construimos.

---

*Última actualización: 2026-05-30*
*Mantenido por: COALA SwarmOps*
