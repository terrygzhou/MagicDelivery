# MagicDelivery

Enterprise Architecture artefacts for **MagicDelivery's AgenticEA** AI transformation programme — generated using ArcKit TOGAF ADM and Agent Architecture plugins.

## Programme

| Field | Value |
|-------|-------|
| **Program** | AgenticEA — AI Agent Transformation |
| **Organisation** | MagicDelivery |
| **Scope** | Omnichannel AI agents across customer service, shopping, parcel tracking |
| **Budget** | USD $18.5M |
| **Timeline** | 12–24 months |
| **Classification** | OFFICIAL |

## Enterprise Architecture

### TOGAF ADM Cycle (15 artefacts)

| Phase | Artefact | Description |
|-------|----------|-------------|
| Foundation | PRIN | Enterprise Architecture Principles |
| Foundation | STKE | Stakeholder Drivers & Goals |
| Foundation | REQ | Requirements (functional, non-functional, integration, data) |
| Foundation | ADR | Architecture Decision Records |
| Foundation | RISK | Risk Register |
| Foundation | STRAT | Architecture Strategy (current → target state, 3-phase roadmap) |
| Preliminary | ADMP | Architecture Vision & Scope |
| Phase A | BPCM | Business Capability Map |
| Phase C | APPINV | Application Portfolio Inventory |
| Phase C | APPR | Application Rationalization |
| Phase E | GAPA | Gap Analysis |
| Phase F | TRANS | Transition Architecture & Migration Plan |
| Phase G | BORD | Architecture Board & Governance |
| Phase H | ACHG | Architecture Change Management |
| Repository | REPO | Cross-Project Architecture Repository |

### Agent Architecture (6 artefacts)

| Artefact | Description |
|----------|-------------|
| AGT-INV | Agent Inventory (8 agent types) |
| AGT-DES | Agent Design (architecture, patterns, orchestration) |
| AGT-INT | Agent Integration (multi-agent, cross-domain) |
| AGT-GOV | Agent Governance (guardrails, oversight, compliance) |
| AGT-SEC | Agent Security (controls, sandboxing, privacy) |
| AGT-MAT | Agent Maturity Assessment |

## ArcKit Plugin Workflow

This project was generated using two ArcKit plugins working together:

### ArcKit TOGAF ADM Plugin

The **TOGAF ADM** plugin drives the Architecture Development Method lifecycle, producing artefacts sequentially through dependency chains:

```
Foundation → PRIN → STKE → REQ → (ADR + RISK + STRAT)
    → ADMP → BPCM → (APPINV → APPR → GAPA → TRANS)
    → BORD → ACHG
    → REPO (cross-project synthesis)
```

**Key features**:
- Template-driven artefact generation with quality validation
- Dependency-aware sequential processing
- Enterprise governance framework integration
- 15 artefacts covering full ADM cycle (Preliminary → Phase H)

### ArcKit Agent Architecture Plugin

The **Agent Architecture** plugin generates AI agent-specific design artefacts following parallel dependency chains:

```
AGT-INV → AGT-DES → (AGT-INT + AGT-GOV + AGT-SEC)
    → AGT-MAT (requires all above)
```

**Key features**:
- Agent inventory and design specification
- Multi-agent orchestration patterns
- Governance, security, and maturity frameworks
- 6 artefacts covering agent lifecycle

### Plugin Integration

Both plugins follow strict dependency graphs, ensuring artefacts are generated in the correct order with proper traceability between:
- Business capabilities and application portfolios
- Agent designs and security controls
- Gap analysis and transition planning
- Governance frameworks and change management

## Artefacts

| Folder | Contents |
|--------|----------|
| `000-global/` | Enterprise-wide principles (PRIN) |
| `001-agentic-ea/` | AgenticEA programme artefacts (15 TOGAF ADM + 5 agent architecture) |

## Technology

- **ArcKit Version**: 5.15.2
- **Plugins**: `arckit-togaf-adm`, `arckit-agent-architecture`
- **Model**: Qwen3.6-27B
- **Generated**: 2026-07-01