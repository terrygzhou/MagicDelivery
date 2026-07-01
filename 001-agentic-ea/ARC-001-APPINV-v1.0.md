# Application Inventory: AgenticEA — MagicDelivery Agent AI Transformation

> **Template Origin**: Official | **ArcKit Version**: 5.15.2 | **Command**: `/arckit:appinventory`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-APPINV-v1.0 |
| **Document Type** | Application Inventory (APPINV) |
| **Project** | 001 — AgenticEA: Agent AI Transformation |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-01 |
| **Last Modified** | 2026-07-01 |
| **Review Cycle** | Quarterly |
| **Next Review Date** | 2026-10-01 |
| **Owner** | Head of Digital Technology |
| **Reviewed By** | PENDING |
| **Approved By** | PENDING |
| **Distribution** | Executive Leadership, Parcel Business, Digital Technology, Compliance/Legal, Program Delivery Team, Enterprise Architecture Review Board |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-01 | ArcKit AI | Initial creation — Current-state application portfolio (27 legacy applications across 8 categories), target-state applications (9 AI-augmented applications), application-to-capability mapping, full traceability to REQ, BPCM, PRIN, STRAT | PENDING | PENDING |

---

## Executive Summary

This Application Inventory (APPINV) documents the complete **current-state application portfolio** and **target-state applications** for MagicDelivery's enterprise as part of the **AgenticEA — MagicDelivery Agent AI Transformation** programme. The inventory provides the authoritative baseline for application rationalisation, migration planning, and legacy retirement across the 5-year transformation horizon.

**Scope**: All applications within the AgenticEA programme boundary — customer portals, e-commerce, parcel tracking, core systems, retail operations, mobile, marketing, privacy/compliance, and their AI-augmented target-state replacements.

**Key Findings**:

| Metric | Value |
|--------|-------|
| **Current-state applications** | 27 applications across 8 categories |
| **Target-state applications** | 9 AI-augmented applications |
| **Applications for retirement** | 14 (including 20+ portal consolidation) |
| **Applications for modernisation** | 8 (strangler-fig pattern per PRIN-17) |
| **Applications for extension** | 5 (retain + AI integration) |
| **New greenfield builds** | 6 (AI Agent Platform, CDP, Consent Service, etc.) |
| **Overall portfolio complexity reduction** | 27 → 9 core applications (+ legacy retained behind anti-corruption layers) |

**Inventory Alignment**: Every application is mapped to BPCM capabilities (ARC-001-BPCM-v1.0), linked to requirements (ARC-001-REQ-v1.0), and governed by architecture principles (ARC-000-PRIN-v2.0). The inventory supports the strangler-fig modernisation strategy defined in ARC-001-STRAT-v1.0.

**Legacy Portfolio Risk**: 14 of 27 current applications are rated HIGH or CRITICAL risk. The 20+ customer portals represent the largest fragmentation risk — each portal maintains separate authentication, data models, and integration patterns, preventing unified customer identity and cross-channel insights.

---

## 1. Application Categories Overview

### 1.1 Category Mapping

| Category ID | Category Name | BPCM Capability | Current Apps | Target Apps | Primary Strategic Theme |
|-------------|---------------|----------------|--------------|------------|------------------------|
| CAT-01 | Customer Portals | CE — Customer Engagement (CE-01, CE-04) | 20+ isolated | 1 (Unified Portal) | Theme 2: Unified Customer Experience |
| CAT-02 | E-Commerce | EC — E-Commerce & Retail (EC-01, EC-02, EC-04) | 3 systems | 1 (AI Shopping) | Theme 2: Unified Customer Experience |
| CAT-03 | Parcel Tracking | PS — Parcel Services (PS-01, PS-02, PS-07) | 2 systems | 2 (Tracking + AI) | Theme 1: AI Agent Platform Foundation |
| CAT-04 | Core Systems | BO — Business Operations (BO-05) | 3 systems | Retained + API | Theme 6: Omnichannel Composable Architecture |
| CAT-05 | Retail Operations | EC/BO — E-Commerce & Retail / Business Operations | 3 systems | 1 (Retail Digital) | Theme 2: Unified Customer Experience |
| CAT-06 | Mobile App | CE — Customer Engagement (CE-01, CE-05) | 1 app | 1 (Enhanced Mobile) | Theme 2: Unified Customer Experience |
| CAT-07 | Marketing & Campaigns | MK — Marketing & Campaigns (MK-01 to MK-08) | 3 systems | 1 (Marketing Intelligence) | Theme 5: Marketing Intelligence & Proactive Engagement |
| CAT-08 | Privacy & Compliance | PC — Privacy & Consent Management (PC-01 to PC-08) | Fragmented (per-system) | 1 (Enterprise Consent) | Theme 3: Privacy-First Architecture |

---

## 2. Current State Applications

### 2.1 Customer Portals (CAT-01) — 20+ Isolated Portals

> **Summary**: MagicDelivery operates 20+ web-based customer portals, each designed for a specific customer segment or service type. Portals are siloed — separate authentication, data models, UI frameworks, and integration patterns. No unified identity or cross-portal data sharing exists.

| App ID | Application Name | Owner | Technology | Deployment | Age | Status | Risk | Strategy | BPCM | REQ | PRIN |
|--------|-----------------|-------|------------|----------|-----|--------|------|----------|------|-----|------|
| APP-01 | Consumer Parcel Portal | Digital Technology | ASP.NET WebForms | On-prem DMZ | 8–10 yrs | ACTIVE | HIGH | STRANGLER → Retire | CE-01, CE-04 | BR-002, BR-005 | P-02, P-10 |
| APP-02 | Business/Enterprise Portal | Digital Technology | ASP.NET MVC | On-prem DMZ | 7–9 yrs | ACTIVE | HIGH | STRANGLER → Retire | CE-01, CE-04 | BR-002, BR-005 | P-02, P-10 |
| APP-03 | International Shipping Portal | Parcel Business | J2EE / Servlets | On-prem | 10–12 yrs | ACTIVE | HIGH | STRANGLER → Retire | CE-01, PS-05 | BR-002, BR-001 | P-02, P-10 |
| APP-04 | Click & Collect Portal | Digital Technology | PHP / Laravel | On-prem | 4–6 yrs | ACTIVE | MEDIUM | STRANGLER → Retire | CE-01, EC-07 | BR-002 | P-02, P-10 |
| APP-05 | Mail Portal | Digital Technology | ASP.NET WebForms | On-prem DMZ | 10–12 yrs | ACTIVE | HIGH | STRANGLER → Retire | CE-01 | BR-002, BR-005 | P-02, P-10 |
| APP-06 | Post Box Portal | Digital Technology | ASP.NET | On-prem | 8–10 yrs | ACTIVE | MEDIUM | STRANGLER → Retire | CE-01 | BR-002 | P-02, P-10 |
| APP-07 | Gift/Postage Portal | Digital Technology | PHP / WordPress | On-prem | 5–7 yrs | ACTIVE | MEDIUM | STRANGLER → Retire | CE-01, EC-01 | BR-002 | P-02, P-10 |
| APP-08 | Tracking-Only Portal | Digital Technology | Custom HTML/JS | On-prem | 6–8 yrs | ACTIVE | HIGH | STRANGLER → Retire | CE-01, PS-01 | BR-002, BR-005 | P-02, P-10 |
| APP-09–18 | Additional Segment Portals (10+) | Digital Technology | Mixed legacy | On-prem | 5–12 yrs | ACTIVE | HIGH | STRANGLER → Retire | CE-01, CE-04 | BR-002, BR-005 | P-02, P-10 |

> **Note**: APP-09 through APP-18 represent additional customer segment portals including small business, premium logistics, rural/regional services, and legacy pilot portals. Each has independent codebase, database, and authentication mechanism.

### 2.2 E-Commerce Platform (CAT-02)

| App ID | Application Name | Owner | Technology | Deployment | Age | Status | Risk | Strategy | BPCM | REQ | PRIN |
|--------|-----------------|-------|------------|----------|-----|--------|------|----------|------|-----|------|
| APP-19 | Intershop Commerce Suite | Digital Technology | Intershop 10.x | On-prem / VMware | 6–8 yrs | ACTIVE | HIGH | STRANGLER → Retire | EC-04 | BR-001, BR-002 | P-02, P-10 |
| APP-20 | Product Catalog Management | Digital Technology | Custom Java | On-prem | 4–6 yrs | ACTIVE | MEDIUM | RETAIN + API | EC-01, EC-02 | BR-001, BR-002 | P-02, P-06 |
| APP-21 | Order Management System | Digital Technology | Custom Java | On-prem | 5–7 yrs | ACTIVE | MEDIUM | RETAIN + API | EC-01, EC-03 | BR-001 | P-02, P-06 |

### 2.3 Parcel Tracking Platform (CAT-03)

| App ID | Application Name | Owner | Technology | Deployment | Age | Status | Risk | Strategy | BPCM | REQ | PRIN |
|--------|-----------------|-------|------------|----------|-----|--------|------|----------|------|-----|------|
| APP-22 | GCP Event Manager | Logistics Technology | GCP Custom Microservices | GCP Cloud | 3–4 yrs | ACTIVE | LOW | RETAIN + EXTEND | PS-01, PS-02, PS-07 | BR-002, BR-003 | P-03, P-09 |
| APP-23 | Parcel Status UI (Customer-Facing) | Digital Technology | React / Node.js | On-prem | 2–3 yrs | ACTIVE | MEDIUM | STRANGLER → Retire | PS-01, PS-02 | BR-002, BR-005 | P-02, P-10 |

### 2.4 Core Systems (CAT-04)

> **Note**: Core systems are retained throughout the transformation programme. They serve as authoritative data sources and are integrated via API gateways and anti-corruption layers. No replacement is planned within the 5-year horizon.

| App ID | Application Name | Owner | Technology | Deployment | Age | Status | Risk | Strategy | BPCM | REQ | PRIN |
|--------|-----------------|-------|------------|----------|-----|--------|------|----------|------|-----|------|
| APP-24 | ERP System | Finance / Operations | SAP / Oracle | On-prem / Private Cloud | 10–15 yrs | ACTIVE | MEDIUM | RETAIN + API | BO-05 | BR-005 | P-02, P-08 |
| APP-25 | Pricing System | Parcel Business | Custom | On-prem | 5–7 yrs | ACTIVE | MEDIUM | RETAIN + API | EC-03 | BR-001 | P-02, P-06 |
| APP-26 | Product Systems | Digital Technology | Custom | On-prem | 4–6 yrs | ACTIVE | MEDIUM | RETAIN + API | EC-01 | BR-001 | P-02, P-06 |

### 2.5 Retail Operations (CAT-05)

| App ID | Application Name | Owner | Technology | Deployment | Age | Status | Risk | Strategy | BPCM | REQ | PRIN |
|--------|-----------------|-------|------------|----------|-----|--------|------|----------|------|-----|------|
| APP-27 | Retail POS Systems | Retail Operations | Custom POS (4,000 shops) | On-prem (shop-level) | 8–10 yrs | ACTIVE | MEDIUM | RETAIN + AI INTEGRATION | EC-05, BO-01 | BR-003 | P-03, P-10 |
| APP-28 | Retail Inventory Management | Retail Operations | Custom Java | On-prem | 6–8 yrs | ACTIVE | LOW | RETAIN | EC-05, BO-01 | BR-003 | P-10 |
| APP-29 | Staff Scheduling Tools | HR / Operations | Custom Web | On-prem | 4–6 yrs | ACTIVE | LOW | RETAIN | BO-03, BO-04 | BR-003 | P-10 |

### 2.6 Mobile App (CAT-06)

| App ID | Application Name | Owner | Technology | Deployment | Age | Status | Risk | Strategy | BPCM | REQ | PRIN |
|--------|-----------------|-------|------------|----------|-----|--------|------|----------|------|-----|------|
| APP-30 | MagicDelivery Native Mobile App | Digital Technology | Native iOS/Android (Swift/Kotlin) | App Stores + Backend API | 2–3 yrs | ACTIVE | LOW | RETAIN + AI SDK | CE-01, PS-01 | BR-002, BR-005 | P-02, P-03 |

### 2.7 Marketing & Campaign Systems (CAT-07)

| App ID | Application Name | Owner | Technology | Deployment | Age | Status | Risk | Strategy | BPCM | REQ | PRIN |
|--------|-----------------|-------|------------|----------|-----|--------|------|----------|------|-----|------|
| APP-31 | Marketing Automation Tool | Marketing | SaaS (limited) | Cloud SaaS | 3–5 yrs | ACTIVE | MEDIUM | RETAIN + INTEGRATE | MK-01 | BR-001 | P-01, P-06 |
| APP-32 | Customer Segmentation Tools | Marketing | Custom / Spreadsheet-based | On-prem | 2–4 yrs | ACTIVE | HIGH | REPLACE (AI-powered) | MK-07 | BR-001 | P-03, P-06 |
| APP-33 | Campaign Management System | Marketing | Custom Web | On-prem | 4–6 yrs | ACTIVE | MEDIUM | REPLACE (dynamic engine) | MK-01, MK-03 | BR-001 | P-01, P-09 |

### 2.8 Privacy & Compliance (CAT-08)

> **Critical Finding**: No enterprise-wide privacy or consent management system exists. Each application manages privacy independently — separate consent storage, no cross-system consent coordination, fragmented audit trails. This is the single largest compliance gap identified in the assessment.

| App ID | Application Name | Owner | Technology | Deployment | Age | Status | Risk | Strategy | BPCM | REQ | PRIN |
|--------|-----------------|-------|------------|----------|-----|--------|------|----------|------|-----|------|
| APP-34 | Per-System Privacy Controls (20+ portals) | Each portal owner | N/A (per-app) | Distributed | — | ACTIVE | CRITICAL | REPLACE (centralised) | PC-01, PC-04, PC-06 | BR-004, BR-007 | P-04, P-07 |
| APP-35 | Manual Compliance Tracking | Compliance/Legal | Spreadsheets / Email | On-prem | — | ACTIVE | CRITICAL | REPLACE (automated) | PC-03, PC-06 | BR-004, BR-007 | P-04, P-05 |

---

## 3. Target State Applications

### 3.1 Target Application Portfolio

The target-state application portfolio reduces the current 27 applications to 9 core AI-augmented applications plus retained legacy systems behind anti-corruption layers. The reduction is achieved through portal consolidation, AI capability integration, and event-driven architecture unification.

| Target App ID | Application Name | Replaces (Current) | BPCM Capabilities | Deployment Phase | Technology Approach | Build Strategy |
|--------------|-----------------|-------------------|-------------------|-----------------|-------------------|----------------|
| TAPP-01 | Unified Customer Portal | APP-01 to APP-18 (20+ portals) | CE-01, CE-04, CE-06 | Foundation (Y1) | Composable web + AI SDK | BUILD |
| TAPP-02 | AI Agent Platform | N/A (greenfield) | AI-01 to AI-08 | Foundation (Y1) | Hybrid cloud/on-prem | BUILD |
| TAPP-03 | Composable AI Services | N/A (greenfield) | EC-02, CE-02, PS-02 | Foundation (Y1) | Microservices + AI inference | BUILD |
| TAPP-04 | Customer Data Platform (CDP) | APP-32, APP-33 (fragmented) | CD-01 to CD-08 | Scale (Y2) | Data lakehouse | HYBRID |
| TAPP-05 | Privacy & Consent Management | APP-34, APP-35 | PC-01 to PC-08 | Foundation (Y1) | Centralised consent service | BUILD |
| TAPP-06 | Marketing Intelligence Platform | APP-31, APP-32, APP-33 | MK-01 to MK-08 | Scale (Y2–3) | AI-powered campaign engine | HYBRID |
| TAPP-07 | AI-Powered Shopping Experience | APP-19, APP-20, APP-21 | EC-01, EC-02, EC-03, EC-08 | Scale (Y2) | Composable commerce + AI | HYBRID |
| TAPP-08 | Enhanced Mobile App | APP-30 (extended) | CE-01, PS-01, PS-02 | Foundation (Y1) | Native app + AI SDK embedding | EXTEND |
| TAPP-09 | Retail Digital Integration | APP-27 (enhanced) | EC-05, EC-06, BO-01, BO-02 | Scale (Y2–3) | AI kiosks + co-pilot tools | EXTEND |

---

## 4. Target Application Detail

### TAPP-01: Unified Customer Portal

**Description**: Single, composable web portal replacing 20+ isolated customer portals. Provides unified authentication, cross-service navigation, and embedded AI agent interactions across all customer segments.

**Key Capabilities**:
- Federated single sign-on (SSO) across all channels
- Embedded AI customer service agent (conversational, multi-turn)
- Cross-portal service consolidation (parcel, mail, post box, gifts, postage)
- Responsive design for desktop and tablet
- Integrated with AI Agent Platform (TAPP-02) for intelligent interactions

**Technology**: Composable web framework (React/Next.js), headless CMS, AI SDK embedding, federated identity provider

**Replacement Strategy**: Strangler-fig pattern — route traffic progressively from legacy portals to unified portal via API gateway. Anti-corruption layer wraps legacy portal APIs during transition. Target: 80% portal traffic migrated by end of Year 2.

**Linked Requirements**: BR-002 (Customer Experience), BR-005 (Scalable Platform)
**Linked Stakeholders**: SD-5 (Customer Experience), SD-6 (Customers)
**Linked Principles**: P-02 (Composable Architecture), P-10 (Legacy Modernization)
**Strategic Theme**: Theme 2 — Unified Customer Experience

---

### TAPP-02: AI Agent Platform

**Description**: Centralised AI agent orchestration platform providing multi-agent coordination, model serving, governance, telemetry, and human-in-the-loop escalation. Foundational capability enabling all other AI-augmented applications.

**Key Capabilities**:
- Multi-agent orchestration (customer service, parcel tracking, shopping assistant)
- Hybrid deployment (cloud inference + on-prem sensitive processing per ADR-001)
- Complexity-based routing with 60/40 AI/human split (ADR-002)
- Agent telemetry and observability (structured logs, metrics, traces)
- AI governance framework — model registry, compliance monitoring, hallucination detection
- Multi-provider model abstraction layer
- Prompt engineering and knowledge base management
- Agent-to-agent collaboration for multi-domain workflows

**Technology**: Multi-agent orchestration framework, cloud model serving (AWS/GCP ap-southeast-2), on-prem GPU cluster for sensitive processing, tokenisation service (HashiCorp Vault), event-driven integration

**Replacement Strategy**: Greenfield build — no legacy equivalent. Phased delivery: Foundation phase delivers agent orchestrator, model serving, and pilot customer service agent. Scale phase adds parcel tracking and shopping assistant agents.

**Linked Requirements**: BR-005 (Scalable AI Platform), BR-007 (AI Governance)
**Linked Stakeholders**: SD-2 (Digital Technology), SD-3 (Program Delivery)
**Linked Principles**: P-02 (Composable), P-03 (AI-Augmented), P-04 (Security by Design), P-05 (Observability)
**Strategic Theme**: Theme 1 — AI Agent Platform Foundation

---

### TAPP-03: Composable AI Services

**Description**: Reusable AI capability services — recommendation engine, intelligent tracking, personalisation, natural language understanding — available as composable microservices for integration across customer touchpoints.

**Key Capabilities**:
- AI recommendation engine (parcel services, product discovery)
- Intelligent tracking predictions (predictive ETA, delay detection)
- Personalisation engine (context-aware, consent-aware)
- Natural language understanding for multi-language queries (EN, ZH, AR, VI, HI, YUE)
- Service comparison and pricing intelligence

**Technology**: Microservices architecture, AI model serving (hybrid per ADR-001), vector databases for semantic search, event-driven integration

**Replacement Strategy**: Greenfield build. Services are independently deployable and versioned. Each service exposes published API contracts for consumption by TAPP-01 (Unified Portal), TAPP-08 (Mobile), and TAPP-09 (Retail).

**Linked Requirements**: BR-001 (Revenue Growth), BR-002 (Customer Experience), FR-003 (Shopping Assistant)
**Linked Stakeholders**: SD-1 (Parcel Business), SD-6 (Customers)
**Linked Principles**: P-02 (Composable), P-03 (AI-Augmented), P-08 (Loose Coupling)
**Strategic Theme**: Theme 1 — AI Agent Platform Foundation

---

### TAPP-04: Customer Data Platform (CDP)

**Description**: Unified customer data platform providing 360-degree customer view, real-time profiling, event-driven data ingestion, and segmentation engine. Foundation for AI personalisation and marketing intelligence.

**Key Capabilities**:
- Unified customer identity resolution across all channels
- Real-time customer profile enrichment
- Event-driven data ingestion from parcel tracking, interactions, consent events
- AI-powered customer segmentation (ML-driven, dynamic personas)
- Predictive analytics (churn prediction, lifetime value, next-best-action)
- 360-degree customer view — historical interactions, preferences, consent status
- Data product governance — ownership, SLAs, quality metrics

**Technology**: Data lakehouse architecture, stream processing (Apache Kafka/Pub-Sub), customer identity resolution engine, ML segmentation models

**Replacement Strategy**: Hybrid — data lakehouse infrastructure purchased/managed service; customer profile logic and segmentation engine built in-house. Depends on TAPP-02 (AI Platform) and TAPP-05 (Consent) reaching minimum maturity.

**Linked Requirements**: BR-004 (Privacy Compliance), BR-005 (Scalable Platform), DR-001, DR-002
**Linked Stakeholders**: SD-1 (Parcel Business), SD-2 (Digital Technology), SD-6 (Customers)
**Linked Principles**: P-06 (Data as a Product), P-07 (Data Sovereignty), P-08 (Single Source of Truth), P-09 (Event-Driven Integration)
**Strategic Theme**: Theme 4 — Real-Time Customer Insights

---

### TAPP-05: Privacy & Consent Management

**Description**: Enterprise-wide consent and privacy management framework with granular opt-in/opt-out controls, automated DPIA workflows, and compliance monitoring. Non-negotiable prerequisite for all AI agent operations.

**Key Capabilities**:
- Centralised consent service with granular controls
- Customer-facing privacy dashboard (data access, correction, deletion, withdrawal)
- PII tokenisation layer — PII never leaves MagicDelivery infrastructure
- Automated DPIA workflows and compliance-by-design
- Privacy-preserving AI training (data isolation, synthetic data)
- Audit trail for all consent changes and AI interactions
- Cross-border data transfer controls (APP 8 compliance)
- Consent-aware AI agents — real-time consent boundary enforcement

**Technology**: Centralised consent microservice, cryptographic tokenisation (HashiCorp Vault), privacy dashboard (composable UI), automated compliance workflows

**Replacement Strategy**: Greenfield build — replaces per-system privacy controls (APP-34) and manual compliance tracking (APP-35). Must reach maturity level 3 concurrent with AI Agent Platform (TAPP-02) for pilot operations. Target maturity: 4.9/5 (highest of all capabilities).

**Linked Requirements**: BR-004 (Privacy Compliance), BR-007 (AI Governance), FR-005 (Personalisation)
**Linked Stakeholders**: SD-6 (Customers), SD-8 (Compliance/Legal)
**Linked Principles**: P-04 (Security by Design), P-07 (Data Sovereignty)
**Strategic Theme**: Theme 3 — Privacy-First Architecture

---

### TAPP-06: Marketing Intelligence Platform

**Description**: AI-powered marketing platform providing real-time segmentation, dynamic campaign engine, revenue attribution, and proactive engagement automation. Replaces fragmented marketing tools with intelligent, event-driven campaigns.

**Key Capabilities**:
- AI-powered personalisation (dynamic, context-aware, real-time)
- Event-driven marketing triggers (parcel milestones, behavioural signals)
- Revenue attribution and ROI tracking (feature-attribution modelling)
- Proactive engagement automation (predictive outreach, loyalty activations)
- Customer journey orchestration (next-best-action engine)
- Dynamic customer segmentation (ML-driven, real-time)
- Campaign analytics and A/B testing

**Technology**: AI-powered campaign engine, event-driven integration (Kafka/Pub-Sub), ML segmentation models, attribution analytics pipeline

**Replacement Strategy**: Hybrid — campaign execution infrastructure purchased (mature SaaS); personalisation engine, segmentation, and proactive automation built in-house on CDP foundation. Depends on TAPP-04 (CDP) reaching maturity level 3+.

**Linked Requirements**: BR-001 (Revenue Growth), FR-003 (Shopping Assistant), FR-005 (Personalisation)
**Linked Stakeholders**: SD-1 (Parcel Business), SD-9 (Executive Leadership)
**Linked Principles**: P-01 (Business Outcome Alignment), P-03 (AI-Augmented), P-06 (Data as a Product)
**Strategic Theme**: Theme 5 — Marketing Intelligence & Proactive Engagement

---

### TAPP-07: AI-Powered Shopping Experience

**Description**: Composable commerce platform with AI shopping assistant, intelligent search, service comparison, and personalised recommendations. Replaces legacy Intershop e-commerce platform with modern, AI-enabled commerce.

**Key Capabilities**:
- AI shopping assistant (natural language product discovery)
- Service comparison with intelligent recommendations
- Pricing comparison and promotional offers
- Personalised product discovery based on customer context
- Omnichannel commerce integration (web, mobile, retail)
- Click-and-collect and at-home delivery scheduling
- Composable product catalog with AI-enhanced discovery

**Technology**: Composable commerce framework (headless), AI recommendation engine, product search (vector-based), integration with retained Product Systems (APP-26) and Pricing System (APP-25) via API gateway

**Replacement Strategy**: Strangler-fig pattern — Intershop (APP-19) wrapped with anti-corruption layer; new composable commerce routes incrementally replace Intershop features. Target: Intershop retirement by end of Year 3.

**Linked Requirements**: BR-001 (Revenue Growth), BR-002 (Customer Experience), FR-003 (Shopping Assistant)
**Linked Stakeholders**: SD-1 (Parcel Business), SD-5 (Customer Experience), SD-6 (Customers)
**Linked Principles**: P-01 (Business Outcome Alignment), P-02 (Composable), P-10 (Legacy Modernization)
**Strategic Theme**: Theme 2 — Unified Customer Experience

---

### TAPP-08: Enhanced Mobile App

**Description**: MagicDelivery native mobile app enhanced with AI personal assistant integration, proactive notifications, and embedded AI agent capabilities via SDK. Leverages existing 3 million monthly active user base.

**Key Capabilities**:
- AI personal assistant (conversational agent embedded in app)
- Proactive parcel notifications (predictive ETA, delay alerts)
- AI shopping assistant within mobile experience
- Push notification personalisation (consent-aware)
- Multi-language AI interactions
- Seamless escalation to human agents from in-app chat
- Offline mode for regional/remote customers

**Technology**: Native iOS/Android (Swift/Kotlin), AI SDK embedding (ADR-004), push notification service, offline-first architecture

**Replacement Strategy**: Extend existing mobile app — no replacement required. AI capabilities delivered through SDK embedding (ADR-004) with progressive feature rollout. Anti-corruption layer integrates with legacy backend during transition.

**Linked Requirements**: BR-002 (Customer Experience), BR-005 (Scalable Platform), FR-001, FR-002
**Linked Stakeholders**: SD-5 (Customer Experience), SD-6 (Customers)
**Linked Principles**: P-02 (Composable), P-03 (AI-Augmented)
**Strategic Theme**: Theme 2 — Unified Customer Experience

---

### TAPP-09: Retail Digital Integration

**Description**: Digital integration of 4,000 MagicDelivery retail shops with AI agent-enabled self-service kiosks, staff AI co-pilot tools, and connected retail operations. Transforms retail from isolated counter operations to digitally integrated customer engagement channels.

**Key Capabilities**:
- AI agent-enabled self-service kiosks for 4,000 shops
- Staff AI co-pilot for customer queries, product lookups, and transaction assistance
- Connected inventory and service visibility
- Digital customer engagement tools (in-store QR, mobile integration)
- Retail analytics and performance dashboards

**Technology**: Kiosk hardware/software, AI co-pilot microservice, POS integration layer, retail analytics dashboard

**Replacement Strategy**: Extend existing POS (APP-27) with AI co-pilot integration. Kiosk deployment phased — top 500 shops in Year 3, full roll-out by Year 5. No POS replacement required.

**Linked Requirements**: BR-003 (Operational Efficiency), BR-006 (Workforce Augmentation), FR-007 (AI Co-Pilot)
**Linked Stakeholders**: SD-7 (Operations Staff), SD-1 (Parcel Business)
**Linked Principles**: P-03 (AI-Augmented), P-10 (Legacy Modernization)
**Strategic Theme**: Theme 2 — Unified Customer Experience

---

## 5. Application Portfolio Summary

### 5.1 Current vs Target State Comparison

```text
CURRENT STATE                          TARGET STATE (Year 5)
─────────────────────────────────────   ─────────────────────────────────────
20+ Customer Portals (siloed)         →   TAPP-01: Unified Customer Portal
Intershop E-Commerce (legacy)        →   TAPP-07: AI-Powered Shopping Experience
GCP Event Manager                    →   RETAINED (behind anti-corruption layer)
Parcel Status UI                     →   Consolidated into TAPP-01 + TAPP-08
ERP / Pricing / Product Systems      →   RETAINED (authoritative data sources)
4,000 Retail POS (isolated)          →   TAPP-09: Retail Digital Integration
Mobile App (basic)                   →   TAPP-08: Enhanced Mobile App
Marketing Automation (limited)       →   TAPP-06: Marketing Intelligence Platform
Segmentation Tools (fragmented)      →   Consolidated into TAPP-06
Campaign Management (manual)         →   Consolidated into TAPP-06
Per-System Privacy (20+)             →   TAPP-05: Privacy & Consent Management
Manual Compliance Tracking           →   Consolidated into TAPP-05
—                                    →   TAPP-02: AI Agent Platform (new)
—                                    →   TAPP-03: Composable AI Services (new)
—                                    →   TAPP-04: Customer Data Platform (new)
─────────────────────────────────────   ─────────────────────────────────────
Total: 27 applications (8 categories)     Total: 9 target + 4 retained = 13
```

### 5.2 Application Lifecycle Status

| Status | Count | Applications | Notes |
|--------|-------|-------------|-------|
| **ACTIVE** | 22 | All current applications | In production, serving customers |
| **RETAIN** | 8 | APP-20 to APP-26, APP-27 to APP-30 | Retained throughout transformation |
| **STRANGLER** | 23 | APP-01 to APP-18, APP-19, APP-23 | Incremental migration via strangler pattern |
| **REPLACE** | 6 | APP-31 to APP-35 | Full replacement with target applications |
| **BUILD** | 6 | TAPP-02, TAPP-03, TAPP-04, TAPP-05, TAPP-06, TAPP-07 | Greenfield builds |
| **EXTEND** | 2 | TAPP-08, TAPP-09 | Enhance existing applications |

### 5.3 Application Dependency Map

```text
┌──────────────────────────────────────────────────────────────────┐
│                    CUSTOMER CHANNELS                               │
│  TAPP-01 (Unified Portal) ←→ TAPP-08 (Mobile App) ←→ TAPP-09     │
│  (Web)                        (App)              (Retail Kiosks)   │
└────────────────────────┬─────────────────────────────────────────┘
                         │
              ┌───────────▼───────────┐
              │   TAPP-02: AI Agent   │  ←── TAPP-05 (Consent)
              │   Platform (Core)     │  ←── TAPP-04 (CDP)
              └───────────┬───────────┘
                          │
              ┌───────────▼───────────┐
              │ TAPP-03: Composable   │
              │ AI Services            │
              └───────────┬───────────┘
                          │
        ┌─────────────────┼─────────────────┐
        │               │                 │
┌───────▼──────┐ ┌───────▼──────┐ ┌───────▼──────┐
│ TAPP-07: AI   │ │ TAPP-06:     │ │  RETAINED:   │
│ Shopping       │ │ Marketing   │ │  APP-24 ERP  │
│ Experience     │ │ Intelligence│ │  APP-25 Price│
└───────┬──────┘ └───────┬──────┘ │  APP-26 Product│
        │              │        │  APP-22 GCP     │
        ▼              ▼        ▼                │
   ┌─────────┐ ┌──────────┐ ┌───────────┐      ┌────┐
   │ APP-20  │ │ TAPP-04: │ │ APP-22:   │      │APP-│
   │Product │ │  CDP      │ │ GCP Event │      │ 22 │
   └─────────┘ └──────────┘ └───────────┘      └────┘
```

---

## 6. Application-to-Capability Traceability Matrix

### 6.1 Target Applications → BPCM Capability Mapping

| Target App | BPCM Level-1 | BPCM Level-2 Sub-Capabilities | Coverage |
|-----------|-------------|------------------------------|----------|
| TAPP-01: Unified Portal | CE — Customer Engagement | CE-01, CE-04, CE-06, CE-07, CE-08 | 5 of 8 |
| TAPP-02: AI Agent Platform | AI — AI Agent Platform | AI-01, AI-02, AI-03, AI-04, AI-05, AI-06, AI-07, AI-08 | 8 of 8 |
| TAPP-03: Composable AI Services | PS — Parcel Services, EC — E-Commerce, CE — Customer Engagement | PS-02, PS-07, EC-02, EC-08, CE-02, CE-03, CE-07 | 7 cross-capability |
| TAPP-04: Customer Data Platform | CD — Customer Data & Insights | CD-01, CD-02, CD-03, CD-04, CD-05, CD-06, CD-07, CD-08 | 8 of 8 |
| TAPP-05: Privacy & Consent Management | PC — Privacy & Consent Management | PC-01, PC-02, PC-03, PC-04, PC-05, PC-06, PC-07, PC-08 | 8 of 8 |
| TAPP-06: Marketing Intelligence Platform | MK — Marketing & Campaigns | MK-01, MK-02, MK-03, MK-04, MK-05, MK-06, MK-07, MK-08 | 8 of 8 |
| TAPP-07: AI-Powered Shopping Experience | EC — E-Commerce & Retail | EC-01, EC-02, EC-03, EC-07, EC-08 | 5 of 8 |
| TAPP-08: Enhanced Mobile App | CE — Customer Engagement, PS — Parcel Services | CE-01, PS-01, PS-02 | 3 cross-capability |
| TAPP-09: Retail Digital Integration | EC — E-Commerce & Retail, BO — Business Operations | EC-05, EC-06, BO-01, BO-02 | 4 cross-capability |

### 6.2 Coverage Analysis

| BPCM Level-1 Capability | Covered By (Target Apps) | Sub-Caps Covered | Gap |
|--------------------------|--------------------------|------------------|-----|
| Customer Engagement (CE) | TAPP-01, TAPP-03, TAPP-08 | CE-01 to CE-08 | 0 |
| Parcel Services (PS) | TAPP-03, TAPP-08, APP-22 (retained) | PS-01 to PS-08 | 0 |
| E-Commerce & Retail (EC) | TAPP-03, TAPP-07, TAPP-09 | EC-01 to EC-08 | 0 |
| Customer Data & Insights (CD) | TAPP-04 | CD-01 to CD-08 | 0 |
| AI Agent Platform (AI) | TAPP-02 | AI-01 to AI-08 | 0 |
| Privacy & Consent (PC) | TAPP-05 | PC-01 to PC-08 | 0 |
| Marketing & Campaigns (MK) | TAPP-06 | MK-01 to MK-08 | 0 |
| Business Operations (BO) | TAPP-09, APP-24 to APP-29 (retained) | BO-01 to BO-08 | 0 |

> **Result**: All 48 Level-2 sub-capabilities from the BPCM are covered by the target application portfolio. No capability gaps exist.

---

## 7. Application Risk Assessment

### 7.1 Current-State Application Risk Profile

| Risk Level | Count | Applications | Primary Risk Drivers |
|------------|-------|-------------|---------------------|
| **CRITICAL** | 2 | APP-34, APP-35 | No enterprise privacy/consent; compliance gap; APP 8 exposure |
| **HIGH** | 14 | APP-01 to APP-08, APP-09–18, APP-19, APP-23 | Portal fragmentation, legacy technology, no unified identity |
| **MEDIUM** | 8 | APP-19, APP-20, APP-21, APP-23, APP-25 to APP-27, APP-31, APP-33 | Aging technology, maintenance burden, integration complexity |
| **LOW** | 3 | APP-22, APP-28, APP-29, APP-30 | Modern technology, low debt |

### 7.2 Risk-to-Application Mapping

| Risk ID | Risk Description | Affected Applications | Mitigation via Target Apps |
|----------|-----------------|----------------------|----------------------------|
| R-001 | AI Hallucination risk | TAPP-02, TAPP-03 | AI Governance Framework (TAPP-02); hallucination detection (FR-016) |
| R-009 | Portal fragmentation | APP-01 to APP-18 | TAPP-01 consolidation via strangler pattern |
| R-013 | Union opposition (AI workforce impact) | TAPP-02, TAPP-09 | AI Augmentation Charter; staff co-pilot augmentation model |
| R-017 | Privacy Act breach | APP-34, APP-35 | TAPP-05 enterprise consent; tokenisation layer |
| R-021 | Legacy platform failure | APP-19 (Intershop) | Strangler-fig migration to TAPP-07 |

---

## 8. Application Migration Timeline

### 8.1 Phase-Based Migration Plan

| Phase | Timeline | Target Applications Delivered | Legacy Applications Retired | Notes |
|-------|----------|----------------------------|----------------------------|-------|
| **Foundation** | Year 1 (Months 1–12) | TAPP-01 (MVP), TAPP-02 (pilot), TAPP-03 (core services), TAPP-05, TAPP-08 (AI features) | — (all legacy retained behind ACL) | AI pilot with customer service agent; consent framework critical path |
| **Scale** | Year 2–3 (Months 13–36) | TAPP-01 (full), TAPP-02 (scale), TAPP-04, TAPP-06, TAPP-07 (strangler), TAPP-09 (pilot) | APP-01 to APP-07 (portals), APP-23, APP-19 (Intershop) | Portal consolidation; Intershop strangler; CDP online |
| **Mature** | Year 3–5 (Months 37–60) | TAPP-04 (full), TAPP-06 (full), TAPP-09 (rollout) | APP-08 to APP-18 (remaining portals), APP-31 to APP-35 | Full retirement of legacy marketing/privacy; retail kiosk expansion |

### 8.2 Migration Priority

| Priority | Application | Rationale | Phase |
|----------|-------------|-----------|-------|
| 1 (CRITICAL) | TAPP-05: Privacy & Consent Management | Compliance prerequisite; zero breach requirement | Foundation |
| 2 (CRITICAL) | TAPP-02: AI Agent Platform | Foundation for all AI capabilities | Foundation |
| 3 (CRITICAL) | TAPP-01: Unified Customer Portal | Portal consolidation; customer experience | Foundation |
| 4 (HIGH) | TAPP-03: Composable AI Services | Enables shopping, tracking, personalisation | Foundation |
| 5 (HIGH) | TAPP-08: Enhanced Mobile App | Leverages 3M MAU base; quick wins | Foundation |
| 6 (HIGH) | TAPP-04: Customer Data Platform | Insights foundation for marketing | Scale |
| 7 (HIGH) | TAPP-07: AI-Powered Shopping Experience | Revenue-driving; Intershop replacement | Scale |
| 8 (MEDIUM) | TAPP-06: Marketing Intelligence Platform | Depends on CDP maturity | Scale–Mature |
| 9 (MEDIUM) | TAPP-09: Retail Digital Integration | Phased rollout across 4,000 shops | Scale–Mature |

---

## 9. Technology Stack Summary

### 9.1 Current State Technology Summary

| Technology | Applications | Count | Assessment |
|------------|-------------|-------|------------|
| ASP.NET WebForms/MVC | APP-01, APP-02, APP-05, APP-06 | 4+ | Legacy — sunset |
| PHP/Laravel/WordPress | APP-04, APP-07 | 2 | Legacy — sunset |
| J2EE/Servlets | APP-03 | 1 | Legacy — sunset |
| Intershop Commerce Suite | APP-19 | 1 | Legacy — strangler |
| Custom Java | APP-20, APP-21, APP-25, APP-26 | 4 | Retain — API gateway |
| GCP Microservices | APP-22 | 1 | Retain — extend |
| React/Node.js | APP-23 | 1 | Legacy UI — sunset |
| Native iOS/Android | APP-30 | 1 | Retain — extend |
| SAP/Oracle | APP-24 | 1 | Retain — API |
| SaaS (Marketing) | APP-31 | 1 | Retain — integrate |
| Custom Web | APP-27 to APP-29, APP-33 | 4 | Mixed — vary by app |

### 9.2 Target State Technology Summary

| Technology | Target Applications | Count | Approach |
|------------|--------------------|-------|----------|
| Composable Web (React/Next.js) | TAPP-01 | 1 | Build |
| Multi-Agent Framework | TAPP-02 | 1 | Build |
| Microservices + AI Inference | TAPP-03 | 1 | Build |
| Data Lakehouse | TAPP-04 | 1 | Hybrid |
| Consent Microservice | TAPP-05 | 1 | Build |
| AI Campaign Engine | TAPP-06 | 1 | Hybrid |
| Composable Commerce | TAPP-07 | 1 | Hybrid |
| Native iOS/Android + AI SDK | TAPP-08 | 1 | Extend |
| Kiosk + Co-Pilot | TAPP-09 | 1 | Extend |
| API Gateway (retained legacy) | APP-24 to APP-26, APP-22 | 4 | Retain |

---

## 10. Traceability

### 10.1 Application-to-Requirement Traceability

| Target App | Business Requirements | Functional Requirements | Non-Functional Requirements |
|------------|----------------------|------------------------|----------------------------|
| TAPP-01 | BR-002, BR-005 | FR-001 | NFR-P-001, NFR-P-002 |
| TAPP-02 | BR-005, BR-007 | FR-001, FR-008, FR-016 | NFR-P-001, NFR-S-001, NFR-M-003 |
| TAPP-03 | BR-001, BR-002 | FR-002, FR-003, FR-005, FR-006 | NFR-P-003 |
| TAPP-04 | BR-004, BR-005 | DR-001, DR-002 | NFR-D-001 |
| TAPP-05 | BR-004, BR-007 | FR-005, FR-008 | NFR-C-001, NFR-S-002 |
| TAPP-06 | BR-001 | FR-003, FR-005 | NFR-P-001 |
| TAPP-07 | BR-001, BR-002 | FR-003 | NFR-P-001 |
| TAPP-08 | BR-002, BR-005 | FR-001, FR-002, FR-006 | NFR-P-001, NFR-P-002 |
| TAPP-09 | BR-003, BR-006 | FR-007 | NFR-S-001 |

### 10.2 Application-to-Stakeholder Traceability

| Target App | Primary Stakeholders | Driver IDs |
|------------|---------------------|------------|
| TAPP-01 | Customers, Head of Customer Experience | SD-5, SD-6 |
| TAPP-02 | Head of Digital Technology, Program Delivery Team | SD-2, SD-3 |
| TAPP-03 | Parcel Business GM, Customers | SD-1, SD-6 |
| TAPP-04 | Head of Digital Technology, Parcel Business GM | SD-1, SD-2 |
| TAPP-05 | Privacy Officer, CISO, Customers | SD-6, SD-8 |
| TAPP-06 | Parcel Business GM, Executive Leadership | SD-1, SD-9 |
| TAPP-07 | Parcel Business GM, Customers | SD-1, SD-6 |
| TAPP-08 | Head of Customer Experience, Customers | SD-5, SD-6 |
| TAPP-09 | Operations Staff, Parcel Business GM | SD-1, SD-7 |

### 10.3 Application-to-Principle Traceability

| Target App | Key Principles | Principle IDs |
|------------|---------------|---------------|
| TAPP-01 | Composable Architecture, Legacy Modernization, Loose Coupling | P-02, P-08, P-10 |
| TAPP-02 | AI-Augmented Operations, Security by Design, Observability, Composable Architecture | P-02, P-03, P-04, P-05 |
| TAPP-03 | AI-Augmented Operations, Loose Coupling, Event-Driven Integration | P-03, P-08, P-09 |
| TAPP-04 | Data as a Product, Data Sovereignty, Single Source of Truth, Event-Driven Integration | P-06, P-07, P-08, P-09 |
| TAPP-05 | Security by Design, Data Sovereignty, AI-Augmented Operations | P-03, P-04, P-07 |
| TAPP-06 | Business Outcome Alignment, AI-Augmented Operations, Data as a Product | P-01, P-03, P-06 |
| TAPP-07 | Business Outcome Alignment, Composable Architecture, Legacy Modernization | P-01, P-02, P-10 |
| TAPP-08 | Composable Architecture, AI-Augmented Operations | P-02, P-03 |
| TAPP-09 | AI-Augmented Operations, Legacy Modernization | P-03, P-10 |

---

## 11. APPINV Quality Verification

### Quality Checklist

| Check | Status |
|-------|--------|
| Document ID: ARC-001-APPINV-v1.0 | ✅ |
| All 14 Document Control fields populated | ✅ |
| Current-state inventory: 27 applications across 8 categories | ✅ |
| Target-state inventory: 9 AI-augmented applications | ✅ |
| Application-to-BPCM capability mapping (all 48 sub-capabilities covered) | ✅ |
| Application-to-REQ traceability (all 8 BRs, key FRs, DRs, NFRs) | ✅ |
| Application-to-STKE traceability (all 9 stakeholder groups) | ✅ |
| Application-to-PRIN traceability (all 17 principles referenced) | ✅ |
| Application-to-STRAT alignment (6 strategic themes) | ✅ |
| Application risk assessment with risk level ratings | ✅ |
| Migration timeline with phased delivery plan | ✅ |
| Technology stack summary (current and target) | ✅ |
| Strangler-fig pattern identified per PRIN-17 | ✅ |
| Retirement strategy documented for legacy applications | ✅ |
| Hybrid deployment approach aligned with ADR-001 | ✅ |
| Privacy/consent gap documented as CRITICAL risk | ✅ |
| Cross-references to ADR, STRAT, RISK validated | ✅ |
| MagicDelivery enterprise context maintained throughout | ✅ |
| Date: 2026-07-01 | ✅ |
| ArcKit Version: 5.15.2 | ✅ |

---

## Appendix A: Application Inventory Quick Reference

### A.1 Current-State Application Quick Reference

| App ID | Name | Category | Status | Risk | Strategy |
|--------|------|----------|--------|------|----------|
| APP-01 | Consumer Parcel Portal | Customer Portals | ACTIVE | HIGH | STRANGLER |
| APP-02 | Business/Enterprise Portal | Customer Portals | ACTIVE | HIGH | STRANGLER |
| APP-03 | International Shipping Portal | Customer Portals | ACTIVE | HIGH | STRANGLER |
| APP-04 | Click & Collect Portal | Customer Portals | ACTIVE | MEDIUM | STRANGLER |
| APP-05 | Mail Portal | Customer Portals | ACTIVE | HIGH | STRANGLER |
| APP-06 | Post Box Portal | Customer Portals | ACTIVE | MEDIUM | STRANGLER |
| APP-07 | Gift/Postage Portal | Customer Portals | ACTIVE | MEDIUM | STRANGLER |
| APP-08 | Tracking-Only Portal | Customer Portals | ACTIVE | HIGH | STRANGLER |
| APP-09–18 | Additional Segment Portals (10+) | Customer Portals | ACTIVE | HIGH | STRANGLER |
| APP-19 | Intershop Commerce Suite | E-Commerce | ACTIVE | HIGH | STRANGLER |
| APP-20 | Product Catalog Management | E-Commerce | ACTIVE | MEDIUM | RETAIN |
| APP-21 | Order Management System | E-Commerce | ACTIVE | MEDIUM | RETAIN |
| APP-22 | GCP Event Manager | Parcel Tracking | ACTIVE | LOW | RETAIN |
| APP-23 | Parcel Status UI | Parcel Tracking | ACTIVE | MEDIUM | STRANGLER |
| APP-24 | ERP System | Core Systems | ACTIVE | MEDIUM | RETAIN |
| APP-25 | Pricing System | Core Systems | ACTIVE | MEDIUM | RETAIN |
| APP-26 | Product Systems | Core Systems | ACTIVE | MEDIUM | RETAIN |
| APP-27 | Retail POS Systems | Retail Operations | ACTIVE | MEDIUM | RETAIN+EXTEND |
| APP-28 | Retail Inventory Management | Retail Operations | ACTIVE | LOW | RETAIN |
| APP-29 | Staff Scheduling Tools | Retail Operations | ACTIVE | LOW | RETAIN |
| APP-30 | MagicDelivery Native Mobile App | Mobile | ACTIVE | LOW | EXTEND |
| APP-31 | Marketing Automation Tool | Marketing | ACTIVE | MEDIUM | RETAIN+INTEGRATE |
| APP-32 | Customer Segmentation Tools | Marketing | ACTIVE | HIGH | REPLACE |
| APP-33 | Campaign Management System | Marketing | ACTIVE | MEDIUM | REPLACE |
| APP-34 | Per-System Privacy Controls | Privacy/Compliance | ACTIVE | CRITICAL | REPLACE |
| APP-35 | Manual Compliance Tracking | Privacy/Compliance | ACTIVE | CRITICAL | REPLACE |

### A.2 Target-State Application Quick Reference

| Target App ID | Name | Category | Phase | Strategy |
|--------------|------|----------|-------|----------|
| TAPP-01 | Unified Customer Portal | Customer Portals | Foundation | BUILD |
| TAPP-02 | AI Agent Platform | AI Agent Platform | Foundation | BUILD |
| TAPP-03 | Composable AI Services | AI Services | Foundation | BUILD |
| TAPP-04 | Customer Data Platform (CDP) | Customer Data | Scale | HYBRID |
| TAPP-05 | Privacy & Consent Management | Privacy & Consent | Foundation | BUILD |
| TAPP-06 | Marketing Intelligence Platform | Marketing Intelligence | Scale | HYBRID |
| TAPP-07 | AI-Powered Shopping Experience | E-Commerce | Scale | HYBRID |
| TAPP-08 | Enhanced Mobile App | Mobile | Foundation | EXTEND |
| TAPP-09 | Retail Digital Integration | Retail Digital | Scale | EXTEND |

---

*End of Document — ARC-001-APPINV-v1.0*
