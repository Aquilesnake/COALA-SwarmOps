# PRICES.md — Precios Reales de APIs (Actualizar Manualmente)

> **Propósito:** Fuente de verdad para costos. Todos los agentes del swarm deben leer este archivo antes de estimar cualquier costo.
>
> **Frecuencia de actualización:** Cada 30 días o cuando un proveedor anuncie cambio de precios.
>
> ⚠️ **No uses precios de memoria. Siempre lee este archivo.**

---

## Precios por Proveedor (Actualizado: 2026-05-27)

### DeepSeek (API Directa — platform.deepseek.com)

| Modelo | Input / 1M tok | Output / 1M tok | Notas |
|--------|---------------|-----------------|-------|
| deepseek-chat | $0.14 | $0.28 | Equivale a "Flash" para tareas simples |
| deepseek-coder | $0.44 | $0.87 | Equivale a "Pro" para código complejo |
| deepseek-reasoner | $0.55 | $2.19 | Razonamiento profundo (no usado aún) |

### Moonshot AI — Kimi (API Directa — platform.moonshot.cn)

| Modelo | Input / 1M tok | Output / 1M tok | Notas |
|--------|---------------|-----------------|-------|
| kimi-k2.5 | ~$0.30 | ~$1.20 | Validación, review, seguridad |
| kimi-k2.6 | ~$0.50 | ~$2.00 | Planificación, orquestación |

> **Nota Moonshot:** Precios exactos pueden variar según verificación de empresa y volumen. Confirmar en https://platform.moonshot.cn/pricing

### Ollama (Local — $0 siempre)

| Modelo | Costo | VRAM |
|--------|-------|------|
| ejecutor-qwen2.5:latest | $0 | ~12 GB |
| qwen3.5:9b-opt | $0 | ~6 GB |
| granite3.2:8b | $0 | ~6 GB |

### OpenRouter (Agregador — openrouter.ai)

| Modelo | Input / 1M tok | Output / 1M tok |
|--------|---------------|-----------------|
| openrouter/deepseek/deepseek-v4-flash | $0.14 | $0.28 |
| openrouter/deepseek/deepseek-v4-pro | $0.44 | $0.87 |
| openrouter/moonshotai/kimi-k2.5 | $0.44 | $2.00 |
| openrouter/moonshotai/kimi-k2.6 | $0.74 | $3.49 |

---

## Comparativa API Directa vs OpenRouter

| Modelo | API Directa (out) | OpenRouter (out) | Ahorro Directo |
|--------|-------------------|-------------------|---------------|
| DeepSeek Flash | $0.28 | $0.28 | ~0% (igual) |
| DeepSeek Pro | $0.87 | $0.87 | ~0% (igual) |
| Kimi K2.5 | ~$1.20 | $2.00 | ~40% |
| Kimi K2.6 | ~$2.00 | $3.49 | ~43% |

> **Conclusión:** Para DeepSeek, API directa y OpenRouter cuestan lo mismo. Para Kimi (Moonshot), la API directa ahorra ~40%. Usa Moonshot directo para T2/T3 siempre que sea posible.

---

## Costo Real por Feature (Datos Empíricos)

Basado en uso real del swarm (mayo 2026):

| Feature | SP | Costo API | % T0 local |
|---------|----|-----------|------------|
| Feature simple (bugfix, ajuste UI) | 1-2 | $0.05 - $0.50 | 80-90% |
| Feature media (endpoint, componente) | 3-5 | $0.50 - $2.00 | 60-75% |
| Feature compleja (módulo, integración) | 8-13 | $2.00 - $8.00 | 50-65% |
| **Acumulado histórico** | — | **< $35.00** | **~65%** |

> **Nota:** El 65% del trabajo se resuelve en T0 (Ollama local, $0). Esto explica por qué los costos son tan bajos comparados con estimaciones teóricas.

---

## Cómo Actualizar Este Archivo

### Paso 1: Verificar precios actuales

```bash
# OpenRouter (siempre disponible)
curl -s https://openrouter.ai/api/v1/models | python -c "import sys,json; [print(m['id'], m.get('pricing',{})) for m in json.load(sys.stdin)['data'] if 'deepseek' in m['id'] or 'kimi' in m['id']]"

# DeepSeek directo
# Visitar: https://platform.deepseek.com/pricing

# Moonshot directo
# Visitar: https://platform.moonshot.cn/pricing
```

### Paso 2: Actualizar este archivo

Modificar las tablas de arriba con los precios obtenidos.

### Paso 3: Commit

```bash
git add docs/PRICES.md
git commit -m "docs: actualizar precios APIs a [FECHA]"
```

---

## Regla para Agentes del Swarm

Todo agente que estime costos DEBE:

1. Leer `docs/PRICES.md` antes de calcular
2. Usar precio de API DIRECTA si está configurada
3. Usar precio de OpenRouter solo si no hay API directa
4. Si PRICES.md tiene > 30 días, advertir: "⚠️ PRICES.md desactualizado. Los costos pueden no ser exactos."
5. **NUNCA inventar precios de memoria.**

---

*Fuente de verdad para costos. Actualizar cada 30 días.*
*Última verificación: 2026-05-27*
