# COLLAPSE.md

**Context and model collapse prevention protocol for AI agents — detect degradation before coherence fails.**

COLLAPSE.md is a plain-text Markdown file you place in the root of any AI agent project. It defines collapse triggers (context window exhaustion, model drift, repetition loops, coherence degradation), prevention measures (summarisation checkpoints, context rotation, drift detection), recovery steps (checkpoint state, compress context, notify, pause, await approval), and audit logging — so your agent detects cognitive failure early and never produces corrupted outputs.

- Full specification: [collapse.md](https://collapse.md)
- AI-readable: [llms.txt](https://collapse.md/llms.txt)
- License: MIT

---

## Quick Start

Copy [`COLLAPSE.md`](./COLLAPSE.md) into your project root:

```
your-project/
├── AGENTS.md
├── CLAUDE.md
├── COLLAPSE.md   ← add this
├── README.md
└── src/
```

---

## The AI Agent Safety Stack

COLLAPSE.md is part of a twelve-file open standard for AI agent safety, quality, and accountability:

### Operational Control

| Spec | Purpose | Repo | Site |
|------|---------|------|------|
| THROTTLE.md | Rate and cost control — slow down before hitting limits | [throttle-md/spec](https://github.com/throttle-md/spec) | [throttle.md](https://throttle.md) |
| ESCALATE.md | Human notification and approval protocols | [escalate-md/spec](https://github.com/escalate-md/spec) | [escalate.md](https://escalate.md) |
| FAILSAFE.md | Safe fallback to last known good state | [failsafe-md/spec](https://github.com/failsafe-md/spec) | [failsafe.md](https://failsafe.md) |
| KILLSWITCH.md | Emergency stop — halt all agent activity | [killswitch-md/spec](https://github.com/killswitch-md/spec) | [killswitch.md](https://killswitch.md) |
| TERMINATE.md | Permanent shutdown — no restart without human intervention | [terminate-md/spec](https://github.com/terminate-md/spec) | [terminate.md](https://terminate.md) |

### Data Security

| Spec | Purpose | Repo | Site |
|------|---------|------|------|
| ENCRYPT.md | Data classification and protection requirements | [encrypt-md/spec](https://github.com/encrypt-md/spec) | [encrypt.md](https://encrypt.md) |
| ENCRYPTION.md | Technical encryption standards and key rotation | [encryption-md/spec](https://github.com/encryption-md/spec) | [encryption.md](https://encryption.md) |

### Output Quality

| Spec | Purpose | Repo | Site |
|------|---------|------|------|
| SYCOPHANCY.md | Anti-sycophancy — require citations, enforce honest disagreement | [sycophancy-md/spec](https://github.com/sycophancy-md/spec) | [sycophancy.md](https://sycophancy.md) |
| COMPRESSION.md | Context compression — summarise safely, verify coherence | [compression-md/spec](https://github.com/compression-md/spec) | [compression.md](https://compression.md) |
| **COLLAPSE.md** | **Drift prevention — detect collapse, enforce recovery** | **[collapse-md/spec](https://github.com/collapse-md/spec)** | **[collapse.md](https://collapse.md)** |

### Accountability

| Spec | Purpose | Repo | Site |
|------|---------|------|------|
| FAILURE.md | Failure mode mapping — every error state and response | [failure-md/spec](https://github.com/failure-md/spec) | [failure.md](https://failure.md) |
| LEADERBOARD.md | Agent benchmarking — track quality, detect regression | [leaderboard-md/spec](https://github.com/leaderboard-md/spec) | [leaderboard.md](https://leaderboard.md) |

---

## Why This Exists

AI agents spend money, send messages, modify files, and call external APIs — often autonomously. Regulations are catching up:

- **EU AI Act** (August 2026) — mandates human oversight and shutdown capabilities
- **Colorado AI Act** (June 2026) — requires impact assessments and transparency
- **US state laws** — California, Texas, Illinois and others have active AI governance requirements

These specifications give you a standardised, auditable record of your agent's safety boundaries.

---

## Contributing

PRs welcome for additional detection patterns, language-specific parsers, and integration guides.

## License

MIT — use freely, modify freely, no attribution required.
