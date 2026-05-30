# Contribuyendo a COALA SwarmOps

> **Cómo participar en el ecosistema COALA SwarmOps.**

---

## Bienvenido

COALA SwarmOps es un ecosistema de orquestación de ingeniería open source en evolución. Ya sea que estés corrigiendo un typo, añadiendo una feature, o proponiendo cambios arquitectónicos, tu contribución es valorada.

Antes de contribuir, por favor lee:
- [FOUNDATION_ES.md](FOUNDATION_ES.md) — Por qué importa v6.2 y nuestro camino de evolución
- [PHILOSOPHY_ES.md](PHILOSOPHY_ES.md) — Los principios que guían cada decisión
- [STRATEGY_ES.md](STRATEGY_ES.md) — Hacia dónde va el proyecto

---

## Inicio Rápido

### 1. Fork y Clone

```bash
git clone https://github.com/Aquilesnake/COALA-SwarmOps.git
cd COALA-SwarmOps
```

### 2. Instalar Dependencias

```bash
# Docker es requerido para ejecución local
docker --version

# Ollama para modelos locales (opcional pero recomendado)
# Windows: https://ollama.com/download/windows
# Linux: curl -fsSL https://ollama.com/install.sh | sh
```

### 3. Ejecutar Tests

```bash
# Próximamente — suite de tests en desarrollo
```

---

## Tipos de Contribución

### Documentación

- Corregir typos, clarificar explicaciones
- Añadir ejemplos a docs existentes
- Traducir documentación
- **Buen primer issue:** Sí

### Bug Fixes

- Identificar el issue con pasos de reproducción
- Escribir un test que falle antes del fix
- Implementar el fix
- Asegurar que el test pase
- **Buen primer issue:** A veces

### Features

- Discutir la feature en GitHub Discussions primero
- Escribir una especificación siguiendo el flujo de trabajo SDD
- Obtener aprobación de un mantenedor
- Implementar con TDD
- **Buen primer issue:** No

### Definiciones de Agentes

- Proponer nuevos roles de agente en discussions
- Seguir la estructura de tiers existente
- Incluir justificación de costo
- **Buen primer issue:** No

---

## Desarrollo Dirigido por Especificaciones (SDD)

Todas las contribuciones de features deben seguir SDD:

1. **Escribir una spec** en `docs/specs/{feature-slug}/`
2. **Incluir cuatro documentos:**
   - `requirements.md` — Qué y por qué
   - `design.md` — Cómo funciona
   - `tasks.md` — Pasos de implementación
   - `testing.md` — Cómo verificar
3. **Obtener revisión** de un mantenedor
4. **Implementar** con TDD red-green-refactor
5. **Validar** a través de todos los gates

---

## Estándares de Código

### General

- TypeScript para código nuevo
- Compatibilidad cross-platform (Windows + Linux)
- Sin dependencias externas sin justificación
- Los comentarios explican por qué, no qué

### Código de Agentes

- Cada agente tiene un rol definido
- Los esquemas de input/output son explícitos
- El tier de costo está documentado
- El comportamiento de fallback está definido

### Tests

- Red-green-refactor obligatorio
- Cada bug fix incluye un test
- Tests de integración para flujos de trabajo
- Tests de compatibilidad Windows donde aplique

---

## Mensajes de Commit

Seguir commits convencionales:

```
type(scope): descripción

[cuerpo opcional]

[footer opcional]
```

Tipos:
- `feat:` Nueva feature
- `fix:` Bug fix
- `docs:` Solo documentación
- `test:` Cambios de tests
- `refactor:` Cambio de código que no es fix ni feature
- `perf:` Mejora de performance
- `chore:` Tareas de mantenimiento

Ejemplos:
```
feat(router): añadir agente Smart Router para clasificación automática de tier

fix(agent): prevenir que Junior ejecute comandos destructivos

docs(foundation): clarificar camino de evolución v6.2
```

---

## Proceso de Pull Request

1. **Branch desde main:**
   ```bash
   git checkout -b feature/tu-feature-name
   ```

2. **Hacer cambios** siguiendo SDD y estándares de código

3. **Actualizar documentación** si el comportamiento cambia

4. **Escribir o actualizar tests**

5. **Asegurar que todos los gates pasen:**
   - [ ] Revisión de spec aprobada
   - [ ] Tests pasan
   - [ ] Documentación actualizada
   - [ ] Sin breaking changes (o justificados y documentados)

6. **Enviar PR** con:
   - Título y descripción claros
   - Referencia a issue relacionado
   - Screenshots/logs si aplica

7. **Revisión** por al menos un mantenedor

8. **Merge** tras aprobación

---

## Setup de Desarrollo

### Windows

```powershell
# Instalar dependencias
# (Próximamente — script de instalación)

# Verificar instalación
.\scripts\verify-install.ps1
```

### Linux

```bash
# Instalar dependencias
# (Próximamente — script de instalación)

# Verificar instalación
./scripts/verify-install.sh
```

---

## Comunicación

- **GitHub Issues:** Reportes de bugs, solicitudes de features
- **GitHub Discussions:** Debates de arquitectura, preguntas
- **Pull Requests:** Contribuciones de código
- **Specs:** Propuestas de features vía `docs/specs/`

### Antes de Preguntar

1. Revisar issues y discussions existentes
2. Leer documentación relevante
3. Buscar en la base de datos de errores: `docs/errors/`

---

## Reconocimiento

Los contribuidores serán:
- Listados en notas de release
- Añadidos a CONTRIBUTORS.md
- Reconocidos en la documentación

---

## Código de Conducta

- Sé respetuoso y constructivo
- Asume buenas intenciones
- Enfócate en valor operacional
- Sé honesto sobre limitaciones
- Acredita el trabajo de otros

---

¡Gracias por contribuir a COALA SwarmOps!

> *"Cada contribución, no importa cuán pequeña, fortalece al swarm."*