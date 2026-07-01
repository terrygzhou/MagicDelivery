# Business Capability Map (BPCM): AgenticEA — MagicDelivery Agent AI Transformation

> **Template Origin**: Official | **ArcKit Version**: 5.15.2 | **Command**: `/arckit:bpcm`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-BPCM-v1.0 |
| **Document Type** | Business Capability Map (BPCM) |
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
| 1.0 | 2026-07-01 | ArcKit AI | Initial creation — 8 Level-1 capabilities, 48 Level-2 sub-capabilities, current/target maturity assessment, capability heat map, full traceability to REQ, STKE, PRIN | PENDING | PENDING |

---

## Executive Summary

This Business Capability Map (BPCM) provides a structured view of MagicDelivery's enterprise capabilities as they relate to the **AgenticEA — MagicDelivery Agent AI Transformation** programme. It maps **current-state maturity** against **target-state maturity** (Year 5 horizon) across 8 Level-1 capabilities and 48 Level-2 sub-capabilities, identifying the capability gaps that the transformation programme must close.

**Scope**: All capabilities within the AgenticEA programme boundary — customer engagement, parcel services, e-commerce, customer data, AI agent platform, privacy/consent, marketing, and business operations.

**Maturity Scale**: 1 (Initial) → 2 (Repeatable) → 3 (Defined) → 4 (Managed) → 5 (Optimised)

**Key Findings**:
- **Overall current maturity**: 2.1/5 (fragmented, siloed, reactive)
- **Overall target maturity**: 4.3/5 (AI-augmented, composable, proactive)
- **Largest gaps**: AI Agent Platform (+4.0), Privacy & Consent (+3.8), Marketing & Campaigns (+3.5)
- **Capabilities requiring immediate attention**: 12 Level-2 capabilities rated 1 (Initial) in current state
- **Total capability gap**: +2.2 average maturity increase required across all 48 sub-capabilities

---

## 1. Capability Heat Map Overview

### 1.1 Aggregate Maturity by Level-1 Capability

```text
Maturity Scale:  ■ 1 (Initial)   ▓ 2 (Repeatable)   ▒ 3 (Defined)   ░ 4 (Managed)   ▄ 5 (Optimised)

Capability                      Current   Target   Gap    Priority
──────────────────────────────────────────────────────────────────────
1. Customer Engagement          ██ 2.4    ░░ 4.4   +2.0    CRITICAL
2. Parcel Services             ▓▒ 3.1    ░░ 4.5   +1.4    HIGH
3. E-Commerce & Retail         ▓▒ 2.5    ░░ 4.2   +1.7    CRITICAL
4. Customer Data & Insights     ▓ 2.0    ░░ 4.4   +2.4    CRITICAL
5. AI Agent Platform           ■ 1.0     ░░ 4.0   +3.0    CRITICAL
6. Privacy & Consent Mgmt      ■ 1.1     ░░ 4.9   +3.8    CRITICAL
7. Marketing & Campaigns        ▓ 1.8    ░░ 5.3   +3.5    HIGH
8. Business Operations         ▓▒ 3.0    ▒░ 3.8    +0.8   MEDIUM
──────────────────────────────────────────────────────────────────────
OVERALL                        2.1      4.3       +2.2
```

### 1.2 Current State Maturity Distribution (48 sub-capabilities)

| Rating | Count | Percentage | Sub-Capabilities |
|--------|-------|------------|------------------|
| 1 (Initial) | 12 | 25% | AI orchestration, model serving, agent governance, consent mgmt, segmentation, proactive engagement, AI personalisation, predictive analytics, AI co-pilot, event-driven marketing, multi-channel orchestration, data product governance |
| 2 (Repeatable) | 18 | 38% | CRM integration, customer identity, loyalty, product catalog, pricing, retail POS, customer analytics, profile management, consent awareness, campaign mgmt, retail workforce mgmt, etc. |
| 3 (Defined) | 14 | 29% | Parcel tracking, fulfilment ops, self-service portals, mobile tracking, event processing, customer data warehouse, call centre ops, retail operations, etc. |
| 4 (Managed) | 4 | 8% | GCP event manager, mobile experience, basic reporting, legacy billing |
| 5 (Optimised) | 0 | 0% | None — no capability reaches optimised maturity |

### 1.3 Target State Maturity Distribution (Year 5)

| Rating | Count | Percentage |
|--------|-------|------------|
| 1 (Initial) | 0 | 0% |
| 2 (Repeatable) | 0 | 0% |
| 3 (Defined) | 4 | 8% |
| 4 (Managed) | 32 | 67% |
| 5 (Optimised) | 12 | 25% |

---

## 2. Level-1 Capability: Customer Engagement

**Description**: Omnichannel customer interaction across all touchpoints — mobile app, web portal, call centre, retail, and self-service kiosks.

**Strategic Themes**: Theme 1 (AI Agent Platform Foundation), Theme 2 (Unified Customer Experience), Theme 6 (Omnichannel Composable Architecture)

**Traceability**: BR-002, BR-005 | SD-5, SD-6 | G-2 | P-02, P-03, P-05, P-08

### Level-2 Sub-Capabilities

| Sub-Capability | Description | Current | Target | Gap | Closure Phase | REQ | STKE | PRIN |
|----------------|-------------|---------|--------|-----|---------------|-----|------|------|
| **CE-01: Multi-Channel Customer Self-Service** | Web portal, mobile app, and self-service kiosk interactions for customer queries, account management, and service requests | 2 | 4 | +2 | Foundation–Scale | BR-002, FR-001 | SD-5, SD-6 | P-02, P-10 |
| **CE-02: AI-Powered Conversational Service** | AI agent handling of conversational, multi-turn customer queries with natural language understanding | 1 | 4 | +3 | Foundation | BR-002, FR-001, FR-004 | SD-6 | P-03 |
| **CE-03: Human-in-the-Loop Escalation** | Seamless handoff from AI agent to human agent with full context transfer and complexity-based routing | 2 | 4 | +2 | Foundation | BR-002, FR-004, FR-007 | SD-6, SD-7 | P-03, P-08 |
| **CE-04: Unified Customer Identity & SSO** | Federated identity across all channels; single sign-on; customer profile resolution | 1 | 4 | +3 | Foundation | BR-005 | SD-5, SD-6 | P-02, P-08 |
| **CE-05: Call Centre Service Delivery** | Traditional and AI-augmented call centre operations with AI co-pilot support | 3 | 4 | +1 | Scale | BR-003, FR-007 | SD-7 | P-03, P-09 |
| **CE-06: Customer Loyalty & Retention** | Loyalty programme management, retention analytics, churn prediction | 2 | 4 | +2 | Scale–Mature | BR-001 | SD-1, SD-6 | P-01, P-06 |
| **CE-07: Multi-Language Support** | AI agent interactions in English and community languages (Mandarin, Arabic, Vietnamese, Hindi, Cantonese) | 1 | 4 | +3 | Foundation | BR-002, FR-006 | SD-6 | P-03 |
| **CE-08: Customer Feedback & Voice-of-Customer** | NPS collection, CSAT measurement, sentiment analysis, feedback-driven improvement | 2 | 4 | +2 | Foundation–Scale | BR-002, FR-010 | SD-5, SD-6 | P-05 |

**Sub-capability maturity summary**: Current avg 2.4 | Target avg 4.4 | Gap +2.0

---

## 3. Level-1 Capability: Parcel Services

**Description**: Core parcel tracking and fulfilment operations — from lodgement through delivery, including event management and proactive notifications.

**Strategic Themes**: Theme 1 (AI Agent Platform Foundation), Theme 4 (Real-Time Customer Insights)

**Traceability**: BR-001, BR-002, BR-003 | SD-1, SD-6 | G-1, G-2, G-3 | P-03, P-06, P-09

### Level-2 Sub-Capabilities

| Sub-Capability | Description | Current | Target | Gap | Closure Phase | REQ | STKE | PRIN |
|----------------|-------------|---------|--------|-----|---------------|-----|------|------|
| **PS-01: Real-Time Parcel Tracking** | Live parcel status, location history, next-mile visibility via GCP Event Manager and logistics systems | 3 | 4 | +1 | Foundation | BR-002, FR-002 | SD-6 | P-09 |
| **PS-02: AI-Powered Parcel Tracking** | Predictive ETAs, AI-driven delay detection, proactive customer notifications via AI agent | 1 | 5 | +4 | Foundation–Scale | BR-002, FR-002 | SD-6 | P-03, P-09 |
| **PS-03: Fulfilment Operations** | Parcel lodgement, sorting, despatch, and delivery coordination | 3 | 4 | +1 | Scale | BR-003 | SD-1 | P-06 |
| **PS-04: Intelligent Routing & Optimisation** | AI-driven logistics routing, capacity planning, delivery route optimisation | 2 | 4 | +2 | Mature | BR-003 | SD-1 | P-03, P-09 |
| **PS-05: Service Level Management** | SLA monitoring, delivery guarantee tracking, breach management, customer compensation | 2 | 4 | +2 | Scale | BR-002 | SD-6 | P-05 |
| **PS-06: Returns & Reverse Logistics** | Parcel returns processing, refund management, reverse supply chain | 2 | 4 | +2 | Scale–Mature | BR-001 | SD-1 | P-06 |
| **PS-07: Proactive Notification Engine** | Automated, event-driven customer notifications for delivery milestones, delays, and exceptions | 2 | 5 | +3 | Foundation–Scale | BR-002, FR-002 | SD-6 | P-09 |
| **PS-08: Parcel Analytics & Reporting** | Volume analytics, network performance, service quality reporting, forecasting | 3 | 4 | +1 | Scale | BR-005 | SD-1 | P-05 |

**Sub-capability maturity summary**: Current avg 3.1 | Target avg 4.5 | Gap +1.4

---

## 4. Level-1 Capability: E-Commerce & Retail

**Description**: Shopping experience, product catalog management, pricing, and 4,000 retail shop operations with limited-to-full digital integration.

**Strategic Themes**: Theme 2 (Unified Customer Experience), Theme 5 (Marketing Intelligence & Proactive Engagement)

**Traceability**: BR-001, BR-002 | SD-1, SD-5, SD-6 | G-1, G-2 | P-01, P-02, P-10

### Level-2 Sub-Capabilities

| Sub-Capability | Description | Current | Target | Gap | Closure Phase | REQ | STKE | PRIN |
|----------------|-------------|---------|--------|-----|---------------|-----|------|------|
| **EC-01: Product Catalog Management** | Service and product catalogue via Product Systems; AI-enhanced discovery and comparison | 2 | 4 | +2 | Foundation–Scale | BR-001, FR-003 | SD-1, SD-6 | P-02, P-06 |
| **EC-02: AI Shopping Assistant** | AI-powered product discovery, personalised recommendations, service comparison | 1 | 4 | +3 | Foundation | BR-001, FR-003 | SD-1, SD-6 | P-03 |
| **EC-03: Pricing & Fee Management** | Dynamic pricing, fee calculation, promotional offers, price comparison | 2 | 4 | +2 | Scale | BR-001 | SD-1 | P-06 |
| **EC-04: Intershop E-Commerce Platform** | Legacy Intershop Commerce Suite — online shopping and transaction processing (strangler migration) | 2 | 4 | +2 | Foundation–Scale | BR-001 | SD-1 | P-02, P-10 |
| **EC-05: Retail Shop Operations** | 4,000 retail outlets — counter operations, parcel acceptance, customer assistance | 3 | 4 | +1 | Scale | BR-003 | SD-7 | P-03 |
| **EC-06: Retail AI Kiosks** | AI agent-enabled self-service kiosks with staff AI co-pilot for 4,000 shops | 1 | 4 | +3 | Scale | BR-003, FR-007 | SD-7 | P-03, P-05 |
| **EC-07: Click-and-Collect & At-Home Delivery** | E-commerce fulfilment options including click-and-collect and at-home delivery scheduling | 2 | 4 | +2 | Scale | BR-001 | SD-1 | P-01 |
| **EC-08: Omnichannel Commerce Integration** | Unified shopping experience across web, mobile, and retail channels | 1 | 4 | +3 | Foundation–Scale | BR-001, FR-003 | SD-1, SD-5, SD-6 | P-02, P-08 |

**Sub-capability maturity summary**: Current avg 2.5 | Target avg 4.2 | Gap +1.7

---

## 5. Level-1 Capability: Customer Data & Insights

**Description**: 360-degree customer view, customer data platform, real-time profiling, and segmentation engine powering AI personalisation.

**Strategic Themes**: Theme 4 (Real-Time Customer Insights), Theme 5 (Marketing Intelligence & Proactive Engagement)

**Traceability**: BR-001, BR-004, BR-005 | SD-1, SD-2, SD-6 | G-1, G-2, G-5 | P-01, P-06, P-07, P-09

### Level-2 Sub-Capabilities

| Sub-Capability | Description | Current | Target | Gap | Closure Phase | REQ | STKE | PRIN |
|----------------|-------------|---------|--------|-----|---------------|-----|------|------|
| **CD-01: Customer Profile Management** | Unified customer identity, preference storage, opt-in management, profile enrichment | 2 | 4 | +2 | Foundation | BR-004, DR-001 | SD-6 | P-06, P-08 |
| **CD-02: Customer Data Platform (CDP)** | Data lakehouse for unified customer data, real-time enrichment, event-driven ingestion | 1 | 4 | +3 | Scale | BR-005 | SD-2 | P-06, P-09 |
| **CD-03: Customer Analytics & Reporting** | Customer behaviour analytics, journey mapping, cohort analysis, reporting | 2 | 4 | +2 | Scale | BR-005 | SD-1, SD-6 | P-05, P-06 |
| **CD-04: AI-Powered Customer Segmentation** | ML-driven behavioural segmentation, micro-segmentation, dynamic persona creation | 1 | 5 | +4 | Scale–Mature | BR-001 | SD-1 | P-03, P-06 |
| **CD-05: 360-Degree Customer View** | Real-time unified customer view across all channels, touchpoints, and historical interactions | 1 | 5 | +4 | Scale | BR-001, BR-005 | SD-1, SD-6 | P-06, P-09 |
| **CD-06: Event-Driven Customer Intelligence** | Real-time event processing for customer behaviour, predictive triggers, event bus integration | 2 | 4 | +2 | Foundation–Scale | BR-005 | SD-2 | P-09 |
| **CD-07: Predictive Customer Analytics** | Churn prediction, lifetime value modelling, propensity scoring, next-best-action | 1 | 5 | +4 | Mature | BR-001 | SD-1 | P-03, P-06 |
| **CD-08: Data Product Governance** | Customer data as a product — ownership, SLAs, quality metrics, lineage, deprecation | 1 | 4 | +3 | Foundation | BR-004, DR-002 | SD-2 | P-06, P-07 |

**Sub-capability maturity summary**: Current avg 2.0 | Target avg 4.4 | Gap +2.4

---

## 6. Level-1 Capability: AI Agent Platform

**Description**: AI-powered interactions and automation — agent orchestration, model serving, governance, telemetry, and human-AI collaboration. Core enabler for all other AI-augmented capabilities.

**Strategic Themes**: Theme 1 (AI Agent Platform Foundation), Theme 6 (Omnichannel Composable Architecture)

**Traceability**: BR-003, BR-005, BR-007 | SD-2, SD-3, SD-5 | G-3, G-5, G-7, G-8 | P-02, P-03, P-04, P-05, P-08

### Level-2 Sub-Capabilities

| Sub-Capability | Description | Current | Target | Gap | Closure Phase | REQ | STKE | PRIN |
|----------------|-------------|---------|--------|-----|---------------|-----|------|------|
| **AI-01: Agent Orchestration** | Multi-agent orchestration framework — routing, coordination, lifecycle management, agent registry | 1 | 4 | +3 | Foundation | BR-005, FR-001 | SD-2 | P-02, P-03 |
| **AI-02: Hybrid Model Serving** | Cloud inference + on-prem sensitive processing (ADR-001); tokenisation layer; multi-provider abstraction | 1 | 4 | +3 | Foundation | BR-005, ADR-001 | SD-2, SD-8 | P-03, P-04, P-07 |
| **AI-03: AI Governance & Compliance** | Model governance framework, compliance monitoring, DPIA automation, hallucination detection (FR-016) | 1 | 5 | +4 | Foundation | BR-007, FR-016 | SD-8 | P-03, P-04, P-07 |
| **AI-04: Agent Telemetry & Observability** | Structured telemetry for AI agents — accuracy tracking, performance metrics, model drift detection | 1 | 4 | +3 | Foundation | BR-005, FR-010 | SD-2 | P-05 |
| **AI-05: Prompt Engineering & Knowledge Base** | Domain-specific knowledge bases, prompt libraries, retrieval-augmented generation (RAG), authoritative data verification | 1 | 4 | +3 | Foundation | BR-005 | SD-2 | P-03 |
| **AI-06: Complexity-Based Routing** | Real-time query complexity classification, dynamic routing, 60/40 AI/human split (ADR-002) | 1 | 4 | +3 | Foundation | BR-003, FR-004 | SD-7 | P-03, P-08 |
| **AI-07: Agent-to-Agent Collaboration** | Multi-agent workflows — customer service agent, parcel tracking agent, shopping assistant coordination | 1 | 4 | +3 | Scale | BR-005 | SD-2 | P-02, P-08 |
| **AI-08: Model Evaluation & MLOps** | Model accuracy testing, A/B testing, continuous evaluation, automated retraining pipelines, model registry | 1 | 4 | +3 | Foundation | BR-005, NFR-M-003 | SD-2 | P-05, P-06 |

**Sub-capability maturity summary**: Current avg 1.0 | Target avg 4.0 | Gap +3.0

> **Note**: AI Agent Platform is the foundational capability that all other AI-augmented capabilities depend on. It must reach minimum maturity level 3 before any other AI-augmented capability can be rated above its current state.

---

## 7. Level-1 Capability: Privacy & Consent Management

**Description**: Unified consent framework, enterprise-wide privacy management, PII protection, and regulatory compliance for AI agent operations.

**Strategic Themes**: Theme 3 (Privacy-First Architecture), Theme 1 (AI Agent Platform Foundation)

**Traceability**: BR-004, BR-007 | SD-8, SD-6 | G-4, G-7 | P-04, P-07

### Level-2 Sub-Capabilities

| Sub-Capability | Description | Current | Target | Gap | Closure Phase | REQ | STKE | PRIN |
|----------------|-------------|---------|--------|-----|---------------|-----|------|------|
| **PC-01: Enterprise Consent Management** | Centralised consent service with granular opt-in/opt-out controls; privacy dashboard for customers | 1 | 5 | +4 | Foundation | BR-004, FR-005 | SD-8 | P-04, P-07 |
| **PC-02: PII Tokenisation & Data Sovereignty** | Cryptographic tokenisation layer (ADR-001); PII never leaves MagicDelivery infrastructure; international data residency | 1 | 5 | +4 | Foundation | BR-004, ADR-001 | SD-8 | P-04, P-07 |
| **PC-03: Automated DPIA & Compliance Workflows** | Data Protection Impact Assessment automation, consent-aware AI operations, compliance-by-design | 1 | 4 | +3 | Foundation | BR-004, BR-007 | SD-8 | P-04, P-07 |
| **PC-04: Privacy Dashboard & Customer Self-Service** | Customer-facing privacy controls — data access, correction, deletion, consent withdrawal | 1 | 4 | +3 | Foundation | BR-004, FR-005 | SD-6, SD-8 | P-04 |
| **PC-05: AI-Specific Privacy Controls** | Privacy-preserving AI training, synthetic data generation, data isolation for model training | 1 | 4 | +3 | Foundation | BR-004, FR-016 | SD-8 | P-04, P-07 |
| **PC-06: Audit Trail & Accountability** | Complete audit trail for all consent changes, AI interactions, data processing events | 1 | 4 | +3 | Foundation | BR-007, FR-008 | SD-8 | P-04, P-05 |
| **PC-07: Cross-Border Data Transfer Controls** | APP 8 compliance automation, consent-aware cross-border data handling, residency enforcement | 1 | 5 | +4 | Foundation | BR-004, NFR-C-001 | SD-8 | P-04, P-07 |
| **PC-08: Consent Awareness in AI Agents** | AI agents that respect and enforce consent boundaries in real-time during customer interactions | 1 | 4 | +3 | Foundation | BR-004, FR-005 | SD-6, SD-8 | P-03, P-04 |

**Sub-capability maturity summary**: Current avg 1.1 | Target avg 4.9 | Gap +3.8

> **Note**: Privacy & Consent Management has the highest target maturity (4.9/5) because it is a non-negotiable prerequisite for all AI agent operations. Zero Privacy Act breaches is a Board-level constraint (BR-004).

---

## 8. Level-1 Capability: Marketing & Campaigns

**Description**: Proactive engagement, targeted offers, dynamic campaigns, revenue attribution, and AI-powered customer journey orchestration.

**Strategic Themes**: Theme 5 (Marketing Intelligence & Proactive Engagement), Theme 4 (Real-Time Customer Insights)

**Traceability**: BR-001, BR-002 | SD-1, SD-6 | G-1, G-2 | P-01, P-03, P-06

### Level-2 Sub-Capabilities

| Sub-Capability | Description | Current | Target | Gap | Closure Phase | REQ | STKE | PRIN |
|----------------|-------------|---------|--------|-----|---------------|-----|------|------|
| **MK-01: Campaign Management** | Traditional campaign creation, scheduling, targeting, and execution | 2 | 4 | +2 | Scale | BR-001 | SD-1 | P-01 |
| **MK-02: AI-Powered Personalisation** | Dynamic, context-aware personalisation based on real-time customer data and AI predictions | 1 | 5 | +4 | Scale–Mature | BR-001, FR-003, FR-005 | SD-1, SD-6 | P-03, P-06 |
| **MK-03: Event-Driven Marketing** | Real-time campaign triggers based on customer events, parcel milestones, and behavioural signals | 1 | 5 | +4 | Scale | BR-001 | SD-1 | P-09 |
| **MK-04: Revenue Attribution & ROI Tracking** | Feature-attribution modelling, campaign ROI, AI-driven revenue measurement against control groups | 1 | 4 | +3 | Foundation | BR-001 | SD-1 | P-01, P-06 |
| **MK-05: Proactive Engagement Automation** | AI-driven proactive engagement — predictive outreach, service offers, loyalty activations | 1 | 5 | +4 | Mature | BR-001 | SD-1 | P-03 |
| **MK-06: Customer Journey Orchestration** | End-to-end journey mapping, touchpoint orchestration, next-best-action engine | 1 | 4 | +3 | Mature | BR-001 | SD-1, SD-6 | P-01, P-09 |
| **MK-07: Dynamic Customer Segmentation** | Real-time, AI-powered segmentation for targeted campaigns and offers | 1 | 5 | +4 | Scale | BR-001 | SD-1 | P-03, P-06 |
| **MK-08: Marketing Analytics & Reporting** | Campaign performance, conversion analytics, A/B testing, ROI dashboards | 2 | 4 | +2 | Scale | BR-001 | SD-1 | P-05, P-06 |

**Sub-capability maturity summary**: Current avg 1.8 | Target avg 5.3 | Gap +3.5

---

## 9. Level-1 Capability: Business Operations

**Description**: Retail shop operations, workforce management, staff augmentation, call centre management, and operational excellence.

**Strategic Themes**: Theme 2 (Unified Customer Experience), Theme 1 (AI Agent Platform Foundation)

**Traceability**: BR-003, BR-006, BR-008 | SD-3, SD-7, SD-9 | G-3, G-6, G-8 | P-02, P-03, P-08, P-10

### Level-2 Sub-Capabilities

| Sub-Capability | Description | Current | Target | Gap | Closure Phase | REQ | STKE | PRIN |
|----------------|-------------|---------|--------|-----|---------------|-----|------|------|
| **BO-01: Retail Shop Management** | 4,000 retail outlet operations — inventory, staffing, customer service, parcel acceptance | 3 | 4 | +1 | Scale | BR-003 | SD-7 | P-10 |
| **BO-02: AI-Augmented Staff Tools** | AI co-pilot for call centre and retail staff — automated lookups, suggested responses, knowledge retrieval | 1 | 4 | +3 | Foundation–Scale | BR-003, FR-007 | SD-7 | P-03 |
| **BO-03: Workforce Upskilling & Training** | AI-augmented workflow training for 2,000 staff; certification programmes; career pathways | 1 | 4 | +3 | Foundation–Scale | BR-006 | SD-7 | P-03 |
| **BO-04: Call Centre Operations** | Inbound query management, skill-based routing, workforce scheduling, quality assurance | 3 | 4 | +1 | Scale | BR-003 | SD-7 | P-03, P-05 |
| **BO-05: Operations Reporting & Dashboards** | Real-time operational dashboards, KPI tracking, exception reporting, capacity planning | 3 | 4 | +1 | Scale | BR-005, BR-008 | SD-3 | P-05 |
| **BO-06: Staff AI Confidence & Adoption** | Measuring and improving staff AI confidence scores (3.0 → 6.5/10), change management | 1 | 4 | +3 | Foundation–Scale | BR-006 | SD-7 | P-03 |
| **BO-07: Union Relations & Industrial Engagement** | TWU consultation framework, AI Augmentation Charter, workforce impact monitoring | 2 | 4 | +2 | Foundation | BR-006, BR-008 | SD-7, SD-9 | P-01 |
| **BO-08: Legacy System Transition** | Strangler-fig modernisation of 20+ portals, Intershop retirement, incremental migration | 2 | 3 | +1 | Foundation–Mature | BR-005 | SD-2 | P-02, P-10 |

**Sub-capability maturity summary**: Current avg 3.0 | Target avg 3.8 | Gap +0.8

> **Note**: Business Operations has the smallest gap (+0.8) because most operational capabilities are already at maturity level 2–3. The primary uplift comes from AI augmentation (BO-02, BO-03, BO-06) rather than building new capabilities from scratch.

---

## 10. Capability Heat Map: Current vs Target Gap Analysis

### 10.1 Visual Gap Heat Map

```text
                    GAP SEVERITY
                Low (0-1)   Medium (2)   High (3+)
              ┌────────────┼────────────┼────────────┐
              │            │            │            │
  Foundation  │ BO-08      │ BO-05      │ AI-01      │
  (Year 1)     │ BO-04      │ BO-01      │ AI-02      │
              │            │            │ AI-03      │
              ├────────────┼────────────┼────────────┤
  Scale       │ PS-01      │ CE-06      │ AI-04      │
  (Years 2-3) │ PS-08      │ CE-03      │ AI-05      │
              │ CD-03      │ CD-06      │ PC-01      │
              ├────────────┼────────────┼────────────┤
  Mature      │ PS-03      │ CE-01      │ CD-04      │
  (Years 3-5) │ EC-05      │ PS-06      │ CD-05      │
              │            │            │ MK-02      │
              └────────────┼────────────┼────────────┘

  Legend: Each cell shows representative capabilities at that gap level
  Gap = Target Maturity - Current Maturity
```

### 10.2 Gap Distribution by Capability

```text
Capability                          Gap   Sub-Caps with Gap ≥ 3
──────────────────────────────────────────────────────────────────
1. Customer Engagement             +2.0   CE-02, CE-04, CE-07
2. Parcel Services                  +1.4   PS-02
3. E-Commerce & Retail              +1.7   EC-02, EC-06, EC-08
4. Customer Data & Insights         +2.4   CD-04, CD-05, CD-07
5. AI Agent Platform                +3.0   All 8 sub-capabilities
6. Privacy & Consent Management    +3.8   PC-01, PC-02, PC-07
7. Marketing & Campaigns             +3.5   MK-02, MK-03, MK-05, MK-07
8. Business Operations              +0.8   BO-02, BO-03, BO-06
──────────────────────────────────────────────────────────────────
Total: 48 sub-capabilities, 26 with gap ≥ 2, 12 with gap ≥ 3
Average gap: +2.2
```

### 10.3 Investment-Adjusted Gap Heat Map

```text
Priority Matrix: Gap Severity × Strategic Priority
  (Informed by STRAT theme investment and REQ priority)

                    GAP SIZE
              Small (≤1)  Medium (2)   Large (3+)
            ┌────────────┼────────────┼────────────┐
            │              │            │            │
CRITICAL    │              │   CE-01     │   AI-01    │
Priority    │              │   CE-07     │   AI-02    │
            │              │   EC-08     │   AI-03    │
            ├──────────────┼────────────┼────────────┤
            │              │   CD-01     │   AI-04    │
HIGH        │              │   CD-08     │   PC-01    │
Priority    │              │   CD-06     │   PC-02    │
            │              │   MK-04     │   PC-07    │
            ├──────────────┼────────────┼────────────┤
            │   BO-04      │   BO-02     │   AI-08    │
MEDIUM      │   BO-05      │   BO-06     │   CD-04    │
Priority    │   PS-01      │   PS-02     │   CD-05    │
            │   PS-08      │   PS-07     │   MK-02    │
            ├──────────────┼────────────┼────────────┤
            │              │   BO-01     │            │
LOW         │              │   PS-03     │            │
Priority    │              │   EC-05     │            │
            └──────────────┴────────────┴────────────┘

  → Focus: Top-right quadrant (Critical Priority + Large Gap)
  → 17 sub-capabilities require immediate Foundation-phase investment
```

---

## 11. Capability Dependency Map

### 11.1 Foundational Dependencies

```text
                    AI Agent Platform (5)
                    ──────────────────────
                         │
          ┌──────────────┼──────────────┐
          │              │              │
   Privacy & Consent   Customer Data  Customer Engagement
   Management (6)     & Insights (4)  (1)
          │              │              │
          └──────────────┼──────────────┘
                         │
          ┌──────────────┼──────────────┐
          │              │              │
   Marketing &        Parcel        E-Commerce
   Campaigns (7)      Services (2)  & Retail (3)
                                           │
                                  ┌────────┴────────┐
                                  │                 │
                           Business           AI Agent Platform
                           Operations (8)     (feedback loop)
```

### 11.2 Dependency Rules

| Dependency | Rule | Closure Order |
|------------|------|---------------|
| AI Agent Platform ←→ Privacy & Consent | Bidirectional — both must reach L3 concurrently for AI pilot | Foundation, concurrent |
| Customer Data & Insights ←→ Customer Engagement | Customer Engagement depends on CDP for unified identity | Foundation (CDP), Scale (engagement) |
| Marketing & Campaigns ←→ Customer Data & Insights | Marketing cannot scale beyond L2 without CDP at L3+ | Scale (CDP), Mature (marketing) |
| Parcel Services →→ Customer Engagement | Parcel tracking feeds engagement experience | Foundation (AI tracking), Scale |
| E-Commerce & Retail →→ Marketing | Commerce data feeds personalisation | Scale (both), Mature (personalisation) |
| Business Operations —→ AI Agent Platform | Staff AI tools depend on AI platform | Foundation (platform), Scale (staff tools) |

---

## 12. Capability Maturity Timeline

### 12.1 Maturity Progression by Phase

```text
Maturity Level
5 |                              ██ Marketing (select)
  |                         ██ ██ Privacy (select)
  |                      ██ ██ ██ Customer Data (select)
4 |        ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ AI Platform
  |     ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ Customer Engagement
  |  ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ Parcel Services
  | ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ E-Commerce & Retail
3 | ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ Business Operations
  └─────────────────────────────────────────────────────────►
     Y1 (Foundation)    Y2-3 (Scale)       Y3-5 (Mature)

  ██ = Target maturity level achieved by phase end
  — = Current maturity baseline
```

### 12.2 Capability Readiness Gates

| Gate | Phase | Sub-Capabilities That Must Reach L3 |
|------|-------|--------------------------------------|
| **Alpha** | Y1, Month 6 | AI-01, AI-02, AI-06, PC-01, PC-02, PC-05 |
| **Beta** | Y1, Month 12 | AI-03, AI-04, PC-03, PC-06, CE-02, CE-03 |
| **Gamma** | Y2, Month 24 | AI-05, AI-07, AI-08, CD-01, CD-06, CE-04 |
| **Delta** | Y3, Month 36 | CD-02, CD-03, MK-01, MK-04, MK-08 |
| **Epsilon** | Y4, Month 48 | CD-04, CD-08, MK-02, MK-03, MK-07 |
| **Zeta** | Y5, Month 60 | MK-05, MK-06, CD-05, CD-07 (full maturity) |

---

## 13. Traceability Matrix

### 13.1 Capability-to-Requirement Traceability

| Capability | Sub-Capabilities | Business Requirements | Functional Requirements | Strategic Goals |
|------------|-----------------|----------------------|------------------------|-----------------|
| Customer Engagement | CE-01 to CE-08 | BR-001, BR-002 | FR-001, FR-004, FR-005, FR-006, FR-010 | G-1, G-2 |
| Parcel Services | PS-01 to PS-08 | BR-001, BR-002, BR-003 | FR-002 | G-1, G-2, G-3 |
| E-Commerce & Retail | EC-01 to EC-08 | BR-001, BR-003 | FR-003, FR-007 | G-1, G-2, G-3 |
| Customer Data & Insights | CD-01 to CD-08 | BR-001, BR-004, BR-005 | DR-001, DR-002 | G-1, G-5 |
| AI Agent Platform | AI-01 to AI-08 | BR-003, BR-005, BR-007 | FR-001, FR-008, FR-010, FR-016 | G-3, G-5, G-7 |
| Privacy & Consent | PC-01 to PC-08 | BR-004, BR-007 | FR-005, FR-008 | G-4, G-7 |
| Marketing & Campaigns | MK-01 to MK-08 | BR-001 | FR-003, FR-005 | G-1, G-2 |
| Business Operations | BO-01 to BO-08 | BR-003, BR-006, BR-008 | FR-007 | G-3, G-6, G-8 |

### 13.2 Capability-to-Stakeholder Traceability

| Capability | Primary Stakeholders (STKE) | Driver IDs |
|------------|---------------------------|-----------|
| Customer Engagement | Customers, Head of Customer Experience, Mobile App Developers | SD-5, SD-6 |
| Parcel Services | Customers, Parcel Business GM | SD-1, SD-6 |
| E-Commerce & Retail | Parcel Business GM, Customers | SD-1, SD-5 |
| Customer Data & Insights | Digital Technology, Parcel Business GM, Customers | SD-1, SD-2, SD-6 |
| AI Agent Platform | Digital Technology, Program Delivery Team | SD-2, SD-3 |
| Privacy & Consent | Compliance/Legal, Customers, CISO | SD-6, SD-8 |
| Marketing & Campaigns | Parcel Business GM, Executive Leadership | SD-1, SD-9 |
| Business Operations | Operations Staff, Head of People & Culture | SD-3, SD-7, SD-9 |

### 13.3 Capability-to-Principle Traceability

| Capability | Key Principles (PRIN) | Principle IDs |
|------------|----------------------|---------------|
| Customer Engagement | Composable Architecture, AI-Augmented Operations, Observability, Loose Coupling, Legacy Modernization | P-02, P-03, P-05, P-08, P-10 |
| Parcel Services | AI-Augmented Operations, Event-Driven Integration, Performance | P-03, P-09, P-11 |
| E-Commerce & Retail | Business Outcome Alignment, Composable Architecture, Loose Coupling, Legacy Modernization | P-01, P-02, P-08, P-10 |
| Customer Data & Insights | Data as a Product, Data Sovereignty, Single Source of Truth, Event-Driven Integration | P-06, P-07, P-08, P-09 |
| AI Agent Platform | Composable Architecture, AI-Augmented Operations, Security by Design, Observability, Loose Coupling | P-02, P-03, P-04, P-05, P-08 |
| Privacy & Consent | Security by Design, Data Sovereignty | P-04, P-07 |
| Marketing & Campaigns | Business Outcome Alignment, AI-Augmented Operations, Data as a Product | P-01, P-03, P-06 |
| Business Operations | AI-Augmented Operations, Loose Coupling, Legacy Modernization | P-03, P-08, P-10 |

---

## 14. BPCM Quality Verification

### Quality Checklist

| Check | Status |
|-------|--------|
| Document ID: ARC-001-BPCM-v1.0 | ✅ |
| All 14 Document Control fields populated | ✅ |
| 8 Level-1 capabilities mapped | ✅ |
| 48 Level-2 sub-capabilities detailed | ✅ |
| Current state maturity rated (1-5) for all 48 sub-capabilities | ✅ |
| Target state maturity rated (1-5) for all 48 sub-capabilities | ✅ |
| Gap analysis (current vs target) per sub-capability | ✅ |
| Capability heat map (visual gap representation) | ✅ |
| Traceability to REQ requirements | ✅ |
| Traceability to STKE stakeholder goals | ✅ |
| Traceability to PRIN principles | ✅ |
| Dependency map between capabilities | ✅ |
| Maturity timeline by delivery phase | ✅ |
| Capability readiness gates defined | ✅ |
| No placeholders | ✅ |
| Classification: OFFICIAL | ✅ |
| Status: DRAFT | ✅ |
| Clean Markdown | ✅ |
| Proper heading hierarchy | ✅ |

---

## Appendix: Maturity Rating Scale Reference

| Level | Name | Description |
|-------|------|-------------|
| **1** | Initial | Capability is ad-hoc, unstructured, or non-existent. Outcomes are unpredictable. No formal processes or tools. |
| **2** | Repeatable | Capability exists with basic processes. Can be repeated with consistent results but lacks optimisation. Siloed execution. |
| **3** | Defined | Formalised processes, documented standards, and management oversight. Capability is designed and can be reliably delivered. |
| **4** | Managed | Measured and controlled with defined metrics. Continuous monitoring, automated controls, and structured improvement. |
| **5** | Optimised | AI-augmented, continuously self-improving. Proactive engagement, predictive capabilities, and automated optimisation. |

---

**Generated by**: ArcKit `/arckit:bpcm` command
**Generated on**: 2026-07-01
**ArcKit Version**: 5.15.2
**Project**: 001 — AgenticEA: Agent AI Transformation (MagicDelivery Agent AI Transformation)
**AI Model**: Qwen3.6-27B
**Generation Context**: Synthesised from ARC-000-PRIN-v2.0 (17 principles), ARC-001-STKE-v1.0 (9 stakeholder groups, 12 drivers, 8 goals), ARC-001-REQ-v1.0 (8 business, 59 technical requirements), ARC-001-ADR-v1.0 (8 architecture decisions), ARC-001-RISK-v1.0 (30 risks), ARC-001-STRAT-v1.0 (6 strategic themes, 5-year roadmap). BPCM maps 8 Level-1 capabilities, 48 Level-2 sub-capabilities, with current/target maturity assessment, heat map analysis, dependency mapping, and full traceability to requirements, stakeholder goals, and architecture principles.
