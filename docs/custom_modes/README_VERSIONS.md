# COALA SwarmOps — Custom Modes Versions

## Free Tier: v6.0 Starter Swarm

**Included in this repository.** Copy `custom_modes_v6.0.yaml` to your RooCode custom modes folder to get started in 15 minutes.

### What You Get (Free)

| Feature | v6.0 |
|---------|------|
| **Agents** | Core starter team (T1 executors + T0 local + T3 planners) |
| **Pipeline** | Basic SDD: Requirements → Specification → Coordination |
| **Tiers** | T0 (local $0) + T1 (cloud) + T3 (strategic) |
| **Gates** | None — direct execution |
| **Anti-duplicate** | No |
| **Human gate** | No |
| **CoALA memory** | No |
| **Agnostic CLI** | No |
| **Circuit breaker** | No |
| **Score** | Starter baseline |

### Perfect For
- Trying the swarm concept
- Small personal projects
- Learning how multi-agent orchestration works
- Evaluating before upgrading

---

## Premium Tiers

Upgrade to unlock production-grade swarms with more agents, validation gates, cost optimization, and advanced reasoning.

| Tier | Version | Price | Agents | Highlights |
|------|---------|-------|--------|------------|
| 🥉 **Starter** | v6.1 | $7.99 one-time | Expanded | Anti-duplicate, human gate, T2 basic escalation |
| 🥈 **Production** | v6.2 | $19.99 one-time | Full team | 3 validation gates, CoALA memory, full T2 escalation. **+ POS/Inventory docker-compose template** |
| 🥇 **Docker & Ecommerce** | v6.3 | $14.99 one-time | Full team + | CoALA loop, Agnostic CLI, RAG expanded. **+ Ecommerce docker-compose template** |
| 💰 **Pro** | v6.5 | $49/mo | Expanded | T0 local agents ($0 cost), circuit breaker, error learning, monthly updates |
| 🏢 **Enterprise** | v6.7 | $299/mo | Maximum | Tiered cloud agents, enhanced local agents, full validation gates, all starter templates, priority support, roadmap voting |

### How to Upgrade

1. **One-time purchases (v6.1, v6.2, v6.3):** [Buy Me a Coffee](https://buymeacoffee.com/coalaswarmops)
2. **Subscriptions (v6.5, v6.7):** [GitHub Sponsors](https://github.com/sponsors/Aquilesnake)

After purchase, you'll receive:
- The YAML file for your version
- Docker-compose templates (where included)
- Installation instructions

---

## Version Comparison (Score Dimensions)

| Dimension | v6.0 (Free) | v6.2 (Production) | v6.7 (Enterprise) |
|-----------|-------------|-------------------|-------------------|
| Architecture T0-T3 | Baseline | Good | Excellent |
| Error Handling | Baseline | Good | Excellent |
| Role Coverage | Baseline | Good | Excellent |
| Validation Gates | Minimal | Good | Excellent |
| Security | Baseline | Good | Excellent |
| Cost Scalability | Baseline | Good | Excellent |
| TDD & Quality | Baseline | Good | Excellent |
| **Total** | **~33** | **~82** | **~92** |

---

## Installation (All Versions)

```bash
# 1. Copy the YAML to RooCode custom modes
# Windows:
copy custom_modes_v6.X.yaml %USERPROFILE%\.vscode\extensions\roo-code\.roo\custom_modes.yaml

# Linux / macOS:
cp custom_modes_v6.X.yaml ~/.vscode/extensions/roo-code/.roo/custom_modes.yaml

# 2. Restart VS Code
# 3. Open Command Palette → "Roo Code: Switch Mode"
```

Full guide: [`docs/INSTALL.md`](../INSTALL.md)

---

## FAQ

**Q: Can I keep the YAML after canceling a subscription?**
A: Yes. You sponsor 1 month, download your YAML, and it's yours. Cancel anytime.

**Q: What's the difference between one-time and subscription?**
A: One-time (v6.1-v6.3) = you get the YAML as-is. Subscription (v6.5, v6.7) = you get updates, new versions, and support.

**Q: Is v6.0 enough for production?**
A: v6.0 is for learning and small projects. Production teams should use v6.2+ for validation gates and CoALA memory.

**Q: Do you offer custom swarms for my tech stack?**
A: Enterprise tier includes roadmap voting — if enough clients request a stack, we build it.

---

*Last updated: 2026-05-30*
*Maintained by: COALA SwarmOps*
