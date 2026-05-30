# Contributing to COALA SwarmOps

> **How to participate in the COALA SwarmOps ecosystem.**

---

## Welcome

COALA SwarmOps is an evolving open-source engineering orchestration ecosystem. Whether you are fixing a typo, adding a feature, or proposing architectural changes, your contribution is valued.

Before contributing, please read:
- [FOUNDATION.md](FOUNDATION.md) — Why v6.2 matters and our evolution path
- [PHILOSOPHY.md](PHILOSOPHY.md) — The principles that guide every decision
- [STRATEGY.md](STRATEGY.md) — Where the project is going

---

## Quick Start

### 1. Fork and Clone

```bash
git clone https://github.com/Aquilesnake/COALA-SwarmOps.git
cd COALA-SwarmOps
```

### 2. Install Dependencies

```bash
# Docker is required for local execution
docker --version

# Ollama for local models (optional but recommended)
# Windows: https://ollama.com/download/windows
# Linux: curl -fsSL https://ollama.com/install.sh | sh
```

### 3. Run Tests

```bash
# Coming soon — test suite is under development
```

---

## Contribution Types

### Documentation

- Fix typos, clarify explanations
- Add examples to existing docs
- Translate documentation
- **Good first issue:** Yes

### Bug Fixes

- Identify the issue with reproduction steps
- Write a test that fails before the fix
- Implement the fix
- Ensure the test passes
- **Good first issue:** Sometimes

### Features

- Discuss the feature in GitHub Discussions first
- Write a specification following SDD workflow
- Get approval from a maintainer
- Implement with TDD
- **Good first issue:** No

### Agent Definitions

- Propose new agent roles in discussions
- Follow existing tier structure
- Include cost justification
- **Good first issue:** No

---

## Specification-Driven Development (SDD)

All feature contributions must follow SDD:

1. **Write a spec** in `docs/specs/{feature-slug}/`
2. **Include four documents:**
   - `requirements.md` — What and why
   - `design.md` — How it works
   - `tasks.md` — Implementation steps
   - `testing.md` — How to verify
3. **Get review** from a maintainer
4. **Implement** with red-green-refactor TDD
5. **Validate** through all gates

---

## Code Standards

### General

- TypeScript for new code
- Cross-platform compatibility (Windows + Linux)
- No external dependencies without justification
- Comments explain why, not what

### Agent Code

- Each agent has a defined role
- Input/output schemas are explicit
- Cost tier is documented
- Fallback behavior is defined

### Tests

- Red-green-refactor mandatory
- Every bug fix includes a test
- Integration tests for workflows
- Windows compatibility tests where applicable

---

## Commit Messages

Follow conventional commits:

```
type(scope): description

[optional body]

[optional footer]
```

Types:
- `feat:` New feature
- `fix:` Bug fix
- `docs:` Documentation only
- `test:` Test changes
- `refactor:` Code change neither fix nor feature
- `perf:` Performance improvement
- `chore:` Maintenance tasks

Examples:
```
feat(router): add Smart Router agent for automatic tier classification

fix(agent): prevent Junior from executing destructive commands

docs(foundation): clarify v6.2 evolution path
```

---

## Pull Request Process

1. **Branch from main:**
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. **Make changes** following SDD and code standards

3. **Update documentation** if behavior changes

4. **Write or update tests**

5. **Ensure all gates pass:**
   - [ ] Spec review approved
   - [ ] Tests pass
   - [ ] Documentation updated
   - [ ] No breaking changes (or justified and documented)

6. **Submit PR** with:
   - Clear title and description
   - Reference to related issue
   - Screenshots/logs if applicable

7. **Review** by at least one maintainer

8. **Merge** after approval

---

## Development Setup

### Windows

```powershell
# Install dependencies
# (Coming soon — installation script)

# Verify installation
.\scripts\verify-install.ps1
```

### Linux

```bash
# Install dependencies
# (Coming soon — installation script)

# Verify installation
./scripts/verify-install.sh
```

---

## Communication

- **GitHub Issues:** Bug reports, feature requests
- **GitHub Discussions:** Architecture debates, questions
- **Pull Requests:** Code contributions
- **Specs:** Feature proposals via `docs/specs/`

### Before Asking

1. Check existing issues and discussions
2. Read relevant documentation
3. Search error database: `docs/errors/`

---

## Recognition

Contributors will be:
- Listed in release notes
- Added to CONTRIBUTORS.md
- Acknowledged in documentation

---

## Code of Conduct

- Be respectful and constructive
- Assume good intentions
- Focus on operational value
- Honest about limitations
- Credit others' work

---

Thank you for contributing to COALA SwarmOps!

> *"Every contribution, no matter how small, strengthens the swarm."*