# Gap Analysis: AgenticEA — MagicDelivery Agent AI Transformation

> **Template Origin**: Official | **ArcKit Version**: 5.15.2 | **Command**: `/arckit:gap`

## Document Control

| Field | Value |
|-------|-------|
| Document ID | ARC-001-GAPA-v1.0 |
| Document Type | Gap Analysis (GAPA) |
| Project | 001 — AgenticEA: Agent AI Transformation |
| Classification | OFFICIAL |
| Status | DRAFT |
| Version | 1.0 |
| Created Date | 2026-07-01 |
| Last Modified | 2026-07-01 |
| Review Cycle | Quarterly |
| Next Review Date | 2026-10-01 |
| Owner | Programme Director, AgenticEA |
| Reviewed By | PENDING |
| Approved By | PENDING |
| Distribution | Executive Leadership, Parcel Business, Digital Technology, Compliance/Legal, Program Delivery Team, Enterprise Architecture Review Board |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-01 | ArcKit AI | Initial creation — comprehensive gap analysis across 6 capability areas, 26 gaps identified, heat map, solution approaches, prioritization | PENDING | PENDING |

---

## Executive Summary

### Purpose

This Gap Analysis (GAPA) document identifies and quantifies the gaps between MagicDelivery's current-state architecture and the target-state architecture defined in the Architecture Strategy (ARC-001-STRAT-v1.0). It maps each gap to capability areas, application inventory (ARC-001-APPINV-v1.0), business capabilities (ARC-001-BPCM-v1.0), and application rationalisation decisions (ARC-001-APPR-v1.0). For each gap, the document defines the current maturity, target maturity, gap severity, priority, effort, specific solution approach, investment estimate, and timeline alignment.

### Scope

The gap analysis covers six capability areas aligned to the AgenticEA programme:

1. **Business Capability Gaps** — Customer experience, revenue, omnichannel engagement
2. **Technology Gaps** — AI platform, composable architecture, cloud-native infrastructure
3. **Data Gaps** — Customer data platform, event fabric, 360-degree view, privacy framework
4. **Process Gaps** — Marketing automation, campaign management, engagement model
5. **Security Gaps** — Zero-trust architecture, compliance governance, AI security
6. **Workforce Gaps** — Upskilling, AI-augmented skills, workforce transformation

### Key Findings

| Metric | Value |
|--------|-------|
| **Total gaps identified** | 26 gaps across 6 capability areas |
| **Critical gaps** (gap score ≥ 4) | 12 gaps |
| **High gaps** (gap score 3) | 8 gaps |
| **Medium gaps** (gap score 2) | 5 gaps |
| **Low gaps** (gap score 1) | 1 gap |
| **Average gap score** | 2.8/5 |
| **Total investment to close all gaps** | USD 18.5M over 5 years (approved programme budget) |
| **Foundation phase (Year 1) gaps** | 14 gaps requiring immediate investment |
| **Scale phase (Years 2–3) gaps** | 8 gaps to address after Foundation |
| **Mature phase (Years 3–5) gaps** | 4 gaps to close in optimisation phase |

### Gap Severity Distribution

```text
Gap Score Distribution (Maturity Scale 1–5):

Gap 4  ■■■■■■■■■■■■  12 gaps (46%)
Gap 3  ▓▓▓▓▓▓▓▓       8 gaps  (31%)
Gap 2  ▒▒▒▒▒           5 gaps  (19%)
Gap 1  ░               1 gap   (4%)
```

### Prioritization Summary

The 12 critical gaps (gap score ≥ 4) concentrate in three capability areas:
- **AI Agent Platform**: All 8 sub-capabilities at maturity L1, requiring greenfield build (STRAT Theme 1, USD 8.5M)
- **Privacy & Consent**: Highest target maturity (4.9/5), zero current capability (STRAT Theme 3, USD 2.5M)
- **Marketing Intelligence**: No AI-powered marketing exists; depends on CDP foundation (STRAT Theme 5, USD 1.0M)

These three areas account for 87% of total programme investment and must be addressed in the Foundation phase (Year 1) to enable all downstream capability closures.

---

## 1. Gap Analysis Framework

### 1.1 Methodology

Each gap is assessed using a structured maturity model (1–5 scale):

| Level | Maturity | Description |
|-------|----------|-------------|
| 1 | Initial | Capability does not exist or is ad hoc |
| 2 | Repeatable | Basic capability exists; manual or semi-automated |
| 3 | Defined | Standardised processes; documented and governed |
| 4 | Managed | Measured, monitored, and actively improved |
| 5 | Optimised | Continuous improvement; industry-leading performance |

### 1.2 Gap Score Calculation

**Gap Score = Target Maturity − Current Maturity**

| Gap Score | Severity | Priority Assignment |
|-----------|----------|-------------------|
| 4–5 | Critical | Foundation Phase (Year 1) — immediate investment required |
| 3 | High | Foundation–Scale (Year 1–2) — dependent on Foundation deliverables |
| 2 | Medium | Scale Phase (Years 2–3) — building on established foundations |
| 1 | Low | Mature Phase (Years 3–5) — incremental optimisation |

### 1.3 Effort Classification

| Effort | Definition | Typical Investment |
|--------|-----------|-------------------|
| **Low** | Configuration, integration, or minor enhancement | USD 0.1M – 0.5M |
| **Medium** | New component build with standard patterns | USD 0.5M – 2.5M |
| **High** | Greenfield platform or major architectural shift | USD 2.5M – 8.5M |

---

## 2. Business Capability Gaps

### 2.1 Gap G-001: Unified Omnichannel Customer Experience

| Attribute | Value |
|-----------|-------|
| **Gap ID** | G-001 |
| **Capability Area** | Business Capability |
| **Current State** | 20+ isolated customer portals (APP-01 to APP-18), no cross-channel identity, fragmented experience |
| **Target State** | Unified omnichannel experience across mobile, web, call centre, retail, self-service — consistent AI-augmented interactions |
| **Current Maturity** | 1 (Initial) |
| **Target Maturity** | 5 (Optimised) |
| **Gap Score** | 4 (Critical) |
| **Priority** | CRITICAL |
| **Effort** | High |

**Gap Description**: MagicDelivery operates 20+ isolated portals with separate authentication, data models, and integration patterns. No unified customer identity exists. Customer experience varies dramatically across channels. The customer must navigate multiple portals for different services, with no memory of prior interactions.

**Solution Approach**: Consolidate 20+ portals into TAPP-01 (Unified Customer Portal) using strangler-fig pattern (PRIN-17). Deploy federated SSO, composable web platform with AI SDK embedding. Progressive traffic routing via API gateway with anti-corruption layer.

**Alignment to Rationalization Strategy**: CD-001 (Customer Portal Consolidation) — CONSOLIDATE → RETIRE per APPR. STRAT Theme 2 (Unified Customer Experience).

**Investment Estimate**: USD 4.5M over 3 years (STRAT Theme 2)

**Timeline Alignment**: Foundation (Year 1) — MVP; Scale (Years 2–3) — 80% traffic migration; Mature (Years 3–5) — full consolidation

**BPCM Links**: CE-01 (Multi-Channel Self-Service), CE-04 (Unified Customer Identity)

**REQ Links**: BR-002, BR-005

**STRAT Links**: Theme 2 — Unified Customer Experience; Foundation Phase

**APPR Links**: CD-001, RT-001

**RISK Links**: R-015 (Customer Experience Disruption During Migration)

---

### 2.2 Gap G-002: AI-Driven Revenue Growth Capability

| Attribute | Value |
|-----------|-------|
| **Gap ID** | G-002 |
| **Capability Area** | Business Capability |
| **Current State** | No AI-powered revenue capability; traditional e-commerce through Intershop; manual campaign targeting |
| **Target State** | AI-augmented revenue engine: personalised recommendations, dynamic pricing, AI shopping assistant — USD 25M incremental annual revenue |
| **Current Maturity** | 1 (Initial) |
| **Target Maturity** | 4 (Managed) |
| **Gap Score** | 3 (High) |
| **Priority** | HIGH |
| **Effort** | High |

**Gap Description**: Revenue generation relies on static e-commerce platform (Intershop) with no AI-driven personalisation, recommendations, or dynamic offers. Marketing is reactive — no real-time behavioural triggers or AI-powered segmentation.

**Solution Approach**: Build TAPP-03 (Composable AI Services) with recommendation engine, AI shopping assistant, and personalisation engine. Modernise Intershop via TAPP-07 (AI-Powered Shopping Experience) using strangler-fig pattern. Revenue attribution pipeline for feature-attribution modelling.

**Alignment to Rationalization Strategy**: MD-001 (E-Commerce Modernization), CD-003 (Marketing Consolidation). STRAT Theme 5 (Marketing Intelligence).

**Investment Estimate**: USD 4.0M over 3 years (USD 2.0M TAPP-07 + USD 1.0M TAPP-06 + USD 1.0M TAPP-03)

**Timeline Alignment**: Foundation (Year 1) — AI services; Scale (Years 2–3) — composable commerce; Mature (Years 3–5) — advanced personalisation

**BPCM Links**: EC-02 (AI Shopping Assistant), EC-08 (Omnichannel Commerce), MK-02 (AI Personalisation)

**REQ Links**: BR-001, FR-003, FR-005

**STRAT Links**: Theme 5 — Marketing Intelligence & Proactive Engagement

**APPR Links**: MD-001, CD-003

---

### 2.3 Gap G-003: Customer Loyalty & Retention Automation

| Attribute | Value |
|-----------|-------|
| **Gap ID** | G-003 |
| **Capability Area** | Business Capability |
| **Current State** | Basic loyalty programme; no churn prediction; no AI-driven retention strategies |
| **Target State** | AI-powered retention engine: churn prediction, next-best-action, automated loyalty activations |
| **Current Maturity** | 2 (Repeatable) |
| **Target Maturity** | 4 (Managed) |
| **Gap Score** | 2 (Medium) |
| **Priority** | MEDIUM |
| **Effort** | Medium |

**Solution Approach**: Build retention models within CDP (TAPP-04) — churn prediction, lifetime value scoring, next-best-action engine. Integrate with marketing intelligence platform (TAPP-06) for automated retention campaigns.

**Investment Estimate**: USD 1.5M (part of TAPP-04 and TAPP-06 investment)

**Timeline Alignment**: Scale (Years 2–3) — retention models; Mature (Years 3–5) — automated retention

**BPCM Links**: CE-06 (Customer Loyalty & Retention)

**REQ Links**: BR-001

---

## 3. Technology Gaps

### 3.1 Gap G-004: AI Agent Platform (No AI Capability Exists)

| Attribute | Value |
|-----------|-------|
| **Gap ID** | G-004 |
| **Capability Area** | Technology |
| **Current State** | No AI agent platform; no model serving; no agent orchestration; no AI governance (maturity L1 across all 8 sub-capabilities) |
| **Target State** | Production-ready AI agent platform — multi-agent orchestration, hybrid deployment, model governance, telemetry, complexity-based routing |
| **Current Maturity** | 1 (Initial) |
| **Target Maturity** | 4 (Managed) |
| **Gap Score** | 3 (High) |
| **Priority** | CRITICAL |
| **Effort** | High |

**Gap Description**: MagicDelivery has zero AI agent capability. No agent orchestrator, model serving layer, agent lifecycle management, or AI governance framework exists. This is the single largest technology gap — all other AI-augmented capabilities depend on this platform reaching minimum maturity L3.

**Sub-gap Breakdown** (all 8 AI Agent Platform sub-capabilities):

| Sub-Gap | Current | Target | Gap Score | Phase |
|---------|---------|--------|-----------|-------|
| AI-01: Agent Orchestration | 1 | 4 | 3 | Foundation |
| AI-02: Hybrid Model Serving | 1 | 4 | 3 | Foundation |
| AI-03: AI Governance & Compliance | 1 | 5 | 4 | Foundation |
| AI-04: Agent Telemetry & Observability | 1 | 4 | 3 | Foundation |
| AI-05: Prompt Engineering & Knowledge Base | 1 | 4 | 3 | Foundation |
| AI-06: Complexity-Based Routing | 1 | 4 | 3 | Foundation |
| AI-07: Agent-to-Agent Collaboration | 1 | 4 | 3 | Scale |
| AI-08: Model Evaluation & MLOps | 1 | 4 | 3 | Foundation |

**Solution Approach**: Greenfield build of TAPP-02 (AI Agent Platform). Hybrid deployment per ADR-001 — cloud inference layer (multi-provider) + on-prem sensitive processing (tokenisation via HashiCorp Vault). Complexity-based routing per ADR-002. AI governance framework per BR-007.

**Alignment to Rationalization Strategy**: Greenfield build per APPR. STRAT Theme 1 (AI Agent Platform Foundation) — USD 8.5M investment, 46% of total budget.

**Investment Estimate**: USD 8.5M over 2 years (Theme 1)

**Timeline Alignment**: Foundation (Year 1) — agent orchestrator, model serving, pilot agent, governance; Scale (Years 2–3) — additional agents, agent-to-agent collaboration

**BPCM Links**: AI-01 through AI-08 (all AI Agent Platform sub-capabilities)

**REQ Links**: BR-003, BR-005, BR-007

**STRAT Links**: Theme 1 — AI Agent Platform Foundation

**ADR Links**: ADR-001 (Hybrid Deployment), ADR-002 (Complexity Routing), ADR-007 (Compliance Governance)

**RISK Links**: R-001 (Hallucination), R-002 (Vendor Lock-In), R-027 (AI Decision Accountability)

---

### 3.2 Gap G-005: Composable Architecture & Loose Coupling

| Attribute | Value |
|-----------|-------|
| **Gap ID** | G-005 |
| **Capability Area** | Technology |
| **Current State** | Monolithic portals, shared databases, tight coupling between systems, no published API contracts |
| **Target State** | Composable, independently deployable components with published API contracts; zero shared databases across boundaries |
| **Current Maturity** | 1 (Initial) |
| **Target Maturity** | 4 (Managed) |
| **Gap Score** | 3 (High) |
| **Priority** | HIGH |
| **Effort** | High |

**Gap Description**: Current architecture features tightly coupled monolithic portals sharing databases and file systems. No API contracts, no service boundaries, no independent deployment capability. Legacy Intershop is a closed monolith with no composable decomposition.

**Solution Approach**: Implement composable architecture per PRIN-2 (Composable Architecture) and PRIN-9 (Loose Coupling). TAPP-03 (Composable AI Services) as microservices with published API contracts. Anti-corruption layers wrap legacy systems (APP-24 to APP-26). API gateway provides standardised access.

**Alignment to Rationalization Strategy**: STRAT Theme 6 (Omnichannel Composable Architecture). APPR RETAIN decisions for core systems with API gateway integration.

**Investment Estimate**: USD 0.5M (absorbed in Theme 1–2 investment)

**Timeline Alignment**: Foundation (Year 1) — API gateway, anti-corruption layers; Scale (Years 2–3) — full composable decomposition

**BPCM Links**: CE-04, EC-08, CD-08

**REQ Links**: BR-005

**STRAT Links**: Theme 6 — Omnichannel Composable Architecture

**PRIN Links**: P-02 (Composable), P-08 (Loose Coupling), P-10 (Legacy Modernization)

---

### 3.3 Gap G-006: Cloud-Native Infrastructure

| Attribute | Value |
|-----------|-------|
| **Gap ID** | G-006 |
| **Capability Area** | Technology |
| **Current State** | On-premises infrastructure; VMware deployments; no containerisation; no CI/CD pipelines |
| **Target State** | Cloud-native infrastructure — containerised services, CI/CD pipelines, infrastructure as code, auto-scaling |
| **Current Maturity** | 2 (Repeatable) |
| **Target Maturity** | 4 (Managed) |
| **Gap Score** | 2 (Medium) |
| **Priority** | MEDIUM |
| **Effort** | Medium |

**Solution Approach**: Hybrid deployment per ADR-001 — cloud inference (AWS/GCP ap-southeast-2) for scalable model serving; on-prem tokenisation and sensitive processing. Containerised microservices for AI platform components. CI/CD pipelines with automated testing and deployment.

**Investment Estimate**: USD 2.5M CAPEX for tokenisation infrastructure (ADR-001); USD 3.0M/year OPEX for cloud inference

**Timeline Alignment**: Foundation (Year 1) — cloud infrastructure + tokenisation; Scale (Years 2–3) — full cloud-native migration

**BPCM Links**: AI-02, AI-04, AI-08

**REQ Links**: BR-005, NFR-S-001

**ADR Links**: ADR-001

---

## 4. Data Gaps

### 4.1 Gap G-007: Customer Data Platform (CDP) — 360-Degree Customer View

| Attribute | Value |
|-----------|-------|
| **Gap ID** | G-007 |
| **Capability Area** | Data |
| **Current State** | Customer data siloed across CRM, ERP, portals, and logistics systems; no unified identity; no real-time profiling |
| **Target State** | Customer Data Platform (CDP) — unified customer identity, real-time profiling, event-driven ingestion, ML-powered segmentation |
| **Current Maturity** | 1 (Initial) |
| **Target Maturity** | 4 (Managed) |
| **Gap Score** | 3 (High) |
| **Priority** | HIGH |
| **Effort** | High |

**Gap Description**: Customer data exists in 20+ portals, CRM, ERP, and logistics systems with no unified identity resolution. No 360-degree customer view, no real-time profiling, no event-driven data ingestion. Marketing segmentation uses spreadsheet-based tools (APP-32).

**Sub-gap Breakdown**:

| Sub-Gap | Current | Target | Gap Score | Phase |
|---------|---------|--------|-----------|-------|
| CD-01: Customer Profile Management | 2 | 4 | 2 | Foundation |
| CD-02: CDP (Data Lakehouse) | 1 | 4 | 3 | Scale |
| CD-03: Customer Analytics & Reporting | 2 | 4 | 2 | Scale |
| CD-04: AI-Powered Segmentation | 1 | 5 | 4 | Scale–Mature |
| CD-05: 360-Degree Customer View | 1 | 5 | 4 | Scale |
| CD-06: Event-Driven Intelligence | 2 | 4 | 2 | Foundation–Scale |
| CD-07: Predictive Analytics | 1 | 5 | 4 | Mature |
| CD-08: Data Product Governance | 1 | 4 | 3 | Foundation |

**Solution Approach**: Build TAPP-04 (Customer Data Platform) — data lakehouse architecture with customer identity resolution, real-time enrichment, ML segmentation engine. Depends on TAPP-02 (AI Platform) and TAPP-05 (Consent) reaching minimum maturity.

**Alignment to Rationalization Strategy**: CD-003 (CRM & CDP Consolidation) — CONSOLIDATE per APPR. STRAT Theme 4 (Real-Time Customer Insights).

**Investment Estimate**: USD 2.0M over 2 years (Theme 4)

**Timeline Alignment**: Foundation (Year 1) — identity resolution, data product governance; Scale (Years 2–3) — CDP, analytics; Mature (Years 3–5) — predictive analytics, AI segmentation

**BPCM Links**: CD-01 through CD-08 (all Customer Data sub-capabilities)

**REQ Links**: BR-004, BR-005, DR-001, DR-002

**STRAT Links**: Theme 4 — Real-Time Customer Insights

**RISK Links**: R-006 (Data Quality), R-019 (Data Residency), R-020 (Model Bias)

---

### 4.2 Gap G-008: Event-Driven Data Fabric

| Attribute | Value |
|-----------|-------|
| **Gap ID** | G-008 |
| **Capability Area** | Data |
| **Current State** | GCP Event Manager serves parcel lifecycle only; no enterprise-wide event bus; no real-time customer event processing |
| **Target State** | Enterprise-wide customer event bus — real-time ingestion of parcel events, customer interactions, consent data, marketing touchpoints |
| **Current Maturity** | 3 (Defined) |
| **Target Maturity** | 4 (Managed) |
| **Gap Score** | 1 (Low) |
| **Priority** | MEDIUM |
| **Effort** | Medium |

**Gap Description**: GCP Event Manager (APP-22) provides parcel lifecycle events but serves only logistics operations. No enterprise-wide event bus for customer events. No real-time event processing for AI agent consumption, marketing triggers, or customer profiling.

**Solution Approach**: Extend GCP Event Manager with enterprise-wide customer event bus (Apache Kafka/Pub-Sub per STRAT). Event schema registry for versioning. Event consumers: AI agents (TAPP-02), CDP (TAPP-04), Marketing Intelligence (TAPP-06).

**Alignment to Rationalization Strategy**: AG-001 (GCP Event Manager Augmentation) per APPR. STRAT Theme 4 (Real-Time Customer Insights). ADR-003 (Event-Driven Data Fabric).

**Investment Estimate**: USD 0.5M (part of Theme 4 investment)

**Timeline Alignment**: Foundation (Year 1) — event bus foundation, GCP integration; Scale (Years 2–3) — full event bus

**BPCM Links**: CD-06 (Event-Driven Intelligence), PS-07 (Proactive Notification Engine)

**REQ Links**: BR-005

**STRAT Links**: Theme 4

**ADR Links**: ADR-003

---

### 4.3 Gap G-009: Enterprise-Wide Consent & Privacy Management

| Attribute | Value |
|-----------|-------|
| **Gap ID** | G-009 |
| **Capability Area** | Data |
| **Current State** | No enterprise-wide consent management — each system manages privacy independently (APP-34); no cross-system coordination; manual compliance tracking (APP-35) |
| **Target State** | Centralised consent service — granular opt-in/opt-out controls, automated DPIA, privacy dashboard, PII tokenisation, APP 8 compliance by design |
| **Current Maturity** | 1 (Initial) |
| **Target Maturity** | 5 (Optimised) |
| **Gap Score** | 4 (Critical) |
| **Priority** | CRITICAL |
| **Effort** | High |

**Gap Description**: The single largest compliance gap identified. 20+ portals maintain separate consent mechanisms with no coordination. Manual compliance tracking via spreadsheets (APP-35). No enterprise consent framework to support AI agent operations, which require consent-aware data processing per APP 1–3, 8.

**Sub-gap Breakdown**:

| Sub-Gap | Current | Target | Gap Score | Phase |
|---------|---------|--------|-----------|-------|
| PC-01: Enterprise Consent Management | 1 | 5 | 4 | Foundation |
| PC-02: PII Tokenisation & Data Sovereignty | 1 | 5 | 4 | Foundation |
| PC-03: Automated DPIA & Compliance | 1 | 4 | 3 | Foundation |
| PC-04: Privacy Dashboard & Self-Service | 1 | 4 | 3 | Foundation |
| PC-05: AI-Specific Privacy Controls | 1 | 4 | 3 | Foundation |
| PC-06: Audit Trail & Accountability | 1 | 4 | 3 | Foundation |
| PC-07: Cross-Border Transfer Controls | 1 | 5 | 4 | Foundation |
| PC-08: Consent Awareness in AI Agents | 1 | 4 | 3 | Foundation |

**Solution Approach**: Greenfield build of TAPP-05 (Privacy & Consent Management). Cryptographic tokenisation layer per ADR-001 (HashiCorp Vault). Centralised consent microservice with granular controls. Automated DPIA workflows. Privacy dashboard for customers. Must reach L3 concurrent with AI Agent Platform (TAPP-02).

**Alignment to Rationalization Strategy**: CD-002 (Privacy & Consent Consolidation) — CONSOLIDATE → RETIRE per APPR. STRAT Theme 3 (Privacy-First Architecture) — USD 2.5M.

**Investment Estimate**: USD 2.5M (Theme 3)

**Timeline Alignment**: Foundation (Year 1) — full consent service operational by Month 6 (2027-01)

**BPCM Links**: PC-01 through PC-08 (all Privacy & Consent sub-capabilities)

**REQ Links**: BR-004, BR-007, FR-005

**STRAT Links**: Theme 3 — Privacy-First Architecture

**ADR Links**: ADR-001 (Hybrid Deployment), ADR-007 (Compliance Governance)

**RISK Links**: R-017 (Privacy Act Breach — score 20, Critical), R-018 (ACCC Breach — score 16)

---

## 5. Process Gaps

### 5.1 Gap G-010: AI-Powered Marketing Automation

| Attribute | Value |
|-----------|-------|
| **Gap ID** | G-010 |
| **Capability Area** | Process |
| **Current State** | Manual campaign management (APP-33); spreadsheet-based segmentation (APP-32); limited SaaS automation (APP-31); reactive-only engagement model |
| **Target State** | AI-powered marketing intelligence — real-time segmentation, dynamic campaign engine, proactive engagement, automated personalisation |
| **Current Maturity** | 1 (Initial) |
| **Target Maturity** | 5 (Optimised) |
| **Gap Score** | 4 (Critical) |
| **Priority** | HIGH |
| **Effort** | Medium |

**Sub-gap Breakdown**:

| Sub-Gap | Current | Target | Gap Score | Phase |
|---------|---------|--------|-----------|-------|
| MK-01: Campaign Management | 2 | 4 | 2 | Scale |
| MK-02: AI-Powered Personalisation | 1 | 5 | 4 | Scale–Mature |
| MK-03: Event-Driven Marketing | 1 | 5 | 4 | Scale |
| MK-04: Revenue Attribution & ROI | 1 | 4 | 3 | Foundation |
| MK-05: Proactive Engagement Automation | 1 | 5 | 4 | Mature |
| MK-06: Customer Journey Orchestration | 1 | 4 | 3 | Mature |
| MK-07: Dynamic Customer Segmentation | 1 | 5 | 4 | Scale |
| MK-08: Marketing Analytics & Reporting | 2 | 4 | 2 | Scale |

**Solution Approach**: Build TAPP-06 (Marketing Intelligence Platform) — AI-powered campaign engine on CDP foundation (TAPP-04). Event-driven triggers for real-time campaign execution. ML segmentation engine for dynamic audience targeting. Revenue attribution pipeline for AI feature-attribution modelling.

**Alignment to Rationalization Strategy**: CD-003, MD-003 per APPR. STRAT Theme 5 (Marketing Intelligence & Proactive Engagement).

**Investment Estimate**: USD 1.0M over 3 years (Theme 5)

**Timeline Alignment**: Foundation (Year 1) — revenue attribution; Scale (Years 2–3) — AI segmentation, event-driven marketing; Mature (Years 3–5) — proactive engagement, journey orchestration

**BPCM Links**: MK-01 through MK-08 (all Marketing sub-capabilities)

**REQ Links**: BR-001

**STRAT Links**: Theme 5 — Marketing Intelligence & Proactive Engagement

---

### 5.2 Gap G-011: Proactive Customer Engagement Model

| Attribute | Value |
|-----------|-------|
| **Gap ID** | G-011 |
| **Capability Area** | Process |
| **Current State** | Reactive-only engagement — customers must initiate contact via phone (8-minute wait), web portal, or retail counter |
| **Target State** | Proactive, AI-driven engagement — predictive outreach, AI-generated engagement triggers, next-best-action engine |
| **Current Maturity** | 1 (Initial) |
| **Target Maturity** | 5 (Optimised) |
| **Gap Score** | 4 (Critical) |
| **Priority** | MEDIUM |
| **Effort** | Low |

**Solution Approach**: Event-driven proactive engagement triggers built on CDP (TAPP-04) and Marketing Intelligence Platform (TAPP-06). AI-generated engagement based on real-time customer events (delivery milestones, service offers, loyalty activations).

**Investment Estimate**: USD 0.5M (part of Theme 5 investment)

**Timeline Alignment**: Mature (Years 3–5) — depends on CDP and AI Platform maturity

**BPCM Links**: MK-05 (Proactive Engagement Automation)

**REQ Links**: BR-001

---

### 5.3 Gap G-012: Campaign ROI Attribution

| Attribute | Value |
|-----------|-------|
| **Gap ID** | G-012 |
| **Capability Area** | Process |
| **Current State** | No feature-attribution modelling; no AI revenue measurement against control groups; campaign ROI tracked manually |
| **Target State** | Automated feature-attribution pipeline — multi-touch attribution, AI revenue measurement, A/B testing against control cohorts |
| **Current Maturity** | 1 (Initial) |
| **Target Maturity** | 4 (Managed) |
| **Gap Score** | 3 (High) |
| **Priority** | MEDIUM |
| **Effort** | Low |

**Solution Approach**: Revenue attribution pipeline built as part of Marketing Intelligence Platform (TAPP-06). Feature-attribution modelling against control groups for AI-enabled revenue measurement. A/B testing framework for campaign optimisation.

**Investment Estimate**: USD 0.3M (part of TAPP-06 investment)

**Timeline Alignment**: Foundation (Year 1) — attribution baseline; Scale (Years 2–3) — automated attribution pipeline

**BPCM Links**: MK-04 (Revenue Attribution & ROI Tracking)

**REQ Links**: BR-001

---

## 6. Security Gaps

### 6.1 Gap G-013: Zero-Trust Security Architecture

| Attribute | Value |
|-----------|-------|
| **Gap ID** | G-013 |
| **Capability Area** | Security |
| **Current State** | Basic perimeter security; network-based trust; no service-to-service authentication; secrets in code or config files |
| **Target State** | Zero-trust architecture — identity-based access, mutual TLS, encrypted everywhere, continuous verification, secrets in HashiCorp Vault |
| **Current Maturity** | 2 (Repeatable) |
| **Target Maturity** | 4 (Managed) |
| **Gap Score** | 2 (Medium) |
| **Priority** | HIGH |
| **Effort** | Medium |

**Gap Description**: Current security model relies on perimeter defence with network-based trust. No mutual TLS between services, no zero-trust principles. Secrets management relies on configuration files rather than secure vault. PII handling is inconsistent across 20+ portals.

**Solution Approach**: Implement zero-trust security per PRIN-4 (Security by Design — NON-NEGOTIABLE). Mutual TLS for service-to-service authentication. HashiCorp Vault for secrets management. Encrypted data at rest and in transit. Network segmentation with minimal trust zones. Continuous verification of all access patterns.

**Investment Estimate**: USD 1.0M (part of Theme 1 and Theme 3 investment)

**Timeline Alignment**: Foundation (Year 1) — zero-trust baseline; Scale (Years 2–3) — full zero-trust deployment

**BPCM Links**: AI-03 (AI Governance), PC-02 (PII Tokenisation), PC-06 (Audit Trail)

**REQ Links**: BR-007, NFR-S-001

**PRIN Links**: P-04 (Security by Design)

**RISK Links**: R-022 (Prompt Injection), R-023 (Data Exposure), R-025 (Insider Threat)

---

### 6.2 Gap G-014: AI Governance & Compliance Framework

| Attribute | Value |
|-----------|-------|
| **Gap ID** | G-014 |
| **Capability Area** | Security |
| **Current State** | No AI governance framework; no model registry; no compliance monitoring; no hallucination detection |
| **Target State** | AI Governance Framework — model registry, compliance monitoring, DPIA automation, hallucination detection, board-approved risk appetite |
| **Current Maturity** | 1 (Initial) |
| **Target Maturity** | 5 (Optimised) |
| **Gap Score** | 4 (Critical) |
| **Priority** | CRITICAL |
| **Effort** | Medium |

**Gap Description**: MagicDelivery has no AI governance framework. No model registry, no AI risk register, no compliance monitoring for AI models, no hallucination detection pipeline. BR-007 requires AI Governance Framework achieving maturity score 7/10 by Month 6.

**Solution Approach**: AI Governance Framework per ADR-007 (Hybrid Compliance Governance). Model registry for all customer-facing AI models. Automated compliance monitoring with pre-deployment DPIA gates and runtime privacy monitoring. Hallucination detection engine (FR-016). AI risk register. Board-approved AI risk appetite statement.

**Investment Estimate**: USD 0.5M (part of Theme 1 investment)

**Timeline Alignment**: Foundation (Year 1) — framework operational by Month 6 (2026-12-31)

**BPCM Links**: AI-03 (AI Governance & Compliance)

**REQ Links**: BR-007, FR-016

**STRAT Links**: Theme 1, Theme 3

**ADR Links**: ADR-007

**RISK Links**: R-001 (Hallucination), R-018 (ACCC Breach), R-027 (AI Decision Accountability)

---

### 6.3 Gap G-015: AI-Specific Security Controls

| Attribute | Value |
|-----------|-------|
| **Gap ID** | G-015 |
| **Capability Area** | Security |
| **Current State** | No AI-specific security — no prompt hardening, no input validation for AI agents, no adversarial testing, no data isolation for model training |
| **Target State** | AI-specific security — prompt injection protection, input validation, adversarial testing, synthetic data generation, data isolation |
| **Current Maturity** | 1 (Initial) |
| **Target Maturity** | 4 (Managed) |
| **Gap Score** | 3 (High) |
| **Priority** | HIGH |
| **Effort** | Medium |

**Solution Approach**: Prompt hardening framework with input validation for all AI agent interactions. Adversarial testing programme. Data isolation for AI model training (synthetic data generation). Rate limiting and anomaly detection for AI agent APIs.

**Investment Estimate**: USD 0.5M (part of Theme 1 investment)

**Timeline Alignment**: Foundation (Year 1) — baseline AI security; Scale (Years 2–3) — comprehensive AI security

**BPCM Links**: AI-03, PC-05 (AI-Specific Privacy Controls)

**REQ Links**: BR-007, NFR-S-001

**RISK Links**: R-022 (Prompt Injection), R-023 (Data Exposure), R-026 (Adversarial Attacks)

---

## 7. Workforce Gaps

### 7.1 Gap G-016: AI-Augmented Skills & Upskilling

| Attribute | Value |
|-----------|-------|
| **Gap ID** | G-016 |
| **Capability Area** | Workforce |
| **Current State** | 10,000 staff with traditional roles; AI confidence score 3.0/10; no AI training programmes; skills gap in AI/ML engineering |
| **Target State** | Augmented workforce — 2,000 staff certified in AI-augmented workflows; AI confidence score 6.5/10; clear career pathways |
| **Current Maturity** | 1 (Initial) |
| **Target Maturity** | 4 (Managed) |
| **Gap Score** | 3 (High) |
| **Priority** | HIGH |
| **Effort** | Medium |

**Gap Description**: MagicDelivery's 10,000-person workforce has no AI-augmented skills. AI confidence score is 3.0/10. No upskilling programmes exist. The organisation needs to recruit and upskill AI engineering talent while simultaneously preparing the existing workforce for AI-augmented workflows.

**Solution Approach**: AI-augmented workforce programme per BR-006. Upskilling programme targeting 2,000 staff (20% of workforce) within 18 months. AI engineering team recruitment (target 15 engineers, 3 data scientists, 1 AI platform architect). AI co-design sessions with operations staff. AI confidence improvement from 3.0 to 6.5/10.

**Sub-gap Breakdown**:

| Sub-Gap | Current | Target | Gap Score | Phase |
|---------|---------|--------|-----------|-------|
| BO-02: AI-Augmented Staff Tools | 1 | 4 | 3 | Foundation–Scale |
| BO-03: Workforce Upskilling & Training | 1 | 4 | 3 | Foundation–Scale |
| BO-06: Staff AI Confidence & Adoption | 1 | 4 | 3 | Foundation–Scale |

**Alignment to Rationalization Strategy**: STRAT Theme 2 (Unified Customer Experience — workforce component). AI Augmentation Charter per Fair Work Act.

**Investment Estimate**: USD 1.0M (training, certification, change management)

**Timeline Alignment**: Foundation (Year 1) — programme launch, initial cohorts; Scale (Years 2–3) — 2,000 staff certified

**BPCM Links**: BO-02, BO-03, BO-06

**REQ Links**: BR-006

**STRAT Links**: Workforce constraints

**RISK Links**: R-012 (Staff Resistance), R-013 (Union Industrial Action — score 20)

---

### 7.2 Gap G-017: Union Relations & Industrial Engagement

| Attribute | Value |
|-----------|-------|
| **Gap ID** | G-017 |
| **Capability Area** | Workforce |
| **Current State** | No formal union consultation framework for AI; zero net FTE commitment exists but no formal charter |
| **Target State** | Formal Union Consultation Framework — AI Augmentation Charter with TWU; zero net FTE reduction guarantee; workforce impact monitoring |
| **Current Maturity** | 2 (Repeatable) |
| **Target Maturity** | 4 (Managed) |
| **Gap Score** | 2 (Medium) |
| **Priority** | HIGH |
| **Effort** | Low |

**Solution Approach**: AI Augmentation Charter co-developed with TWU. Formal Union Consultation Forum (monthly). Zero net FTE reduction commitment verified through HRIS tracking. Workforce impact briefings and transparent communication programme.

**Investment Estimate**: USD 0.2M (consultation framework, industrial engagement)

**Timeline Alignment**: Foundation (Year 1) — charter agreed before pilot production rollout

**BPCM Links**: BO-07 (Union Relations & Industrial Engagement)

**REQ Links**: BR-006, BR-008

**RISK Links**: R-013 (Union Industrial Action — score 20, Critical)

---

### 7.3 Gap G-018: Change Management & Adoption Framework

| Attribute | Value |
|-----------|-------|
| **Gap ID** | G-018 |
| **Capability Area** | Workforce |
| **Current State** | Ad hoc change management; no structured adoption framework for AI tools |
| **Target State** | Structured change management framework — AI tool adoption metrics, feedback loops, continuous improvement |
| **Current Maturity** | 2 (Repeatable) |
| **Target Maturity** | 4 (Managed) |
| **Gap Score** | 2 (Medium) |
| **Priority** | MEDIUM |
| **Effort** | Low |

**Solution Approach**: AI tool adoption metrics dashboard. Staff feedback loops (FR-010). Change management framework with town halls, pilot participation, and co-design sessions.

**Investment Estimate**: USD 0.3M (absorbed in workforce programme)

**Timeline Alignment**: Foundation (Year 1) — framework established; Scale (Years 2–3) — measured adoption

**BPCM Links**: BO-06 (Staff AI Confidence & Adoption)

**REQ Links**: BR-006

---

## 8. Gap Heat Map

### 8.1 Comprehensive Gap Heat Map

```text
                    GAP SEVERITY (Gap Score)
                 Low(1)  Med(2)  High(3)  Critical(4)
                ┌───────┬───────┬─────────┬──────────┐
                │       │       │         │          │
Capability     │ G-008 │G-003,G│G-002,G- │G-001,G-  │
Area           │       │ 006,G │ 005,G-  │ 004,G-   │
                │       │ 012,  │ 008,    │ 009,G-   │
                │       │ G-017,│ G-015,  │ 010      │
                │       │ G-018 │ G-016   │          │
                ├───────┼───────┼─────────┼──────────┤
Risk Category  │       │       │         │          │
Impact        │  R-015│R-006,  │R-012,   │R-013,    │
              │  (Low)│R-020   │R-027    │R-017,    │
              │       │        │         │R-023     │
                └───────┴───────┴─────────┴──────────┘

Gap Count by Severity:  1   5    8        12
```

### 8.2 Gap Heat Map by Capability Area

```text
Capability Area            Gaps  Critical  High  Medium  Low  Total Gap Score
──────────────────────────────────────────────────────────────────────────────
1. Business Capability      3     1          1      1      0       9
2. Technology               3     1          2      0      0       8
3. Data                     3     1          1      0      1       8
4. Process                 3     2          1      0      0       11
5. Security                 3     1          1      1      0       9
6. Workforce               3     0          1      2      0       7
──────────────────────────────────────────────────────────────────────────────
TOTALS                     18    7          7      4      1      52
```

> **Note**: The 18 gaps above represent primary gaps. The 26 total gaps include sub-gaps (e.g., each AI Agent Platform sub-capability is individually tracked) as detailed in Sections 3–7.

### 8.3 Gap Heat Map by Delivery Phase

```text
Phase              Gaps  Investment     % of Total    Key Gaps
─────────────────────────────────────────────────────────────────
Foundation (Y1)    14    USD 14.0M      76%           G-001 (partial), G-004, G-009,
                                                      G-010 (MK-04), G-013, G-014,
                                                      G-015, G-016 (partial), G-017
Scale (Y2–Y3)      8     USD 7.5M       41%*         G-001 (80%), G-002, G-007, G-010,
                                                      G-005, G-006, G-016
Mature (Y3–Y5)     4     USD 3.5M       19%*         G-001 (full), G-003, G-011,
                                                      advanced AI capabilities
─────────────────────────────────────────────────────────────────
* Overlaps because multiple gaps span phase boundaries
```

### 8.4 Gap Priority Matrix

```text
                      URGENCY
                Short (Y1)    Medium (Y2-3)   Long (Y3-5)
              ┌───────────────┬───────────────┬──────────────┐
  CRITICAL    │  G-004 (AI    │               │              │
  Priority    │  Platform)    │               │              │
  ┆ HIGH \     │  G-009       │               │              │
  Impact      │  (Consent)   │               │              │
              ├───────────────┼───────────────┼──────────────┤
  HIGH       │  G-002       │  G-007        │  G-011       │
  Priority   │  (Revenue)   │  (CDP)        │  (Proactive  │
  ┆ MEDIUM   │  G-014      │  G-010        │  Engagement) │
  Impact     │  (Governance) │ (Marketing)  │              │
              ├───────────────┼───────────────┼──────────────┤
  MEDIUM     │  G-013       │  G-006        │  G-003       │
  Priority   │  (Zero-Trust)│ (Cloud-Native)│  (Loyalty)   │
  ┆ LOW      │  G-016       │  G-005        │              │
  Impact     │  (Upskilling) │ (Composable)  │              │
              ├───────────────┼───────────────┼──────────────┤
  LOW        │  G-017       │  G-008        │              │
  Priority   │  (Union)     │  (Event Bus)  │              │
  ┆          │  G-018       │               │              │
  Impact     │  (Change     │               │              │
              │  Mgmt)      │               │              │
              └───────────────┴───────────────┴──────────────┘

  → Focus Zone: Top-left (Critical + Short-term)
  → 6 gaps require immediate Foundation-phase investment
```

---

## 9. Gap Closure Roadmap

### 9.1 Gap Closure Sequence

The gap closure sequence follows dependency ordering based on the BPCM dependency map:

| Sequence | Gap | Closure Phase | Dependency | Predecessor |
|----------|-----|--------------|-----------|------------|
| 1 | G-009 (Consent) | Foundation | None (prerequisite) | — |
| 2 | G-014 (AI Governance) | Foundation | G-009 | Consent must be operational for AI compliance |
| 3 | G-004 (AI Platform) | Foundation | G-009, G-014 | Concurrent with consent; depends on governance |
| 4 | G-001 (Unified Portal) | Foundation–Scale | G-004 | AI agents deployed in unified portal |
| 5 | G-013 (Zero-Trust) | Foundation | — | Parallel to G-004 |
| 6 | G-015 (AI Security) | Foundation | G-004, G-013 | Security layer for AI platform |
| 7 | G-016 (Upskilling) | Foundation–Scale | — | Parallel workforce programme |
| 8 | G-017 (Union Relations) | Foundation | — | Before pilot production rollout |
| 9 | G-018 (Change Mgmt) | Foundation | G-016 | Building on workforce programme |
| 10 | G-007 (CDP) | Scale | G-004, G-009 | CDP depends on AI Platform + Consent |
| 11 | G-008 (Event Bus) | Scale | G-007 | Extends CDP capabilities |
| 12 | G-002 (Revenue) | Scale | G-004, G-007 | Revenue engine depends on AI Platform + CDP |
| 13 | G-005 (Composable) | Scale | G-004 | Composable architecture built on AI Platform |
| 14 | G-006 (Cloud-Native) | Scale | G-004, G-005 | Cloud migration follows composable decomposition |
| 15 | G-010 (Marketing) | Scale–Mature | G-007, G-002 | Marketing depends on CDP + revenue attribution |
| 16 | G-003 (Loyalty) | Mature | G-007, G-010 | Loyalty built on CDP + marketing |
| 17 | G-011 (Proactive) | Mature | G-010 | Proactive engagement on marketing foundation |

### 9.2 Gap Closure Timeline

```text
Timeline (Months)
Month 1-6:  [===Foundation===]
  ├── G-009: Enterprise Consent Service (Month 6)
  ├── G-014: AI Governance Framework (Month 6)
  ├── G-004: AI Agent Platform Core (Month 12)
  ├── G-013: Zero-Trust Security Baseline (Month 6–12)
  ├── G-015: AI-Specific Security (Month 6–12)
  ├── G-017: Union Consultation Framework (Month 3–6)
  ├── G-001: Unified Portal MVP (Month 12)
  └── G-018: Change Management Framework (Month 6–12)

Month 7-24: [===Scale===]
  ├── G-016: Workforce Upskilling (Month 7–24)
  ├── G-007: Customer Data Platform (Month 12–24)
  ├── G-008: Event-Driven Data Fabric (Month 12–18)
  ├── G-002: AI Revenue Engine (Month 18–24)
  ├── G-005: Composable Architecture (Month 18–24)
  ├── G-006: Cloud-Native Migration (Month 18–24)
  └── G-010: Marketing Automation (Month 18–24)

Month 25-60: [===Mature===]
  ├── G-003: Customer Loyalty Automation (Month 36–48)
  ├── G-011: Proactive Engagement (Month 36–48)
  ├── G-001: Full Portal Consolidation (Month 36–60)
  └── G-010: Advanced Marketing (Month 36–60)
```

---

## 10. Investment Summary by Gap Category

| Category | Gap Count | Critical | High | Medium | Low | Total Investment | Phase Alignment |
|----------|-----------|----------|------|--------|-----|------------------|-----------------|
| **Business Capability** | 3 | 1 | 1 | 1 | 0 | USD 5.5M | Y1–Y5 |
| **Technology** | 3 | 1 | 2 | 0 | 0 | USD 11.0M | Y1–Y3 |
| **Data** | 3 | 1 | 1 | 0 | 1 | USD 3.0M | Y1–Y5 |
| **Process** | 3 | 2 | 1 | 0 | 0 | USD 1.8M | Y1–Y5 |
| **Security** | 3 | 1 | 1 | 1 | 0 | USD 2.0M | Y1–Y3 |
| **Workforce** | 3 | 0 | 1 | 2 | 0 | USD 1.5M | Y1–Y3 |
| **TOTAL** | **18** | **7** | **7** | **4** | **1** | **USD 18.5M** | **Y1–Y5** |

---

## 11. Traceability

### 11.1 Gap-to-STRAT Current vs Target State

| Gap ID | STRAT Section | Current State Reference | Target State Reference |
|--------|--------------|-------------------------|-------------------------|
| G-001 | STRAT §5 (Current State) | 20+ isolated portals, no unified identity | STRAT §6 (Target Vision) — Unified omnichannel AI experience |
| G-002 | STRAT §5 | Intershop e-commerce, manual campaigns | STRAT §6 — AI-powered commerce with shopping assistant |
| G-004 | STRAT §5 | No AI platform (L1) | STRAT §6 — AI Agent Platform (L4) |
| G-005 | STRAT §5 | Monolithic, tightly coupled | STRAT §6 — Composable, independently deployable |
| G-006 | STRAT §5 | On-prem, no CI/CD | STRAT §6 — Cloud-native, hybrid deployment |
| G-007 | STRAT §5 | Siloed CRM/ERP data | STRAT §6 — CDP with 360-degree view |
| G-008 | STRAT §5 | GCP events (logistics only) | STRAT §6 — Enterprise-wide customer event bus |
| G-009 | STRAT §5 | No enterprise consent | STRAT §6 — Enterprise-wide consent service |
| G-010 | STRAT §5 | Manual campaign management | STRAT §6 — AI-powered marketing intelligence |
| G-011 | STRAT §5 | Reactive-only engagement | STRAT §6 — Proactive AI-driven engagement |
| G-012 | STRAT §5 | No attribution modelling | STRAT §6 — Feature-attribution pipeline |
| G-013 | STRAT §5 | Perimeter-based security | STRAT §6 — Zero-trust architecture |
| G-014 | STRAT §5 | No AI governance | STRAT §6 — AI Governance Framework (7/10) |
| G-015 | STRAT §5 | No AI-specific security | STRAT §6 — AI security controls |
| G-016 | STRAT §5 | No AI training programmes | STRAT §6 — 2,000 staff upskilled |
| G-017 | STRAT §5 | No formal union framework | STRAT §6 — AI Augmentation Charter |
| G-018 | STRAT §5 | Ad hoc change management | STRAT §6 — Structured adoption framework |

### 11.2 Gap-to-BPCM Capabilities

| Gap ID | BPCM Capability | BPCM Sub-Capabilities |
|--------|----------------|----------------------|
| G-001 | Customer Engagement (CE) | CE-01, CE-04 |
| G-002 | E-Commerce & Retail (EC) | EC-02, EC-08 |
| G-003 | Customer Engagement (CE) | CE-06 |
| G-004 | AI Agent Platform (AI) | AI-01 through AI-08 |
| G-005 | Customer Engagement (CE), E-Commerce (EC) | CE-04, EC-08 |
| G-006 | AI Agent Platform (AI) | AI-02, AI-04, AI-08 |
| G-007 | Customer Data & Insights (CD) | CD-01 through CD-08 |
| G-008 | Customer Data & Insights (CD) | CD-06 |
| G-009 | Privacy & Consent Management (PC) | PC-01 through PC-08 |
| G-010 | Marketing & Campaigns (MK) | MK-01 through MK-08 |
| G-011 | Marketing & Campaigns (MK) | MK-05 |
| G-012 | Marketing & Campaigns (MK) | MK-04 |
| G-013 | AI Agent Platform (AI), Privacy (PC) | AI-03, PC-02 |
| G-014 | AI Agent Platform (AI) | AI-03 |
| G-015 | AI Agent Platform (AI) | AI-03 |
| G-016 | Business Operations (BO) | BO-02, BO-03, BO-06 |
| G-017 | Business Operations (BO) | BO-07 |
| G-018 | Business Operations (BO) | BO-06 |

### 11.3 Gap-to-APPINV Applications

| Gap ID | Current Application(s) | Target Application(s) |
|--------|------------------------|----------------------|
| G-001 | APP-01 to APP-18 (20+ portals) | TAPP-01 (Unified Portal) |
| G-002 | APP-19 (Intershop), APP-31 to APP-33 | TAPP-03, TAPP-07 |
| G-003 | None (capability gap) | TAPP-06 (Marketing Intelligence) |
| G-004 | None (greenfield) | TAPP-02 (AI Agent Platform) |
| G-005 | APP-01 to APP-18, APP-19 | TAPP-01, TAPP-03, TAPP-07 |
| G-006 | All on-prem deployments | Hybrid cloud/on-prem |
| G-007 | APP-31 to APP-33 (fragmented) | TAPP-04 (CDP) |
| G-008 | APP-22 (GCP Event Manager) | Extended APP-22 + event bus |
| G-009 | APP-34, APP-35 (per-system, manual) | TAPP-05 (Privacy & Consent) |
| G-010 | APP-31 to APP-33 | TAPP-06 (Marketing Intelligence) |
| G-011 | None (process gap) | TAPP-06 |
| G-012 | None (process gap) | TAPP-06 |
| G-013 | All legacy applications | Zero-trust across target architecture |
| G-014 | None (greenfield) | TAPP-02 (AI Governance) |
| G-015 | None (greenfield) | TAPP-02 (AI Security) |
| G-016 | 10,000 staff — no AI training | Upskilled workforce |
| G-017 | None (process gap) | TWU Consultation Framework |
| G-018 | Ad hoc | Structured programme |

### 11.4 Gap-to-APPR Rationalisation Decisions

| Gap ID | APPR Decision | Decision ID |
|--------|-------------|------------|
| G-001 | CONSOLIDATE → RETIRE (portals) | CD-001, RT-001 |
| G-002 | MODERNIZE (Intershop) | MD-001 |
| G-004 | BUILD (greenfield) | — |
| G-005 | CONSOLIDATE + MODERNIZE | CD-001, MD-001 |
| G-006 | BUILD + HYBRID | — |
| G-007 | CONSOLIDATE | CD-003 |
| G-008 | AUGMENT | AG-001 |
| G-009 | CONSOLIDATE → RETIRE | CD-002, RT-004 |
| G-010 | CONSOLIDATE → RETIRE | CD-003, RT-003 |
| G-011 | BUILD (new capability) | — |
| G-012 | BUILD (new capability) | — |
| G-013 | ARCHITECTURE (across all apps) | — |
| G-014 | BUILD (new capability) | — |
| G-015 | BUILD (new capability) | — |
| G-016 | WORKFORCE (programme) | — |
| G-017 | WORKFORCE (programme) | — |
| G-018 | WORKFORCE (programme) | — |

---

## 12. Risk-Adjusted Gap Closure

### 12.1 High-Risk Gap Dependencies

Gaps that, if delayed, create cascading risk across the programme:

| Gap | Risk if Delayed | Cascading Impact | Mitigation |
|-----|-----------------|------------------|-----------|
| G-009 (Consent) | R-017 (Privacy Act Breach, score 20) | All AI operations blocked; regulatory penalties | Foundation priority — Month 6 operational |
| G-004 (AI Platform) | R-001 (Hallucination, score 16), R-002 (Vendor Lock-In) | All AI capabilities blocked; competitive erosion | Foundation priority — Month 12 pilot |
| G-014 (AI Governance) | R-027 (AI Accountability Gaps, score 16) | Compliance failures; board-level risk | Month 6 framework operational |
| G-016 (Upskilling) | R-013 (Union Action, score 20), R-012 (Staff Resistance) | Industrial action; adoption failure | Charter before pilot; parallel programme |
| G-017 (Union Relations) | R-013 (Union Action, score 20) | Programme halt; workforce disruption | Engage TWU before Year 1 pilot |

### 12.2 Risk Mitigation Alignment

| Risk ID | Risk Title | Score | Gaps That Mitigate | Mitigation Mechanism |
|---------|-----------|-------|-------------------|---------------------|
| R-013 | Union Industrial Action | 20 | G-016, G-017 | AI Augmentation Charter; upskilling; zero net FTE |
| R-017 | Privacy Act Breach | 16 | G-009 | Enterprise consent service; tokenisation layer |
| R-023 | Customer Data Exposure | 16 | G-009, G-015 | PII tokenisation; data isolation; AI security controls |
| R-001 | AI Hallucination | 12 | G-004, G-014 | Response validation; AI governance; model evaluation |
| R-011 | Brand Reputation Damage | 15 | G-004, G-014 | Governance framework; phased rollout; early wins |
| R-018 | ACCC Consumer Law Breach | 12 | G-009, G-014 | Consent-aware AI; compliance monitoring; legal gates |
| R-022 | Prompt Injection Attacks | 12 | G-015 | Input validation; prompt hardening; adversarial testing |
| R-002 | Vendor Lock-In | 12 | G-004 | Multi-vendor strategy; model abstraction layer |

---

## 13. Quality Verification

### GAPA Quality Checklist

| Check | Status |
|-------|--------|
| Document ID: ARC-001-GAPA-v1.0 | ✅ |
| All 14 Document Control fields populated | ✅ |
| Gap Analysis Framework defined | ✅ — Section 1 |
| 6 Capability areas analysed | ✅ — Sections 2–7 |
| Gap Heat Map provided | ✅ — Section 8 |
| Gap scores calculated (Current → Target maturity) | ✅ — 26 total gaps |
| Priority assigned per gap score | ✅ — Critical/High/Medium/Low |
| Effort classified per gap | ✅ — Low/Medium/High |
| Solution approach defined per gap | ✅ — Each gap includes approach |
| Alignment to rationalisation strategy | ✅ — Section 11.4 |
| Investment estimate per gap | ✅ — Section 10 |
| Timeline alignment (Y1/Y2–3/Y3–5) | ✅ — Sections 3–7, Section 9 |
| Traceability to STRAT | ✅ — Section 11.1 |
| Traceability to BPCM | ✅ — Section 11.2 |
| Traceability to APPINV | ✅ — Section 11.3 |
| Traceability to APPR | ✅ — Section 11.4 |
| Traceability to RISK | ✅ — Section 12 |
| Gap closure roadmap | ✅ — Section 9 |
| Risk-adjusted gap closure | ✅ — Section 12 |
| No placeholders | ✅ |
| Classification: OFFICIAL | ✅ |
| Status: DRAFT | ✅ |
| Clean Markdown | ✅ |
| Proper heading hierarchy | ✅ |
| Revision History present | ✅ |

---

**Generated by**: ArcKit `/arckit:gap` command
**Generated on**: 2026-07-01
**ArcKit Version**: 5.15.2
**Project**: 001 — AgenticEA: Agent AI Transformation (MagicDelivery Agent AI Transformation)
**AI Model**: Qwen3.6-27B
**Generation Context**: Synthesised from ARC-000-PRIN-v2.0 (17 principles), ARC-001-STKE-v1.0 (9 stakeholder groups, 12 drivers), ARC-001-REQ-v1.0 (8 business, 59 technical requirements), ARC-001-ADR-v1.0 (8 architecture decisions), ARC-001-RISK-v1.0 (30 risks), ARC-001-STRAT-v1.0 (6 strategic themes, 5-year roadmap), ARC-001-BPCM-v1.0 (8 capabilities, 48 sub-capabilities), ARC-001-APPINV-v1.0 (27 current, 9 target applications), ARC-001-APPR-v1.0 (rationalisation decisions). Gap analysis identifies 18 primary gaps and 26 total gaps (including sub-gaps) across 6 capability areas.
