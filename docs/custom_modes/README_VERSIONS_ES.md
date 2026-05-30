# COALA SwarmOps — Versiones de Custom Modes

## Tier Gratuito: v6.0 Starter Swarm

**Incluido en este repositorio.** Copia `custom_modes_v6.0.yaml` a tu carpeta de custom modes de RooCode para comenzar en 15 minutos.

### Qué Recibes (Gratis)

| Funcionalidad | v6.0 |
|---------------|------|
| **Workers** | 14 (8 T1 + 3 T0 local + 3 T3 planners) |
| **Pipeline** | SDD básico: us-enricher → fastforward-writer → micromanager |
| **Tiers** | T0 (local $0) + T1 (cloud) + T3 (estratégico) |
| **Gates** | Ninguno — ejecución directa |
| **Anti-duplicado** | No |
| **Human gate** | No (us-enricher puede saltar) |
| **Memoria CoALA** | No |
| **CLI Agnóstica** | No |
| **Circuit breaker** | No |
| **Puntaje** | ~60/100 |

### Ideal Para
- Probar el concepto del swarm
- Proyectos personales pequeños
- Aprender cómo funciona la orquestación multi-agente
- Evaluar antes de actualizar

---

## Tiers Premium

Actualiza para desbloquear swarms de grado producción con más workers, gates de validación, optimización de costos y razonamiento avanzado.

| Tier | Versión | Precio | Workers | Destacados |
|------|---------|--------|---------|------------|
| 🥉 **Starter** | v6.1 | $7.99 pago único | 18 | Anti-duplicado, human gate, escalación T2 básica |
| 🥈 **Production** | v6.2 | $19.99 pago único | 24+ | 3 gates de validación, memoria CoALA, escalación T2 completa. **+ Template docker-compose de sistema POS/Inventario** |
| 🥇 **Docker & Ecommerce** | v6.3 | $14.99 pago único | 25+ | Bucle CoALA, CLI Agnóstica, RAG expandido. **+ Template docker-compose de ecommerce** |
| 💰 **Pro** | v6.5 | $49/mes | 18 | Agentes T0 locales (costo $0), circuit breaker, aprendizaje de errores, actualizaciones mensuales |
| 🏢 **Enterprise** | v6.7 | $299/mes | 21 | DeepSeek+Kimi por tiers, agentes T0.5 Flash, validadores Kimi K2.5, todos los templates starter, soporte prioritario, voto en roadmap |

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
| Arquitectura T0-T3 | 6/15 | 12/15 | 14/15 |
| Manejo de Errores | 4/15 | 11/15 | 13/15 |
| Cobertura de Roles | 8/15 | 12/15 | 14/15 |
| Gates de Validación | 2/10 | 8/10 | 9/10 |
| Seguridad | 5/10 | 8/10 | 8/10 |
| Escalabilidad de Costos | 3/10 | 6/10 | 7/10 |
| TDD y Calidad | 3/5 | 4/5 | 5/5 |
| **Total** | **~33** | **82** | **~92** |

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

*Última actualización: 2026-05-29*
*Mantenido por: COALA SwarmOps*
