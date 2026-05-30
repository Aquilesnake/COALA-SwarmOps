# Política de Seguridad — COALA SwarmOps

## Versiones Soportadas

| Versión | Cobertura de Tiers | Actualizaciones de Seguridad |
|---------|-------------------|------------------------------|
| **v6.7** | T0-T3 · 21 agentes · pipeline SDD | ✅ Activo |
| **v6.5** | T0-T3 · 18 agentes | ✅ Activo |
| **v6.2** | Swarm operativo estable | ⚠️ Solo correcciones críticas |
| **< v6.2** | Experimental | ❌ Sin soporte |

## Reportar una Vulnerabilidad

**NO abras un Issue público en GitHub para vulnerabilidades de seguridad.**

Repórtalas de forma privada:

- **Email:** [agregar tu email de contacto]
- **Tiempo de respuesta esperado:** 48 horas
- **Política de divulgación:** Seguimos divulgación coordinada. La corrección se publica antes de que la vulnerabilidad sea revelada públicamente. Recibirás crédito en las notas de versión (a menos que prefieras anonimato).

### Qué Incluir en el Reporte

1. Descripción de la vulnerabilidad
2. Pasos para reproducir
3. Versiones afectadas
4. Impacto potencial
5. Corrección sugerida (si tienes)

## Arquitectura de Seguridad

COALA SwarmOps sigue principios de seguridad por diseño:

| Capa | Protección |
|------|-----------|
| **T0 (Local)** | Modelos Ollama ejecutados localmente. Los datos nunca salen de la máquina. |
| **T1-T3 (Nube)** | API keys nunca almacenadas en el repo. Proveedores aislados por tier. |
| **Pipeline SDD** | 5 gates + Auditor de Seguridad (T2) valida cada PR antes del merge. |
| **OWASP Top 10** | Verificaciones base de seguridad en todo el código generado. |
| **PCI-DSS** | Verificaciones de cumplimiento para features relacionadas con pagos. |
| **Escaneo de Dependencias** | Planificado para v7.0 — `npm audit` / `pip-audit` automatizado en CI. |

## Buenas Prácticas de Seguridad para Usuarios

1. **Nunca subas archivos `apikey`** — están en `.gitignore`
2. **Usa variables de entorno** para todas las API keys
3. **Rota las keys** cada 90 días
4. **Revisa el código generado** — el Auditor de Seguridad valida, pero la revisión humana agrega defensa en profundidad
5. **Mantén Ollama actualizado** — los modelos locales reciben parches de seguridad

## Historial de Divulgación de Vulnerabilidades

| Fecha | Severidad | Descripción | Versión Corregida |
|-------|-----------|-------------|-------------------|
| — | — | Sin vulnerabilidades reportadas aún | — |

---

*Tomamos la seguridad de nuestro ecosistema swarm con seriedad. Gracias por ayudar a mantener COALA SwarmOps seguro.*
