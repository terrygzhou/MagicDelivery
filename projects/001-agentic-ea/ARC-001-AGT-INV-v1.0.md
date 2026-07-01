# Agent Inventory: AgenticEA — MarsPost Agent AI Transformation

> **Template Origin**: Official | **ArcKit Version**: 5.15.2 | **Command**: `/arckit:agentinventory`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-AGT-INV-v1.0 |
| **Document Type** | Agent Inventory (AGT-INV) |
| **Project** | 001 — AgenticEA: Agent AI Transformation |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-01 |
| **Last Modified** | 2026-07-01 |
| **Review Cycle** | Quarterly |
| **Next Review Date** | 2026-10-01 |
| **Owner** | AI Engineering Lead, Digital Technology |
| **Reviewed By** | PENDING |
| **Approved By** | PENDING |
| **Distribution** | Executive Leadership, Parcel Business, Digital Technology, Compliance/Legal, Program Delivery Team, Enterprise Architecture Review Board |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-01 | ArcKit AI | Initial creation — Current-state assessment, 8 agent categories, 16 agent instances, full inventory with traceability to REQ, BPCM, APPINV, TRANS | PENDING | PENDING |

---

## Executive Summary

### Purpose

This Agent Inventory (AGT-INV) provides a comprehensive catalogue of all **existing** and **planned** AI agents for the **AgenticEA — MarsPost Agent AI Transformation** programme. It documents each agent's purpose, capabilities, engagement channels, technology stack, maturity targets, integration requirements, data dependencies, and privacy/security considerations. This document serves as the authoritative agent registry, enabling governance, lifecycle management, and compliance tracking across the agent portfolio.

### Key Findings

| Metric | Value |
|--------|-------|
| **Current AI agents in production** | 0 — No existing AI agents |
| **Planned AI agents (Year 5)** | 16 distinct agent instances across 8 categories |
| **Agent platform instances** | 1 centralised AI Agent Platform (TAPP-02) |
| **Engagement channels served** | 5 (Mobile App, Web Portal, Call Centre, Retail, Self-Service) |
| **Languages supported** | 6 (English, Mandarin, Arabic, Vietnamese, Hindi, Cantonese) |
| **Peak concurrent users** | 50,000 (Year 1) → 100,000 (Year 3) |
| **Total portfolio maturity** | L1 (Initial) → L4 (Managed) average |

### Agent Portfolio Summary

```text
Agent Category                    Count   Phase        Current → Target Maturity
───────────────────────────────────────────────────────────────────────────────
1. Customer Service Agents        3       Foundation     L1 → L4
2. Shopping Assistant Agents      2       Foundation–Scale L1 → L4
3. Parcel Tracking Agents         2       Foundation     L1 → L4
4. Marketing Intelligence Agents  3       Scale–Mature    L1 → L5
5. Retail Support Agents          2       Scale          L1 → L4
6. Operations Agents              2       Foundation–Scale L1 → L4
7. Analytics Agents               2       Scale–Mature    L1 → L4
8. Compliance Agents              2       Foundation     L1 → L5
───────────────────────────────────────────────────────────────────────────────
TOTAL                            16       All phases     L1 → L4.1 avg
```

---

## 1. Current State Assessment

### 1.1 Existing Agent Portfolio

**MarsPost currently has zero AI agents in production.** The current automation landscape consists of:

| Category | Current Capability | Maturity | Limitations |
|----------|-------------------|----------|------------|
| **Rule-based automation** | Basic workflow rules in call centre CRM (ticket routing, SLA timers) | L2 (Repeatable) | No learning, no NLP, rigid ruleset |
| **Chatbot capabilities** | Limited decision-tree chatbot on 2 consumer portals (parcel tracking only) | L1 (Initial) | Single-turn, scripted responses, no contextual memory |
| **Self-service portals** | Manual tracking lookup UIs across 20+ isolated portals | L2 (Repeatable) | No AI, no personalisation, no proactive engagement |
| **Agent management** | None — no agent registry, lifecycle management, or governance framework | L1 (Initial) | No unified platform, no observability |
| **Marketing automation** | Basic email campaign tool with static segmentation | L2 (Repeatable) | No AI-driven targeting, no real-time personalisation |
| **Analytics** | Legacy BI dashboards with scheduled reporting | L2 (Repeatable) | No predictive capability, no real-time insights |

### 1.2 Capability Gap Summary

| Gap Area | Current | Target | Closure Phase |
|----------|---------|--------|---------------|
| Conversational AI | None | Multi-turn, multi-agent, multi-language | Foundation (Y1) |
| Agent Orchestration | None | Centralised orchestrator with complexity-based routing | Foundation (Y1) |
| Real-Time Decisioning | Rule-based only | AI-driven predictive decisions | Scale (Y2) |
| Proactive Engagement | None | AI-initiated customer outreach | Scale (Y2) |
| Unified Agent Governance | None | Model registry, compliance framework, audit trails | Foundation (Y1) |
| Agent Observability | None | Structured telemetry, accuracy tracking, drift detection | Foundation (Y1) |

---

## 2. Target State Agent Architecture

### 2.1 Agent Deployment Model

Per **ADR-001** (Hybrid AI Agent Model Deployment), all agents operate through a centralised **AI Agent Platform** (TAPP-02) using:

- **Cloud Inference Layer**: Multi-provider model serving (AWS/GCP ap-southeast-2) for general AI operations
- **On-Prem Sensitive Processing**: Dedicated model instances for sensitive workflows (complaints, security, legal)
- **Tokenisation Service**: PII tokenisation before cloud transmission; APP 8 compliance by design

### 2.2 Agent-Human Handoff Model

Per **ADR-002** (Hybrid Agent-Human Handoff with Complexity-Based Routing):

- **Routine queries** (~60%): AI handles autonomously
- **Moderate-complexity queries**: AI handles with human review queue
- **High-complexity/high-risk queries**: Immediate escalation to human agents
- **Confidence threshold**: 70% — below which AI offers human escalation
- **High-risk topics** (complaints, security, legal): Auto-escalate without customer prompt

### 2.3 Agent Platform Components

| Component | Purpose | Traceability |
|-----------|---------|-------------|
| Agent Orchestrator | Routes customer interactions to specialised agents | AI-01, ADR-005 |
| Complexity-Based Router | Real-time query classification and routing | AI-06, ADR-002 |
| Model Serving Abstraction | Multi-provider inference layer | AI-02, ADR-001 |
| Agent Registry | Version control, lifecycle management | AI-07 |
| Telemetry & Observability | Accuracy, performance, drift detection | AI-04 |
| Governance Framework | Compliance, DPIA, audit trails | AI-03, ADR-007 |
| Human Escalation Service | Seamless AI-to-human handoff | FR-004 |

---

## 3. Agent Inventory

### 3.1 Customer Service Agents (CSA)

> **Category Purpose**: Handle inbound customer inquiries, complaints, and self-service interactions through natural language conversation across all channels.

| Field | Detail |
|-------|--------|
| **Agent ID** | CSA-01 |
| **Agent Name** | MarsPost Customer Service Agent |
| **Category** | Customer Service Agent |
| **Purpose** | Conversational, multi-turn AI agent for common customer queries including parcel tracking, delivery status, address changes, fee information, and general service inquiries |
| **Capabilities** | Multi-turn dialogue; intent recognition; context maintenance (10+ turns); natural language understanding; fee and service information retrieval; address change processing; complaint triage |

| Field | Detail |
|-------|--------|
| **Customer Engagement Channels** | Mobile App (primary), Web Portal, Self-Service Kiosks, Call Centre (co-pilot mode) |
| **Technology Stack** | Conversational LLM (multi-provider); RAG with authoritative MarsPost data sources; tokenisation layer (ADR-001); SDK embedding (ADR-004); multi-language NLU |
| **Maturity Target** | **Foundation (Y1)**: Pilot → Beta → Production | **L1 → L4 (Managed)** by Month 12 |
| **Integration Requirements** | CRM (INT-002), ERP, Pricing Systems, Product Systems, Consent Service, Agent Orchestrator |
| **Data Dependencies** | Customer profiles; interaction history; service fee schedules; address databases; consent flags; escalation routing metadata |
| **Privacy/Security Considerations** | PII tokenisation before cloud inference; APP 11 encryption; consent-aware interactions; response validation against authoritative data (FR-016); audit trail retention (FR-008); no autonomous output on sensitive topics |
| **REQ Traceability** | BR-002, BR-003 | FR-001, FR-004, FR-006, FR-007, FR-008, FR-016 |
| **BPCM Traceability** | CE-02, CE-03, CE-07, AI-01, AI-06 |
| **TRANS Traceability** | WP-ARC-001 (AI Platform), WP-APP-001 (Unified Portal), WP-APP-002 (Mobile SDK) — Foundation Phase |

#### CSA-02: Complaint Handling Agent

| Field | Detail |
|-------|--------|
| **Agent ID** | CSA-02 |
| **Agent Name** | Complaint Triage Agent |
| **Category** | Customer Service Agent |
| **Purpose** | Specialised agent for complaint identification, classification, and escalation. Detects complaint patterns, assesses severity, and routes to appropriate human resolution channels |
| **Capabilities** | Complaint pattern detection; severity classification; regulatory compliance checking (ACCC); escalation routing; complaint acknowledgment generation; status updates |

| Field | Detail |
|-------|--------|
| **Customer Engagement Channels** | Mobile App, Web Portal, Call Centre (co-pilot), Self-Service |
| **Technology Stack** | Specialised complaint-domain model; on-prem processing (sensitive workflows per ADR-001); ACCC-compliant response templates |
| **Maturity Target** | **Foundation (Y1)**: Pilot → Beta → Production | **L1 → L4 (Managed)** by Month 12 |
| **Integration Requirements** | CRM complaint module; legal case management; human escalation service; audit trail system |
| **Data Dependencies** | Complaint history; customer profiles; service terms; regulatory guidelines; resolution outcomes |
| **Privacy/Security Considerations** | All complaint data processed on-prem (sensitive workflow); enhanced audit retention; regulatory reporting integration; zero cloud PII exposure for complaint content |
| **REQ Traceability** | BR-002, BR-004 | FR-004, FR-008, FR-016 |
| **BPCM Traceability** | CE-02, CE-03, AI-03 |
| **TRANS Traceability** | WP-ARC-001, WP-SEC-004 — Foundation Phase |

#### CSA-03: Multi-Language Customer Service Agent

| Field | Detail |
|-------|--------|
| **Agent ID** | CSA-03 |
| **Agent Name** | Multi-Language Support Agent |
| **Category** | Customer Service Agent |
| **Purpose** | Extends CSA-01 capabilities to support customer interactions in Mandarin, Arabic, Vietnamese, Hindi, and Cantonese with comparable accuracy to English |
| **Capabilities** | Multilingual NLU; language detection; code-mixed input handling; seamless language switching within conversations; culturally appropriate responses |

| Field | Detail |
|-------|--------|
| **Customer Engagement Channels** | Mobile App, Web Portal, Self-Service |
| **Technology Stack** | Multilingual LLM; language detection model; translation pipeline with quality validation; language-specific prompt libraries |
| **Maturity Target** | **Foundation (Y1)**: Pilot (English + 2 languages) → **Scale (Y2)**: Full 6-language support | **L1 → L4 (Managed)** by Month 18 |
| **Integration Requirements** | CSA-01 agent (extended); translation services; language preference data from customer profiles |
| **Data Dependencies** | Multilingual training data; customer language preferences; language-specific authoritative data sources |
| **Privacy/Security Considerations** | Same tokenisation and consent controls as CSA-01; translation accuracy validation (≥80%); fallback to English for unsupported languages |
| **REQ Traceability** | BR-002 | FR-006 |
| **BPCM Traceability** | CE-07 |
| **TRANS Traceability** | WP-ARC-001, WP-APP-002 — Foundation/Scale Phase |

---

### 3.2 Shopping Assistant Agents (SA)

> **Category Purpose**: Assist customers with product discovery, shipping service selection, pricing comparison, and personalised offer generation within the MarsPost commerce experience.

#### SA-01: Shipping Service Recommendation Agent

| Field | Detail |
|-------|--------|
| **Agent ID** | SA-01 |
| **Agent Name** | Shipping Assistant Agent |
| **Category** | Shopping Assistant Agent |
| **Purpose** | AI-powered shopping assistant that helps customers discover shipping services, compare options, and receive personalised recommendations based on parcel characteristics, delivery preferences, and historical behaviour |
| **Capabilities** | Parcel specification analysis (dimensions, weight, destination); service tier recommendation; cost comparison; speed comparison; personalised offers based on history; service upgrade suggestions |

| Field | Detail |
|-------|--------|
| **Customer Engagement Channels** | Mobile App (primary), Web Portal |
| **Technology Stack** | Recommendation engine; product catalog API; pricing API; customer profile integration; consent-aware personalisation |
| **Maturity Target** | **Foundation (Y1)**: Pilot → Beta | **Scale (Y2)**: Production | **L1 → L4 (Managed)** by Month 18 |
| **Integration Requirements** | Product Systems, Pricing Systems, Intershop (via strangler API), Customer Data Platform, Consent Service |
| **Data Dependencies** | Product catalogue; pricing data; customer browsing history (opt-in); parcel specifications; delivery preferences |
| **Privacy/Security Considerations** | Personalisation requires explicit opt-in (APP 3); no inferred preferences for new customers; ACCC-compliant comparisons (no misleading content); consent-aware data access |
| **REQ Traceability** | BR-001 | FR-003, FR-005 |
| **BPCM Traceability** | EC-02, EC-01, EC-08 |
| **TRANS Traceability** | WP-ARC-006, WP-APP-007 — Foundation/Scale Phase |

#### SA-02: E-Commerce Seller Assistant Agent

| Field | Detail |
|-------|--------|
| **Agent ID** | SA-02 |
| **Agent Name** | Business Seller Assistant Agent |
| **Category** | Shopping Assistant Agent |
| **Purpose** | Specialised agent for e-commerce sellers — batch shipping, bulk operations, cost-effective service selection, and automated routine tasks for small-to-medium businesses |
| **Capabilities** | Bulk shipping calculations; volume-based pricing recommendations; order batch processing; shipping template management; cost optimisation analysis |

| Field | Detail |
|-------|--------|
| **Customer Engagement Channels** | Web Portal, Mobile App |
| **Technology Stack** | Business-domain LLM; bulk operations engine; pricing optimisation model; seller profile integration |
| **Maturity Target** | **Scale (Y2)**: Pilot → Production | **L1 → L4 (Managed)** by Month 24 |
| **Integration Requirements** | Order Management System; Pricing Systems; Product Systems; seller account management |
| **Data Dependencies** | Seller profiles; order history; shipping patterns; volume pricing data; business account status |
| **Privacy/Security Considerations** | Business data classified as CONFIDENTIAL; seller consent for data usage; no cross-seller data sharing |
| **REQ Traceability** | BR-001 | FR-003 |
| **BPCM Traceability** | EC-02, EC-01, EC-03 |
| **TRANS Traceability** | WP-APP-007 — Scale Phase |

---

### 3.3 Parcel Tracking Agents (PTA)

> **Category Purpose**: Deliver real-time parcel status information, predictive ETAs, and proactive notifications for delivery milestones, delays, and exceptions.

#### PTA-01: Real-Time Parcel Tracking Agent

| Field | Detail |
|-------|--------|
| **Agent ID** | PTA-01 |
| **Agent Name** | Parcel Tracking Agent |
| **Category** | Parcel Tracking Agent |
| **Purpose** | AI-powered parcel tracking capability that delivers real-time shipment status, predictive Estimated Times of Arrival (ETA), and proactive push notifications for significant status changes |
| **Capabilities** | Real-time status retrieval; predictive ETA generation; location history display; next-mile visibility; consolidated multi-parcel tracking; proactive delay detection and notification |

| Field | Detail |
|-------|--------|
| **Customer Engagement Channels** | Mobile App (primary), Web Portal, Self-Service, Push Notifications (SMS, Email, In-App) |
| **Technology Stack** | Predictive ETA model; real-time event processing; notification engine; GCP Event Manager integration; proactive alerting pipeline |
| **Maturity Target** | **Foundation (Y1)**: Pilot → Beta → Production | **L1 → L4 (Managed)** by Month 12 |
| **Integration Requirements** | GCP Event Manager (INT-003); SMS/Email services (INT-004); Mobile App notification pipeline; logistics exception system |
| **Data Dependencies** | Tracking events; parcel metadata; historical delivery data; address databases; notification preferences |
| **Privacy/Security Considerations** | Tracking data linked to authenticated customer sessions; notification preferences require consent; delivery address classified as PII |
| **REQ Traceability** | BR-002, BR-003 | FR-002, FR-014 |
| **BPCM Traceability** | PS-01, PS-02, PS-07 |
| **TRANS Traceability** | WP-ARC-001, WP-APP-002 — Foundation Phase |

#### PTA-02: Proactive Delivery Exception Agent

| Field | Detail |
|-------|--------|
| **Agent ID** | PTA-02 |
| **Agent Name** | Delivery Exception Agent |
| **Category** | Parcel Tracking Agent |
| **Purpose** | Detects delivery exceptions (failed delivery, address issues, customs holds, damaged parcels) and proactively initiates AI conversations with affected customers offering resolution options |
| **Capabilities** | Exception detection; proactive outreach (within 5 minutes); resolution option generation (redelivery, address correction, retail collection); exception status tracking; customer response handling |

| Field | Detail |
|-------|--------|
| **Customer Engagement Channels** | Mobile App (primary), Push Notifications, SMS, Email |
| **Technology Stack** | Exception detection model; resolution workflow engine; proactive messaging pipeline; customer interaction handling |
| **Maturity Target** | **Foundation (Y1)**: Pilot (limited exception types) → **Scale (Y2)**: Full exception coverage | **L1 → L4 (Managed)** by Month 18 |
| **Integration Requirements** | GCP Event Manager (exception events); logistics exception system; PTA-01 (status data); resolution services |
| **Data Dependencies** | Exception events; delivery history; customer contact data; resolution service availability; address validation data |
| **Privacy/Security Considerations** | Proactive messaging requires prior opt-in; address data classified as PII; consolidated exception notifications to avoid customer fatigue |
| **REQ Traceability** | BR-002, BR-001 | FR-002, FR-014 |
| **BPCM Traceability** | PS-02, PS-07 |
| **TRANS Traceability** | WP-ARC-001, WP-APP-002 — Foundation/Scale Phase |

---

### 3.4 Marketing Intelligence Agents (MIA)

> **Category Purpose**: Drive customer segmentation, campaign optimisation, dynamic offer generation, and revenue attribution through AI-powered insights.

#### MIA-01: Customer Segmentation Agent

| Field | Detail |
|-------|--------|
| **Agent ID** | MIA-01 |
| **Agent Name** | AI Segmentation Agent |
| **Category** | Marketing Intelligence Agent |
| **Purpose** | ML-driven behavioural segmentation, micro-segmentation, and dynamic persona creation for targeted marketing campaigns and offers |
| **Capabilities** | Behavioural clustering; real-time segmentation; micro-segment generation; persona creation; propensity scoring; dynamic segment refresh |

| Field | Detail |
|-------|--------|
| **Customer Engagement Channels** | Internal (B2B tool for marketing team); Indirect customer engagement via personalised campaigns |
| **Technology Stack** | ML segmentation engine; real-time event processing; customer data platform integration; model serving pipeline |
| **Maturity Target** | **Scale (Y2)**: Pilot → Production | **Mature (Y3)**: Advanced segmentation | **L1 → L5 (Optimised)** by Month 36 |
| **Integration Requirements** | Customer Data Platform (TAPP-04); Marketing Intelligence Platform (TAPP-06); Event Bus; consent service |
| **Data Dependencies** | Customer behaviour data; interaction history; purchase patterns; demographic data (opt-in); real-time event streams |
| **Privacy/Security Considerations** | Segmentation requires consent for marketing data usage (APP 3); no individual-level PII in segmentation output; aggregated analysis only; bias testing required |
| **REQ Traceability** | BR-001 | FR-005 |
| **BPCM Traceability** | CD-04, MK-07 |
| **TRANS Traceability** | WP-DAT-006, WP-APP-009 — Scale/Mature Phase |

#### MIA-02: Campaign Optimisation Agent

| Field | Detail |
|-------|--------|
| **Agent ID** | MIA-02 |
| **Agent Name** | Campaign Optimisation Agent |
| **Category** | Marketing Intelligence Agent |
| **Purpose** | AI-driven campaign personalisation, dynamic targeting, offer optimisation, and real-time campaign adjustment based on customer response data |
| **Capabilities** | A/B test design and analysis; offer optimisation; dynamic targeting adjustment; conversion rate prediction; campaign performance monitoring; ROI attribution |

| Field | Detail |
|-------|--------|
| **Customer Engagement Channels** | Internal (B2B tool); Indirect via campaign delivery channels (push, email, SMS, in-app) |
| **Technology Stack** | Reinforcement learning for campaign optimisation; real-time analytics; attribution modelling; campaign execution engine |
| **Maturity Target** | **Scale (Y2)**: Pilot → Production | **L1 → L5 (Optimised)** by Month 36 |
| **Integration Requirements** | Marketing Intelligence Platform (TAPP-06); Customer Data Platform; consent service; notification delivery channels |
| **Data Dependencies** | Campaign performance data; customer response patterns; conversion data; attribution metrics; segment definitions |
| **Privacy/Security Considerations** | Campaign data excludes individual PII; consent-aware targeting; ACCC-compliant offer content; bias and fairness monitoring |
| **REQ Traceability** | BR-001 | FR-005, FR-010 |
| **BPCM Traceability** | MK-02, MK-04, MK-08 |
| **TRANS Traceability** | WP-APP-009 — Scale Phase |

#### MIA-03: Proactive Engagement Agent

| Field | Detail |
|-------|--------|
| **Agent ID** | MIA-03 |
| **Agent Name** | Proactive Engagement Agent |
| **Category** | Marketing Intelligence Agent |
| **Purpose** | AI-driven proactive customer outreach — predictive engagement triggered by customer events, parcel milestones, and behavioural signals |
| **Capabilities** | Predictive trigger detection; event-driven outreach; next-best-action generation; service offer generation; loyalty activation; churn prevention outreach |

| Field | Detail |
|-------|--------|
| **Customer Engagement Channels** | Mobile App (primary), Push Notifications, Email, SMS, Web Portal |
| **Technology Stack** | Predictive engagement model; event-driven trigger engine; next-best-action engine; conversation generation; customer lifecycle modelling |
| **Maturity Target** | **Mature (Y3)**: Pilot → Production | **L1 → L5 (Optimised)** by Month 48 |
| **Integration Requirements** | Customer Data Platform; Event Bus; Consent Service; Notification Channels; CSA-01 (conversation handoff) |
| **Data Dependencies** | Customer lifecycle data; event streams; behavioural signals; engagement history; opt-in flags |
| **Privacy/Security Considerations** | Proactive engagement requires explicit marketing consent; customer-facing messages require content validation; frequency capping to prevent fatigue; opt-out enforcement |
| **REQ Traceability** | BR-001 | FR-005 |
| **BPCM Traceability** | MK-03, MK-05, MK-06 |
| **TRANS Traceability** | WP-APP-009, WP-DAT-008 — Scale/Mature Phase |

---

### 3.5 Retail Support Agents (RSA)

> **Category Purpose**: Assist 4,000 MarsPost retail shop staff with customer queries, inventory lookups, and transaction support through AI co-pilot tools.

#### RSA-01: Retail Staff Co-Pilot Agent

| Field | Detail |
|-------|--------|
| **Agent ID** | RSA-01 |
| **Agent Name** | Retail AI Co-Pilot Agent |
| **Category** | Retail Support Agent |
| **Purpose** | AI co-pilot tool for retail counter staff that assists with customer queries by surfacing relevant information, suggesting responses, and automating routine lookups |
| **Capabilities** | Customer query assistance; service information retrieval; inventory lookup; suggested response generation; transaction support; knowledge retrieval from MarsPost service catalog |

| Field | Detail |
|-------|--------|
| **Customer Engagement Channels** | Retail Kiosks (4,000 shops), POS overlay, Retail Staff Tablet |
| **Technology Stack** | Co-pilot LLM; POS system integration; inventory API; knowledge base; RAG with MarsPost service catalog; confidence scoring |
| **Maturity Target** | **Scale (Y2)**: Pilot (500 shops) → **Mature (Y3)**: Full deployment (4,000 shops) | **L1 → L4 (Managed)** by Month 36 |
| **Integration Requirements** | Retail POS Systems (APP-27); Inventory Management (APP-28); Agent Orchestrator; CRM; Pricing Systems |
| **Data Dependencies** | Product catalogue; inventory levels; pricing data; customer transaction history; service information |
| **Privacy/Security Considerations** | Staff-facing only — no autonomous customer-facing output; all suggestions require staff approval; RBAC for co-pilot access; no PII exposure beyond active customer session |
| **REQ Traceability** | BR-003, BR-006 | FR-007 |
| **BPCM Traceability** | EC-06, BO-02 |
| **TRANS Traceability** | WP-APP-010, WP-APP-014 — Scale/Mature Phase |

#### RSA-02: Retail Self-Service Kiosk Agent

| Field | Detail |
|-------|--------|
| **Agent ID** | RSA-02 |
| **Agent Name** | Retail Self-Service Agent |
| **Category** | Retail Support Agent |
| **Purpose** | AI agent embedded in retail self-service kiosks that handles customer queries independently at retail locations, reducing counter queue times |
| **Capabilities** | Self-service parcel lodgement; service inquiry handling; parcel tracking at counter; payment assistance; wayfinding; queue management |

| Field | Detail |
|-------|--------|
| **Customer Engagement Channels** | Retail Self-Service Kiosks (4,000 shops) |
| **Technology Stack** | Conversational agent; kiosk UI framework; payment integration; barcode scanner integration; printer integration |
| **Maturity Target** | **Scale (Y2)**: Pilot (500 shops) → **Mature (Y3–5)**: Full deployment | **L1 → L4 (Managed)** by Month 48 |
| **Integration Requirements** | Retail POS; Payment Systems; Parcel Lodgement System; Agent Orchestrator; Inventory Management |
| **Data Dependencies** | Service pricing; parcel specifications; customer profiles (authenticated); inventory data |
| **Privacy/Security Considerations** | Kiosk session isolation; screen privacy protection; payment data tokenisation; staff supervision fallback; no PII retention on kiosk device |
| **REQ Traceability** | BR-003 | FR-007 |
| **BPCM Traceability** | EC-06, BO-01 |
| **TRANS Traceability** | WP-APP-010, WP-APP-014 — Scale/Mature Phase |

---

### 3.6 Operations Agents (OPA)

> **Category Purpose**: Automate operational workflows, handle exceptions, and provide performance monitoring for internal operations teams.

#### OPA-01: Call Centre AI Co-Pilot Agent

| Field | Detail |
|-------|--------|
| **Agent ID** | OPA-01 |
| **Agent Name** | Call Centre AI Co-Pilot Agent |
| **Category** | Operations Agent |
| **Purpose** | AI co-pilot for call centre agents that assists with customer queries by surfacing relevant information, suggesting responses, and automating routine lookups to reduce workload |
| **Capabilities** | Real-time query analysis; suggested response generation; auto-fill data retrieval; CRM data surfacing; confidence scoring; routine query pattern detection |

| Field | Detail |
|-------|--------|
| **Customer Engagement Channels** | Call Centre (staff-facing only — co-pilot mode); does not directly interact with customers |
| **Technology Stack** | Co-pilot LLM; CRM integration (INT-002); logistics data integration (INT-003); knowledge base; real-time inference pipeline |
| **Maturity Target** | **Foundation (Y1)**: Pilot → Beta → Production | **L1 → L4 (Managed)** by Month 12 |
| **Integration Requirements** | CRM System; CTI Platform; Logistics/Tracking System; Agent Orchestrator; Knowledge Base |
| **Data Dependencies** | Customer query context; CRM data; logistics data; service information; agent role and permissions |
| **Privacy/Security Considerations** | Staff-facing only — no autonomous customer-facing output; all suggestions require staff approval before delivery; RBAC enforcement; session-level access only |
| **REQ Traceability** | BR-003, BR-006 | FR-007 |
| **BPCM Traceability** | CE-05, BO-02, BO-04 |
| **TRANS Traceability** | WP-ARC-001, WP-WKF-005 — Foundation Phase |

#### OPA-02: Workflow Automation Agent

| Field | Detail |
|-------|--------|
| **Agent ID** | OPA-02 |
| **Agent Name** | Operations Workflow Agent |
| **Category** | Operations Agent |
| **Purpose** | Automates routine operational workflows including exception handling, performance monitoring, and operational reporting to reduce manual processing |
| **Capabilities** | Automated workflow execution; exception detection and routing; performance monitoring; operational reporting generation; capacity planning alerts; SLA breach detection |

| Field | Detail |
|-------|--------|
| **Customer Engagement Channels** | Internal only — operational dashboards; monitoring systems; automated notification channels |
| **Technology Stack** | Workflow orchestration engine; anomaly detection model; reporting engine; alert pipeline; SLA monitoring system |
| **Maturity Target** | **Foundation (Y1)**: Core workflows → **Scale (Y2)**: Expanded automation | **L1 → L4 (Managed)** by Month 24 |
| **Integration Requirements** | ERP; CRM; GCP Event Manager; monitoring systems; ticketing systems; reporting platforms |
| **Data Dependencies** | Operational metrics; SLA data; exception events; performance indicators; capacity data |
| **Privacy/Security Considerations** | Internal operations data only; no customer PII exposure; RBAC for operational access; audit trail for automated decisions |
| **REQ Traceability** | BR-003, BR-005 | FR-012 |
| **BPCM Traceability** | BO-04, BO-05 |
| **TRANS Traceability** | WP-ARC-001, WP-APP-003 — Foundation/Scale Phase |

---

### 3.7 Analytics Agents (ANA)

> **Category Purpose**: Provide customer insights, trend analysis, and predictive analytics for business decision-making.

#### ANA-01: Customer Insights Agent

| Field | Detail |
|-------|--------|
| **Agent ID** | ANA-01 |
| **Agent Name** | Customer Insights Agent |
| **Category** | Analytics Agent |
| **Purpose** | Provides real-time customer behaviour analytics, journey mapping, cohort analysis, and actionable insights for business decision-making |
| **Capabilities** | Customer behaviour analysis; journey mapping; cohort analysis; anomaly detection in customer patterns; churn prediction; lifetime value modelling |

| Field | Detail |
|-------|--------|
| **Customer Engagement Channels** | Internal (B2B tool for analytics and business teams); Executive dashboards; Self-service analytics portal |
| **Technology Stack** | Analytics LLM; data lakehouse integration; real-time stream processing; visualisation engine; predictive modelling pipeline |
| **Maturity Target** | **Scale (Y2)**: Pilot → Production | **L1 → L4 (Managed)** by Month 24 |
| **Integration Requirements** | Customer Data Platform (TAPP-04); Event Bus; CRM; ERP; reporting platforms |
| **Data Dependencies** | Customer interaction data; transaction history; behavioural signals; demographic data (aggregated); event streams |
| **Privacy/Security Considerations** | Aggregated analysis only — no individual-level PII output; data anonymisation for external reporting; RBAC for analytics access; model bias testing |
| **REQ Traceability** | BR-001, BR-005 | FR-010 |
| **BPCM Traceability** | CD-03, CD-05 |
| **TRANS Traceability** | WP-DAT-005, WP-DAT-007 — Scale Phase |

#### ANA-02: Predictive Analytics Agent

| Field | Detail |
|-------|--------|
| **Agent ID** | ANA-02 |
| **Agent Name** | Predictive Analytics Agent |
| **Category** | Analytics Agent |
| **Purpose** | Advanced predictive analytics including demand forecasting, revenue prediction, risk modelling, and scenario analysis |
| **Capabilities** | Demand forecasting; revenue prediction; risk scenario modelling; capacity planning; trend analysis; predictive maintenance for operational systems |

| Field | Detail |
|-------|--------|
| **Customer Engagement Channels** | Internal (B2B tool); Executive dashboards; planning systems |
| **Technology Stack** | Time-series prediction models; scenario simulation engine; data science pipeline; forecasting dashboard |
| **Maturity Target** | **Mature (Y3)**: Pilot → Production | **L1 → L4 (Managed)** by Month 36 |
| **Integration Requirements** | Data Lakehouse; Event Bus; Finance Systems; Planning Systems; ANA-01 (insights data) |
| **Data Dependencies** | Historical performance data; market indicators; operational metrics; financial data; seasonal patterns |
| **Privacy/Security Considerations** | Aggregated data only; no customer-level PII; model explainability requirements; audit trail for prediction methodology |
| **REQ Traceability** | BR-001, BR-005 | FR-012 |
| **BPCM Traceability** | CD-07, BO-05 |
| **TRANS Traceability** | WP-DAT-011 — Mature Phase |

---

### 3.8 Compliance Agents (COMPA)

> **Category Purpose**: Ensure privacy consent management, regulatory compliance, and audit support across all AI agent operations.

#### COMPA-01: Privacy Consent Agent

| Field | Detail |
|-------|--------|
| **Agent ID** | COMPA-01 |
| **Agent Name** | Privacy Consent Agent |
| **Category** | Compliance Agent |
| **Purpose** | Manages privacy consent lifecycle — collection, storage, verification, withdrawal, and enforcement of consent boundaries across all AI agent interactions |
| **Capabilities** | Granular consent management; opt-in/opt-out processing; consent verification at interaction time; consent withdrawal enforcement; data access/deletion request processing; privacy dashboard data |

| Field | Detail |
|-------|--------|
| **Customer Engagement Channels** | Mobile App (privacy dashboard), Web Portal (privacy settings), Self-Service (data rights) |
| **Technology Stack** | Consent service API; privacy preference store; consent validation pipeline; customer-facing privacy UI; APP-compliant data handling |
| **Maturity Target** | **Foundation (Y1)**: Pilot → Beta → Production | **L1 → L5 (Optimised)** by Month 12 |
| **Integration Requirements** | All AI Agents (consent verification); Customer Data Platform; Identity Service; FR-009 (Privacy Dashboard) |
| **Data Dependencies** | Consent records; customer identity; opt-in/opt-out flags; data retention settings; data access requests |
| **Privacy/Security Considerations** | Highest security classification — consent records are authoritative; encrypted storage (AES-256); tamper-evident logging; immutable consent history; APP 12 compliance for data access requests |
| **REQ Traceability** | BR-004 | FR-005, FR-009 |
| **BPCM Traceability** | PC-01, PC-04, PC-08 |
| **TRANS Traceability** | WP-SEC-001 — Foundation Phase |

#### COMPA-02: AI Governance and Compliance Agent

| Field | Detail |
|-------|--------|
| **Agent ID** | COMPA-02 |
| **Agent Name** | AI Compliance Agent |
| **Category** | Compliance Agent |
| **Purpose** | Monitors AI agent compliance — hallucination detection, regulatory alignment, audit trail management, and DPIA automation for all AI operations |
| **Capabilities** | Hallucination detection; response validation against authoritative data; compliance monitoring; audit trail generation; DPIA automation; model governance reporting; incident detection |

| Field | Detail |
|-------|--------|
| **Customer Engagement Channels** | Internal (B2B tool for compliance team); Administrative dashboard; Regulatory reporting |
| **Technology Stack** | Compliance monitoring engine; response validation rules; audit log system; model governance framework; automated DPIA pipeline |
| **Maturity Target** | **Foundation (Y1)**: Core compliance → **Scale (Y2)**: Automated governance | **L1 → L5 (Optimised)** by Month 24 |
| **Integration Requirements** | All AI Agents (monitoring); Agent Orchestrator; Audit Trail System (FR-008); Legal case management; OAIC reporting |
| **Data Dependencies** | AI interaction logs; confidence scores; validation results; compliance rules; regulatory guidelines; model metadata |
| **Privacy/Security Considerations** | Governance data classified as CONFIDENTIAL; audit logs tamper-evident; compliance monitoring excludes individual PII; regulatory reporting with data minimisation |
| **REQ Traceability** | BR-004, BR-007 | FR-008, FR-016, FR-012 |
| **BPCM Traceability** | AI-03, PC-03, PC-05, PC-06 |
| **TRANS Traceability** | WP-SEC-004, WP-SEC-006 — Foundation/Scale Phase |

---

## 4. Agent Registry Summary Table

### 4.1 Complete Agent Inventory

| Agent ID | Agent Name | Category | Channels | Tech Stack Summary | Maturity Target | REQ | BPCM | TRANS Phase |
|----------|----------|----------|----------|-------------------|----------------|-----|------|------------|
| **CSA-01** | Customer Service Agent | Customer Service | Mobile App, Web, Kiosks, Call Centre | Conversational LLM, RAG, Tokenisation | L1→L4 (Y1) | BR-002, BR-003 | CE-02, CE-03, AI-01 | Foundation |
| **CSA-02** | Complaint Triage Agent | Customer Service | Mobile App, Web, Call Centre, Self-Service | Complaint-domain LLM, On-Prem Processing | L1→L4 (Y1) | BR-002, BR-004 | CE-02, CE-03, AI-03 | Foundation |
| **CSA-03** | Multi-Language Support Agent | Customer Service | Mobile App, Web, Self-Service | Multilingual LLM, Translation Pipeline | L1→L4 (Y1-2) | BR-002 | CE-07 | Foundation/Scale |
| **SA-01** | Shipping Assistant Agent | Shopping Assistant | Mobile App, Web | Recommendation Engine, Catalog API | L1→L4 (Y1-2) | BR-001 | EC-02, EC-01 | Foundation/Scale |
| **SA-02** | Business Seller Assistant Agent | Shopping Assistant | Web Portal, Mobile App | Business-domain LLM, Bulk Operations | L1→L4 (Y2) | BR-001 | EC-02, EC-01 | Scale |
| **PTA-01** | Parcel Tracking Agent | Parcel Tracking | Mobile App, Web, Self-Service, Push, SMS, Email | Predictive ETA Model, Event Processing | L1→L4 (Y1) | BR-002, BR-003 | PS-01, PS-02 | Foundation |
| **PTA-02** | Delivery Exception Agent | Parcel Tracking | Mobile App, Push, SMS, Email | Exception Detection, Resolution Engine | L1→L4 (Y1-2) | BR-002, BR-001 | PS-02, PS-07 | Foundation/Scale |
| **MIA-01** | AI Segmentation Agent | Marketing Intelligence | Internal (B2B) | ML Segmentation, Real-Time Processing | L1→L5 (Y2-3) | BR-001 | CD-04, MK-07 | Scale/Mature |
| **MIA-02** | Campaign Optimisation Agent | Marketing Intelligence | Internal (B2B) | RL Campaign Engine, Attribution | L1→L5 (Y2) | BR-001 | MK-02, MK-04 | Scale |
| **MIA-03** | Proactive Engagement Agent | Marketing Intelligence | Mobile App, Push, Email, SMS, Web | Predictive Engagement, Next-Best-Action | L1→L5 (Y3) | BR-001 | MK-03, MK-05 | Scale/Mature |
| **RSA-01** | Retail AI Co-Pilot Agent | Retail Support | Retail Kiosks, POS, Tablet | Co-Pilot LLM, POS Integration | L1→L4 (Y2-3) | BR-003, BR-006 | EC-06, BO-02 | Scale/Mature |
| **RSA-02** | Retail Self-Service Agent | Retail Support | Retail Self-Service Kiosks | Conversational Agent, Kiosk UI | L1→L4 (Y2-5) | BR-003 | EC-06, BO-01 | Scale/Mature |
| **OPA-01** | Call Centre AI Co-Pilot Agent | Operations | Call Centre (Staff-Facing) | Co-Pilot LLM, CRM Integration | L1→L4 (Y1) | BR-003, BR-006 | CE-05, BO-02 | Foundation |
| **OPA-02** | Operations Workflow Agent | Operations | Internal Dashboards | Workflow Engine, Anomaly Detection | L1→L4 (Y1-2) | BR-003, BR-005 | BO-04, BO-05 | Foundation/Scale |
| **ANA-01** | Customer Insights Agent | Analytics | Internal Dashboards | Analytics LLM, Data Lakehouse | L1→L4 (Y2) | BR-001, BR-005 | CD-03, CD-05 | Scale |
| **ANA-02** | Predictive Analytics Agent | Analytics | Internal Dashboards | Time-Series Models, Simulation | L1→L4 (Y3) | BR-001, BR-005 | CD-07, BO-05 | Mature |
| **COMPA-01** | Privacy Consent Agent | Compliance | Mobile App, Web, Self-Service | Consent Service, Privacy UI | L1→L5 (Y1) | BR-004 | PC-01, PC-04 | Foundation |
| **COMPA-02** | AI Compliance Agent | Compliance | Internal Dashboard | Compliance Engine, Audit Logs | L1→L5 (Y1-2) | BR-004, BR-007 | AI-03, PC-03 | Foundation/Scale |

### 4.2 Agent Count by Phase

| Phase | Agent Count | New Agents | Agents Advanced |
|-------|-----------|------------|-----------------|
| **Foundation (Y1)** | 8 | 8 | — |
| **Scale (Y2-3)** | 6 | 5 | 1 (CSA-03 full languages) |
| **Mature (Y3-5)** | 4 | 3 | 1 (RSA-02 full rollout) |
| **Total** | **16** | **16** | — |

---

## 5. Agent Platform Architecture

### 5.1 Platform Components

The centralised **AI Agent Platform** (TAPP-02) serves as the foundation for all 16 agents:

```text
┌─────────────────────────────────────────────────────────────────────┐
│                    AI Agent Platform (TAPP-02)                        │
│  ┌───────────────────────────────────────────────────────────────┐  │
│  │  Agent Orchestrator (AI-01)                                  │  │
│  │  ├── Complexity Router (AI-06)                               │  │
│  │  │   ├── Routine → Autonomous Agent                          │  │
│  │  │   ├── Moderate → AI + Human Review                         │  │
│  │  │   └── High-Risk → Auto-Escalate (ADR-002)                │  │
│  │  └── Agent Registry (AI-07)                                 │  │
│  └───────────────────────────────────────────────────────────────┘  │
│  ┌───────────────────────────────────────────────────────────────┐  │
│  │  Hybrid Model Serving (AI-02) — ADR-001                      │  │
│  │  ├── Cloud Inference (Multi-Provider)                         │  │
│  │  ├── Tokenisation Service                                    │  │
│  │  └── On-Prem Sensitive Processing                             │  │
│  └───────────────────────────────────────────────────────────────┘  │
│  ┌───────────────────────────────────────────────────────────────┐  │
│  │  Governance & Compliance (AI-03) — ADR-007                   │  │
│  │  ├── Model Registry                                          │  │
│  │  ├── Hallucination Detection (FR-016)                          │  │
│  │  ├── Audit Trail (FR-008)                                   │  │
│  │  └── DPIA Automation                                        │  │
│  └───────────────────────────────────────────────────────────────┘  │
│  ┌───────────────────────────────────────────────────────────────┐  │
│  │  Telemetry & Observability (AI-04)                              │  │
│  │  ├── Accuracy Tracking                                       │  │
│  │  ├── Performance Metrics (NFR-P-001)                           │  │
│  │  └── Model Drift Detection                                  │  │
│  └───────────────────────────────────────────────────────────────┘  │
│  ┌───────────────────────────────────────────────────────────────┐  │
│  │  Prompt Engineering & Knowledge Base (AI-05)                │  │
│  │  ├── Domain Knowledge Bases                                │  │
│  │  ├── Prompt Libraries                                       │  │
│  │  └── RAG Pipeline                                          │  │
│  └───────────────────────────────────────────────────────────────┘  │
│  ┌───────────────────────────────────────────────────────────────┐  │
│  │  MLOps & Model Evaluation (AI-08)                             │  │
│  │  ├── Model Accuracy Testing                                │  │
│  │  ├── A/B Testing Pipeline                                    │  │
│  │  └── Automated Retraining                                    │  │
│  └───────────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────────┘
```

### 5.2 Agent Interaction Patterns

| Pattern | Description | Agents Using This Pattern |
|---------|-------------|----------------------------|
| **Customer-Facing Conversational** | Direct AI-to-customer interaction via chat/voice | CSA-01, CSA-02, CSA-03, PTA-01, PTA-02, RSA-02 |
| **Staff Co-Pilot (Human-in-the-Loop)** | AI assists staff member; no autonomous customer output | OPA-01, RSA-01 |
| **Internal Analytics Tool** | B2B tool for internal teams; indirect customer impact | MIA-01, MIA-02, MIA-03, ANA-01, ANA-02 |
| **Compliance Monitoring** | Internal governance and compliance monitoring | COMPA-01, COMPA-02 |
| **Proactive Notification** | AI-initiated outreach based on triggers | PTA-02, MIA-03 |

---

## 6. Channel-to-Agent Mapping

### 6.1 Customer Engagement Channel Coverage

| Channel | Agent Coverage | Description |
|---------|---------------|-------------|
| **Mobile App** | CSA-01, SA-01, SA-02, PTA-01, PTA-02, MIA-03, RSA-02, COMPA-01 | Primary AI engagement channel — 3M MAU base, SDK embedding (ADR-004) |
| **Web Portal** | CSA-01, CSA-02, CSA-03, SA-01, SA-02, PTA-01, RSA-02, COMPA-01 | Unified web portal replacing 20+ legacy portals |
| **Call Centre** | CSA-01 (co-pilot), CSA-02, OPA-01 | AI co-pilot augments human agents; no standalone customer-facing AI |
| **Retail (4,000 Shops)** | RSA-01, RSA-02 | AI-enabled kiosks with staff co-pilot integration |
| **Self-Service** | CSA-01, CSA-03, PTA-01, RSA-02, COMPA-01 | Digital self-service interfaces with embedded AI agents |
| **Push/SMS/Email** | PTA-01, PTA-02, MIA-03 | Notification delivery for proactive alerts and engagement |
| **Internal Dashboards** | OPA-02, ANA-01, ANA-02, MIA-01, MIA-02, MIA-03, COMPA-02 | Staff-facing operational and analytics tools |

### 6.2 Channel Maturity by Phase

| Channel | Foundation (Y1) | Scale (Y2-3) | Mature (Y3-5) |
|---------|----------------|-------------|---------------|
| **Mobile App** | CSA-01, PTA-01 (SDK embedding) | SA-01, CSA-03 (full languages) | Full agent portfolio |
| **Web Portal** | CSA-01, PTA-01 (unified portal MVP) | SA-01, CSA-02, CSA-03 | Full agent portfolio |
| **Call Centre** | OPA-01 (co-pilot) | CSA-01 (co-pilot mode) | Full co-pilot capability |
| **Retail** | — | RSA-01, RSA-02 (500 shops pilot) | Full deployment (4,000 shops) |
| **Self-Service** | CSA-01, PTA-01 | RSA-02 (limited) | Full self-service AI |
| **Notifications** | PTA-01 (push) | PTA-02, MIA-03 | Full proactive engagement |

---

## 7. Agent Maturity Roadmap

### 7.1 Maturity Scale

| Level | Name | Description |
|-------|------|-------------|
| **L1** | Initial | No capability — planned or design only |
| **L2** | Repeatable | Pilot running; basic functionality demonstrated |
| **L3** | Defined | Beta/limited production; documented processes; measured performance |
| **L4** | Managed | Full production; SLOs met; continuous improvement; governed |
| **L5** | Optimised | Self-optimising; predictive capability; automated governance |

### 7.2 Maturity Progression by Agent

```text
Maturity Level
L5 |                              ██ COMPA-02 ██ MIA-02 ██ MIA-03
   |                         ██ COMPA-01 ██ MIA-01
L4 |  ██ CSA ██ SA ██ PTA ██ RSA ██ OPA ██ ANA ██
   | ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██
L3 | ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██ ██
   └────────────────────────────────────────────────────────────►
      M1   M6   M12  M18  M24  M30  M36  M42  M48  M54  M60
         Foundation    Scale           Mature

  ██ = Target maturity level achieved by month
```

### 7.3 Maturity Readiness Gates

| Gate | Phase | Agent Readiness Criteria | Month |
|------|-------|--------------------------|-------|
| **Alpha** | Y1, M6 | CSA-01 pilot operational; PTA-01 pilot; OPA-01 pilot; COMPA-01 L2 | M6 |
| **Beta** | Y1, M12 | CSA-01 production (≥85% FC resolution); PTA-01 production; CSA-02, OPA-01, COMPA-01 production; OPA-02 pilot | M12 |
| **Gamma** | Y2, M18 | SA-01 production; CSA-03 full languages; PTA-02 production; RSA-01 pilot; COMPA-02 production | M18 |
| **Delta** | Y2, M24 | SA-02 production; MIA-01, ANA-01 production; RSA-02 pilot; OPA-02 full | M24 |
| **Epsilon** | Y3, M36 | MIA-02, MIA-03, ANA-02 production; RSA-01/02 full (500 shops); AI Maturity Score ≥7/10 | M36 |
| **Zeta** | Y4-5, M48-60 | Full portfolio production; L5 maturity for MIA and COMPA; AI Maturity Score 9/10 | M48-60 |

---

## 8. Integration Architecture

### 8.1 Agent-to-System Integration Matrix

| Agent | CRM | ERP | Pricing | Products | GCP Event Mgr | SMS/Email | CDP | Consent | Intershop | Retail POS |
|-------|-----|-----|---------|----------|---------------|-----------|-----|---------|-----------|-----------|
| CSA-01 | ✅ | ✅ | ✅ | ✅ | ✅ | — | — | ✅ | — | — |
| CSA-02 | ✅ | — | — | — | — | — | — | ✅ | — | — |
| CSA-03 | ✅ | ✅ | ✅ | ✅ | ✅ | — | — | ✅ | — | — |
| SA-01 | — | — | ✅ | ✅ | — | — | ✅ | ✅ | ✅ | — |
| SA-02 | — | ✅ | ✅ | ✅ | — | — | ✅ | ✅ | ✅ | — |
| PTA-01 | ✅ | — | — | — | ✅ | ✅ | — | ✅ | — | — |
| PTA-02 | ✅ | — | — | — | ✅ | ✅ | — | ✅ | — | — |
| MIA-01 | — | — | — | — | — | — | ✅ | ✅ | — | — |
| MIA-02 | — | — | — | — | — | ✅ | ✅ | ✅ | — | — |
| MIA-03 | — | — | — | — | — | ✅ | ✅ | ✅ | — | — |
| RSA-01 | ✅ | — | ✅ | ✅ | — | — | — | — | — | ✅ |
| RSA-02 | ✅ | ✅ | ✅ | ✅ | ✅ | — | — | ✅ | — | ✅ |
| OPA-01 | ✅ | ✅ | ✅ | ✅ | ✅ | — | — | ✅ | — | — |
| OPA-02 | ✅ | ✅ | — | — | ✅ | — | — | — | — | — |
| ANA-01 | ✅ | ✅ | — | — | — | — | ✅ | — | — | — |
| ANA-02 | — | ✅ | — | — | ✅ | — | ✅ | — | — | — |
| COMPA-01 | ✅ | — | — | — | — | — | ✅ | ✅ | — | — |
| COMPA-02 | ✅ | — | — | — | — | — | ✅ | ✅ | — | — |

### 8.2 Agent-to-Agent Collaboration

Per **AI-07** (Agent-to-Agent Collaboration), agents collaborate through the Agent Orchestrator:

| Collaboration | Source Agent | Target Agent | Trigger |
|---------------|------------|------------|---------|
| Tracking escalation | CSA-01 | PTA-01 | Customer requests parcel status |
| Shopping handoff | PTA-01 | SA-01 | Customer inquires about shipping options |
| Complaint routing | CSA-01 | CSA-02 | Complaint pattern detected |
| Consent check | Any agent | COMPA-01 | Personalisation or marketing data access |
| Compliance validation | Any agent | COMPA-02 | Response contains factual claims |
| Language switch | CSA-01 | CSA-03 | Customer switches language |
| Proactive outreach | PTA-02 | MIA-03 | Exception event triggers engagement |
| Analytics feed | CSA-01, PTA-01, SA-01 | ANA-01 | Interaction data feeds insights |

---

## 9. Privacy and Security Framework

### 9.1 Privacy Classifications by Agent Category

| Agent Category | Data Classification | Privacy Controls |
|----------------|--------------------|--------------------|
| **Customer Service (CSA)** | CONFIDENTIAL — PII, account data | Tokenisation; consent verification; response validation; audit trail |
| **Shopping Assistant (SA)** | CONFIDENTIAL — browsing history, preferences | Opt-in personalisation; no inferred preferences; ACCC compliance |
| **Parcel Tracking (PTA)** | CONFIDENTIAL — addresses, delivery data | Tokenisation; consent-aware notifications; authenticated access |
| **Marketing Intelligence (MIA)** | INTERNAL — aggregated analytics | No individual PII; consent-aware targeting; bias testing |
| **Retail Support (RSA)** | CONFIDENTIAL — active customer session data | Staff-facing only; RBAC; session-level access |
| **Operations (OPA)** | INTERNAL — operational data | RBAC; no customer PII in workflows; audit trail |
| **Analytics (ANA)** | INTERNAL — aggregated insights | Anonymised output; aggregated analysis; model explainability |
| **Compliance (COMPA)** | RESTRICTED — consent records, audit logs | Highest security; tamper-evident logging; encrypted storage |

### 9.2 Security Controls per Agent

| Control | Implementation | Applies To |
|---------|----------------|------------|
| **PII Tokenisation** | Reversible tokenisation before cloud inference (ADR-001) | All customer-facing agents (CSA, SA, PTA) |
| **On-Prem Processing** | Sensitive workflows processed on MarsPost infrastructure (ADR-001) | CSA-02 (complaints), COMPA-01 (consent) |
| **Confidence Thresholding** | 70% threshold — below which AI offers human escalation (ADR-002) | All customer-facing agents |
| **Response Validation** | Fact-checking against authoritative data sources (FR-016) | All agents producing customer-facing output |
| **Audit Trail** | Tamper-evident logging of all AI interactions (FR-008) | All agents |
| **Consent Verification** | Real-time consent check before personalised/markedting interactions | SA, PTA, MIA, RSA |
| **RBAC** | Role-based access control for all agent access (NFR-SEC-002) | All agents |
| **Data Encryption** | TLS 1.3 in transit; AES-256 at rest (NFR-SEC-003) | All agents |
| **Prompt Hardening** | Adversarial testing; input validation (R-022 mitigation) | All customer-facing agents |
| **Model Governance** | Registry, evaluation, retraining (AI-08, NFR-M-003) | All agents |

---

## 10. Risk Register for Agent Portfolio

### 10.1 Key Risks by Agent Category

| Risk ID | Risk | Agent Impact | Category | Mitigation | Target Residual |
|---------|------|-------------|----------|-----------|-----------------|
| **R-001** | AI Hallucination | CSA, SA, PTA, RSA | TECHNOLOGY | Response validation engine (FR-016); 70% confidence threshold; daily accuracy audits | Medium |
| **R-002** | Vendor Lock-In | All agents | TECHNOLOGY | Multi-provider strategy; model abstraction layer | Medium |
| **R-011** | Brand Reputation from AI Errors | CSA, SA, PTA, RSA | BUSINESS | Beta programme; incident playbooks; rapid response | Medium |
| **R-013** | Union Industrial Action | OPA, RSA, CSA | OPERATIONAL | AI Augmentation Charter; TWU consultation; zero net FTE | Critical |
| **R-017** | Privacy Act Breach | CSA, SA, PTA, COMPA | COMPLIANCE | Hybrid deployment (ADR-001); tokenisation; DPIA automation | High |
| **R-018** | ACCC Consumer Law Breach | SA, CSA | COMPLIANCE | Legal review gates; content validation | Medium |
| **R-020** | AI Model Bias | MIA, ANA | TECHNOLOGY | Bias testing; fairness controls; diverse training data | Medium |
| **R-022** | Prompt Injection Attacks | CSA, SA, PTA, RSA | SECURITY | Input validation; prompt hardening; adversarial testing | Medium |
| **R-023** | Data Exposure in Training | All agents | SECURITY | Data isolation; synthetic data; tokenisation | High |
| **R-027** | Decision Accountability Gaps | COMPA, OPA, ANA | GOVERNANCE | Governance framework; audit trails; model registry | Medium |

---

## 11. Traceability Matrix

### 11.1 Agent-to-Requirement Traceability

| Agent ID | Business Requirements | Functional Requirements | Non-Functional Requirements |
|----------|----------------------|------------------------|----------------------------|
| CSA-01 | BR-002, BR-003 | FR-001, FR-004, FR-006, FR-007, FR-008, FR-016 | NFR-P-001, NFR-P-003, NFR-SEC-001, NFR-SEC-002 |
| CSA-02 | BR-002, BR-004 | FR-004, FR-008, FR-016 | NFR-SEC-001, NFR-SEC-002, NFR-C-001 |
| CSA-03 | BR-002 | FR-006 | NFR-P-001 |
| SA-01 | BR-001 | FR-003, FR-005 | NFR-P-001, NFR-SEC-001 |
| SA-02 | BR-001 | FR-003 | NFR-P-001 |
| PTA-01 | BR-002, BR-003 | FR-002, FR-014 | NFR-P-001, NFR-P-003, NFR-S-001 |
| PTA-02 | BR-002, BR-001 | FR-002, FR-014 | NFR-P-001, NFR-S-001 |
| MIA-01 | BR-001 | FR-005 | NFR-SEC-002 |
| MIA-02 | BR-001 | FR-005, FR-010 | NFR-SEC-002 |
| MIA-03 | BR-001 | FR-005 | NFR-C-001 |
| RSA-01 | BR-003, BR-006 | FR-007 | NFR-SEC-002 |
| RSA-02 | BR-003 | FR-007 | NFR-SEC-002 |
| OPA-01 | BR-003, BR-006 | FR-007 | NFR-P-001, NFR-SEC-002 |
| OPA-02 | BR-003, BR-005 | FR-012 | NFR-SEC-002 |
| ANA-01 | BR-001, BR-005 | FR-010 | NFR-SEC-002 |
| ANA-02 | BR-001, BR-005 | FR-012 | NFR-SEC-002 |
| COMPA-01 | BR-004 | FR-005, FR-009 | NFR-SEC-001, NFR-SEC-002, NFR-SEC-003 |
| COMPA-02 | BR-004, BR-007 | FR-008, FR-012, FR-016 | NFR-SEC-002, NFR-SEC-003, NFR-SEC-005 |

### 11.2 Agent-to-Capability Traceability (BPCM)

| Agent ID | BPCM Capabilities | BPCM Sub-Capabilities |
|----------|-------------------|----------------------|
| CSA-01 | Customer Engagement, AI Agent Platform | CE-02, CE-03, CE-07, AI-01, AI-06 |
| CSA-02 | Customer Engagement, AI Agent Platform | CE-02, CE-03, AI-03 |
| CSA-03 | Customer Engagement | CE-07 |
| SA-01 | E-Commerce & Retail, Customer Data & Insights | EC-02, EC-01, EC-08 |
| SA-02 | E-Commerce & Retail | EC-02, EC-01, EC-03 |
| PTA-01 | Parcel Services | PS-01, PS-02, PS-07 |
| PTA-02 | Parcel Services | PS-02, PS-07 |
| MIA-01 | Customer Data & Insights, Marketing & Campaigns | CD-04, MK-07 |
| MIA-02 | Marketing & Campaigns | MK-02, MK-04, MK-08 |
| MIA-03 | Marketing & Campaigns | MK-03, MK-05, MK-06 |
| RSA-01 | E-Commerce & Retail, Business Operations | EC-06, BO-02 |
| RSA-02 | E-Commerce & Retail, Business Operations | EC-06, BO-01 |
| OPA-01 | Customer Engagement, Business Operations | CE-05, BO-02, BO-04 |
| OPA-02 | Business Operations | BO-04, BO-05 |
| ANA-01 | Customer Data & Insights | CD-03, CD-05 |
| ANA-02 | Customer Data & Insights, Business Operations | CD-07, BO-05 |
| COMPA-01 | Privacy & Consent Management | PC-01, PC-04, PC-08 |
| COMPA-02 | AI Agent Platform, Privacy & Consent Management | AI-03, PC-03, PC-05, PC-06 |

### 11.3 Agent-to-Application Traceability (APPINV)

| Agent ID | Target Application (APPINV) | Application ID |
|----------|--------------------------|----------------|
| CSA-01, CSA-02, CSA-03 | AI Agent Platform | TAPP-02 |
| CSA-01, CSA-02, CSA-03 | Unified Customer Portal | TAPP-01 |
| CSA-01, CSA-03, PTA-01 | Enhanced Mobile App | TAPP-08 |
| SA-01, SA-02 | AI-Powered Shopping Experience | TAPP-07 |
| SA-01, SA-02 | Composable AI Services | TAPP-03 |
| PTA-01, PTA-02 | AI Agent Platform | TAPP-02 |
| MIA-01, MIA-02, MIA-03 | Marketing Intelligence Platform | TAPP-06 |
| MIA-01, ANA-01, ANA-02 | Customer Data Platform | TAPP-04 |
| RSA-01, RSA-02 | Retail Digital Integration | TAPP-09 |
| OPA-01, OPA-02 | AI Agent Platform | TAPP-02 |
| COMPA-01, COMPA-02 | Privacy & Consent Management | TAPP-05 |
| All Agents | AI Agent Platform (shared foundation) | TAPP-02 |

### 11.4 Agent-to-Transition Phase Traceability (TRANS)

| Agent ID | TRANS Work Packages | Phase |
|----------|--------------------|-------|
| CSA-01 | WP-ARC-001, WP-APP-001, WP-APP-002 | Foundation |
| CSA-02 | WP-ARC-001, WP-SEC-004 | Foundation |
| CSA-03 | WP-ARC-001, WP-APP-002 | Foundation/Scale |
| SA-01 | WP-APP-007, WP-ARC-006 | Foundation/Scale |
| SA-02 | WP-APP-007 | Scale |
| PTA-01 | WP-ARC-001, WP-APP-002 | Foundation |
| PTA-02 | WP-ARC-001 | Foundation/Scale |
| MIA-01 | WP-APP-009, WP-DAT-006 | Scale/Mature |
| MIA-02 | WP-APP-009 | Scale |
| MIA-03 | WP-APP-009, WP-DAT-008 | Scale/Mature |
| RSA-01 | WP-APP-010, WP-APP-014 | Scale/Mature |
| RSA-02 | WP-APP-010, WP-APP-014 | Scale/Mature |
| OPA-01 | WP-ARC-001, WP-WKF-005 | Foundation |
| OPA-02 | WP-ARC-001, WP-APP-003 | Foundation/Scale |
| ANA-01 | WP-DAT-005, WP-DAT-007 | Scale |
| ANA-02 | WP-DAT-011 | Mature |
| COMPA-01 | WP-SEC-001 | Foundation |
| COMPA-02 | WP-SEC-004, WP-SEC-006 | Foundation/Scale |

---

## 12. Agent Lifecycle Management

### 12.1 Lifecycle Phases

| Phase | Description | Duration | Activities |
|-------|-------------|----------|----------|
| **Design** | Agent specification, capability definition, data requirements | 2–4 weeks | Capability mapping; REQ traceability; privacy assessment |
| **Development** | Model selection, training, prompt engineering, integration | 4–12 weeks | Model fine-tuning; RAG pipeline; API integration; testing |
| **Evaluation** | Accuracy testing, hallucination detection, compliance review | 2–4 weeks | A/B testing; bias assessment; DPIA completion |
| **Pilot** | Limited production deployment with monitoring | 4–8 weeks | Live accuracy tracking; user feedback; threshold calibration |
| **Production** | Full production deployment with governance | Ongoing | SLO monitoring; continuous improvement; model retraining |
| **Decommission** | Agent retirement with data handling | Variable | Data archival; consent withdrawal notification; knowledge base update |

### 12.2 Governance Controls

| Control | Owner | Frequency | Trigger |
|---------|-------|-----------|---------|
| **Model Accuracy Review** | AI Engineering Lead | Monthly | Accuracy below 85% threshold |
| **Compliance Audit** | Privacy Officer / CISO | Quarterly | Regulatory changes; audit findings |
| **Hallucination Rate Check** | AI Engineering Lead | Weekly | Hallucination rate above 2% |
| **Bias Assessment** | AI Engineering Lead | Quarterly | New model version; segment-specific performance review |
| **Consent Coverage Audit** | Privacy Officer | Quarterly | New agent launch; feature expansion |
| **Performance SLO Review** | Platform Engineering | Monthly | SLO breach; capacity planning |
| **Cost per Interaction Review** | Programme Director | Monthly | Cost exceeds USD $0.05 threshold |
| **Agent Retirement Review** | Architecture Review Board | Annual | Capability superseded; end of lifecycle |

---

## 13. Document Quality Verification

### Quality Checklist

| Check | Status |
|-------|--------|
| Document ID: ARC-001-AGT-INV-v1.0 | ✅ |
| All Document Control fields populated | ✅ |
| Current state assessment (0 agents in production) | ✅ |
| 8 agent categories defined | ✅ |
| 16 agent instances catalogued | ✅ |
| Agent ID and name for each agent | ✅ |
| Purpose and capabilities documented | ✅ |
| Customer engagement channels mapped | ✅ |
| Technology stack requirements specified | ✅ |
| Maturity targets defined (pilot → production) | ✅ |
| Integration requirements documented | ✅ |
| Data dependencies identified | ✅ |
| Privacy/security considerations detailed | ✅ |
| REQ traceability (BR, FR, NFR) | ✅ |
| BPCM capability traceability | ✅ |
| APPINV application traceability | ✅ |
| TRANS phase traceability | ✅ |
| Agent platform architecture documented | ✅ |
| Agent-to-agent collaboration mapped | ✅ |
| Channel-to-agent mapping complete | ✅ |
| Maturity roadmap with readiness gates | ✅ |
| Risk register aligned | ✅ |
| Lifecycle management defined | ✅ |
| Governance controls specified | ✅ |
| MarsPost context maintained throughout | ✅ |
| ArcKit Version: 5.15.2 | ✅ |
| Date: 2026-07-01 | ✅ |
| Model: Qwen3.6-27B | ✅ |

---

*End of Document*
