# Instalación Rápida — Cognitive Forge v6.7

## Requisitos

- **Windows 10/11 Pro**, **Linux** o **macOS**
  - No se requieren librerías nativas adicionales. Todo el sistema corre sobre la extensión RooCode y el archivo `custom_modes.yaml`.
- Ollama instalado con modelos:
  - `ejecutor-qwen2.5:latest` (T0 · ejecutor de comandos)
  - `qwen3.5:9b-opt` (T0 · fast checker)
  - `granite3.2:8b` (T0 · context scout)
- **RooCode** (VS Code extension) o cualquier cliente compatible con el formato `custom_modes.yaml`
- curl (incluido en Windows 10+, macOS y la mayoría de distribuciones Linux)

## Proveedores de API Soportados

El swarm puede operar con **API keys directas del proveedor** o a través de **OpenRouter** como fallback.

| Proveedor | Modelo | API Directa | OpenRouter | Notas |
|-----------|--------|-------------|------------|-------|
| DeepSeek | deepseek-chat / deepseek-coder / deepseek-reasoner | `platform.deepseek.com` | `openrouter/deepseek/*` | API directa ~20-30% más barata |
| Moonshot AI | Kimi K2.5 / Kimi K2.6 | `platform.moonshot.cn` | `openrouter/moonshotai/*` | Requiere verificación de empresa para altos volúmenes |
| OpenRouter | Agregador universal | — | `openrouter.ai` | Útil para testing y fallback; añade markup ~15-25% |

> **Recomendación:** Usa API keys directas en producción para reducir costos. OpenRouter es ideal para testing o como fallback si un proveedor directo falla.

## Paso 1: Instalar Ollama (Tier 0 Local)

```bash
# Windows (PowerShell)
winget install Ollama.Ollama

# macOS
brew install ollama

# Linux
curl -fsSL https://ollama.com/install.sh | sh

# Descargar modelos T0
ollama pull ejecutor-qwen2.5:latest
ollama pull qwen3.5:9b-opt
ollama pull granite3.2:8b
```

## Paso 2: Configurar Cliente de IA

> **Nota:** No está limitado a RooCode. Cualquier extensión o cliente que utilice el formato estándar `custom_modes.yaml` es compatible.

### Opción A: RooCode (VS Code)
1. Abrir VS Code → Extensiones → RooCode
2. Settings (icono de engranaje):
   - API Provider: **OpenRouter** (fallback) o proveedor directo
   - Si usas DeepSeek directo: selecciona "OpenAI Compatible" y configura Base URL `https://api.deepseek.com/v1`
   - Si usas Moonshot directo: Base URL `https://api.moonshot.cn/v1`
   - API Key: `sk-{tu-key}`
   - Model por defecto: según tier deseado
   - Context Window: **16384**
3. Guardar

### Opción B: Otro cliente compatible
- Copiar `custom_modes_v6.7.yaml` a la ruta que tu cliente utilice para modos personalizados.
- Asegurar que el cliente soporte el schema: `slug`, `name`, `roleDefinition`, `customInstructions`, `groups`, `model`.

## Paso 3: Configurar API Keys

### DeepSeek Directo
```bash
# Guardar en variable de entorno o configurar en el cliente
export DEEPSEEK_API_KEY="sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
# Precio aproximado: ~$0.14 input / $0.28 output por 1M tokens (Flash)
```

### Moonshot AI (Kimi) Directo
```bash
export MOONSHOT_API_KEY="sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
# Precio aproximado: ~$0.30 input / $1.20 output por 1M tokens (K2.5)
```

### OpenRouter (Fallback)
```bash
export OPENROUTER_API_KEY="sk-or-v1-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
# Registrarse en https://openrouter.ai/
# Agregar créditos (mínimo $5)
```

> **Trazabilidad de costos:** Hasta que Nexus esté operativo, registra manualmente cada feature en `docs/COST_REPORTS/FEAT-XXX_cost.md` con el formato descrito en [docs/COST_TRACKER.md](docs/COST_TRACKER.md).

## Paso 4: Copiar Custom Modes

```bash
# Windows
copy docs\custom_modes\custom_modes_v6.7.yaml %USERPROFILE%\.vscode\extensions\roo-code\.roo\custom_modes.yaml

# Linux / macOS
cp docs/custom_modes/custom_modes_v6.7.yaml ~/.vscode/extensions/roo-code/.roo/custom_modes.yaml

# O si tu cliente usa otra ruta, verificar en:
# Settings → Custom Modes Path
```

## Paso 5: Verificar Swarm

```
# En el chat del cliente compatible, escribir:
/enrich_us "Como cliente, quiero pagar con tarjeta de crédito"

# El swarm debería:
# 1. us-enricher (T2 · Kimi K2.5) → generar historia enriquecida
# 2. fastforward-writer (T3 · Kimi K2.6) → generar 4 documentos
# 3. spec-validator (T2 · Kimi K2.5) → validar artifact folder
# 4. micromanager (T3 · Kimi K2.6) → planificar ejecución
```

Si el comando `/enrich_us` no está disponible, verificar que el archivo `custom_modes.yaml` se haya cargado correctamente en el cliente.

## Paso 6: Verificar Workers T0.5 (DS Flash)

```
# Probar flash-fast-coder (DS Flash):
/code_flash "crea una función TypeScript que valide un email"

# Probar flash-deep-thinker (DS Flash):
/think_flash "analiza el archivo src/components/submitButton.css y sugiere mejoras"

# Probar flash-code-scout (DS Flash):
/scout_flash "encuentra todos los archivos que usan fetch() y analiza el patrón"
```

## Arquitectura de Tiers y Costos

### Modelo Actual (v6.7): API Keys Directas

| Tier | Workers | Modelo | Costo input/1M | Costo output/1M | Cuándo se usa |
|------|---------|--------|----------------|-----------------|---------------|
| T0 | 3 (qwen-coder, qwen-checker, granite-scout) | Ollama local 8-32B | $0 | $0 | Comandos 1-2 líneas, checks sintaxis |
| T0.5 | 3 (flash-scout, flash-coder, flash-thinker) | DeepSeek Flash (directo) | ~$0.14 | ~$0.28 | Código ≤100 líneas, análisis multi-archivo |
| T1 | 3 (senior, devops, rag) | DeepSeek Pro (directo) | ~$0.44 | ~$0.87 | Git, Docker, comandos complejos |
| T2 | 8 (validadores, gates) | Kimi K2.5 (Moonshot directo) | ~$0.30 | ~$1.20 | Validación, code review, seguridad |
| T3 | 4 (orquestadores) | Kimi K2.6 (Moonshot directo) | ~$0.50 | ~$2.00 | Planificación, memoria, artifact gen |

**Escalación:** T0 ($0) → T0.5 (~$0.14) → T1 (~$0.44) → T2 (~$0.30/$1.20) → STOP

> **Nota:** Si usas OpenRouter, los costos son aproximadamente un 20-30% superiores debido al markup de la plataforma.

### Tabla de costos por worker individual (API Directa)

| Worker | Slug | Modelo API Directa | Costo/1M tok in | Costo/1M tok out |
|--------|------|-------------------|----------------|-----------------|
| Qwen Coder Executor | qwen-coder-executor | ollama/ejecutor-qwen2.5:latest | $0 | $0 |
| Qwen Fast Checker | qwen-fast-checker | ollama/qwen3.5:9b-opt | $0 | $0 |
| Granite Context Scout | granite-context-scout | ollama/granite3.2:8b | $0 | $0 |
| Flash Code Scout | flash-code-scout | deepseek/deepseek-chat | ~$0.14 | ~$0.28 |
| Flash Fast Coder | flash-fast-coder | deepseek/deepseek-chat | ~$0.14 | ~$0.28 |
| Flash Deep Thinker | flash-deep-thinker | deepseek/deepseek-chat | ~$0.14 | ~$0.28 |
| Senior Engineer | senior | deepseek/deepseek-coder | ~$0.44 | ~$0.87 |
| DevOps Inspector | devops-inspector | deepseek/deepseek-coder | ~$0.44 | ~$0.87 |
| RAG Ecommerce Pro | rag-pro | deepseek/deepseek-coder | ~$0.44 | ~$0.87 |
| Spec Validator | spec-validator | moonshotai/kimi-k2.5 | ~$0.30 | ~$1.20 |
| Evidence Checker | evidence-checker | moonshotai/kimi-k2.5 | ~$0.30 | ~$1.20 |
| Test Engineer | test-engineer | moonshotai/kimi-k2.5 | ~$0.30 | ~$1.20 |
| Code Reviewer | code-reviewer | moonshotai/kimi-k2.5 | ~$0.30 | ~$1.20 |
| Security Auditor | security-auditor | moonshotai/kimi-k2.5 | ~$0.30 | ~$1.20 |
| US Enricher | us-enricher | moonshotai/kimi-k2.5 | ~$0.30 | ~$1.20 |
| Senior Engineer K | senior-ds | moonshotai/kimi-k2.5 | ~$0.30 | ~$1.20 |
| DevOps Architect | devops-architect | moonshotai/kimi-k2.5 | ~$0.30 | ~$1.20 |
| MicroManager | micromanager | moonshotai/kimi-k2.6 | ~$0.50 | ~$2.00 |
| Strategic Planner | strategic-planner | moonshotai/kimi-k2.6 | ~$0.50 | ~$2.00 |
| FastForward Writer | fastforward-writer | moonshotai/kimi-k2.6 | ~$0.50 | ~$2.00 |
| Context Guardian | context-guardian | moonshotai/kimi-k2.6 | ~$0.50 | ~$2.00 |

### Comparativa de Costos por Feature Típica (5 SP) — v6.0 vs v6.2 vs v6.7

| Fase | Worker | Tokens est. | Costo v6.0 | Costo v6.2 | Costo v6.7 | Notas |
|------|--------|------------|-----------|-----------|-----------|-------|
| FASE 0 | us-enricher | 8K | $1.76 (Flash) | $3.52 (Kimi K2.5) | $2.40 (Kimi K2.5 directo) | v6.0 usaba Flash; v6.2+ requiere validación T2 |
| FASE 1 | fastforward | 15K | $4.20 (Kimi K2.6) | $11.10 (Kimi K2.6) | $7.50 (Kimi K2.6 directo) | v6.0 no tenía FastForward; costo simulado de planner básico |
| FASE 2 | strategic | 6K | $1.76 (Pro) | $4.44 (Kimi K2.6) | $3.00 (Kimi K2.6 directo) | v6.0 no tenía planner formal |
| FASE 3 | branch | 4K | $0.56 (Flash) | $0.56 (Flash) | $0.56 (Flash) | Sin cambios |
| FASE 4 | tests-first | 5K | $1.10 (Pro) | $2.20 (Kimi K2.5) | $1.50 (Kimi K2.5 directo) | v6.0 usaba Pro; v6.2+ usa T2 para gates |
| FASE 5 | implement | 8K | $1.76 (Pro) | $3.52 (Kimi K2.5) | $2.40 (Kimi K2.5 directo) | v6.0 usaba Pro; v6.2+ usa T2 para calidad |
| FASE 6 | verify | 3K | $0.66 (Pro) | $1.32 (Kimi K2.5) | $0.90 (Kimi K2.5 directo) | v6.0 sin evidence-checker formal |
| FASE 7 | security | 4K | $0.88 (Pro) | $1.76 (Kimi K2.5) | $1.20 (Kimi K2.5 directo) | v6.0 sin security-auditor formal |
| FASE 8 | commit + PR | 2K | $0.28 (Flash) | $0.28 (Flash) | $0.28 (Flash) | Sin cambios |
| FASE 9 | update memory | 5K | $4.20 (Kimi K2.6) | $3.70 (Kimi K2.6) | $2.50 (Kimi K2.6 directo) | v6.0 sin context-guardian formal |
| **TOTAL** | | ~60K | **~$17.16** | **~$32.40** | **~$22.24** | v6.7 ahorra ~$10.16 vs v6.2 por API directa |

**Análisis de la comparativa:**

| Métrica | v6.0 | v6.2 | v6.7 |
|---------|------|------|------|
| Probabilidad de éxito E2E sin intervención | ~35% | ~85% | ~90% |
| Costo evitable por duplicados/alucinaciones | ~25% del budget | ~5% del budget | ~3% del budget |
| Tiempo de ciclo promedio (feature) | 1.8x | 1.0x | 0.9x |
| Abortos de pipeline (requieren reinicio manual) | ~40% | ~5% | ~3% |
| Workers totales | 14 | 24+ | 21 |
| Tier 0 local | ❌ No | ✅ Sí | ✅ Sí |
| Tier 0.5 Flash | ❌ No | ❌ No | ✅ Sí |
| Gates de validación | ❌ No | ✅ 3 gates | ✅ 3 gates |
| Escalación automática T2 | ❌ No | ✅ Completa | ✅ Completa |
| Costo por feature ~5 SP | ~$17 | ~$32 | ~$22 |

> **Conclusión:** v6.7 ofrece la mejor relación calidad/costo. Es ~30% más caro que v6.0 pero con ~2.5x más probabilidad de éxito. Es ~31% más barato que v6.2 gracias a API keys directas, manteniendo la misma calidad de validación.

## Troubleshooting

### "Ollama connection error"
- Verificar que Ollama esté corriendo: `ollama serve`
- Verificar modelo descargado: `ollama list`

### "custom_modes.yaml no carga"
- Verificar ruta correcta en el cliente
- Validar YAML: usar https://www.yamllint.com/

### "T0 falla inmediatamente"
- Verificar VRAM disponible: `nvidia-smi` (si tienes GPU)
- Reducir num_ctx en el Modelfile de Ollama

### "API Key error: insufficient credits"
- **DeepSeek directo:** Verificar en https://platform.deepseek.com/
- **Moonshot directo:** Verificar en https://platform.moonshot.cn/
- **OpenRouter:** Verificar en https://openrouter.ai/credits
- Recargar con mínimo $5-$10
- Los modelos Kimi K2.5/K2.6 tienen costo de output más alto (~$1.20-$2.00/1M tok)
- Una feature típica gasta $8-$45 total

### "Kimi K2.5 no responde desde API directa"
- Verificar que la API key tenga permisos para el modelo
- Moonshot puede requerir verificación de empresa para altos volúmenes
- Usar OpenRouter como fallback temporal

### "Proveedor cambió de precio"
- Revisar `docs/COST_TRACKER.md` para actualizar precios manualmente
- Hermes (futuro) notificará automáticamente cambios de pricing
- Nexus (futuro) mantendrá histórico de costos real

## Próximos Pasos

1. Explorar el ecosistema completo en [ECOSYSTEM_CONTEXT.md](ECOSYSTEM_CONTEXT.md)
2. Leer el manual de usuario en [USER_GUIDE.md](USER_GUIDE.md)
3. Revisar la hoja de ruta de Hermes y Nexus en [HERMES_NEXUS_ROADMAP.md](HERMES_NEXUS_ROADMAP.md)
4. Configurar trazabilidad de costos en [COST_TRACKER.md](COST_TRACKER.md)
