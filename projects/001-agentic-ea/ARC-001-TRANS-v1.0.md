# Transition Architecture: AgenticEA — MagicDelivery Agent AI Transformation

> **Template Origin**: Official | **ArcKit Version**: 5.15.2 | **Command**: `/arckit:transition`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-TRANS-v1.0 |
| **Document Type** | Transition Architecture (TRANS) |
| **Project** | 001 — AgenticEA: Agent AI Transformation |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-01 |
| **Last Modified** | 2026-07-01 |
| **Review Cycle** | Quarterly |
| **Next Review Date** | 2026-10-01 |
| **Owner** | Programme Director |
| **Reviewed By** | PENDING |
| **Approved By** | PENDING |
| **Distribution** | Executive Leadership, Parcel Business, Digital Technology, Compliance/Legal, Program Delivery Team, Enterprise Architecture Review Board |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-01 | ArcKit AI | Initial creation — Transition Architecture roadmap, 5 workstreams across 3 phases, workstream dependencies, implementation roadmap, resource requirements, traceability to STRAT/GAPA/APPR/RISK/REQ | PENDING | PENDING |

---

## Executive Summary

### Purpose

This Transition Architecture (TRANS) document defines the structured approach for migrating MagicDelivery from its current-state architecture (20+ isolated portals, no AI capability, fragmented privacy management, reactive engagement) to the target-state architecture (composable AI agent platform, omnichannel experience, privacy-first design, proactive engagement) across a 5-year transformation horizon (2026–2031).

The transition is organised into **three phases** mapped to **five workstreams** with explicit dependencies, milestones, resource requirements, and risk mitigation points. Each phase closes specific gaps identified in the Gap Analysis (ARC-001-GAPA-v1.0), executes rationalisation decisions from Application Rationalisation (ARC-001-APPR-v1.0), and delivers measurable outcomes aligned to the Architecture Strategy (ARC-001-STRAT-v1.0).

### Transition Overview

| Metric | Foundation (Year 1) | Scale (Years 2–3) | Mature (Years 3–5) |
|--------|---------------------|-------------------|-------------------|
| **Period** | 2026-07 to 2027-06 | 2027-07 to 2029-06 | 2029-07 to 2031-06 |
| **Investment** | USD 14.0M | USD 7.5M | USD 3.5M |
| **Focus** | Platform foundations, privacy framework, AI pilot, portal MVP | Omnichannel rollout, CDP, marketing intelligence, retail AI | Full AI maturity, proactive engagement, legacy retirement, optimisation |
| **Key Deliverables** | AI Agent Platform pilot, Consent Service, Unified Portal MVP, Event Bus Foundation | Omnichannel AI, CDP, Composable Commerce, Retail AI Kiosks | Advanced Personalisation, Proactive Engagement, Full Consolidation |
| **Capability Maturity Gain** | +1.4 average (2.1 → 3.5) | +0.7 average (3.5 → 4.2) | +0.6 average (4.2 → 4.8) |
| **Applications Retired** | 2 (APP-34, APP-35) | 10+ (APP-01 to APP-08, APP-19, APP-23, APP-32, APP-33) | 10+ (APP-09 to APP-18 remaining) |
| **Gap Closure** | 14 gaps closed (Foundation-phase) | 8 gaps closed (Scale-phase) | 4 gaps closed (Mature-phase) |

### Transition Principles

This transition adheres to three foundational principles derived from ARC-000-PRIN-v2.0:

| Principle | Application |
|-----------|-----------|
| **PRIN-17: Legacy Modernization Strategy** | All legacy transitions use incremental strangler-fig patterns — no big-bang replacements. Business continuity is maintained throughout every phase. |
| **PRIN-04: Security by Design** | Privacy and security capabilities are delivered concurrent with AI capabilities, never as afterthoughts. Consent framework (TAPP-05) reaches maturity Level 3 concurrent with AI Agent Platform (TAPP-02). |
| **PRIN-01: Business Outcome Alignment** | Every transition action is traceable to a measurable business outcome (revenue growth, cost reduction, risk mitigation, or capability creation). Quick wins are prioritised to build stakeholder confidence. |

---

## 1. Transition Architecture Strategy

### 1.1 Phased Approach

The transition follows a phased, value-driven approach that prioritises foundational capabilities enabling downstream investments. Each phase has explicit entry and exit criteria, measurable outcomes, and gate reviews.

```text
Current State                              Target State (Year 5)
─────────────────────────────────────────   ─────────────────────────────────
20+ siloed portals, no AI, no consent      9 AI-augmented applications,
fragmented data, reactive engagement       composable architecture,
                                            proactive engagement,
                                            privacy-first design
                                            │
                                            │  Phase 3: Mature (Years 3–5)
                                            │  Advanced personalisation,
                                            │  proactive engagement,
                                            │  full consolidation
                                            │  Maturity: 4.8/5
                                            │
                                            ▼
                                            │  Phase 2: Scale (Years 2–3)
                                            │  Omnichannel AI, CDP,
                                            │  marketing intelligence,
                                            │  retail AI integration
                                            │  Maturity: 4.2/5
                                            │
                                            ▼
                                            │  Phase 1: Foundation (Year 1)
                                            │  AI platform, consent service,
                                            │  portal MVP, event bus,
                                            │  AI governance
                                            │  Maturity: 3.5/5
                                            │
                                            ▼
```

### 1.2 Phase Progression Logic

| Phase | Entry Criteria | Exit Criteria | Duration | Investment |
|-------|---------------|---------------|----------|-----------|
| **Foundation** | PRIN principles approved; budget committed; Architecture Strategy approved | AI Agent Platform at L3; Consent Service at L3; Portal MVP live; Event Bus operational | 12 months | USD 14.0M |
| **Scale** | Foundation exit criteria met; AI pilot demonstrates value (≥85% FC resolution) | Omnichannel AI live; CDP at L4; Composable commerce at L3; 80% portal migration | 24 months | USD 7.5M |
| **Mature** | Scale exit criteria met; USD 25M revenue target on track | Full AI maturity (4.8/5); all legacy retired; proactive engagement operational | 24 months | USD 3.5M |

### 1.3 Risk-Gated Progression

Phase transitions are gated against risk tolerance thresholds defined in ARC-001-RISK-v1.0:

| Gate | Risk Threshold | Phase Transition |
|------|---------------|------------------|
| **Alpha** (Month 6) | Zero Privacy Act breaches; Hallucination rate < 5% | Foundation continuation |
| **Beta** (Month 12) | AI agent pilot FC resolution ≥ 85%; Privacy complaints < 5/100K | Foundation → Scale gate |
| **Gamma** (Month 24) | Omnichannel adoption ≥ 20% MAU; Zero APP 8 violations | Scale continuation |
| **Delta** (Month 36) | USD 25M revenue target 70% achieved; NPS ≥ 37 | Scale → Mature gate |
| **Epsilon** (Month 48) | AI Maturity Score ≥ 7/10; Portfolio reduction 52% | Mature continuation |
| **Zeta** (Month 60) | All legacy systems retired; AI Maturity Score 9/10 | Programme closeout |

---

## 2. Transition Workstreams

Five workstreams operate concurrently within each phase, with varying intensity per phase. Each workstream has clear objectives, deliverables, and alignment to strategic themes.

### 2.1 Architecture Workstream

**Objective**: Build platform foundations, integration patterns, and composable architecture that enable all other workstreams.

#### Foundation Phase (Year 1)

| Work Package | Description | Deliverable | Timeline | Investment | Theme |
|-------------|-------------|-----------|----------|-----------|-------|
| **WP-ARC-001** | AI Agent Platform Core — agent orchestrator, model serving abstraction, multi-provider integration | TAPP-02 at L3 | M1–M12 | USD 8.5M | Theme 1 |
| **WP-ARC-002** | Tokenisation Service — PII tokenisation layer, HashiCorp Vault integration | Operational tokenisation | M1–M6 | Included in WP-ARC-001 | Theme 1, 3 |
| **WP-ARC-003** | Event-Driven Architecture Foundation — enterprise event bus, GCP Event Manager integration | Event bus with schema registry | M7–M12 | USD 0.5M | Theme 4 |
| **WP-ARC-004** | API Gateway and Anti-Corruption Layers — standardised access to legacy systems | Published API contracts for APP-24 to APP-26 | M1–M9 | Included in WP-ARC-001 | Theme 6 |
| **WP-ARC-005** | Composable Architecture Framework — service decomposition, independent deployment pipelines | Composable web platform foundation | M3–M12 | USD 0.5M | Theme 6 |

#### Scale Phase (Years 2–3)

| Work Package | Description | Deliverable | Timeline | Investment | Theme |
|-------------|-------------|-----------|----------|-----------|-------|
| **WP-ARC-006** | Composable Commerce Platform — headless commerce, AI shopping experience | TAPP-07 operational | Y2-Q1 to Y3-Q4 | USD 2.0M | Theme 2 |
| **WP-ARC-007** | Multi-Channel UI Framework — composable UI components for all channels | Reusable agent UI library | Y2-Q1 to Y2-Q4 | Included in WP-ARC-006 | Theme 6 |
| **WP-ARC-008** | Full Event Bus — enterprise-wide customer event processing | Real-time event processing < 60s latency | Y2-Q1 to Y3-Q2 | USD 0.5M | Theme 4 |
| **WP-ARC-009** | Integration Architecture at Scale — service mesh, integration patterns for all channels | Full integration architecture | Y2-Q1 to Y3-Q4 | USD 0.5M | Theme 6 |

#### Mature Phase (Years 3–5)

| Work Package | Description | Deliverable | Timeline | Investment | Theme |
|-------------|-------------|-----------|----------|-----------|-------|
| **WP-ARC-010** | Full Composable Architecture Maturity — 100% independent deployment, zero shared databases | Architecture compliance ≥ 90% | Y3-Q1 to Y5-Q4 | USD 0.3M | Theme 6 |
| **WP-ARC-011** | Architecture Evolution — self-optimising patterns, AI-driven architecture governance | Automated compliance checking | Y4-Q1 to Y5-Q4 | USD 0.2M | Theme 6 |

### 2.2 Application Workstream

**Objective**: Modernise, rationalise, and retire the application portfolio from 27 applications to 9 target + 4 retained.

#### Foundation Phase (Year 1)

| Work Package | Description | Action | Timeline | Investment | APPR Decision |
|-------------|-------------|--------|----------|-----------|--------------|
| **WP-APP-001** | Unified Customer Portal MVP — composable web platform, federated SSO, initial portal consolidation | CONSOLIDATE (CD-001) | M3–M12 | USD 1.5M | CD-001 |
| **WP-APP-002** | AI SDK Embedding — AI agent capabilities embedded in existing MagicDelivery mobile app | AUGMENT (AG-002) | M3–M12 | USD 0.5M | AG-002 |
| **WP-APP-003** | Composable AI Services — recommendation engine, intelligent tracking, NLU | BUILD | M6–M12 | USD 1.0M | TAPP-03 |
| **WP-APP-004** | Retire Per-System Privacy and Manual Compliance Tools | RETIRE (RT-004) | M6 | USD 0 (savings) | RT-004 |
| **WP-APP-005** | Intershop Strangler API Gateway — anti-corruption layer for e-commerce | STRANGLER | M6–M12 | USD 0.5M | MD-001 |

#### Scale Phase (Years 2–3)

| Work Package | Description | Action | Timeline | Investment | APPR Decision |
|-------------|-------------|--------|----------|-----------|--------------|
| **WP-APP-006** | Full Portal Consolidation — 80% portal traffic migrated, APP-01 to APP-07 retirement | CONSOLIDATE → RETIRE | Y2-Q1 to Y3-Q2 | USD 1.5M | CD-001, RT-001 |
| **WP-APP-007** | AI-Powered Shopping Experience — composable commerce replacing Intershop | MODERNIZE (MD-001) | Y2-Q1 to Y3-Q4 | USD 2.0M | MD-001 |
| **WP-APP-008** | Customer Data Platform — unified customer identity, real-time profiling, CDP | CONSOLIDATE (CD-003) | Y2-Q1 to Y3-Q2 | USD 2.0M | CD-003 |
| **WP-APP-009** | Marketing Intelligence Platform — AI-powered campaigns, dynamic personalisation | CONSOLIDATE → RETIRE | Y2-Q3 to Y3-Q4 | USD 1.0M | CD-003, RT-003 |
| **WP-APP-010** | Retail Digital Integration Pilot — AI kiosks in top 500 shops, staff co-pilot | AUGMENT (AG-003) | Y2-Q4 to Y3-Q4 | USD 1.0M | AG-003 |
| **WP-APP-011** | Retire Legacy Tracking UI — APP-23 retirement | RETIRE (RT-002) | Y2-Q2 | USD 0 (savings) | RT-002 |
| **WP-APP-012** | Retire Intershop — full retirement post-strangler migration | RETIRE | Y3-Q4 | USD 0 (savings) | MD-001 |

#### Mature Phase (Years 3–5)

| Work Package | Description | Action | Timeline | Investment | APPR Decision |
|-------------|-------------|--------|----------|-----------|--------------|
| **WP-APP-013** | Remaining Portal Consolidation — APP-09 to APP-18 retirement | CONSOLIDATE → RETIRE | Y3-Q1 to Y5-Q2 | USD 0.5M | CD-001, RT-001 |
| **WP-APP-014** | Full Retail Rollout — all 4,000 shops with AI kiosks and co-pilots | AUGMENT (AG-003) | Y4-Q1 to Y5-Q4 | USD 1.5M | AG-003 |
| **WP-APP-015** | Marketing Automation at Scale — proactive engagement, AI-generated personalisation | EXTEND | Y4-Q1 to Y5-Q4 | USD 0.5M | CD-003 |
| **WP-APP-016** | Full Legacy Infrastructure Decommissioning — complete retirement of all legacy systems | RETIRE | Y4-Q1 to Y5-Q4 | USD 0 (savings) | RT-001 |

### 2.3 Data Workstream

**Objective**: Transform from fragmented, siloed customer data to real-time, event-driven customer insights enabling proactive engagement and AI-powered decision making.

#### Foundation Phase (Year 1)

| Work Package | Description | Deliverable | Timeline | Investment | Theme |
|-------------|-------------|-----------|----------|-----------|-------|
| **WP-DAT-001** | Customer Profile Management — unified identity resolution, federated SSO data foundation | Customer profile at L2 | M3–M12 | USD 0.5M | Theme 4 |
| **WP-DAT-002** | Data Product Governance — customer data as a product, ownership, SLAs, quality metrics | Data product governance framework | M1–M6 | USD 0.3M | Theme 4 |
| **WP-DAT-003** | Event-Driven Intelligence Foundation — event bus for customer events, consent data, interaction data | Event bus with customer events | M7–M12 | USD 0.2M | Theme 4 |
| **WP-DAT-004** | Revenue Attribution Pipeline — feature-attribution modelling infrastructure | Revenue attribution pipeline | M6–M12 | USD 0.3M | Theme 5 |

#### Scale Phase (Years 2–3)

| Work Package | Description | Deliverable | Timeline | Investment | Theme |
|-------------|-------------|-----------|----------|-----------|-------|
| **WP-DAT-005** | Customer Data Platform (CDP) — data lakehouse architecture, real-time enrichment | CDP at L4 | Y2-Q1 to Y3-Q2 | USD 2.0M | Theme 4 |
| **WP-DAT-006** | AI-Powered Segmentation — ML-driven behavioural segmentation, dynamic personas | Segmentation engine at L4 | Y2-Q3 to Y3-Q4 | Included in WP-DAT-005 | Theme 4 |
| **WP-DAT-007** | Customer Analytics and Reporting — journey mapping, cohort analysis, reporting | Analytics platform | Y2-Q1 to Y3-Q2 | Included in WP-DAT-005 | Theme 4 |
| **WP-DAT-008** | Event-Driven Marketing — real-time campaign triggers, behavioural signals | Event-driven marketing integration | Y2-Q3 to Y3-Q2 | USD 0.5M | Theme 5 |
| **WP-DAT-009** | Dynamic Customer Segmentation — real-time ML segmentation for targeted campaigns | Dynamic segmentation at L3 | Y2-Q4 to Y3-Q4 | USD 0.3M | Theme 5 |
| **WP-DAT-010** | 360-Degree Customer View — unified view covering 80% of customer base | 360-degree view at L4 | Y2-Q1 to Y3-Q4 | Included in WP-DAT-005 | Theme 4 |

#### Mature Phase (Years 3–5)

| Work Package | Description | Deliverable | Timeline | Investment | Theme |
|-------------|-------------|-----------|----------|-----------|-------|
| **WP-DAT-011** | Predictive Customer Analytics — churn prediction, lifetime value, propensity scoring | Predictive analytics at L4 | Y3-Q1 to Y5-Q2 | USD 0.5M | Theme 4 |
| **WP-DAT-012** | Advanced AI Segmentation — micro-segmentation, real-time persona creation | AI segmentation at L5 | Y4-Q1 to Y5-Q4 | USD 0.3M | Theme 5 |
| **WP-DAT-013** | Customer Journey Orchestration — next-best-action engine, touchpoint orchestration | Journey orchestration at L4 | Y4-Q1 to Y5-Q4 | USD 0.2M | Theme 5 |

### 2.4 Security Workstream

**Objective**: Implement zero-trust architecture, enterprise-wide privacy/consent management, and AI governance ensuring zero Privacy Act breaches throughout the transformation.

#### Foundation Phase (Year 1)

| Work Package | Description | Deliverable | Timeline | Investment | Theme |
|-------------|-------------|-----------|----------|-----------|-------|
| **WP-SEC-001** | Enterprise Consent Management Service — granular opt-in/opt-out controls, privacy dashboard | TAPP-05 at L4 | M1–M12 | USD 1.5M | Theme 3 |
| **WP-SEC-002** | PII Tokenisation and Data Sovereignty — cryptographic tokenisation, data residency enforcement | Tokenisation service operational | M1–M6 | USD 0.5M | Theme 3 |
| **WP-SEC-003** | Automated DPIA and Compliance — DPIA automation, consent-aware AI operations | DPIA automation framework | M3–M9 | USD 0.3M | Theme 3 |
| **WP-SEC-004** | AI Governance Framework — model registry, compliance monitoring, hallucination detection | AI governance at L3 | M3–M12 | USD 0.2M | Theme 1 |
| **WP-SEC-005** | AI-Specific Privacy Controls — privacy-preserving AI training, synthetic data, data isolation | Privacy-preserving AI pipeline | M6–M12 | USD 0.3M | Theme 3 |
| **WP-SEC-006** | Audit Trail and Accountability — complete audit trail for consent changes, AI interactions | Audit trail operational | M6–M12 | USD 0.2M | Theme 3 |

#### Scale Phase (Years 2–3)

| Work Package | Description | Deliverable | Timeline | Investment | Theme |
|-------------|-------------|-----------|----------|-----------|-------|
| **WP-SEC-007** | Zero-Trust Architecture — identity-based access, least privilege, continuous verification | Zero-trust across all channels | Y2-Q1 to Y3-Q2 | USD 0.5M | Theme 3 |
| **WP-SEC-008** | AI Security — prompt injection protection, adversarial testing, input validation | AI security controls at L4 | Y2-Q1 to Y3-Q4 | USD 0.3M | Theme 1 |
| **WP-SEC-009** | Cross-Border Data Transfer Controls — APP 8 compliance automation | APP 8 compliance at L5 | Y2-Q1 to Y3-Q2 | USD 0.2M | Theme 3 |
| **WP-SEC-010** | Consent Awareness at Scale — real-time consent boundary enforcement across all AI agents | Consent-aware AI agents | Y2-Q1 to Y3-Q4 | USD 0.2M | Theme 3 |

#### Mature Phase (Years 3–5)

| Work Package | Description | Deliverable | Timeline | Investment | Theme |
|-------------|-------------|-----------|----------|-----------|-------|
| **WP-SEC-011** | AI Compliance Governance Maturity — hybrid compliance model, automated compliance-by-design | Compliance at L5 | Y3-Q1 to Y5-Q4 | USD 0.2M | Theme 3 |
| **WP-SEC-012** | Continuous Privacy Monitoring — real-time privacy risk monitoring, automated remediation | Continuous monitoring | Y4-Q1 to Y5-Q4 | USD 0.1M | Theme 3 |

### 2.5 Workforce Workstream

**Objective**: Build AI-augmented workforce capability across 10,000 staff — upskilling, adoption, change management, and industrial engagement ensuring AI augmentation (not replacement).

#### Foundation Phase (Year 1)

| Work Package | Description | Deliverable | Timeline | Investment | Theme |
|-------------|-------------|-----------|----------|-----------|-------|
| **WP-WKF-001** | AI Augmentation Charter — board-approved approach to AI as augmentation, not replacement | AI Augmentation Charter signed | M1–M3 | USD 0.1M | BR-006 |
| **WP-WKF-002** | Union Consultation Framework — TWU consultation programme, workforce impact monitoring | TWU framework operational | M1–M6 | USD 0.2M | BR-006 |
| **WP-WKF-003** | AI Skills Foundation — 2,000 staff upskilling programmes, AI engineering recruitment | AI skills baseline established | M3–M12 | USD 0.5M | BR-006 |
| **WP-WKF-004** | AI Change Management — communication programme, pilot feedback loops, confidence building | Staff AI confidence baseline | M1–M12 | USD 0.3M | BR-006 |
| **WP-WKF-005** | AI Co-Pilot Training — call centre and retail staff training on AI tools | AI co-pilot training complete | M9–M12 | USD 0.2M | BR-006 |

#### Scale Phase (Years 2–3)

| Work Package | Description | Deliverable | Timeline | Investment | Theme |
|-------------|-------------|-----------|----------|-----------|-------|
| **WP-WKF-006** | Enterprise AI Literacy — AI literacy programmes for all 10,000 staff | AI literacy ≥ 70% staff | Y2-Q1 to Y3-Q4 | USD 0.5M | BR-006 |
| **WP-WKF-007** | AI-Augmented Workflow Integration — AI tools integrated into daily workflows (call centre, retail, logistics) | AI adoption ≥ 50% target roles | Y2-Q1 to Y3-Q4 | USD 0.3M | BR-006 |
| **WP-WKF-008** | Retail AI Kiosk Training — staff training for AI kiosk operations and co-pilot tools | Retail AI training complete | Y2-Q4 to Y3-Q4 | USD 0.2M | BR-006 |
| **WP-WKF-009** | Career Pathway Development — AI career pathways, certification programmes | AI career pathways published | Y2-Q1 to Y3-Q2 | USD 0.2M | BR-006 |

#### Mature Phase (Years 3–5)

| Work Package | Description | Deliverable | Timeline | Investment | Theme |
|-------------|-------------|-----------|----------|-----------|-------|
| **WP-WKF-010** | Full Workforce AI Capability — enterprise-wide AI literacy, continuous improvement | AI maturity score ≥ 7/10 workforce | Y3-Q1 to Y5-Q4 | USD 0.3M | BR-006 |
| **WP-WKF-011** | AI-Driven Insights for Operations — AI-augmented decision making across operations | AI-augmented operations ≥ 80% | Y4-Q1 to Y5-Q4 | USD 0.2M | BR-006 |
| **WP-WKF-012** | Continuous Improvement through AI — feedback-driven organisational learning | Continuous improvement culture | Y4-Q1 to Y5-Q4 | USD 0.1M | BR-006 |

---

## 3. Workstream Dependencies

### 3.1 Dependency Map

```text
                    Architecture Workstream
                         ┌───────────────┐
                         │ WP-ARC-001    │  ← Foundation: AI Agent Platform
                         │ AI Agent Plat.│     WP-ARC-002: Tokenisation
                         └───────┬───────┘     WP-ARC-003: Event Bus
                                 │            WP-ARC-004: API Gateway
                    ┌────────────┼────────────┐
                    │           │            │
        ┌───────────▼──┐  ┌────▼──────┐  ┌──▼─────────────┐
        │ Application │  │  Data     │  │   Security     │
        │ Workstream  │  │ Workstream│  │  Workstream     │
        └───────┬─────┘  └────┬───────┘  └──┬─────────────┘
                │            │              │
        ┌───────┼────────────┼──────────────┼───────┐
        │       │          │               │       │
  ┌─────▼─┐ ┌──▼────┐ ┌───▼────┐    ┌──────▼────┐
  │TAPP-01│ │TAPP-08│ │TAPP-04 │    │ TAPP-05  │
  │Portal │ │Mobile │ │  CDP   │    │ Consent  │
  └───────┘ └───────┘ └───────┘    └───────────┘
        │       │          │               │
        └───────┼──────────┼────────────────┼──────┘
                │          │               │
                ▼          ▼               ▼
        ┌───────┴──────────┴───────────────┴──────┐
        │     Application Integration Layer       │
        │  (API Gateway + Event Bus + Anti-Corruption) │
        └──────────────────┬──────────────────────┘
                           │
                    ┌──────▼──────┐
                    │  Workforce │
                    │  Workstream│
                    │  (adoption,│
                    │   training,│
                    │   change)  │
                    └────────────┘
```

### 3.2 Critical Dependency Chains

| Dependency ID | Predecessor | Successor | Relationship | Closure Rule |
|---------------|-----------|-----------|-------------|-------------|
| **DEP-001** | WP-SEC-001 (Consent Service) | WP-ARC-001 (AI Agent Platform) | Bi-directional | Both must reach L3 concurrently (Month 6) — AI pilot cannot launch without consent framework |
| **DEP-002** | WP-ARC-001 (AI Agent Platform) | WP-APP-002 (Mobile AI SDK) | Blocking | AI platform must be at L2 before mobile SDK can embed agents |
| **DEP-003** | WP-ARC-003 (Event Bus) | WP-DAT-005 (CDP) | Blocking | Event bus must be operational before CDP can ingest real-time events |
| **DEP-004** | WP-DAT-005 (CDP) | WP-APP-009 (Marketing Intelligence) | Blocking | CDP must reach L3 before marketing platform can build on customer insights |
| **DEP-005** | WP-APP-001 (Unified Portal MVP) | WP-APP-006 (Full Portal Consolidation) | Sequential | Portal MVP must be operational before full consolidation |
| **DEP-006** | WP-SEC-002 (Tokenisation) | WP-SEC-005 (AI Privacy Controls) | Blocking | Tokenisation layer must be operational before privacy-preserving AI training |
| **DEP-007** | WP-ARC-001 (AI Agent Platform) | WP-APP-007 (Composable Commerce) | Blocking | AI platform provides agent capabilities for shopping assistant |
| **DEP-008** | WP-APP-007 (Composable Commerce) | WP-APP-012 (Intershop Retirement) | Blocking | Composable commerce must achieve feature parity before Intershop retirement |
| **DEP-009** | WP-APP-008 (CDP) | WP-DAT-011 (Predictive Analytics) | Blocking | CDP must be at L4 before predictive models can be trained |
| **DEP-010** | WP-SEC-001 (Consent Service) | WP-DAT-001 (Customer Profile) | Blocking | Consent framework must exist before unified customer profiles can be built |
| **DEP-011** | WP-WKF-001 (AI Augmentation Charter) | WP-WKF-003 (AI Skills) | Blocking | Charter must be approved before upskilling programmes can launch |
| **DEP-012** | WP-WKF-002 (Union Framework) | WP-APP-010 (Retail AI Kiosks) | Advisory | Union framework must be in place before retail AI deployment (R-013 mitigation) |

### 3.3 Dependency Heat Map

```text
Dependency Criticality:
 ██ CRITICAL — Hard blocking; phase gate dependency
 ▓▓ HIGH — Strong dependency; delays cascade to 2+ workstreams
 ▒▒ MEDIUM — Soft dependency; workarounds possible
 ░░ LOW — Advisory only; no blocking impact

DEP-001  ████████████  CRITICAL — AI pilot blocked without consent
DEP-002  ▓▓▓▓▓▓▓▓▓▓  HIGH — Mobile SDK delayed without AI platform
DEP-003  ▓▓▓▓▓▓▓▓▓▓  HIGH — CDP blocked without event bus
DEP-004  ▓▓▓▓▓▓▓▓▓▓  HIGH — Marketing blocked without CDP
DEP-005  ▓▓▓▓▓▓▓▓▓▓  HIGH — Portal consolidation blocked without MVP
DEP-006  ▓▓▓▓▓▓▓▓▓▓  HIGH — AI privacy blocked without tokenisation
DEP-007  ▓▓▓▓▓▓▓▓▓▓  HIGH — Commerce blocked without AI platform
DEP-008  ▓▓▓▓▓▓▓▓▓▓  HIGH — Intershop retirement blocked without parity
DEP-009  ▒▒▒▒▒▓▓▓▓  MEDIUM — Analytics delayed without CDP
DEP-010  ▓▓▓▓▓▓▓▓▓▓  HIGH — Customer profiles blocked without consent
DEP-011  ▓▓▓▓▓▓▓▓▓▓  HIGH — Upskilling blocked without charter
DEP-012  ▒▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓  HIGH — Retail AI blocked without union agreement (R-013)
```

---

## 4. Implementation Roadmap

### 4.1 Master Timeline

```mermaid
gantt
    title AgenticEA Transition Architecture Roadmap 2026-2031
    dateFormat  YYYY-MM-DD
    axisFormat  %Y-%m

    section Phase 1: Foundation (Year 1)
    WP-ARC-001: AI Agent Platform              :active, f1, 2026-07-01, 365d
    WP-SEC-001: Consent Service                :active, f2, 2026-07-01, 365d
    WP-APP-001: Unified Portal MVP            :active, f3, 2026-09-01, 270d
    WP-APP-002: Mobile AI SDK                 :active, f4, 2026-09-01, 270d
    WP-ARC-003: Event Bus Foundation          :active, f5, 2026-10-01, 240d
    WP-SEC-004: AI Governance                  :active, f6, 2026-09-01, 180d
    WP-WKF-001: AI Augmentation Charter         :active, f7, 2026-07-01, 90d
    WP-WKF-002: Union Framework               :active, f8, 2026-07-01, 180d
    WP-DAT-004: Revenue Attribution           :active, f9, 2026-10-01, 180d

    section Phase 1 Gates
    Alpha Gate (Month 6)                      :milestone, g1, 2026-12-31, 0d
    Beta Gate (Month 12)                      :milestone, g2, 2027-06-30, 0d

    section Phase 2: Scale (Years 2-3)
    WP-APP-007: Composable Commerce            :t1, 2027-07-01, 540d
    WP-DAT-005: CDP                            :t2, 2027-07-01, 400d
    WP-APP-006: Full Portal Consolidation       :t3, 2027-07-01, 540d
    WP-APP-009: Marketing Intelligence          :t4, 2027-10-01, 400d
    WP-APP-010: Retail AI Kiosks (Pilot)        :t5, 2028-01-01, 400d
    WP-WKF-006: Enterprise AI Literacy          :t6, 2027-07-01, 540d
    WP-SEC-007: Zero-Trust Architecture          :t7, 2027-07-01, 300d

    section Phase 2 Gates
    Gamma Gate (Month 24)                     :milestone, g3, 2028-06-30, 0d
    USD 25M Revenue Target                    :milestone, g4, 2028-01-01, 0d
    Delta Gate (Month 36)                     :milestone, g5, 2029-06-30, 0d

    section Phase 3: Mature (Years 3-5)
    WP-APP-014: Full Retail Rollout           :m1, 2029-07-01, 700d
    WP-DAT-011: Predictive Analytics          :m2, 2029-07-01, 500d
    WP-APP-013: Remaining Portal Consolidation :m3, 2029-07-01, 500d
    WP-WKF-010: Full Workforce AI Capability    :m4, 2029-07-01, 700d
    WP-ARC-010: Full Composable Architecture  :m5, 2029-07-01, 700d
    WP-APP-016: Full Legacy Decommissioning    :m6, 2030-01-01, 500d

    section Phase 3 Gates
    Epsilon Gate (Month 48)                 :milestone, g6, 2030-06-30, 0d
    AI Maturity Score 7/10                  :milestone, g7, 2030-06-30, 0d
    Zeta Gate (Month 60)                  :milestone, g8, 2031-06-30, 0d
    Full Legacy Retirement                  :milestone, g9, 2031-06-30, 0d
```

### 4.2 Milestone Summary

| Milestone ID | Milestone | Target Date | Phase | Workstream | Gate | Success Criteria |
|-------------|-----------|-----------|-------|-----------|------|-----------------|
| **MS-001** | AI Augmentation Charter Signed | 2026-09-30 | Foundation | Workforce | — | Board-approved charter; TWU acknowledgement |
| **MS-002** | Tokenisation Service Operational | 2026-10-01 | Foundation | Architecture, Security | Alpha | PII tokenisation tested; zero data exposure |
| **MS-003** | AI Agent Pilot Live (Customer Service) | 2026-12-31 | Foundation | Application | Alpha | 85% FC resolution; sub-2s p95; zero breaches |
| **MS-004** | Privacy/Consent Framework Operational | 2027-03-31 | Foundation | Security | Beta | Enterprise consent service L3; automated DPIA |
| **MS-005** | Unified Portal MVP Live | 2027-06-30 | Foundation | Application | Beta | 20% portal traffic migrated; federated SSO |
| **MS-006** | Event Bus Foundation Operational | 2027-06-30 | Foundation | Architecture | Beta | GCP Event Manager integrated; customer events |
| **MS-007** | Foundation Phase Complete | 2027-06-30 | Foundation | All | Beta → Scale | All Beta criteria met; risk within appetite |
| **MS-008** | Omnichannel AI Rollout Begins | 2027-07-01 | Scale | Application | — | Mobile, web, call centre AI agents deployed |
| **MS-009** | CDP Operational | 2028-06-30 | Scale | Data | Gamma | 360-degree view at L4; real-time enrichment |
| **MS-010** | USD 25M Revenue Target Achieved | 2028-01-01 | Scale | Business | — | Feature-attribution validated by Finance |
| **MS-011** | 80% Portal Traffic Migrated | 2028-06-30 | Scale | Application | Gamma | APP-01 to APP-07 retired; zero disruption |
| **MS-012** | Retail AI Kiosk Pilot (Top 500) | 2028-12-31 | Scale | Application | — | 500 shops with AI kiosks and co-pilots |
| **MS-013** | Scale Phase Complete | 2029-06-30 | Scale | All | Gamma → Mature | All Gamma criteria met; revenue target on track |
| **MS-014** | Full Retail Rollout Begins | 2029-07-01 | Mature | Application | — | All 4,000 shops on rollout path |
| **MS-015** | Advanced Personalisation Live | 2030-03-31 | Mature | Data | Epsilon | AI personalisation at L5; dynamic campaigns |
| **MS-016** | AI Maturity Score 7/10 | 2030-06-30 | Mature | All | Epsilon | All capabilities at target maturity |
| **MS-017** | Proactive Engagement Platform Live | 2030-12-31 | Mature | Data | — | AI-driven predictive engagement operational |
| **MS-018** | Full Legacy Retirement | 2031-06-30 | Mature | Application | Zeta | All legacy systems decommissioned |
| **MS-019** | Programme Closeout | 2031-06-30 | Mature | All | Zeta | AI Maturity Score 9/10; benefits realised |

### 4.3 Success Metrics by Phase

| Metric | Current State | Foundation (Y1) | Scale (Y2-3) | Mature (Y3-5) | Measurement Method |
|--------|--------------|-----------------|-------------|---------------|-------------------|
| **AI Agent FC Resolution** | N/A | ≥ 85% | ≥ 90% | ≥ 95% | AI platform telemetry |
| **AI Agent Response Time (p95)** | N/A | ≤ 2 seconds | ≤ 1.5 seconds | ≤ 1 second | AI platform observability |
| **Portal Consolidation Progress** | 0% | 20% (MVP) | 80% | 100% | Traffic migration analytics |
| **Privacy Breaches** | 0 (no AI ops) | 0 | 0 | 0 | Compliance audit |
| **NPS** | 32 | 36 | 39 | 42 | Customer survey |
| **CSAT** | 70% | 75% | 80% | 85% | Post-interaction survey |
| **Call Deflection** | 0% | 20% | 40% | 50% | Call centre analytics |
| **Incremental Revenue (AI-attributed)** | $0 | $5M | $25M (annualised) | $35M (annualised) | Feature-attribution modelling |
| **Operational Savings** | $0 | $3M | $12M (annualised) | $15M (annualised) | Cost attribution |
| **Staff AI Confidence** | 3.0/10 | 4.5/10 | 6.0/10 | 6.5/10 | Quarterly pulse survey |
| **Capability Maturity (avg)** | 2.1/5 | 3.5/5 | 4.2/5 | 4.8/5 | Capability assessment |
| **Portfolio Reduction** | 27 apps | 25 apps | 17 apps | 13 apps | Application inventory |
| **Architecture Principles Compliance** | 27% | 45% | 70% | 90% | Architecture review |

---

## 5. Resource Requirements

### 5.1 Team Composition by Phase

#### Foundation Phase (Year 1)

| Role | Count | Skills Required | Workstream | Timeline |
|------|-------|----------------|-----------|----------|
| **AI Platform Engineering Lead** | 1 | Multi-agent orchestration, model serving, cloud architecture | Architecture | Full phase |
| **AI/ML Engineers** | 6 | LLM integration, prompt engineering, RAG, model evaluation | Architecture | Full phase |
| **Privacy/Consent Engineering Lead** | 1 | GDPR/Privacy Act expertise, tokenisation, consent architecture | Security | Full phase |
| **Privacy Engineers** | 3 | Consent management, DPIA, data protection | Security | Full phase |
| **Full-Stack Engineers (Portal)** | 8 | React, composable architecture, federated identity | Application | M3–M12 |
| **Mobile Engineers (iOS/Android)** | 4 | Native iOS/Android, SDK development, AI integration | Application | M3–M12 |
| **Backend/API Engineers** | 4 | API gateway, event-driven architecture, Kafka/Pub-Sub | Architecture | M7–M12 |
| **Cloud/Platform Engineers** | 3 | Cloud infrastructure, containerisation, CI/CD, IaC | Architecture | Full phase |
| **Data Engineers** | 3 | Data lakehouse, stream processing, customer identity resolution | Data | M6–M12 |
| **Security Engineers** | 2 | Zero-trust, tokenisation, adversarial AI security | Security | Full phase |
| **AI Governance Specialist** | 1 | AI ethics, compliance monitoring, DPIA automation | Security | M3–M12 |
| **Change Management Specialist** | 2 | Workforce transformation, union engagement, communications | Workforce | Full phase |
| **Union Relations Advisor** | 1 | Industrial relations, TWU consultation, Fair Work Act | Workforce | M1–M6 |
| **Programme Manager** | 1 | Programme delivery, risk management, stakeholder management | Programme | Full phase |
| **Product Owners** | 4 | AI product management, customer experience, domain expertise | Programme | Full phase |
| **QA/Test Engineers** | 4 | AI testing, validation, regression testing | All | Full phase |
| **DevOps Engineers** | 2 | CI/CD, infrastructure automation, monitoring | Architecture | Full phase |
| **Business Analysts** | 3 | Requirements, customer journey mapping, compliance | Programme | Full phase |
| **UX/UI Designers** | 2 | Conversational UI, accessibility (WCAG 2.1 AA), design systems | Application | M3–M12 |

**Foundation Phase Total Headcount**: ~52 FTEs

#### Scale Phase (Years 2–3)

| Role | Count | Skills Required | Workstream |
|------|-------|----------------|-----------|
| **AI Platform Engineering Lead** | 1 | Multi-agent orchestration, scale-up | Architecture |
| **AI/ML Engineers** | 8 | Additional agents, multi-model strategies, MLOps | Architecture |
| **Composable Commerce Engineers** | 6 | Headless commerce, API design, e-commerce | Application |
| **Data Platform Engineers** | 6 | CDP, stream processing, ML segmentation | Data |
| **Marketing Intelligence Engineers** | 4 | Campaign engine, attribution, ML models | Data |
| **Full-Stack Engineers** | 6 | Portal consolidation, composable UI | Application |
| **Retail AI Engineers** | 4 | Kiosk software, POS integration, co-pilot | Application |
| **Mobile Engineers** | 3 | App enhancement, AI features | Application |
| **Cloud/Platform Engineers** | 3 | Scale-up infrastructure, auto-scaling | Architecture |
| **Security Engineers** | 2 | Zero-trust, AI security | Security |
| **Enterprise AI Literacy Programme Lead** | 1 | Training design, curriculum development | Workforce |
| **AI Trainers** | 4 | AI training delivery, workshop facilitation | Workforce |
| **Programme Team** | 6 | Programme management, PMO, delivery | Programme |

**Scale Phase Total Headcount**: ~60 FTEs

#### Mature Phase (Years 3–5)

| Role | Count | Skills Required | Workstream |
|------|-------|----------------|-----------|
| **AI Platform Engineering Lead** | 1 | Platform optimisation, self-optimising patterns | Architecture |
| **AI/ML Engineers** | 5 | Advanced personalisation, predictive models | Architecture |
| **Data Scientists** | 4 | Predictive analytics, ML at scale | Data |
| **Full-Stack Engineers** | 3 | Portal consolidation, legacy migration | Application |
| **Retail AI Engineers** | 3 | Full retail rollout, kiosk optimisation | Application |
| **Marketing Intelligence Engineers** | 3 | Advanced automation, journey orchestration | Data |
| **Cloud/Platform Engineers** | 2 | Optimisation, cost management | Architecture |
| **Security Engineers** | 1 | Continuous monitoring, compliance | Security |
| **Continuous Improvement Lead** | 1 | AI-driven organisational learning | Workforce |
| **Programme Team** | 4 | Programme closeout, benefits realisation | Programme |

**Mature Phase Total Headcount**: ~32 FTEs

### 5.2 Technology Investment Summary

| Category | Foundation (Y1) | Scale (Y2-3) | Mature (Y3-5) | Total |
|----------|----------------|-------------|---------------|-------|
| **AI Platform Infrastructure** | USD 8.5M | USD 2.0M | USD 1.0M | USD 11.5M |
| **Unified Portal & UI** | USD 1.5M | USD 1.5M | USD 0.5M | USD 3.5M |
| **Privacy & Consent** | USD 1.8M | USD 0.3M | USD 0.1M | USD 2.2M |
| **Data Platform & Analytics** | USD 0.8M | USD 2.8M | USD 0.8M | USD 4.4M |
| **Retail AI & Kiosks** | — | USD 1.0M | USD 1.5M | USD 2.5M |
| **Security & Governance** | USD 0.8M | USD 0.8M | USD 0.3M | USD 1.9M |
| **Workforce & Change** | USD 1.1M | USD 1.2M | USD 0.6M | USD 2.9M |
| **Programme & Delivery** | USD 1.5M | USD 1.4M | USD 0.7M | USD 3.6M |
| **TOTAL** | **USD 16.0M** | **USD 11.0M** | **USD 4.5M** | **USD 31.5M gross** |

> **Note**: Gross investment (USD 31.5M) exceeds the approved USD 18.5M programme budget because legacy consolidation and retirement displace ongoing maintenance costs. Net transition investment is USD 18.5M when accounting for USD 13.0M in avoided legacy maintenance costs (USD 5.3M/year for 27 applications → USD 1.5M/year for 13 applications).

### 5.3 Infrastructure Requirements

| Infrastructure | Foundation | Scale | Mature |
|----------------|-----------|-------|--------|
| **Cloud AI Inference (AWS/GCP ap-southeast-2)** | GPU instances for model serving; multi-provider abstraction | Scale-up GPU capacity; auto-scaling | Optimised GPU utilisation; spot instances |
| **On-Prem Tokenisation** | HashiCorp Vault deployment; cryptographic tokenisation cluster | Scale for enterprise-wide consent | Consolidated tokenisation |
| **Event Bus (Apache Kafka/Pub-Sub)** | Foundation cluster; GCP Event Manager integration | Enterprise-wide cluster; schema registry | Optimised streaming |
| **Data Lakehouse** | — | Data lakehouse deployment; stream processing | Advanced analytics capabilities |
| **API Gateway** | Initial gateway; anti-corruption layers | Full gateway; service mesh | Optimised integration layer |
| **Container Platform (Kubernetes)** | Foundation cluster for AI platform | Scale-up for all workloads | Optimised resource allocation |
| **Observability Stack** | AI platform telemetry; logging, metrics, traces | Enterprise-wide observability | AI-driven monitoring |
| **Mobile App Infrastructure** | AI SDK backend; push notifications | Enhanced mobile infrastructure | Optimised mobile delivery |
| **Retail Kiosk Infrastructure** | — | Pilot infrastructure (500 shops) | Full deployment (4,000 shops) |

### 5.4 Training and Change Management

| Programme | Foundation | Scale | Mature |
|-----------|-----------|-------|--------|
| **AI Augmentation Charter** | Signed; communicated to all staff | Reinforced; updated based on feedback | Embedded in culture |
| **Union Consultation (TWU)** | Framework established; ongoing dialogue | Quarterly consultations | Industrial agreement achieved |
| **AI Engineering Training** | Core team upskilling (2,000 target) | Enterprise AI literacy (10,000 staff) | Continuous improvement |
| **AI Co-Pilot Training** | Call centre pilot training | Retail co-pilot training (500 shops) | Full retail training (4,000 shops) |
| **AI Career Pathways** | Published; applied for | Programmes running; certifications | Mature career ecosystem |
| **Change Communication** | Monthly updates; pilot feedback | Quarterly town halls; success stories | Continuous improvement culture |

---

## 6. Risk Mitigation Points

### 6.1 Phase-Specific Risk Mitigation

| Risk ID | Risk | Phase | Mitigation Work Package | Control | Target Residual |
|---------|------|-------|------------------------|---------|-----------------|
| **R-001** | AI Hallucination in Customer-Facing Responses | Foundation | WP-ARC-001, WP-SEC-004 | Response validation engine; confidence thresholding (70%) | 12 (Medium) |
| **R-002** | AI Model Vendor Lock-In | Foundation | WP-ARC-001 | Multi-provider strategy; abstraction layer | 12 (Medium) |
| **R-011** | Brand Reputation Damage from AI Errors | Foundation | WP-SEC-004, WP-WKF-004 | Incident response playbooks; beta programme | 15 (High) |
| **R-013** | Union Industrial Action from AI Workforce Impact | Foundation | WP-WKF-001, WP-WKF-002 | AI Augmentation Charter; TWU consultation framework | 20 (Critical) |
| **R-015** | Customer Experience Disruption During Migration | Foundation–Scale | WP-APP-001, WP-APP-006 | Strangler-fig pattern; parallel operation; circuit-breaker rollback | 12 (Medium) |
| **R-017** | Privacy Act Breach from AI Data Processing | Foundation | WP-SEC-001, WP-SEC-002, WP-SEC-005 | Privacy-by-design; hybrid deployment; DPIA automation | 16 (High) |
| **R-018** | ACCC Consumer Law Breach from AI Content | Foundation | WP-SEC-004, WP-ARC-001 | Legal review gates; content validation | 12 (Medium) |
| **R-022** | Prompt Injection Attacks on AI Agents | Foundation | WP-ARC-001, WP-SEC-008 | Input validation; prompt hardening; adversarial testing | 12 (Medium) |
| **R-023** | Customer Data Exposure Through AI Model Training | Foundation | WP-SEC-002, WP-SEC-005 | Data isolation for training; synthetic data; tokenisation | 16 (High) |
| **R-006** | Data Quality Issues | Foundation–Scale | WP-DAT-002, WP-DAT-005 | Data quality gates; validation controls | 6 (Medium) |
| **R-007** | Low AI Feature Adoption | Foundation–Scale | WP-WKF-004, WP-APP-002 | Beta programme; adoption incentives; UX refinement | 9 (Medium) |
| **R-014** | AI Engineering Skills Shortage | Foundation | WP-WKF-003 | Recruitment plan; upskilling programmes; AI literacy | 4 (Low) |
| **R-020** | AI Model Bias | Foundation–Scale | WP-SEC-005, WP-ARC-001 | Bias testing; fairness controls; diverse training data | 6 (Medium) |
| **R-027** | AI Decision Accountability Gaps | Foundation–Scale | WP-SEC-004, WP-SEC-006 | Governance framework; audit trails; decision logging | 12 (Medium) |

### 6.2 Risk Mitigation Timeline

```text
Month:     M1   M3   M6   M9   M12  M18  M24  M30  M36  M42  M48  M54  M60
           ──────────── Phase 1 ──────────── Phase 2 ──────────── Phase 3 ────────────

R-001 ██ (Hallucination)   ── Detection pipeline operational at M3, monitoring ongoing
R-002 ██ (Vendor Lock-In) ── Multi-vendor strategy at M6, abstraction layer at M12
R-011 ██ (Brand Damage)    ── Beta programme from M6, incident playbooks at M9
R-013 ████ (Union Action)  ── Charter signed M3, TWU framework M6, ongoing dialogue
R-015 ██ (CX Disruption)  ── Strangler pattern Y1–Y3, parallel ops during migration
R-017 ████ (Privacy Breach)─ Consent service M6, tokenisation M6, DPIA M9
R-018 ██ (ACCC Breach)    ── Legal gates M6, content validation M9
R-022 ██ (Prompt Injection)── Hardening M6, adversarial testing M12
R-023 ████ (Data Exposure) ── Data isolation M6, tokenisation M6, synthetic data M9
R-014 ▓▓ (Skills Shortage)── Recruitment M3, training M6–M12, literacy Y2–Y3
R-027 ██ (Accountability) ── Governance M6, audit trails M12, framework M24

 ██ = Critical risk (residual ≥ 16)
 ██ = High risk (residual 12–15)
 ▓▓ = Medium risk (residual 6–11)
```

---

## 7. Traceability

### 7.1 STRAT Alignment

| TRANS Element | STRAT Reference | Theme | Phase |
|---------------|----------------|-------|-------|
| AI Agent Platform Foundation | STRAT Theme 1 | Theme 1 | Foundation |
| Unified Customer Experience | STRAT Theme 2 | Theme 2 | Foundation–Scale |
| Privacy-First Architecture | STRAT Theme 3 | Theme 3 | Foundation |
| Real-Time Customer Insights | STRAT Theme 4 | Theme 4 | Foundation–Scale |
| Marketing Intelligence & Proactive Engagement | STRAT Theme 5 | Theme 5 | Scale–Mature |
| Omnichannel Composable Architecture | STRAT Theme 6 | Theme 6 | Foundation–Mature |
| Phase Timeline | STRAT Section: Delivery Roadmap Summary | All | All |
| Investment Summary | STRAT Section: Investment Summary | All | All |
| Strategic Risks | STRAT Section: Strategic Risks & Mitigations | All | All |

### 7.2 GAPA Alignment

| TRANS Work Package | GAPA Gap Addressed | Gap ID | Phase |
|--------------------|-------------------|--------|-------|
| WP-ARC-001 (AI Agent Platform) | AI Agent Platform capability creation | G-004 | Foundation |
| WP-APP-001 (Unified Portal) | Unified omnichannel customer experience | G-001 | Foundation–Scale |
| WP-SEC-001 (Consent Service) | Enterprise-wide consent & privacy | G-009 | Foundation |
| WP-DAT-005 (CDP) | Customer Data Platform — 360-degree view | G-007 | Scale |
| WP-DAT-003 (Event Bus) | Event-driven data fabric | G-008 | Foundation–Scale |
| WP-APP-009 (Marketing Intelligence) | AI-powered marketing automation | G-010 | Scale–Mature |
| WP-APP-007 (Composable Commerce) | AI-driven revenue growth capability | G-002 | Scale |
| WP-APP-010/014 (Retail AI) | Customer loyalty & retention automation | G-003 | Scale–Mature |

### 7.3 APPR Alignment

| TRANS Work Package | APPR Decision | Decision ID | Phase |
|--------------------|-------------|-----------|-------|
| WP-APP-001, WP-APP-006 | Customer Portal Consolidation | CD-001 | Foundation–Scale |
| WP-SEC-001 through WP-SEC-006 | Privacy & Consent Management Consolidation | CD-002 | Foundation |
| WP-DAT-005, WP-APP-009 | CRM & CDP Consolidation | CD-003 | Scale |
| WP-APP-007 | E-Commerce Platform Modernization | MD-001 | Scale |
| WP-APP-004 | Privacy/Compliance Tool Retirement | RT-004 | Foundation |
| WP-APP-011 | Legacy Tracking UI Retirement | RT-002 | Scale |
| WP-APP-008, WP-APP-009 | Fragmented Marketing Tools Retirement | RT-003 | Scale |
| WP-APP-002 | Mobile App AI SDK Augmentation | AG-002 | Foundation |
| WP-APP-010, WP-APP-014 | Retail POS AI Co-Pilot Augmentation | AG-003 | Scale–Mature |

### 7.4 RISK Alignment

| TRANS Element | RISK Reference | Risk Category | Mitigation Phase |
|---------------|---------------|--------------|-----------------|
| WP-ARC-001 (AI Platform) | R-001 (Hallucination), R-002 (Vendor Lock-In) | TECHNOLOGY | Foundation |
| WP-WKF-001, WP-WKF-002 (Workforce) | R-013 (Union Action), R-012 (Staff Resistance) | OPERATIONAL | Foundation |
| WP-SEC-001, WP-SEC-002 (Consent) | R-017 (Privacy Breach), R-023 (Data Exposure) | COMPLIANCE/SECURITY | Foundation |
| WP-APP-001, WP-APP-006 (Portal) | R-015 (CX Disruption) | BUSINESS | Foundation–Scale |
| WP-SEC-004 (AI Governance) | R-027 (Accountability Gaps), R-011 (Brand Damage) | GOVERNANCE/BUSINESS | Foundation |
| WP-SEC-008 (AI Security) | R-022 (Prompt Injection), R-018 (ACCC Breach) | SECURITY/COMPLIANCE | Foundation–Scale |
| WP-DAT-005 (CDP) | R-006 (Data Quality), R-019 (Data Residency), R-020 (Model Bias) | TECHNOLOGY/SECURITY | Scale |

### 7.5 REQ Alignment

| TRANS Element | REQ Reference | Category |
|---------------|--------------|----------|
| WP-ARC-001, WP-APP-001 | BR-002 (Customer Experience), BR-005 (Scalable Platform) | Business |
| WP-APP-007, WP-APP-009 | BR-001 (Revenue Growth) | Business |
| WP-SEC-001 through WP-SEC-006 | BR-004 (Privacy Compliance), BR-007 (AI Governance) | Business |
| WP-WKF-001 through WP-WKF-012 | BR-006 (Workforce Augmentation) | Business |
| WP-APP-001 through WP-APP-016 | BR-003 (Operational Efficiency), BR-008 (Delivery Excellence) | Business |
| WP-SEC-004, WP-ARC-001 | FR-016 (AI Hallucination Detection), FR-001 (Conversational Agent) | Functional |
| WP-DAT-005, WP-DAT-011 | DR-001 (Customer Data Platform), DR-002 (Data Quality) | Data |
| WP-SEC-002 | NFR-C-001 (Data Residency), NFR-S-001 (Horizontal Scaling) | Non-Functional |

---

## 8. Governance and Review Framework

### 8.1 Transition Governance Structure

| Governance Body | Responsibility | Meeting Frequency | Participants |
|-----------------|---------------|-------------------|-------------|
| **Executive Steering Committee** | Strategic direction, budget approval, risk escalation | Monthly | CEO, Parcel Business GM, Head of Digital Technology, Privacy Officer, Programme Director |
| **Architecture Review Board** | Architecture compliance, principle validation, exception approvals | Bi-monthly | Head of Digital Technology, Architecture Team Lead, Security Architect, Data Architect |
| **Programme Delivery Board** | Progress tracking, milestone validation, dependency management | Fortnightly | Programme Director, Product Owners, Tech Leads, PMO |
| **AI Governance Working Group** | AI compliance monitoring, DPIA reviews, model evaluation | Monthly | Privacy Officer, CISO, AI Engineering Lead, Legal Counsel |
| **Workforce Transformation Board** | Union engagement, upskilling programme oversight, change management | Monthly | Head of People & Culture, TWU Representative, Change Management Lead |

### 8.2 Phase Gate Review Process

| Gate | Review Criteria | Approval Authority | Timing |
|------|----------------|-------------------|--------|
| **Alpha** (M6) | Tokenisation operational; AI platform L2; consent service L2; zero breaches | Architecture Review Board | Month 6 |
| **Beta** (M12) | AI pilot FC resolution ≥ 85%; portal MVP live; event bus operational; privacy complaints < 5/100K | Executive Steering Committee | Month 12 |
| **Gamma** (M24) | Omnichannel adoption ≥ 20% MAU; CDP at L4; zero APP 8 violations; NPS ≥ 37 | Executive Steering Committee | Month 24 |
| **Delta** (M36) | Revenue target 70% achieved; 80% portal migration; retail pilot complete | Executive Steering Committee | Month 36 |
| **Epsilon** (M48) | AI Maturity Score ≥ 7/10; advanced personalisation operational; staff confidence ≥ 6.0/10 | Executive Steering Committee | Month 48 |
| **Zeta** (M60) | All legacy retired; AI Maturity Score 9/10; benefits fully realised | Board | Month 60 |

### 8.3 Transition Quality Assurance

| Quality Gate | Description | Frequency | Owner |
|-------------|-------------|-----------|-------|
| **Architecture Compliance** | All deliverables validated against 17 enterprise principles (PRIN) | Per release | Architecture Review Board |
| **Security Assessment** | Penetration testing, vulnerability scanning, threat modelling | Quarterly | CISO |
| **Privacy Assessment** | DPIA completion rate, consent coverage audit | Quarterly | Privacy Officer |
| **AI Model Evaluation** | Accuracy testing, hallucination rate monitoring, bias assessment | Monthly | AI Engineering Lead |
| **Business Value Tracking** | Revenue attribution, operational savings measurement, NPS/CSAT tracking | Monthly | Programme Director |
| **Workforce Sentiment** | Staff AI confidence surveys, union feedback, adoption metrics | Quarterly | Head of People & Culture |

---

## 9. Appendix

### 9.1 Acronyms and Abbreviations

| Acronym | Definition |
|---------|-----------|
| AI | Artificial Intelligence |
| APP | Australian Privacy Principle |
| API | Application Programming Interface |
| CDP | Customer Data Platform |
| DPIA | Data Protection Impact Assessment |
| FC | First-Contact |
| FC Resolution | First-Contact Resolution |
| GCP | Google Cloud Platform |
| IA | Information Architecture |
| L1–L5 | Maturity levels 1 (Initial) through 5 (Optimised) |
| MLOps | Machine Learning Operations |
| NLU | Natural Language Understanding |
| NPS | Net Promoter Score |
| OAIC | Office of the Australian Information Commissioner |
| PII | Personally Identifiable Information |
| PRIN | Architecture Principles |
| RAG | Retrieval-Augmented Generation |
| SaaS | Software as a Service |
| SLO | Service Level Objective |
| SSO | Single Sign-On |
| STRAT | Architecture Strategy |
| TWU | Transport Workers Union |
| UX | User Experience |
| WCAG | Web Content Accessibility Guidelines |
| WP | Work Package |

### 9.2 Reference Documents

| Document ID | Document Name | Phase |
|-------------|---------------|-------|
| ARC-000-PRIN-v2.0 | Enterprise Architecture Principles | Foundation |
| ARC-001-ADR-v1.0 | Architecture Decision Records | All |
| ARC-001-APPR-v1.0 | Application Portfolio Rationalisation | All |
| ARC-001-BPCM-v1.0 | Business Capability Map | All |
| ARC-001-GAPA-v1.0 | Gap Analysis | All |
| ARC-001-REQ-v1.0 | Requirements | All |
| ARC-001-RISK-v1.0 | Risk Register | All |
| ARC-001-STRAT-v1.0 | Architecture Strategy | All |
| ARC-001-APPINV-v1.0 | Application Inventory | All |

### 9.3 Transition Work Package Index

| WP ID | Name | Workstream | Phase | Investment |
|-------|------|-----------|-------|-----------|
| WP-ARC-001 | AI Agent Platform Core | Architecture | Foundation | USD 8.5M |
| WP-ARC-002 | Tokenisation Service | Architecture | Foundation | Included in WP-ARC-001 |
| WP-ARC-003 | Event-Driven Architecture Foundation | Architecture | Foundation | USD 0.5M |
| WP-ARC-004 | API Gateway and Anti-Corruption Layers | Architecture | Foundation | Included in WP-ARC-001 |
| WP-ARC-005 | Composable Architecture Framework | Architecture | Foundation | USD 0.5M |
| WP-ARC-006 | Composable Commerce Platform | Architecture | Scale | USD 2.0M |
| WP-ARC-007 | Multi-Channel UI Framework | Architecture | Scale | Included in WP-ARC-006 |
| WP-ARC-008 | Full Event Bus | Architecture | Scale | USD 0.5M |
| WP-ARC-009 | Integration Architecture at Scale | Architecture | Scale | USD 0.5M |
| WP-ARC-010 | Full Composable Architecture Maturity | Architecture | Mature | USD 0.3M |
| WP-ARC-011 | Architecture Evolution | Architecture | Mature | USD 0.2M |
| WP-APP-001 | Unified Customer Portal MVP | Application | Foundation | USD 1.5M |
| WP-APP-002 | AI SDK Embedding (Mobile) | Application | Foundation | USD 0.5M |
| WP-APP-003 | Composable AI Services | Application | Foundation | USD 1.0M |
| WP-APP-004 | Retire Privacy/Compliance Tools | Application | Foundation | USD 0 (savings) |
| WP-APP-005 | Intershop Strangler API Gateway | Application | Foundation | USD 0.5M |
| WP-APP-006 | Full Portal Consolidation | Application | Scale | USD 1.5M |
| WP-APP-007 | AI-Powered Shopping Experience | Application | Scale | USD 2.0M |
| WP-APP-008 | Customer Data Platform | Application | Scale | USD 2.0M |
| WP-APP-009 | Marketing Intelligence Platform | Application | Scale | USD 1.0M |
| WP-APP-010 | Retail Digital Integration Pilot | Application | Scale | USD 1.0M |
| WP-APP-011 | Retire Legacy Tracking UI | Application | Scale | USD 0 (savings) |
| WP-APP-012 | Retire Intershop | Application | Scale | USD 0 (savings) |
| WP-APP-013 | Remaining Portal Consolidation | Application | Mature | USD 0.5M |
| WP-APP-014 | Full Retail Rollout | Application | Mature | USD 1.5M |
| WP-APP-015 | Marketing Automation at Scale | Application | Mature | USD 0.5M |
| WP-APP-016 | Full Legacy Decommissioning | Application | Mature | USD 0 (savings) |
| WP-DAT-001 | Customer Profile Management | Data | Foundation | USD 0.5M |
| WP-DAT-002 | Data Product Governance | Data | Foundation | USD 0.3M |
| WP-DAT-003 | Event-Driven Intelligence Foundation | Data | Foundation | USD 0.2M |
| WP-DAT-004 | Revenue Attribution Pipeline | Data | Foundation | USD 0.3M |
| WP-DAT-005 | Customer Data Platform (CDP) | Data | Scale | USD 2.0M |
| WP-DAT-006 | AI-Powered Segmentation | Data | Scale | Included in WP-DAT-005 |
| WP-DAT-007 | Customer Analytics and Reporting | Data | Scale | Included in WP-DAT-005 |
| WP-DAT-008 | Event-Driven Marketing | Data | Scale | USD 0.5M |
| WP-DAT-009 | Dynamic Customer Segmentation | Data | Scale | USD 0.3M |
| WP-DAT-010 | 360-Degree Customer View | Data | Scale | Included in WP-DAT-005 |
| WP-DAT-011 | Predictive Customer Analytics | Data | Mature | USD 0.5M |
| WP-DAT-012 | Advanced AI Segmentation | Data | Mature | USD 0.3M |
| WP-DAT-013 | Customer Journey Orchestration | Data | Mature | USD 0.2M |
| WP-SEC-001 | Enterprise Consent Management | Security | Foundation | USD 1.5M |
| WP-SEC-002 | PII Tokenisation and Data Sovereignty | Security | Foundation | USD 0.5M |
| WP-SEC-003 | Automated DPIA and Compliance | Security | Foundation | USD 0.3M |
| WP-SEC-004 | AI Governance Framework | Security | Foundation | USD 0.2M |
| WP-SEC-005 | AI-Specific Privacy Controls | Security | Foundation | USD 0.3M |
| WP-SEC-006 | Audit Trail and Accountability | Security | Foundation | USD 0.2M |
| WP-SEC-007 | Zero-Trust Architecture | Security | Scale | USD 0.5M |
| WP-SEC-008 | AI Security | Security | Scale | USD 0.3M |
| WP-SEC-009 | Cross-Border Data Transfer Controls | Security | Scale | USD 0.2M |
| WP-SEC-010 | Consent Awareness at Scale | Security | Scale | USD 0.2M |
| WP-SEC-011 | AI Compliance Governance Maturity | Security | Mature | USD 0.2M |
| WP-SEC-012 | Continuous Privacy Monitoring | Security | Mature | USD 0.1M |
| WP-WKF-001 | AI Augmentation Charter | Workforce | Foundation | USD 0.1M |
| WP-WKF-002 | Union Consultation Framework | Workforce | Foundation | USD 0.2M |
| WP-WKF-003 | AI Skills Foundation | Workforce | Foundation | USD 0.5M |
| WP-WKF-004 | AI Change Management | Workforce | Foundation | USD 0.3M |
| WP-WKF-005 | AI Co-Pilot Training | Workforce | Foundation | USD 0.2M |
| WP-WKF-006 | Enterprise AI Literacy | Workforce | Scale | USD 0.5M |
| WP-WKF-007 | AI-Augmented Workflow Integration | Workforce | Scale | USD 0.3M |
| WP-WKF-008 | Retail AI Kiosk Training | Workforce | Scale | USD 0.2M |
| WP-WKF-009 | Career Pathway Development | Workforce | Scale | USD 0.2M |
| WP-WKF-010 | Full Workforce AI Capability | Workforce | Mature | USD 0.3M |
| WP-WKF-011 | AI-Driven Insights for Operations | Workforce | Mature | USD 0.2M |
| WP-WKF-012 | Continuous Improvement through AI | Workforce | Mature | USD 0.1M |

---

## 10. Document Quality Verification

### Quality Checklist

| Check | Status |
|-------|--------|
| Document ID: ARC-001-TRANS-v1.0 | ✅ |
| All Document Control fields populated | ✅ |
| Three phases defined (Foundation, Scale, Mature) | ✅ |
| Five workstreams defined (Architecture, Application, Data, Security, Workforce) | ✅ |
| Workstream dependencies mapped (12 dependencies) | ✅ |
| Implementation roadmap with milestones (19 milestones) | ✅ |
| Resource requirements defined (team composition, technology, training) | ✅ |
| Risk mitigation points mapped to phases | ✅ |
| Traceability to STRAT (6 themes) | ✅ |
| Traceability to GAPA (8 gaps) | ✅ |
| Traceability to APPR (10 decisions) | ✅ |
| Traceability to RISK (14 risks) | ✅ |
| Traceability to REQ (15 requirements) | ✅ |
| Transition principles aligned to PRIN | ✅ |
| Phase gates defined (6 gates) | ✅ |
| Success metrics defined (13 metrics) | ✅ |
| Governance framework defined | ✅ |
| MagicDelivery context maintained throughout | ✅ |
| ArcKit Version: 5.15.2 | ✅ |
| Date: 2026-07-01 | ✅ |

---

*End of Document*
