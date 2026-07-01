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

## Generation Method

All artefacts produced using ArcKit plugins following strict dependency chains:

```
TOGAF ADM:  PRIN → STKE → REQ → (ADR + RISK + STRAT) → ADMP → BPCM → APPINV → APPR → GAPA → TRANS → BORD → ACHG → REPO
Agent Arch: AGT-INV → AGT-DES → (AGT-INT + AGT-GOV + AGT-SEC) → AGT-MAT
```

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
