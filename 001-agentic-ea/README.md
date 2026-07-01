# Project 001 — AgenticEA: MagicDelivery Agent AI Transformation

## Overview

**Program**: AgenticEA — Agent AI Transformation Programme  
**Organisation**: MagicDelivery  
**Delivery Vehicle**: MagicDelivery Mobile App (gradual rollout)  
**Domain**: Customer service, shopping, parcel tracking via AI agents  
**Classification**: OFFICIAL  

## Description

AgenticEA is MagicDelivery's strategic AI transformation programme to integrate autonomous AI agents into the MagicDelivery Mobile App, delivering enhanced customer service, parcel tracking, and e-commerce experiences through conversational AI.

### Enterprise Architecture Generation

All EA artefacts were produced using **ArcKit** plugins following the TOGAF ADM lifecycle and Agent Architecture framework:

#### ArcKit TOGAF ADM Plugin
The `togaf-adm` plugin drives the full Architecture Development Method cycle, generating sequential artefacts that build on each other:

1. **Foundation Layer** — Establish governance baseline
   - PRIN (Architecture Principles) — Strategic guardrails and decision framework
   - STKE (Stakeholder Analysis) — Driver, goal, and risk mapping
   - REQ (Requirements) — Functional, non-functional, integration, data requirements
   - ADR (Architecture Decisions) — Technology choices with rationale and alternatives
   - RISK (Risk Register) — Compliance, security, operational risk assessment
   - STRAT (Architecture Strategy) — Current vs target state, 3-phase transformation roadmap

2. **TOGAF ADM Phases** — Sequential artefact generation
   - ADMP (Preliminary) — Architecture vision, scope, success criteria
   - BPCM (Phase A) — Business capability map with maturity assessment
   - APPINV (Phase C) — Application portfolio inventory
   - APPR (Phase C) — Rationalization decisions (consolidate/modernize/retire/augment)
   - GAPA (Phase E) — Gap analysis with heat maps and prioritization
   - TRANS (Phase F) — Transition architecture with workstreams and phased delivery
   - BORD (Phase G) — Governance framework and architecture board charter
   - ACHG (Phase H) — Change management framework and evolution planning

3. **Repository** — Cross-project synthesis and pattern catalog

#### ArcKit Agent Architecture Plugin
The `agent-architecture` plugin generates AI agent-specific design artefacts:

1. **AGT-INV** (Agent Inventory) — Catalog of existing and planned AI agents
2. **AGT-DES** (Agent Design) — Architectural specification for agent capabilities
3. **AGT-INT** (Agent Integration) — Multi-agent orchestration patterns
4. **AGT-GOV** (Agent Governance) — Guardrails, monitoring, and oversight
5. **AGT-SEC** (Agent Security) — Security controls and sandboxing
6. **AGT-MAT** (Agent Maturity) — Program maturity assessment framework

#### Generation Process
All artefacts were generated sequentially following strict dependency chains:
```
PRIN → STKE → REQ → (ADR + RISK + STRAT)
    → ADMP → BPCM → (APPINV → APPR → GAPA → TRANS)
    → BORD → ACHG
    → REPO (cross-project synthesis)
```
Agent architecture follows parallel dependencies:
```
AGT-INV → AGT-DES → (AGT-INT + AGT-GOV + AGT-SEC)
    → AGT-MAT (requires all above)
```

### Strategic Objectives

| Objective | Target | Timeline |
|-----------|--------|----------|
| Incremental AI-attributed revenue | USD $25M annual run-rate | Month 18 |
| Customer experience (NPS) | +10 point improvement (32 → 42) | Month 12 |
| Routine call deflection | 40% reduction | Month 12 |
| Staff upskilling | 2,000 staff AI-certified | Month 18 |
| Privacy compliance | Zero Privacy Act breaches | Continuous |
| Platform capability | 50,000 concurrent users, <2s p95 | Month 12 |

### Programme Budget

- **Total Approved Budget**: USD $18.5M
- **Delivery Window**: 12 to 24 months
- **Variance Threshold**: 10% (budget and timeline)

## Artefacts

| Document ID | Type | Title | Status |
|-------------|------|-------|--------|
| ARC-000-PRIN-v1.0 | PRIN | Enterprise Architecture Principles | DRAFT |
| ARC-000-PRIN-v2.0 | PRIN | Architecture Principles (refined scope) | DRAFT |
| ARC-001-STKE-v1.0 | STKE | Stakeholder Drivers & Goals Analysis | DRAFT |
| ARC-001-REQ-v1.0 | REQ | Requirements | DRAFT |
| ARC-001-ADR-v1.0 | ADR | Architecture Decision Records | DRAFT |
| ARC-001-RISK-v1.0 | RISK | Risk Register | DRAFT |
| ARC-001-STRAT-v1.0 | STRAT | Architecture Strategy | DRAFT |
| ARC-001-ADMP-v1.0 | ADMP | Architecture Vision (ADM Preliminary) | DRAFT |
| ARC-001-BPCM-v1.0 | BPCM | Business Capability Map (Phase A) | DRAFT |
| ARC-001-APPINV-v1.0 | APPINV | Application Inventory (Phase C) | DRAFT |
| ARC-001-APPR-v1.0 | APPR | Application Rationalization (Phase C) | DRAFT |
| ARC-001-GAPA-v1.0 | GAPA | Gap Analysis (Phase E) | DRAFT |
| ARC-001-TRANS-v1.0 | TRANS | Transition Architecture (Phase F) | DRAFT |
| ARC-001-BORD-v1.0 | BORD | Architecture Board (Phase G) | DRAFT |
| ARC-001-ACHG-v1.0 | ACHG | Architecture Change (Phase H) | DRAFT |
| ARC-001-REPO-v1.0 | REPO | Architecture Repository | DRAFT |

## Stakeholders

- **Executive Sponsor**: Parcel Business GM/VP
- **Executive Leadership**: CEO / Board
- **Digital Technology**: Head of Digital Technology / CIO Office
- **Program Delivery**: PMs, Product Owners, Scrum Masters, Tech Leads
- **Compliance/Legal**: Legal & Regulatory Affairs Team
- **Customers**: 10M Australian consumers and businesses
- **Operations Staff**: Call Centre, Retail, Logistics (~10,000 staff)

## Compliance Framework

- **Privacy Act 1988 (Cth)** — Australian Privacy Principles (APPs)
- **Australian Competition and Consumer Law** — ACCC consumer protection obligations
- **Fair Work Act 2009 (Cth)** — Workforce impact and industrial relations
- **OAIC** — Privacy regulator engagement and compliance
- **WCAG 2.1 AA** — Accessibility standards for AI features

## Delivery Principles

- AI augmentation of workforce (zero net FTE reduction pledge)
- Privacy-by-design architecture from inception
- Phased rollout with measurable success gates per phase
- Governance embedded in delivery pipeline, not bolted on
- Customer trust as foundational requirement for adoption

## References

- Enterprise Architecture Principles: `projects/000-global/ARC-000-PRIN-v1.0.md`
- OAIC AI and Privacy Guidance: https://www.oaic.gov.au/artificial-intelligence/
- Australian AI Centre of Excellence: https://aace.edu.au/
- Treasury AI Regulation Review: https://treasury.gov.au/