# Agent Design: AgenticEA — MagicDelivery Agent AI Transformation

> **Template Origin**: Official | **ArcKit Version**: 5.15.2 | **Command**: `/arckit:agentdesign`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-AGT-DES-v1.0 |
| **Document Type** | Agent Design (AGT-DES) |
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
| 1.0 | 2026-07-01 | ArcKit AI | Initial creation — Agent architecture specification, interaction models, orchestration patterns, multi-agent collaboration, memory/state design, knowledge retrieval, performance targets, guardrail patterns, full traceability to AGT-INV, APPINV, ADR, TRANS | PENDING | PENDING |

---

## Executive Summary

### Purpose

This Agent Design (AGT-DES) document provides the comprehensive **agent architecture specification** for the **AgenticEA — MagicDelivery Agent AI Transformation** programme. It defines the structural design, interaction patterns, orchestration approach, memory management, knowledge retrieval, and performance targets for all 16 planned AI agents across 8 categories operating on the centralised AI Agent Platform (TAPP-02).

This document translates the agent inventory (ARC-001-AGT-INV-v1.0) into actionable architectural specifications that engineering teams use to design, develop, and deploy each agent type.

### Scope

| Aspect | Detail |
|--------|--------|
| **Agent Portfolio** | 16 agent instances across 8 categories |
| **Deployment Model** | Hybrid (Cloud Inference + On-Prem Sensitive Processing) per ADR-001 |
| **Agent Platform** | AI Agent Platform (TAPP-02) — centralised orchestration |
| **Engagement Channels** | 5 (Mobile App, Web Portal, Call Centre, Retail, Self-Service) |
| **Languages** | 6 (English, Mandarin, Arabic, Vietnamese, Hindi, Cantonese) |
| **Peak Concurrent Users** | 50,000 (Year 1) → 100,000 (Year 3) |
| **Design Horizon** | 5 years (Foundation → Scale → Mature phases) |

### Key Design Decisions

| Decision | Choice | Rationale |
|----------|--------|-----------|
| **Orchestration Model** | Centralised Agent Orchestrator with Complexity-Based Router | Single point of control; consistent experience; ADR-002 |
| **Deployment Model** | Hybrid Cloud/On-Prem | APP 8 compliance by design; ADR-001 |
| **Agent Communication** | Event-Driven Agent Bus with Structured Messages | Loose coupling; AI-07 capability |
| **Memory Architecture** | Hybrid: Short-Term (Session) + Long-Term (Vector) + Working Memory | Context continuity; personalisation; RAG pipeline |
| **Token Budget Strategy** | Tiered: 4K for tracking, 16K for conversational, 32K for analytics | Cost control (<USD $0.05/interaction); BR-005 |
| **Model Strategy** | Multi-Provider Abstraction with Fallback | Vendor independence; R-002 mitigation |
| **Guardrail Pattern** | Pre-Input Validation + In-Context Constraints + Post-Output Verification | Defence-in-depth; PRIN-04 (Security by Design) |

### Architecture Overview

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         Customer Channels (5)                                │
│   ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐         │
│   │ Mobile   │ │  Web    │ │Call Ctr  │ │ Retail  │ │Self-Svc │         │
│   │  App     │ │ Portal  │ │ (Co-Pilot)│ │ Kiosks  │ │  UI     │         │
│   └────┬─────┘ └────┬─────┘ └────┬─────┘ └────┬─────┘ └────┬─────┘         │
└────────┼────────────┼───────────┼───────────┼────────────┼─────────────────┘
         │            │           │           │            │
         └────────────┴───────────┼───────────┴────────────┘
                                  │  API Gateway / SDK
                                  ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                    AI Agent Platform (TAPP-02)                               │
│  ┌───────────────────────────────────────────────────────────────────────┐  │
│  │  Agent Orchestrator + Complexity Router (ADR-002)                      │  │
│  │  ┌─────────────┬─────────────┬───────────────┬─────────────────────┐  │  │
│  │  │  CSA Agents │  PTA Agents │  SA Agents    │  RSA/OPA/ANA/COMPA  │  │  │
│  │  │  (3 agents) │  (2 agents) │  (2 agents)   │  (9 agents)        │  │  │
│  │  └─────────────┴─────────────┴───────────────┴─────────────────────┘  │  │
│  └───────────────────────────────────────────────────────────────────────┘  │
│  ┌───────────────────────────────────────────────────────────────────────┐  │
│  │  Agent Communication Bus (Event-Driven)                              │  │
│  │  ┌──────┐ ┌──────────┐ ┌────────────┐ ┌───────────┐ ┌──────────┐     │  │
│  │  │Intent│ │  Context │ │  Tool Call │ │   Result  │ │  Status  │     │  │
│  │  │ Event │ │  Event   │ │   Event    │ │   Event   │ │  Event   │     │  │
│  │  └──────┘ └──────────┘ └────────────┘ └───────────┘ └──────────┘     │  │
│  └───────────────────────────────────────────────────────────────────────┘  │
│  ┌───────────────────────────────────────────────────────────────────────┐  │
│  │  Memory Layer: Session Store | Vector DB | Working Memory            │  │
│  └───────────────────────────────────────────────────────────────────────┘  │
│  ┌───────────────────────────────────────────────────────────────────────┐  │
│  │  Knowledge Retrieval: RAG Pipeline | Authoritative Data Sources       │  │
│  └───────────────────────────────────────────────────────────────────────┘  │
│  ┌───────────────────────────────────────────────────────────────────────┐  │
│  │  Guardrails: Validation | Compliance | Privacy | Escalation          │  │
│  └───────────────────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────────────────┘
                                  │
                  ┌───────────────┼────────────────┐
                  │               │                │
          ┌───────▼──────┐ ┌─────▼──────┐ ┌───────▼──────┐
          │  Cloud Inference │ Tokenisation│  On-Prem     │
          │  (Multi-Provider)│   Service   │  Sensitive    │
          └──────────────┘ └────────────┘ └──────────────┘
```

---

## 1. Agent Architecture Principles

### 1.1 Design Principles for Agent Portfolio

| Principle ID | Principle | Statement |
|-------------|-----------|-----------|
| **AP-01** | Agent Autonomy Boundaries | Each agent operates within a clearly defined capability boundary with explicit escalation paths; no agent makes decisions outside its domain without orchestrator approval |
| **AP-02** | Human-Centric AI | All agents serve humans (customers or staff) with transparent AI identity, seamless handoff, and human oversight for high-risk decisions |
| **AP-03** | Privacy by Design | PII tokenisation, consent verification, and data minimisation are built into every agent interaction flow; no PII reaches cloud inference |
| **AP-04** | Composable Agent Design | Agents are independently deployable, version-controlled components with published interfaces; new agents onboard within 2-week cycles |
| **AP-05** | Event-Driven Communication | Agent-to-agent and agent-to-system communication uses asynchronous event-driven patterns for resilience and decoupling |
| **AP-06** | Observability by Default | Every agent emits structured telemetry (accuracy, latency, confidence, escalation rate, token consumption) for real-time governance |
| **AP-07** | Progressive Enhancement | Agent capabilities scale from conversational (L3) to managed (L4) to optimised (L5) with backward-compatible interfaces |
| **AP-08** | Multi-Model Resilience | Agents are model-agnostic through abstraction layer; any single model failure triggers fallback without customer-visible disruption |

### 1.2 Architecture Layers

| Layer | Responsibility | Components |
|-------|---------------|------------|
| **Channel Layer** | Customer-facing interaction surfaces | Mobile SDK, Web Widget, Call Centre UI, Retail Kiosk UI, Self-Service UI |
| **Orchestration Layer** | Agent routing, session management, complexity classification | Agent Orchestrator, Complexity Router, Session Manager |
| **Agent Layer** | Domain-specific AI capabilities | 16 specialised agents (CSA, SA, PTA, MIA, RSA, OPA, ANA, COMPA) |
| **Memory Layer** | Context management, knowledge storage | Session Store, Vector Database, Working Memory, Conversation History |
| **Knowledge Layer** | RAG pipeline, authoritative data | Domain Knowledge Bases, Retrieval Pipeline, Grounding Engine |
| **Platform Layer** | Model serving, governance, observability | Hybrid Model Serving, Tokenisation, Governance Framework, Telemetry |
| **Integration Layer** | System connectivity | CRM, ERP, GCP Event Manager, Pricing, Product Systems, CDP |

---

## 2. Agent Capability Specification

### 2.1 Customer Service Agents (CSA)

#### CSA-01: Customer Service Agent

| Attribute | Specification |
|-----------|---------------|
| **Agent ID** | CSA-01 |
| **Category** | Customer Service |
| **Interaction Mode** | Conversational (multi-turn, 10+ turns) |
| **Primary Channels** | Mobile App (primary), Web Portal, Self-Service, Call Centre (co-pilot) |

**Core Capabilities**:

| Capability | Description | Confidence Target |
|------------|-------------|-------------------|
| **Intent Recognition** | Classifies customer intent from natural language (parcel tracking, fees, address change, general inquiry) | ≥85% accuracy |
| **Context Maintenance** | Maintains conversation context across 10+ turns including entity references and topic shifts | ≥90% context retention |
| **Information Retrieval** | Queries authoritative data sources (CRM, pricing, product catalog) via RAG pipeline | ≥95% data accuracy |
| **Multi-Lingual** | Detects and responds in 6 languages with ≥80% translation accuracy | ≥80% per language |
| **Escalation** | Offers human handoff when confidence <70% or high-risk topics detected | 100% detection |

**Token Budget**: 16,384 tokens (system prompt: ~2,048; context window: ~8,192; response: ~6,144)

**Model Tier**: Primary — Conversational LLM (cloud); Fallback — lighter model for simple queries

**Phase**: Foundation (Y1)

**Traceability**: AGT-INV §3.1 | BR-002, BR-003 | CE-02, CE-03, AI-01 | TAPP-02 | WP-ARC-001

#### CSA-02: Complaint Triage Agent

| Attribute | Specification |
|-----------|---------------|
| **Agent ID** | CSA-02 |
| **Category** | Customer Service |
| **Interaction Mode** | Conversational with classification engine |
| **Primary Channels** | Mobile App, Web Portal, Call Centre (co-pilot), Self-Service |

**Core Capabilities**:

| Capability | Description | Confidence Target |
|------------|-------------|-------------------|
| **Complaint Pattern Detection** | Identifies complaint indicators (language patterns, sentiment, regulatory keywords) | ≥90% detection |
| **Severity Classification** | Routes to appropriate severity level (low/medium/high/critical) | ≥85% accuracy |
| **Regulatory Compliance Check** | Validates response against ACCC consumer law templates | 100% compliance |
| **Acknowledgment Generation** | Creates compliant complaint acknowledgment with reference number | 100% generation |
| **Escalation Routing** | Routes to appropriate human resolution channels based on complaint type | ≥95% accuracy |

**Token Budget**: 8,192 tokens (focused domain scope; on-prem processing)

**Model Tier**: Domain-specific model (on-prem); sensitive workflow per ADR-001

**Phase**: Foundation (Y1)

**Traceability**: AGT-INV §3.1 | BR-002, BR-004 | CE-02, CE-03, AI-03 | TAPP-02 | WP-ARC-001, WP-SEC-004

#### CSA-03: Multi-Language Support Agent

| Attribute | Specification |
|-----------|---------------|
| **Agent ID** | CSA-03 |
| **Category** | Customer Service |
| **Interaction Mode** | Conversational with real-time language detection and switching |
| **Primary Channels** | Mobile App, Web Portal, Self-Service |

**Core Capabilities**:

| Capability | Description | Confidence Target |
|------------|-------------|-------------------|
| **Language Detection** | Detects input language with confidence scoring | ≥95% accuracy |
| **Code-Mixed Input Handling** | Processes mixed-language input; responds in dominant language | ≥80% accuracy |
| **Seamless Language Switching** | Switches languages mid-conversation without losing context | 100% context preserved |
| **Cultural Adaptation** | Generates culturally appropriate responses for each language | Qualitative review |

**Token Budget**: 16,384 tokens (larger for translation context)

**Model Tier**: Multilingual LLM (cloud); Fallback to English for unsupported languages

**Phase**: Foundation (Y1) pilot English + 2 languages → Scale (Y2) full 6-language

**Traceability**: AGT-INV §3.1 | BR-002 | CE-07 | TAPP-08 | WP-ARC-001, WP-APP-002

---

### 2.2 Shopping Assistant Agents (SA)

#### SA-01: Shipping Service Recommendation Agent

| Attribute | Specification |
|-----------|---------------|
| **Agent ID** | SA-01 |
| **Category** | Shopping Assistant |
| **Interaction Mode** | Conversational with recommendation engine |
| **Primary Channels** | Mobile App (primary), Web Portal |

**Core Capabilities**:

| Capability | Description | Confidence Target |
|------------|-------------|-------------------|
| **Parcel Specification Analysis** | Parses dimensions, weight, destination from natural language | ≥90% parsing accuracy |
| **Service Tier Recommendation** | Recommends optimal service tier based on cost, speed, tracking features | ≥85% relevance |
| **Cost Comparison** | Presents ranked comparison of available services | 100% accurate pricing |
| **Personalised Offers** | Generates personalised recommendations based on history (opt-in) | ≥80% conversion lift |
| **Service Upgrade Suggestions** | Identifies opportunities for service upgrades | ACCC-compliant content |

**Token Budget**: 8,192 tokens (product catalog context: ~2,048; recommendation: ~4,096)

**Model Tier**: Recommendation engine + lightweight LLM for conversation

**Phase**: Foundation (Y1) → Scale (Y2)

**Traceability**: AGT-INV §3.2 | BR-001 | EC-02, EC-01, EC-08 | TAPP-07 | WP-ARC-006, WP-APP-007

#### SA-02: Business Seller Assistant Agent

| Attribute | Specification |
|-----------|---------------|
| **Agent ID** | SA-02 |
| **Category** | Shopping Assistant |
| **Interaction Mode** | Conversational with bulk operations |
| **Primary Channels** | Web Portal, Mobile App |

**Core Capabilities**:

| Capability | Description | Confidence Target |
|------------|-------------|-------------------|
| **Bulk Shipping Calculations** | Processes multiple parcels simultaneously | 100% accuracy |
| **Volume Pricing Recommendations** | Identifies volume-based discounts and cost optimisations | ≥90% savings identified |
| **Order Batch Processing** | Batch creates shipping labels and tracking | ≥95% success rate |
| **Shipping Template Management** | Creates and reuses shipping templates for recurring orders | 100% template fidelity |
| **Cost Optimisation Analysis** | Analyses shipping patterns and suggests cost-reduction strategies | ≥15% cost reduction |

**Token Budget**: 8,192 tokens (bulk operations context)

**Model Tier**: Business-domain LLM + calculation engine

**Phase**: Scale (Y2)

**Traceability**: AGT-INV §3.2 | BR-001 | EC-02, EC-01, EC-03 | TAPP-07 | WP-APP-007

---

### 2.3 Parcel Tracking Agents (PTA)

#### PTA-01: Real-Time Parcel Tracking Agent

| Attribute | Specification |
|-----------|---------------|
| **Agent ID** | PTA-01 |
| **Category** | Parcel Tracking |
| **Interaction Mode** | Real-time status delivery with predictive ETA |
| **Primary Channels** | Mobile App (primary), Web Portal, Self-Service, Push, SMS, Email |

**Core Capabilities**:

| Capability | Description | Confidence Target |
|------------|-------------|-------------------|
| **Real-Time Status Retrieval** | Fetches current parcel status from logistics system within 1 second | ≥99% availability |
| **Predictive ETA Generation** | Machine learning ETA based on historical delivery patterns | ≥85% within 4-hour window |
| **Proactive Notification** | Pushes notifications for significant status changes within 30 seconds | ≥98% delivery |
| **Multi-Parcel Consolidation** | Presents consolidated tracking summary for multiple parcels | 100% accuracy |
| **Proactive Delay Detection** | Detects delays and proactively informs customer with revised ETA | ≥90% detection |

**Token Budget**: 4,096 tokens (structured data focus; minimal conversational overhead)

**Model Tier**: Predictive ETA model + lightweight status formatter

**Phase**: Foundation (Y1)

**Traceability**: AGT-INV §3.3 | BR-002, BR-003 | PS-01, PS-02, PS-07 | TAPP-02 | WP-ARC-001, WP-APP-002

#### PTA-02: Delivery Exception Agent

| Attribute | Specification |
|-----------|---------------|
| **Agent ID** | PTA-02 |
| **Category** | Parcel Tracking |
| **Interaction Mode** | Proactive outreach with resolution workflow |
| **Primary Channels** | Mobile App (primary), Push, SMS, Email |

**Core Capabilities**:

| Capability | Description | Confidence Target |
|------------|-------------|-------------------|
| **Exception Detection** | Identifies delivery exceptions from event stream within 5 minutes | ≥95% detection |
| **Resolution Option Generation** | Generates actionable resolution options (redelivery, address correction, retail collection) | ≥90% relevance |
| **Proactive Outreach** | Initiates AI conversation with affected customer | ≥95% delivery within 5 min |
| **Exception Status Tracking** | Tracks resolution progress and provides updates | 100% tracking |
| **Customer Response Handling** | Processes customer responses to resolution offers | ≥85% resolution rate |

**Token Budget**: 8,192 tokens (exception context + resolution workflow)

**Model Tier**: Exception detection model + resolution workflow engine

**Phase**: Foundation (Y1) → Scale (Y2)

**Traceability**: AGT-INV §3.3 | BR-002, BR-001 | PS-02, PS-07 | TAPP-02 | WP-ARC-001, WP-APP-002

---

### 2.4 Marketing Intelligence Agents (MIA)

#### MIA-01: Customer Segmentation Agent

| Attribute | Specification |
|-----------|---------------|
| **Agent ID** | MIA-01 |
| **Category** | Marketing Intelligence |
| **Interaction Mode** | Internal analytics tool (B2B) |
| **Primary Channels** | Internal dashboards, Marketing Intelligence Platform |

**Core Capabilities**:

| Capability | Description | Confidence Target |
|------------|-------------|-------------------|
| **Behavioural Clustering** | ML-driven customer segmentation based on behaviour patterns | ≥85% cluster stability |
| **Real-Time Segmentation** | Processes incoming events to update segments within 60 seconds | ≥90% freshness |
| **Micro-Segment Generation** | Identifies micro-segments (N < 1,000) for targeted campaigns | ≥80% relevance |
| **Persona Creation** | Generates customer personas from behavioural data | Qualitative review |
| **Propensity Scoring** | Predicts likelihood of desired actions (purchase, engagement, churn) | ≥80% AUC |

**Token Budget**: 32,768 tokens (analytical context; batch processing)

**Model Tier**: ML segmentation engine + analytics LLM

**Phase**: Scale (Y2) → Mature (Y3)

**Traceability**: AGT-INV §3.4 | BR-001 | CD-04, MK-07 | TAPP-06, TAPP-04 | WP-DAT-006, WP-APP-009

#### MIA-02: Campaign Optimisation Agent

| Attribute | Specification |
|-----------|---------------|
| **Agent ID** | MIA-02 |
| **Category** | Marketing Intelligence |
| **Interaction Mode** | Internal analytics tool (B2B) with real-time campaign adjustment |
| **Primary Channels** | Internal dashboards, Marketing Intelligence Platform |

**Core Capabilities**:

| Capability | Description | Confidence Target |
|------------|-------------|-------------------|
| **A/B Test Design and Analysis** | Designs and analyses experiment variants | ≥95% statistical validity |
| **Offer Optimisation** | Dynamically adjusts offers based on response data | ≥10% conversion lift |
| **Dynamic Targeting Adjustment** | Real-time segment adjustment based on campaign performance | ≥85% optimisation |
| **Conversion Rate Prediction** | Predicts conversion probability per segment/campaign | ≥80% accuracy |
| **ROI Attribution** | Attributes revenue to specific campaigns and AI features | ≥90% accuracy |

**Token Budget**: 32,768 tokens (campaign data context; attribution modelling)

**Model Tier**: Reinforcement learning engine + attribution model

**Phase**: Scale (Y2) → Mature (Y3)

**Traceability**: AGT-INV §3.4 | BR-001 | MK-02, MK-04, MK-08 | TAPP-06 | WP-APP-009

#### MIA-03: Proactive Engagement Agent

| Attribute | Specification |
|-----------|---------------|
| **Agent ID** | MIA-03 |
| **Category** | Marketing Intelligence |
| **Interaction Mode** | Event-driven proactive outreach |
| **Primary Channels** | Mobile App, Push, Email, SMS, Web Portal |

**Core Capabilities**:

| Capability | Description | Confidence Target |
|------------|-------------|-------------------|
| **Predictive Trigger Detection** | Identifies engagement opportunities from event streams | ≥85% detection |
| **Next-Best-Action Generation** | Recommends optimal engagement action per customer | ≥80% relevance |
| **Service Offer Generation** | Creates contextual service offers based on lifecycle stage | ≥85% conversion |
| **Loyalty Activation** | Identifies loyalty programme opportunities | Qualitative review |
| **Churn Prevention Outreach** | Detects churn signals and initiates retention engagement | ≥70% retention rate |

**Token Budget**: 16,384 tokens (proactive engagement context; conversation generation)

**Model Tier**: Predictive engagement model + conversation generator

**Phase**: Scale (Y2) → Mature (Y3)

**Traceability**: AGT-INV §3.4 | BR-001 | MK-03, MK-05, MK-06 | TAPP-06 | WP-APP-009, WP-DAT-008

---

### 2.5 Retail Support Agents (RSA)

#### RSA-01: Retail Staff Co-Pilot Agent

| Attribute | Specification |
|-----------|---------------|
| **Agent ID** | RSA-01 |
| **Category** | Retail Support |
| **Interaction Mode** | Staff co-pilot (no autonomous customer output) |
| **Primary Channels** | Retail Kiosks, POS overlay, Retail Staff Tablet |

**Core Capabilities**:

| Capability | Description | Confidence Target |
|------------|-------------|-------------------|
| **Customer Query Assistance** | Surfaces relevant information for staff to relay to customers | ≥90% relevance |
| **Service Information Retrieval** | Queries product catalog, pricing, service details via RAG | ≥95% data accuracy |
| **Suggested Response Generation** | Generates draft responses for staff approval | ≥80% staff acceptance rate |
| **Transaction Support** | Assists with parcel lodgement, payment processing, inventory lookup | ≥95% accuracy |
| **Knowledge Retrieval** | Retrieves from MagicDelivery service catalog via RAG pipeline | ≥90% retrieval accuracy |

**Token Budget**: 8,192 tokens (co-pilot suggestions; staff-reviewed)

**Model Tier**: Co-pilot LLM + RAG pipeline (staff-facing, no cloud PII exposure)

**Phase**: Scale (Y2) pilot → Mature (Y3)

**Traceability**: AGT-INV §3.5 | BR-003, BR-006 | EC-06, BO-02 | TAPP-09 | WP-APP-010, WP-APP-014

#### RSA-02: Retail Self-Service Kiosk Agent

| Attribute | Specification |
|-----------|---------------|
| **Agent ID** | RSA-02 |
| **Category** | Retail Support |
| **Interaction Mode** | Conversational self-service at retail kiosks |
| **Primary Channels** | Retail Self-Service Kiosks (4,000 shops) |

**Core Capabilities**:

| Capability | Description | Confidence Target |
|------------|-------------|-------------------|
| **Self-Service Parcel Lodgement** | Guides customers through parcel creation workflow | ≥90% completion rate |
| **Service Inquiry Handling** | Answers service questions at counter | ≥85% accuracy |
| **Parcel Tracking at Counter** | Provides parcel status via barcode/QR scan | 100% accuracy |
| **Payment Assistance** | Guides payment processing | ≥99% success |
| **Queue Management** | Manages self-service queue flow | ≥80% queue reduction |

**Token Budget**: 8,192 tokens (kiosk interaction; limited scope)

**Model Tier**: Conversational agent + kiosk UI framework

**Phase**: Scale (Y2) pilot → Mature (Y3–5)

**Traceability**: AGT-INV §3.5 | BR-003 | EC-06, BO-01 | TAPP-09 | WP-APP-010, WP-APP-014

---

### 2.6 Operations Agents (OPA)

#### OPA-01: Call Centre AI Co-Pilot Agent

| Attribute | Specification |
|-----------|---------------|
| **Agent ID** | OPA-01 |
| **Category** | Operations |
| **Interaction Mode** | Staff co-pilot (real-time query assistance) |
| **Primary Channels** | Call Centre (staff-facing only) |

**Core Capabilities**:

| Capability | Description | Confidence Target |
|------------|-------------|-------------------|
| **Real-Time Query Analysis** | Analyses customer query in real-time during call | ≥85% intent accuracy |
| **Suggested Response Generation** | Generates suggested responses with confidence scoring | ≥80% agent acceptance |
| **Auto-Fill Data Retrieval** | Automatically retrieves CRM data for agent workspace | ≥95% accuracy |
| **CRM Data Surfacing** | Surfaces relevant customer context to agent | ≥90% relevance |
| **Routine Query Pattern Detection** | Identifies routine queries that can be auto-resolved | ≥85% detection |

**Token Budget**: 8,192 tokens (co-pilot suggestions; CRM context)

**Model Tier**: Co-pilot LLM + CRM integration (staff-facing)

**Phase**: Foundation (Y1)

**Traceability**: AGT-INV §3.6 | BR-003, BR-006 | CE-05, BO-02, BO-04 | TAPP-02 | WP-ARC-001, WP-WKF-005

#### OPA-02: Operations Workflow Agent

| Attribute | Specification |
|-----------|---------------|
| **Agent ID** | OPA-02 |
| **Category** | Operations |
| **Interaction Mode** | Automated workflow execution |
| **Primary Channels** | Internal dashboards, monitoring systems, notification channels |

**Core Capabilities**:

| Capability | Description | Confidence Target |
|------------|-------------|-------------------|
| **Automated Workflow Execution** | Executes predefined operational workflows | ≥95% success rate |
| **Exception Detection and Routing** | Detects operational exceptions and routes to resolution | ≥90% detection |
| **Performance Monitoring** | Monitors operational metrics and triggers alerts | ≥99% uptime |
| **Operational Reporting** | Generates operational reports and dashboards | 100% accuracy |
| **SLA Breach Detection** | Detects SLA breaches and initiates corrective actions | ≥95% detection |

**Token Budget**: 4,096 tokens (workflow automation; minimal LLM)

**Model Tier**: Workflow engine + anomaly detection model

**Phase**: Foundation (Y1) → Scale (Y2)

**Traceability**: AGT-INV §3.6 | BR-003, BR-005 | BO-04, BO-05 | TAPP-02 | WP-ARC-001, WP-APP-003

---

### 2.7 Analytics Agents (ANA)

#### ANA-01: Customer Insights Agent

| Attribute | Specification |
|-----------|---------------|
| **Agent ID** | ANA-01 |
| **Category** | Analytics |
| **Interaction Mode** | Internal analytics tool (B2B) |
| **Primary Channels** | Internal dashboards, self-service analytics portal |

**Core Capabilities**:

| Capability | Description | Confidence Target |
|------------|-------------|-------------------|
| **Customer Behaviour Analysis** | Analyses customer interaction patterns and trends | ≥90% insight accuracy |
| **Journey Mapping** | Creates visual customer journey maps from event data | ≥85% completeness |
| **Cohort Analysis** | Segments customers by behaviour and measures outcomes | ≥90% accuracy |
| **Churn Prediction** | Predicts customer churn risk with confidence scoring | ≥80% AUC |
| **Lifetime Value Modelling** | Calculates and tracks customer lifetime value | ≥85% prediction accuracy |

**Token Budget**: 32,768 tokens (analytical context; data exploration)

**Model Tier**: Analytics LLM + data lakehouse integration

**Phase**: Scale (Y2)

**Traceability**: AGT-INV §3.7 | BR-001, BR-005 | CD-03, CD-05 | TAPP-04 | WP-DAT-005, WP-DAT-007

#### ANA-02: Predictive Analytics Agent

| Attribute | Specification |
|-----------|---------------|
| **Agent ID** | ANA-02 |
| **Category** | Analytics |
| **Interaction Mode** | Internal analytics tool (B2B) |
| **Primary Channels** | Executive dashboards, planning systems |

**Core Capabilities**:

| Capability | Description | Confidence Target |
|------------|-------------|-------------------|
| **Demand Forecasting** | Predicts parcel volume and service demand | ≥85% forecast accuracy |
| **Revenue Prediction** | Forecasts revenue based on historical and market data | ≥80% accuracy |
| **Risk Scenario Modelling** | Simulates risk scenarios and impacts | ≥85% model validity |
| **Capacity Planning** | Recommends staffing and capacity adjustments | ≥90% accuracy |
| **Predictive Maintenance** | Predicts operational system maintenance needs | ≥80% detection |

**Token Budget**: 32,768 tokens (scenario simulation; time-series context)

**Model Tier**: Time-series prediction models + scenario simulation engine

**Phase**: Mature (Y3)

**Traceability**: AGT-INV §3.7 | BR-001, BR-005 | CD-07, BO-05 | TAPP-04 | WP-DAT-011

---

### 2.8 Compliance Agents (COMPA)

#### COMPA-01: Privacy Consent Agent

| Attribute | Specification |
|-----------|---------------|
| **Agent ID** | COMPA-01 |
| **Category** | Compliance |
| **Interaction Mode** | Consent management service (API + customer-facing privacy dashboard) |
| **Primary Channels** | Mobile App (privacy dashboard), Web Portal, Self-Service |

**Core Capabilities**:

| Capability | Description | Confidence Target |
|------------|-------------|-------------------|
| **Granular Consent Management** | Manages consent per data purpose, per channel, per agent | 100% accuracy |
| **Opt-In/Opt-Out Processing** | Processes consent changes within current session | <1 second processing |
| **Consent Verification** | Real-time consent check before any agent interaction using personalisation | 100% verification |
| **Data Access/Deletion Processing** | Processes GDPR/APP data rights requests | ≤24 hour processing |
| **Privacy Dashboard Data** | Provides data for customer-facing privacy controls | 100% data freshness |

**Token Budget**: 4,096 tokens (consent records are structured data)

**Model Tier**: Consent service API + lightweight rules engine (highest security)

**Phase**: Foundation (Y1)

**Traceability**: AGT-INV §3.8 | BR-004 | PC-01, PC-04, PC-08 | TAPP-05 | WP-SEC-001

#### COMPA-02: AI Governance and Compliance Agent

| Attribute | Specification |
|-----------|---------------|
| **Agent ID** | COMPA-02 |
| **Category** | Compliance |
| **Interaction Mode** | Internal compliance monitoring |
| **Primary Channels** | Internal dashboards, compliance team, regulatory reporting |

**Core Capabilities**:

| Capability | Description | Confidence Target |
|------------|-------------|-------------------|
| **Hallucination Detection** | Monitors AI output for factual inaccuracies against authoritative data | ≥95% detection |
| **Response Validation** | Validates responses against factual data sources (FR-016) | 100% validation |
| **Compliance Monitoring** | Tracks compliance metrics across all agents in real-time | ≥99% monitoring uptime |
| **Audit Trail Generation** | Creates tamper-evident audit trails for all AI interactions | 100% coverage |
| **DPIA Automation** | Automates Data Protection Impact Assessments for new features | ≥90% automation rate |
| **Model Governance Reporting** | Generates model governance reports for regulatory submission | 100% completeness |

**Token Budget**: 16,384 tokens (compliance context; model metadata; audit data)

**Model Tier**: Compliance monitoring engine + rules engine

**Phase**: Foundation (Y1) → Scale (Y2)

**Traceability**: AGT-INV §3.8 | BR-004, BR-007 | AI-03, PC-03, PC-05, PC-06 | TAPP-02 | WP-SEC-004, WP-SEC-006

---

### 2.9 Agent Capability Summary Matrix

| Agent ID | Category | Interaction Mode | Token Budget | Model Tier | Phase | Data Classification |
|----------|----------|-----------------|-------------|------------|-------|---------------------|
| CSA-01 | Customer Service | Conversational | 16K | Primary LLM | Foundation | CONFIDENTIAL |
| CSA-02 | Customer Service | Conversational | 8K | Domain LLM (on-prem) | Foundation | RESTRICTED |
| CSA-03 | Customer Service | Conversational | 16K | Multilingual LLM | Foundation/Scale | CONFIDENTIAL |
| SA-01 | Shopping Assistant | Conversational | 8K | Recommendation Engine | Foundation/Scale | CONFIDENTIAL |
| SA-02 | Shopping Assistant | Conversational | 8K | Business LLM | Scale | CONFIDENTIAL |
| PTA-01 | Parcel Tracking | Real-Time | 4K | Predictive Model | Foundation | CONFIDENTIAL |
| PTA-02 | Parcel Tracking | Proactive | 8K | Exception Model | Foundation/Scale | CONFIDENTIAL |
| MIA-01 | Marketing Intelligence | Analytics | 32K | ML Engine | Scale/Mature | INTERNAL |
| MIA-02 | Marketing Intelligence | Analytics | 32K | RL Engine | Scale/Mature | INTERNAL |
| MIA-03 | Marketing Intelligence | Proactive | 16K | Predictive Model | Scale/Mature | INTERNAL |
| RSA-01 | Retail Support | Co-Pilot | 8K | Co-Pilot LLM | Scale/Mature | CONFIDENTIAL |
| RSA-02 | Retail Support | Conversational | 8K | Conversational Agent | Scale/Mature | CONFIDENTIAL |
| OPA-01 | Operations | Co-Pilot | 8K | Co-Pilot LLM | Foundation | INTERNAL |
| OPA-02 | Operations | Automated | 4K | Workflow Engine | Foundation/Scale | INTERNAL |
| ANA-01 | Analytics | Analytics | 32K | Analytics LLM | Scale | INTERNAL |
| ANA-02 | Analytics | Analytics | 32K | Time-Series Model | Mature | INTERNAL |
| COMPA-01 | Compliance | Service | 4K | Rules Engine | Foundation | RESTRICTED |
| COMPA-02 | Compliance | Monitoring | 16K | Compliance Engine | Foundation/Scale | CONFIDENTIAL |

---

## 3. Interaction Model

### 3.1 Conversational Patterns

#### 3.1.1 Agent-Customer Conversation Lifecycle

```
Customer Input → Language Detection → Intent Classification → Complexity Score
    ↓
┌───────────────────────────────────────────────────────────────┐
│                    Complexity Router (ADR-002)               │
│                                                               │
│  Routine (≥70% confidence, low-risk) ──→ Agent handles        │
│  Moderate (<70% confidence) ────→ Agent handles + review      │
│  High-Risk (complaints, security, legal) ──→ Auto-escalate    │
│  Customer requests human ────────────→ Immediate escalation  │
└───────────────────────────────────────────────────────────────┘
    ↓
Agent Response → Validation → Token De-tokenisation → Customer Delivery
```

#### 3.1.2 Conversational Pattern Matrix

| Pattern | Description | Agents | Turn Limit | Context Scope |
|---------|-------------|--------|-----------|---------------|
| **Single-Turn** | Question-answer; no context needed | PTA-01 (status lookup), OPA-02 (status check) | 1 turn | None |
| **Multi-Turn** | Conversation with context retention | CSA-01, CSA-03, SA-01, SA-02 | 10+ turns | Session |
| **Proactive** | Agent initiates based on triggers | PTA-02, MIA-03 | Variable | Event-driven |
| **Co-Pilot** | Staff-facing suggestion (no autonomous output) | RSA-01, OPA-01 | Continuous | Active session |
| **Analytics** | Batch processing; no conversation | MIA-01, MIA-02, ANA-01, ANA-02 | N/A | Batch window |
| **Compliance** | Service-oriented; structured interaction | COMPA-01, COMPA-02 | N/A | Audit period |

### 3.2 Escalation Paths

#### 3.2.1 Escalation Decision Flow

| Trigger | Action | Target | Max Time |
|---------|--------|--------|----------|
| Confidence score < 70% | Offer human escalation | Human agent via CRM | 30 seconds |
| Customer says "talk to a person" | Immediate escalation | Human agent via CRM | 30 seconds |
| Complaint keywords detected | Auto-escalate to complaints team | CSA-02 → Human | 15 seconds |
| Security/legal topic detected | Immediate escalation | Security team | 10 seconds |
| High-risk regulatory topic | Auto-escalate with full context | Compliance team | 10 seconds |
| Agent error/hallucination detected | Fallback to cached response or escalate | Human agent | 30 seconds |

#### 3.2.2 Escalation Context Transfer Protocol

When escalation is triggered, the following context is transferred to the human agent:

| Context Element | Source | Format |
|----------------|--------|--------|
| Conversation transcript | Session Store | JSON (full message history) |
| AI confidence scores | Agent output | Numeric array per turn |
| Attempted responses | Agent output | String array |
| Customer profile summary | CRM / CDP | Structured JSON (minimal PII) |
| Intent classification | Complexity Router | Intent label + confidence |
| Escalation reason code | Complexity Router | Code (LOW_CONFIDENCE, CUSTOMER_REQUEST, HIGH_RISK, COMPLAINT, SECURITY, ERROR) |
| Agent ID and version | Agent Registry | Identifier |
| Session correlation ID | Session Manager | UUID |

#### 3.2.3 Escalation SLA

| Escalation Type | Target Time | Measurement |
|----------------|-------------|-------------|
| **Customer-requested escalation** | ≤30 seconds | Time from customer request to human agent connection |
| **Auto-escalation (high-risk)** | ≤15 seconds | Time from trigger detection to human agent assignment |
| **Low-confidence escalation** | ≤30 seconds | Time from confidence check to human agent connection |
| **Complaint escalation** | ≤15 seconds | Time from complaint detection to complaints team |
| **Security escalation** | ≤10 seconds | Time from security trigger to security team |

### 3.3 Agent Interaction Modes by Category

```
┌────────────────────────────────────────────────────────────────────────────┐
│                    Agent Interaction Mode Classification                     │
├──────────────────────┬─────────────────────────────────────────────────────┤
│  Mode               │  Characteristics                                       │
├──────────────────────┼─────────────────────────────────────────────────────┤
│  Conversational      │  Multi-turn, context-aware, natural language        │
│  (CSA, SA, PTA)      │  Customer-facing, proactive option                  │
├──────────────────────┼─────────────────────────────────────────────────────┤
│  Co-Pilot            │  Staff-facing, suggestion-only, no autonomous        │
│  (RSA-01, OPA-01)    │  output, staff approval required                     │
├──────────────────────┼─────────────────────────────────────────────────────┤
│  Analytics (B2B)     │  Batch processing, dashboard output, no conversation│
│  (MIA, ANA)           │  Internal tools, aggregated data                     │
├──────────────────────┼─────────────────────────────────────────────────────┤
│  Compliance Service  │  Structured API interactions, audit-focused          │
│  (COMPA)             │  Internal monitoring + customer privacy UI            │
└──────────────────────┴─────────────────────────────────────────────────────┘
```

---

## 4. Memory and State Management Design

### 4.1 Memory Architecture Overview

The agent memory architecture uses a **three-tier model** to balance context needs, cost efficiency, and privacy compliance:

```
┌──────────────────────────────────────────────────────────────┐
│                      Memory Architecture                       │
│                                                               │
│  ┌─────────────────┐    ┌───────────────────────┐           │
│  │ Short-Term Memory│    │  Long-Term Memory      │           │
│  │ (Session Store)  │    │  (Vector Database)     │           │
│  │ ─────────────── │    │  ────────────────────   │           │
│  │ • Current session│    │  • Customer profile     │           │
│  │ • Conversation  │    │  • Interaction history   │           │
│  │ • Context window│    │  • Preferences          │           │
│  │ • Working state │    │  • Consent records      │           │
│  │ • TTL: Session  │    │  • TTL: Policy-defined   │           │
│  └─────────────────┘    └───────────────────────┘           │
│           │                          │                       │
│           ▼                          ▼                       │
│  ┌───────────────────────────────────────────────────────┐   │
│  │              Working Memory (Agent State)                │   │
│  │  • Tool call state                                      │   │
│  │  • Intermediate results                                   │   │
│  │  • RAG retrieval context                                     │   │
│  │  • TTL: Request lifecycle                                      │   │
│  └───────────────────────────────────────────────────────┘   │
└──────────────────────────────────────────────────────────────┘
```

### 4.2 Short-Term Memory (Session Store)

| Attribute | Specification |
|-----------|---------------|
| **Technology** | Redis (clustered, in-memory with persistence) |
| **Capacity** | Per session: 10 turns × 4K context = ~40K tokens max |
| **TTL** | Session duration (default: 30 minutes idle timeout) |
| **Encryption** | AES-256 at rest; TLS 1.3 in transit |
| **Data Classification** | CONFIDENTIAL (session data linked to authenticated customer) |

**Session Data Schema**:

```json
{
  "session_id": "uuid",
  "customer_id": "tokenised_id",
  "channel": "mobile_app|web|call_centre|retail|self_service",
  "agent_id": "CSA-01|PTA-01|...",
  "messages": [
    {"role": "user|assistant|system", "content": "...", "timestamp": "ISO-8601", "confidence": 0.92},
    ...
  ],
  "context": {
    "intent": "parcel_tracking",
    "entities": {"tracking_number": "tok_abc123", "customer_name": "tok_xyz"},
    "language": "en",
    "turn_count": 5
  },
  "metadata": {
    "created_at": "ISO-8601",
    "last_active": "ISO-8601",
    "escalation_count": 0,
    "total_tokens": 8192
  }
}
```

### 4.3 Long-Term Memory (Vector Database)

| Attribute | Specification |
|-----------|---------------|
| **Technology** | Vector database (e.g., Weaviate, Pinecone, or managed cloud equivalent) |
| **Storage** | Customer profiles, interaction history, preferences, consent records |
| **Indexing** | Semantic embeddings for retrieval; structured indexes for exact match |
| **TTL** | Policy-defined per data category (consent: indefinite; interactions: 2 years) |
| **Encryption** | AES-256 at rest; tokenised PII; APP-compliant retention |

**Vector Memory Schema**:

```json
{
  "customer_profile": {
    "id": "tokenised_customer_id",
    "preferences": {
      "language": "en|zh|ar|vi|hi|yue",
      "notification_channels": ["push", "email", "sms"],
      "consent_flags": {"personalisation": true, "marketing": false, ...}
    },
    "interaction_summary": {
      "total_interactions": 47,
      "last_interaction": "ISO-8601",
      "common_intents": ["parcel_tracking", "fee_inquiry"],
      "satisfaction_trend": "positive"
    },
    "embedded_vectors": ["semantic_embedding_of_preferences", ...]
  }
}
```

### 4.4 Working Memory (Agent State)

| Attribute | Specification |
|-----------|---------------|
| **Scope** | Request lifecycle (single interaction) |
| **Contents** | Tool call results, RAG retrieval context, intermediate computation state |
| **Persistence** | Volatile — discarded after request completion unless explicitly saved |
| **Size** | Up to 32K tokens for analytics agents; 8K for conversational agents |

### 4.5 Context Window Management

| Agent Category | System Prompt Size | Context Budget | Response Budget | Total Token Budget |
|---------------|-------------------|----------------|-----------------|-------------------|
| CSA (Customer Service) | ~2,048 | ~8,192 | ~6,144 | 16,384 |
| SA (Shopping Assistant) | ~1,024 | ~2,048 | ~5,120 | 8,192 |
| PTA (Parcel Tracking) | ~512 | ~2,048 | ~1,536 | 4,096 |
| RSA (Retail Support) | ~1,024 | ~2,048 | ~5,120 | 8,192 |
| OPA (Operations) | ~512 | ~1,024 | ~2,560 | 4,096 |
| MIA (Marketing Intelligence) | ~2,048 | ~16,384 | ~14,336 | 32,768 |
| ANA (Analytics) | ~2,048 | ~16,384 | ~14,336 | 32,768 |
| COMPA (Compliance) | ~1,024 | ~4,096 | ~10,240 | 16,384 |

### 4.6 Token Budget Management Strategy

| Strategy | Implementation | Cost Impact |
|----------|---------------|-------------|
| **Tiered budgets** | Each agent category has defined token budget per interaction | Prevents budget creep |
| **Context compression** | Older conversation turns summarised when approaching limit | Extends conversation depth |
| **Selective retrieval** | RAG retrieves only relevant chunks (not full documents) | Reduces context window usage |
| **Streaming responses** | Responses streamed to reduce p95 latency | Better perceived performance |
| **Early exit** | Simple queries resolved with lightweight model before full LLM call | Cost savings |
| **Cache common responses** | Frequently asked questions cached at tokenisation service level | Eliminates redundant inference |

**Budget Compliance**: Target cost per interaction < USD $0.05 (BR-005). Budget monitoring per agent type with monthly reviews.

---

## 5. Multi-Modal Interaction Patterns

### 5.1 Supported Modalities

| Modality | Agents Supporting | Implementation |
|----------|-------------------|----------------|
| **Text (primary)** | All agents | Natural language conversation |
| **Push Notifications** | PTA-01, PTA-02, MIA-03 | Event-driven alerts via mobile SDK |
| **Email** | PTA-01, PTA-02, MIA-03 | Structured email notifications |
| **SMS** | PTA-01, PTA-02, MIA-03 | Short-form text notifications |
| **Voice (future)** | CSA-01, CSA-03 | Voice-to-text transcription + LLM (Mature phase) |
| **Visual (future)** | PTA-01, PTA-02 | Parcel photo for damage reporting (Mature phase) |

### 5.2 Channel-to-Agent Mapping

| Channel | Agents Available | Interaction Type |
|---------|-----------------|------------------|
| **Mobile App** | CSA-01, SA-01, SA-02, PTA-01, PTA-02, MIA-03, RSA-02, COMPA-01 | Primary AI engagement; SDK embedding (ADR-004) |
| **Web Portal** | CSA-01, CSA-02, CSA-03, SA-01, SA-02, PTA-01, RSA-02, COMPA-01 | Unified web portal; full agent portfolio |
| **Call Centre** | CSA-01 (co-pilot), CSA-02, OPA-01 | Staff co-pilot; no standalone AI |
| **Retail (4,000 shops)** | RSA-01, RSA-02 | Kiosk AI + staff co-pilot |
| **Self-Service** | CSA-01, CSA-03, PTA-01, RSA-02, COMPA-01 | Digital self-service with embedded AI |
| **Push/SMS/Email** | PTA-01, PTA-02, MIA-03 | Notification delivery only |
| **Internal Dashboards** | OPA-02, ANA-01, ANA-02, MIA-01, MIA-02, MIA-03, COMPA-02 | Staff-facing operational tools |

### 5.3 Cross-Channel Continuity

Customer conversations initiated on one channel are tracked via **session correlation** to enable continuity when switching channels:

| Continuity Feature | Implementation |
|-------------------|----------------|
| **Session Correlation ID** | UUID generated at first interaction; shared across channels |
| **Context Portability** | Session state retrievable from Session Store by correlation ID |
| **Channel Handoff** | Customer can switch channels without repeating context |
| **Consistency** | Agent responses consistent regardless of channel (ADR-005) |
| **Privacy** | Tokenised customer ID shared across channels; no raw PII in session store |

---

## 6. Agent-to-Agent Communication Protocols

### 6.1 Communication Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                    Agent Communication Bus                       │
│   (Event-Driven, Structured Messages via Platform Event Bus)      │
│                                                                  │
│  ┌────────────────┐    ┌──────────────────┐    ┌─────────────┐   │
│  │ Agent A        │───→│  Agent Bus       │───→│ Agent B     │   │
│  │ (Publisher)    │    │  (Event Router)  │    │ (Subscriber)│   │
│  └────────────────┘    └──────────────────┘    └─────────────┘   │
│         │                    │                  │               │
│         │   Message Types:  │                  │               │
│         │   • Intent Handoff│                  │               │
│         │   • Data Request │                  │               │
│         │   • Tool Result  │                  │               │
│         │   • Escalation   │                  │               │
│         │   • Status       │                  │               │
└─────────────────────────────────────────────────────────────────┘
```

### 6.2 Agent Communication Protocol Specification

| Attribute | Specification |
|-----------|---------------|
| **Transport** | Internal event bus (Kafka/Pub-Sub managed service) |
| **Message Format** | JSON with schema registry validation |
| **Guarantee** | At-least-once delivery with deduplication |
| **Latency Target** | <500ms for agent-to-agent communication |
| **Encryption** | TLS 1.3 for all bus communication |
| **Authentication** | mTLS between agent services |

### 6.3 Agent-to-Agent Collaboration Matrix

| Source Agent | Target Agent | Communication Pattern | Trigger | Message Type |
|-------------|-------------|---------------------|---------|------------|
| CSA-01 | PTA-01 | Intent Handoff | Customer requests parcel status | `intent_handoff:parcel_tracking` |
| PTA-01 | SA-01 | Intent Handoff | Customer inquires about shipping options | `intent_handoff:shipping_recommendation` |
| CSA-01 | CSA-02 | Intent Handoff | Complaint pattern detected | `intent_handoff:complaint_triage` |
| Any Agent | COMPA-01 | Data Request | Personalisation or marketing data access | `consent_check:request_id` |
| Any Agent | COMPA-02 | Data Request | Response contains factual claims | `validation_check:response_id` |
| CSA-01 | CSA-03 | Intent Handoff | Customer switches language | `language_switch:target_language` |
| PTA-02 | MIA-03 | Event Notification | Exception event triggers engagement | `proactive_trigger:exception_id` |
| CSA-01/PTA-01/SA-01 | ANA-01 | Data Feed | Interaction data feeds insights | `analytics_feed:interaction_data` |

### 6.4 Agent Communication Message Schema

```json
{
  "message_id": "uuid",
  "source_agent": "CSA-01",
  "target_agent": "PTA-01",
  "message_type": "intent_handoff|data_request|tool_result|escalation|status",
  "timestamp": "ISO-8601",
  "correlation_id": "session_uuid",
  "payload": {
    "intent": "parcel_tracking",
    "entities": {"tracking_number": "tok_abc"},
    "context": "summary_of_prior_conversation",
    "confidence": 0.92,
    "metadata": {
      "customer_id": "tokenised_id",
      "channel": "mobile_app",
      "request_id": "req_uuid"
    }
  },
  "ttl_seconds": 300,
  "reply_to": "agent_bus_queue_CSA-01"
}
```

### 6.5 Agent Communication Governance

| Rule | Description |
|------|-------------|
| **No Direct Agent-to-Agent Calls** | All agent communication routed through the Agent Communication Bus |
| **Schema Registry** | All message types registered in schema registry; versioned |
| **Dead Letter Queue** | Failed messages routed to DLQ for inspection and replay |
| **Rate Limiting** | Per-agent rate limits to prevent message storms |
| **Audit Trail** | All agent-to-agent communication logged for governance |
| **Circuit Breaker** | Agent communication fails if target agent unavailable >30 seconds |

---

## 7. Knowledge Retrieval Patterns

### 7.1 RAG Architecture

```
┌──────────────────────────────────────────────────────────────────┐
│                    RAG Pipeline Architecture                     │
│                                                                   │
│  Customer Query                                                    │
│      │                                                            │
│      ▼                                                            │
│  ┌──────────────┐    ┌───────────────┐    ┌────────────────────┐ │
│  │  Query        │    │  Vector Search │    │  Authoritative    │ │
│  │  Embedding    │───→│  (Vector DB)   │───→│  Data Sources      │ │
│  │  Generation   │    │  Top-K Retrieval│   │  (CRM, Pricing,    │ │
│  └──────────────┘    └───────────────┘    │   Products, Service  │ │
│      │                                  └────────────────────┘ │
│      │      │                                                   │
│      │      └─────────────────────────────────────────┐         │
│      ▼                                                 ▼        │
│  ┌─────────────────────┐      ┌──────────────────────────────┐  │
│  │  Context Assembly     │      │  Grounding Engine             │  │
│  │  (System Prompt +     │      │  (Fact Verification +          │  │
│  │   Retrieved Chunks +  │      │   Source Citation)             │  │
│  │   Conversation Hist.)│      └──────────────────────────────┘  │
│  └─────────────────────┘              │                             │
│           │                           ▼                              │
│           ▼                ┌──────────────────────┐                  │
│  ┌─────────────────┐     │  LLM Inference         │                  │
│  │  Token Budget    │────→│  (Cloud or On-Prem)     │                  │
│  │  Check           │     └──────────────────────┘                  │
│  └─────────────────┘           │                                   │
│                                ▼                                  │
│                      ┌────────────────────┐                        │
│                      │  Response          │                        │
│                      │  Validation (FR-016)│                        │
│                      └────────────────────┘                        │
└──────────────────────────────────────────────────────────────────┘
```

### 7.2 Knowledge Sources

| Source | Type | Agents Using | Update Frequency | Authority Level |
|--------|------|-------------|------------------|-----------------|
| **CRM System** | Relational Database | CSA-01, CSA-02, OPA-01, RSA-01 | Real-time | Authoritative (customer data) |
| **Pricing Systems** | API Service | CSA-01, SA-01, SA-02, RSA-01, RSA-02 | Near real-time | Authoritative (fees, pricing) |
| **Product Systems** | API Service | SA-01, SA-02, RSA-01, RSA-02 | Near real-time | Authoritative (catalog) |
| **GCP Event Manager** | Event Stream | PTA-01, PTA-02, OPA-02 | Real-time | Authoritative (logistics) |
| **Service Catalog** | Document Store | CSA-01, CSA-02, RSA-01 | Batch (daily) | Authoritative (service info) |
| **Regulatory Guidelines** | Document Store | CSA-02, COMPA-02 | On-change | Authoritative (compliance) |
| **Customer Data Platform** | Data Lakehouse | SA-01, MIA-01, MIA-02, MIA-03, ANA-01, ANA-02 | Real-time | Authoritative (analytics) |
| **Consent Service** | Database | All agents | Real-time | Authoritative (consent) |

### 7.3 Retrieval Patterns by Agent Category

| Agent Category | Retrieval Pattern | Vector DB | Structured Query | Cache Strategy |
|---------------|------------------|-----------|------------------|----------------|
| **CSA** | Hybrid RAG + Direct API | Service catalog, FAQ | CRM, pricing, products | Common queries cached (TTL: 5 min) |
| **SA** | Catalog-based retrieval + API | Product descriptions | Pricing, availability | Product data cached (TTL: 30 min) |
| **PTA** | Event stream subscription | Historical delivery data | Real-time tracking events | Status cached (TTL: 60 sec) |
| **MIA** | Batch ML processing | Customer behaviour vectors | CDP queries | Segment data cached (TTL: 1 hour) |
| **RSA** | Service catalog RAG | Service info, procedures | Pricing, inventory | Service data cached (TTL: 15 min) |
| **OPA** | API-driven queries | Operational procedures | CRM, ERP, SLA data | Operational data cached (TTL: 5 min) |
| **ANA** | Data lakehouse queries | Analytics datasets | CDP, event bus | Aggregates cached (TTL: 1 hour) |
| **COMPA** | Rules-based verification | Compliance rules | Consent records | Compliance rules cached (TTL: 24 hours) |

### 7.4 Knowledge Base Versioning

| Component | Versioning Strategy | Update Mechanism |
|-----------|-------------------|------------------|
| **System Prompts** | Versioned in Git; deployed via CI/CD | Agent release pipeline |
| **Domain Knowledge Bases** | Semantic versioning; hot-reload supported | Knowledge update pipeline |
| **RAG Indexes** | Incremental updates; full re-index weekly | Scheduled re-index + event-driven updates |
| **Authoritative Data** | API versioning; backward-compatible | Source system integration |

---

## 8. Performance Targets and SLAs

### 8.1 Agent Performance SLAs

| Metric | Target | Applies To | Measurement |
|--------|--------|-----------|-------------|
| **First Response Time** | <2 seconds (p95) | All customer-facing agents | From customer input to first token |
| **Full Resolution Time** | <30 seconds (p95) | CSA, PTA, SA, RSA | From query to complete response |
| **First-Contact Resolution** | ≥85% | CSA-01, PTA-01 | Queries resolved without escalation |
| **Escalation Rate** | ≤40% | CSA-01 (target: routine deflection) | Escalations / total interactions |
| **Escalation Latency** | ≤30 seconds | All agents | From escalation trigger to human connection |
| **Availability** | 99.9% | Customer-facing agents | During trading hours |
| **Accuracy** | ≥85% | CSA-01 (routine queries) | Verified resolution rate |
| **ETA Prediction Accuracy** | ≥85% within 4-hour window | PTA-01 | Predicted vs actual delivery time |
| **Hallucination Rate** | <2% | All agents producing customer-facing output | Verified against authoritative data |

### 8.2 Platform Performance SLAs

| Metric | Target | Measurement |
|--------|--------|-------------|
| **Platform Availability** | 99.9% | Uptime during trading hours |
| **Concurrent Users** | 50,000 (Y1) → 100,000 (Y3) | NFR-S-001 |
| **Model Inference Latency** | <1,500ms (p95) | NFR-P-003 |
| **Tokenisation Overhead** | ~50ms | ADR-001 |
| **Agent-to-Agent Communication** | <500ms | Internal bus latency |
| **New Agent Onboarding** | 2 weeks | BR-005 |
| **Cost per Interaction** | <USD $0.05 | BR-005 |

### 8.3 SLO-Based Alerting

| Alert Condition | Threshold | Severity | Action |
|-----------------|-----------|----------|--------|
| p95 response > 3 seconds | >3 sec p95 for 5 min | P1 | Auto-scale; notify platform team |
| Hallucination rate > 2% | >2% for 1 hour | P1 | Model rollback; notify AI engineering |
| Availability < 99.9% | <99.9% for any 24h period | P1 | Incident response; notify all |
| Escalation rate > 50% | >50% for 1 hour | P2 | Threshold calibration; notify AI team |
| Cost per interaction > USD $0.06 | >USD $0.06 for 1 day | P2 | Budget review; notify programme director |
| Model drift detected | >5% accuracy drop | P2 | Retraining pipeline triggered |
| Tokenisation service latency > 100ms | >100ms p95 | P1 | Failover to backup tokenisation instance |

---

## 9. Model Selection Rationale and Fallback Strategies

### 9.1 Model Strategy Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                    Model Selection Architecture                       │
│                                                                     │
│  ┌─────────────────────────────────────────────────────────────┐    │
│  │  Model Abstraction Layer (Provider-Agnostic)               │    │
│  │  ┌───────────┬───────────┬───────────┬───────────────────┐    │
│  │  │ Provider A│ Provider B│ Provider C│  On-Prem Model    │    │
│  │  │ (Primary) │ (Secondary)│ (Tertiary)│  (Sensitive)      │    │
│  │  └───────────┴───────────┴───────────┴───────────────────┘    │
│  └─────────────────────────────────────────────────────────────┘    │
│                            │                                       │
│                            ▼                                       │
│  ┌─────────────────────────────────────────────────────────────┐    │
│  │  Model Router + Health Check                                │    │
│  │  • Per-agent model assignment                                 │    │
│  │  • Health monitoring (latency, error rate, availability)       │    │
│  │  • Automatic failover to next provider                         │    │
│  │  • Circuit breaker pattern                                   │    │
│  └─────────────────────────────────────────────────────────────┘    │
└─────────────────────────────────────────────────────────────────────┘
```

### 9.2 Model Selection by Agent Category

| Agent Category | Primary Model Type | Rationale | Fallback Strategy |
|---------------|-------------------|-----------|-------------------|
| **CSA** | Conversational LLM (cloud) | Multi-turn dialogue; broad knowledge; natural language | Secondary provider LLM; cached responses for common queries |
| **CSA-02** | Domain-specific LLM (on-prem) | Sensitive complaint processing; APP 8 compliance | Human escalation; cached complaint templates |
| **SA** | Recommendation Engine + lightweight LLM | Fast decisions; product data integration | Rule-based fallback; static product catalogue |
| **PTA** | Predictive Model + lightweight formatter | Real-time performance; minimal LLM overhead | Direct API response; cached status data |
| **RSA** | Co-Pilot LLM + RAG | Staff-facing suggestions; service catalog retrieval | Static knowledge base; human escalation |
| **OPA** | Workflow Engine + lightweight LLM | Automation-focused; minimal conversational need | Rule-based workflow; human escalation |
| **MIA/ANA** | ML Engine + Analytics LLM | Batch processing; data-intensive | Pre-computed analytics; static reports |
| **COMPA** | Rules Engine + lightweight LLM | Compliance rules; structured verification | Static compliance rules; human review |

### 9.3 Fallback Hierarchy

```
Tier 1: Primary Model (Cloud)
    ↓  [Health check fails]
Tier 2: Secondary Model (Alternative Provider)
    ↓  [Health check fails]
Tier 3: Tertiary Model (Different Provider or Region)
    ↓  [Health check fails]
Tier 4: Cache-Only Mode (Pre-computed responses)
    ↓  [Cache miss or sensitive workflow]
Tier 5: On-Prem Model (for sensitive workflows per ADR-001)
    ↓  [All models unavailable]
Tier 6: Graceful Degradation (Limited functionality with notice)
    ↓
Tier 7: Human Escalation (Full handoff)
```

### 9.4 Health Check and Failover

| Check | Frequency | Action on Failure |
|-------|-----------|-------------------|
| **Latency check** | Every 10 seconds | If p95 > 3 sec for 30 sec → failover to next provider |
| **Error rate check** | Every 30 seconds | If error rate > 5% for 60 sec → failover |
| **Availability check** | Every 60 seconds | If health endpoint fails → failover |
| **Quality check** | Every 1 hour (sampling) | If accuracy < 70% → flag for review; no auto-failover |
| **Cost check** | Daily | If cost exceeds budget → alert for review |

### 9.5 Vendor Lock-In Mitigation (R-002)

| Mitigation | Implementation |
|-----------|----------------|
| **Model Abstraction Layer** | Standardised API contract (INT-006); all providers conform |
| **Multi-Provider Strategy** | Minimum 2 cloud providers; on-prem for sensitive workflows |
| **Prompt Portability** | Prompts designed for model-agnostic patterns; no provider-specific features |
| **Model Registry** | All models registered with version, provider, and performance data |
| **Contract Diversification** | No single provider >60% of inference volume |

---

## 10. Agent Orchestration Patterns

### 10.1 Centralised Orchestrator Architecture

```
┌─────────────────────────────────────────────────────────────┐
│              Agent Orchestrator (AI-01)                      │
│                                                              │
│  ┌────────────────────────────────────────────────────────┐ │
│  │  Request Ingestion Layer                               │ │
│  │  • Channel normalisation (SDK → standard format)       │ │
│  │  • Authentication & authorisation                     │ │
│  │  • Rate limiting (per customer, per session)           │ │
│  └────────────────────────────────────────────────────────┘ │
│                                                              │
│  ┌────────────────────────────────────────────────────────┐ │
│  │  Complexity Router (AI-06) — ADR-002                   │ │
│  │  • Intent classification (NLU)                       │ │
│  │  • Complexity scoring (rule-based + ML)               │ │
│  │  • Risk detection (complaints, security, legal)       │ │
│  │  • Routing decision:                                    │ │
│  │    - Routine → Autonomous Agent                       │ │
│  │    - Moderate → AI + Human Review Queue                │ │
│  │    - High-Risk → Immediate Human Escalation            │ │
│  └────────────────────────────────────────────────────────┘ │
│                                                              │
│  ┌────────────────────────────────────────────────────────┐ │
│  │  Agent Dispatch Layer                                    │ │
│  │  • Agent selection based on intent and complexity       │ │
│  │  • Session routing (continuation vs new session)        │ │
│  │  • Agent-to-agent handoff coordination                  │ │
│  │  • Fallback and retry logic                             │ │
│  └────────────────────────────────────────────────────────┘ │
│                                                              │
│  ┌────────────────────────────────────────────────────────┐ │
│  │  Response Orchestration                                    │ │
│  │  • Response validation (FR-016)                        │ │
│  │  • Consent verification (COMPA-01)                    │ │
│  │  • Compliance check (COMPA-02)                        │ │
│  │  • Token de-tokenisation                                  │ │
│  │  • Channel-specific formatting                          │ │
│  └────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
```

### 10.2 Orchestration Flow

| Step | Component | Action | Latency Budget |
|------|-----------|--------|---------------|
| 1 | Request Ingestion | Authenticate, normalise, rate-limit | <50ms |
| 2 | Language Detection | Detect input language | <100ms |
| 3 | Intent Classification | NLU intent detection | <200ms |
| 4 | Complexity Scoring | Calculate complexity and risk score | <100ms |
| 5 | Routing Decision | Route to agent or escalate | <50ms |
| 6 | Session Retrieval | Load session context from Session Store | <100ms |
| 7 | Agent Dispatch | Dispatch to appropriate agent | <50ms |
| 8 | Agent Processing | Agent processes request (varies by agent type) | <1,500ms |
| 9 | Response Validation | Validate against authoritative data (FR-016) | <200ms |
| 10 | Compliance Check | Check consent and compliance | <100ms |
| 11 | De-tokenisation | Convert tokens back to PII | <50ms |
| 12 | Response Delivery | Format and deliver to channel | <100ms |
| **Total** | | **<2,000ms (p95 target)** | |

### 10.3 Agent Registry (AI-07)

| Attribute | Specification |
|-----------|---------------|
| **Purpose** | Version control, lifecycle management, capability discovery |
| **Contents** | Agent ID, version, capabilities, model assignment, health status, SLA compliance |
| **Operations** | Register, deregister, update, health check, capability search |
| **API** | REST with versioned endpoints |
| **Integration** | CI/CD pipeline for automated registration; manual override for emergencies |

---

## 11. Design Patterns

### 11.1 Tool-Use Patterns

#### 11.1.1 Tool Categories

| Tool Category | Examples | Agents Using | Implementation |
|--------------|----------|-------------|----------------|
| **API Calls** | CRM query, pricing lookup, product catalog, GCP Event Manager | All agents | REST/GraphQL APIs with authentication |
| **Database Queries** | Customer profile lookup, interaction history, consent records | CSA, SA, PTA, COMPA | Structured query language with row-level security |
| **Event Publishing** | Notification events, analytics events, consent events | All agents | Event bus with schema registry |
| **External Services** | SMS/Email delivery, payment processing, barcode scanning | PTA, RSA, SA | Third-party service APIs with circuit breakers |
| **File Operations** | Document retrieval, report generation, data export | ANA, COMPA | Secure file system with access controls |

#### 11.1.2 Tool Use Pattern: Structured Tool Calls

```json
{
  "tool_call": {
    "tool_id": "crm_customer_lookup",
    "parameters": {
      "customer_id": "tokenised_id",
      "fields": ["name", "contact", "recent_parceles"]
    },
    "timeout_ms": 5000,
    "retry": {"max_retries": 2, "backoff_ms": 500}
  }
}
```

#### 11.1.3 Tool Result Handling

| Result Type | Handling | Fallback |
|-------------|----------|----------|
| **Success** | Process result; continue conversation | None |
| **Timeout** | Retry with exponential backoff; max 3 retries | Inform customer of temporary unavailability |
| **Authentication Error** | Re-authenticate; retry once | Escalate to human agent |
| **Not Found** | Search alternative data sources | Provide general response |
| **Rate Limited** | Queue request; retry after delay | Provide cached data if available |

### 11.2 Guardrail Patterns

#### 11.2.1 Defence-in-Depth Guardrails

```
┌────────────────────────────────────────────────────────────────┐
│                    Guardrail Layers                             │
│                                                                │
│  Layer 1: Pre-Input Validation                                 │
│  ├── Input sanitisation (XSS, SQL injection prevention)         │
│  ├── Prompt injection detection                                 │
│  ├── Language detection and validation                            │
│  └── Token budget enforcement                                   │
│                                                                │
│  Layer 2: In-Context Constraints                               │
│  ├── System prompt safety constraints                            │
│  ├── Domain boundary enforcement                               │
│  ├── Response length limits                                     │
│  └── Confidence threshold enforcement                            │
│                                                                │
│  Layer 3: Post-Output Verification                             │
│  ├── Factual grounding check (FR-016)                            │
│  ├── PII leakage detection                                       │
│  ├── Compliance rule validation                                 │
│  └── Hallucination detection                                    │
│                                                                │
│  Layer 4: Runtime Monitoring                                    │
│  ├── Real-time accuracy tracking                               │
│  ├── Anomaly detection                                          │
│  └── Automated circuit breaker                                  │
└────────────────────────────────────────────────────────────────┘
```

#### 11.2.2 Privacy Guardrails

| Guardrail | Implementation | Applies To |
|-----------|---------------|-----------|
| **PII Tokenisation** | All PII tokenised before cloud inference (ADR-001) | All customer-facing agents |
| **Consent Verification** | Real-time consent check before personalised interactions | SA, PTA, MIA, RSA |
| **Data Minimisation** | Only requested data fields retrieved | All agents |
| **Response PII Filter** | Scan output for untokenised PII | All agents |
| **Session Isolation** | Customer sessions isolated; no cross-session data leakage | All agents |
| **Audit Logging** | Tamper-evident logging of all interactions | All agents |

#### 11.2.3 Safety Guardrails

| Guardrail | Implementation | Applies To |
|-----------|---------------|-----------|
| **Domain Boundary** | Agent only responds within its capability scope | All agents |
| **High-Risk Topic Detection** | Complaints, security, legal topics auto-escalate | CSA, PTA, RSA |
| **Confidence Threshold** | Below 70% confidence → offer human escalation | All customer-facing agents |
| **Response Validation** | Facts verified against authoritative data sources | All agents (FR-016) |
| **Adversarial Input Detection** | Detect and block prompt injection, jailbreak attempts | All customer-facing agents |
| **Output Length Limits** | Maximum response length enforced per agent category | All agents |

### 11.3 Error Handling and Recovery Patterns

#### 11.3.1 Error Classification

| Error Type | Classification | Recovery Strategy | Customer Impact |
|-----------|---------------|-------------------|-----------------|
| **Transient Error** | Temporary service unavailable | Retry with exponential backoff; max 3 retries | None (automated) |
| **Data Error** | Missing or invalid data | Fallback to cached data or alternative source | Minimal (slight delay) |
| **Model Error** | Model returns low-confidence or hallucinated response | Reroute to fallback model; escalate if persistent | None (seamless) |
| **Authentication Error** | Token expired or invalid | Re-authenticate silently; notify if fails | Minimal (auth prompt) |
| **Infrastructure Error** | Service outage or platform failure | Circuit breaker; graceful degradation; human escalation | Visible (service notice) |
| **Compliance Error** | Consent violation or regulatory issue | Immediately halt interaction; log incident; escalate | Visible (handled by human) |

#### 11.3.2 Circuit Breaker Pattern

| Parameter | Value | Rationale |
|-----------|-------|----------|
| **Failure Threshold** | 5 consecutive failures | Prevents cascading failures |
| **Circuit Open Duration** | 60 seconds | Allows time for service recovery |
| **Half-Open Test** | 1 request after open period | Tests if service has recovered |
| **Recovery Condition** | Test request succeeds | Circuit closes; normal operation resumes |
| **Fallback Action** | Cached response or human escalation | Maintains customer experience |

#### 11.3.3 Retry Policy

| Error Type | Max Retries | Backoff Strategy | Fallback |
|-----------|-----------|------------------|----------|
| **API Timeout** | 3 | Exponential (1s, 2s, 4s) | Cached response or escalation |
| **Rate Limit** | 3 | Exponential with jitter | Queue and retry after delay |
| **Service Unavailable** | 2 | Fixed (5s, 10s) | Alternative service or escalation |
| **Authentication** | 1 | None (immediate retry) | Re-authenticate prompt |
| **Data Error** | 0 | N/A | Alternative data source |

### 11.4 Session Management and State Persistence

#### 11.4.1 Session Lifecycle

```
Session Creation (Customer Login)
    │
    ▼
Session Active (Customer Interaction)
    ├── Conversation turns stored in Session Store
    ├── Context maintained across turns
    ├── Agent-to-agent handoffs within same session
    └── Real-time consent verification
    │
    ▼
Session Idle (No Activity > 30 minutes)
    ├── Session state persisted to long-term storage
    ├── Working memory cleared
    └── Session marked as idle
    │
    ▼
Session Resume (Customer Returns)
    ├── Session state reloaded from long-term storage
    ├── Context summarised for context window
    └── Conversation continues from last interaction
    │
    ▼
Session Termination (Explicit Logout or 24h Inactivity)
    ├── Final session state archived
    ├── Working memory cleared
    ├── Session Store entry expired
    └── Audit trail finalised
```

#### 11.4.2 Session State Persistence

| Persistence Layer | Technology | Contents | TTL |
|-------------------|-----------|----------|-----|
| **Volatile (Working Memory)** | In-memory | Tool call state, RAG context | Request lifecycle |
| **Session (Short-Term)** | Redis Cluster | Conversation history, context | 30 min idle / 24h total |
| **Archival (Long-Term)** | Vector DB + Object Store | Archived sessions, customer history | Policy-defined (2 years for interactions) |
| **Audit** | Tamper-Evident Log | All interactions, compliance data | Indefinite (regulatory requirement) |

---

## 12. Multi-Agent Collaboration Workflows

### 12.1 Collaboration Pattern: Customer Query Resolution

```
Customer: "Where is my parcel?"
    │
    ▼
┌─────────────┐     ┌────────────────┐     ┌───────────────┐
│  Orchestrator│────→│  Complexity    │────→│  CSA-01       │
│  (AI-01)    │     │  Router (AI-06)│     │  (General CS) │
└─────────────┘     └────────────────┘     └───────┬───────┘
                                                  │
                      Classification: ROUTINE      │
                      Intent: parcel_tracking      │
                                                  │
                                                  ▼
                                          ┌───────────────┐
                                          │   Agent Bus   │────→ PTA-01
                                          │ (Intent        │     (Tracking)
                                          │  Handoff)      │     ← Returns status
                                          └───────────────┘
                                                  │
                                                  ▼
                                          ┌───────────────┐
                                          │  COMPA-01     │────→ Consent check: OK
                                          │  (Consent)    │
                                          └───────────────┘
                                                  │
                                                  ▼
                                          ┌───────────────┐
                                          │  COMPA-02     │────→ Validation: OK
                                          │  (Compliance) │
                                          └───────────────┘
                                                  │
                                                  ▼
                                          ┌───────────────┐
                                          │  Response       │────→ Customer
                                          │  Assembly       │     "Your parcel is at..."
                                          └───────────────┘
```

### 12.2 Collaboration Pattern: Complaint Handling

```
Customer: "I want to complain about my delivery"
    │
    ▼
┌─────────────┐     ┌────────────────┐     ┌───────────────┐
│  Orchestrator│────→│  Complexity    │────→│  CSA-02       │
│  (AI-01)    │     │  Router (AI-06)│     │  (Complaint    │
└─────────────┘     └────────────────┘     │   Triage)     │
                                          └───────┬───────┘
                                                  │
                      Classification: HIGH-RISK   │
                      Topic: complaint            │
                      Routing: On-Prem (ADR-001)  │
                                                  │
                                                  ▼
                                          ┌───────────────┐
                                          │  On-Prem       │────→ Complaint processed
                                          │  Processing    │     entirely on-premises
                                          └───────────────┘
                                                  │
                                                  ▼
                                          ┌───────────────┐
                                          │  COMPA-02     │────→ Compliance audit
                                          │  (Compliance) │     ACCC template check
                                          └───────────────┘
                                                  │
                                                  ▼
                                          ┌───────────────┐
                                          │  Escalation    │────→ Human complaints
                                          │  (if needed)   │     team within 15 sec
                                          └───────────────┘
```

### 12.3 Collaboration Pattern: Proactive Engagement

```
[Event Stream] Parcel exception detected (failed delivery)
    │
    ▼
┌───────────────┐     ┌───────────────┐
│   PTA-02       │────→│   MIA-03      │
│   (Exception   │     │   (Proactive  │
│   Detection)   │     │   Engagement)│
└───────┬───────┘     └───────┬───────┘
        │                       │
        │  Exception event       │  Next-best-action:
        │  with customer ID       │  redelivery offer
        │                          │
        ▼                          ▼
┌───────────────┐     ┌───────────────┐
│  COMPA-01      │────→│  COMPA-02     │
│  (Consent      │     │  (Compliance  │
│  Verification) │     │  Validation) │
└───────┬───────┘     └───────┬───────┘
        │                       │
        │  Marketing consent:    │  Content validated
        │  YES                     │
        ▼                          ▼
┌───────────────────────────────────────────────┐
│              Proactive Push Notification        │
│  "Your parcel delivery was attempted but       │
│   failed. Would you like to schedule a         │
│   redelivery? Tap here to choose a time."       │
└───────────────────────────────────────────────┘
```

---

## 13. Security and Compliance Design

### 13.1 Security Architecture

| Layer | Controls | Implementation |
|-------|----------|---------------|
| **Network** | Zero-trust; mTLS; network segmentation | All agent-to-agent and agent-to-service communication encrypted |
| **Identity** | Service accounts; RBAC; least privilege | Each agent has dedicated service account with scoped permissions |
| **Data** | Tokenisation; encryption at rest (AES-256); encrypted in transit (TLS 1.3) | PII never leaves MagicDelivery infrastructure in plaintext |
| **Application** | Input validation; prompt hardening; output filtering | Adversarial testing; R-022 mitigation |
| **Platform** | Secrets management (HashiCorp Vault); automated key rotation | No secrets in code or configuration |
| **Compliance** | Audit logging; DPIA automation; regulatory reporting | APP-compliant by design |

### 13.2 Privacy Architecture

| Component | Privacy Control | Regulatory Basis |
|-----------|----------------|-----------------|
| **Tokenisation Service** | PII tokenised before cloud inference | Privacy Act 1988 APP 8 |
| **Consent Service** | Granular consent per purpose, per channel | Privacy Act 1988 APP 3 |
| **Data Retention** | Automated deletion per retention policy | Privacy Act 1988 APP 11 |
| **Data Access** | Row-level security; role-based access | Privacy Act 1988 APP 11 |
| **Audit Trail** | Tamper-evident logging of all data processing | Privacy Act 1988 APP 12 |
| **Cross-Border** | Zero PII transfer without consent | NFR-C-001; APP 8 |

---

## 14. Traceability Matrix

### 14.1 Agent Design to Agent Inventory (AGT-INV)

| Agent ID | AGT-INV Section | Design Coverage |
|----------|-----------------|-----------------|
| CSA-01 | §3.1 | §2.1 — Full capability spec, interaction model, memory, token budget |
| CSA-02 | §3.1 | §2.1 — On-prem processing, compliance guardrails |
| CSA-03 | §3.1 | §2.1 — Multilingual patterns, language switching |
| SA-01 | §3.2 | §2.2 — Recommendation patterns, RAG integration |
| SA-02 | §3.2 | §2.2 — Bulk operations, seller-specific patterns |
| PTA-01 | §3.3 | §2.3 — Real-time patterns, event processing |
| PTA-02 | §3.3 | §2.3 — Proactive outreach, exception handling |
| MIA-01 | §3.4 | §2.4 — Analytics patterns, ML workflows |
| MIA-02 | §3.4 | §2.4 — Campaign optimisation, attribution |
| MIA-03 | §3.4 | §2.4 — Proactive engagement, event-driven triggers |
| RSA-01 | §3.5 | §2.5 — Co-pilot pattern, staff-facing design |
| RSA-02 | §3.5 | §2.5 — Self-service kiosk design |
| OPA-01 | §3.6 | §2.6 — Co-pilot pattern, real-time assistance |
| OPA-02 | §3.6 | §2.6 — Workflow automation, monitoring |
| ANA-01 | §3.7 | §2.7 — Analytics agent, insight generation |
| ANA-02 | §3.7 | §2.7 — Predictive analytics, scenario modelling |
| COMPA-01 | §3.8 | §2.8 — Consent management, privacy design |
| COMPA-02 | §3.8 | §2.8 — Compliance monitoring, governance |

### 14.2 Agent Design to Application Inventory (APPINV)

| Agent ID | Target Application | APPINV Application ID | Design Reference |
|----------|-------------------|----------------------|------------------|
| CSA-01, CSA-02, CSA-03 | AI Agent Platform | TAPP-02 | §10 — Orchestration |
| CSA-01, CSA-03, PTA-01 | Enhanced Mobile App | TAPP-08 | §5 — Multi-Modal |
| SA-01, SA-02 | AI-Powered Shopping Experience | TAPP-07 | §2.2 — Shopping Agents |
| SA-01, SA-02 | Composable AI Services | TAPP-03 | §7 — RAG Integration |
| PTA-01, PTA-02 | AI Agent Platform | TAPP-02 | §10 — Orchestration |
| MIA-01, MIA-02, MIA-03 | Marketing Intelligence Platform | TAPP-06 | §2.4 — Marketing Agents |
| MIA-01, ANA-01, ANA-02 | Customer Data Platform | TAPP-04 | §7 — Knowledge Retrieval |
| RSA-01, RSA-02 | Retail Digital Integration | TAPP-09 | §2.5 — Retail Agents |
| OPA-01, OPA-02 | AI Agent Platform | TAPP-02 | §10 — Orchestration |
| COMPA-01, COMPA-02 | Privacy & Consent Management | TAPP-05 | §2.8 — Compliance Agents |

### 14.3 Agent Design to Architecture Decisions (ADR)

| ADR | Design Reference | Coverage |
|-----|-------------------|----------|
| **ADR-001** (Hybrid AI Deployment) | §1.2, §2.1 (CSA-02), §9.2, §13.2 | Cloud inference + on-prem sensitive processing; tokenisation layer; model selection |
| **ADR-002** (Agent-Human Handoff) | §3.2, §3.3 | Complexity-based routing; escalation paths; context transfer protocol |
| **ADR-003** (Event-Driven Data Fabric) | §6 — Agent Communication Bus; §7.3 — Event stream subscriptions | Event-driven agent-to-agent communication |
| **ADR-004** (SDK Embedding) | §5.2 — Mobile App channel | SDK-based agent integration in mobile app |
| **ADR-005** (Centralised Agent Backend) | §10 — Orchestration; §5.3 — Cross-channel continuity | Centralised orchestrator; multi-channel consistency |
| **ADR-006** (AI Co-Pilot Augmentation) | §2.5 (RSA-01), §2.6 (OPA-01) | Staff co-pilot pattern; no autonomous customer output |
| **ADR-007** (Hybrid Compliance Governance) | §11.2 — Guardrails; §2.8 (COMPA-02) | Pre-deployment DPIA + runtime compliance monitoring |
| **ADR-008** (Tiers-Based Performance) | §8 — Performance SLAs; §9 — Model Selection | Tiers-based performance; predictive scaling; cost control |

### 14.4 Agent Design to Transition Architecture (TRANS)

| Phase | Agents Deployed | Design Reference |
|-------|-----------------|------------------|
| **Foundation (Y1)** | CSA-01, CSA-02, CSA-03, PTA-01, PTA-02, OPA-01, OPA-02, COMPA-01 | All §2 sections for Foundation-phase agents |
| **Scale (Y2-3)** | SA-01, SA-02, RSA-01, RSA-02, MIA-01, MIA-02, MIA-03, ANA-01, COMPA-02 | All §2 sections for Scale-phase agents |
| **Mature (Y3-5)** | ANA-02, full portfolio L5 maturity | §2.7 (ANA-02) |

### 14.5 Agent Design to Business Capability Map (BPCM)

| BPCM Capability | Agent Design Sections |
|-----------------|---------------------|
| **AI-01: Agent Orchestration** | §10 — Orchestration Patterns |
| **AI-02: Hybrid Model Serving** | §9 — Model Selection; §1.2 Platform Layer |
| **AI-03: AI Governance & Compliance** | §2.8 (COMPA-02); §11.2 — Guardrails |
| **AI-04: Agent Telemetry & Observability** | §8.3 — SLO-Based Alerting; §1.1 AP-06 |
| **AI-05: Prompt Engineering & Knowledge Base** | §7 — Knowledge Retrieval Patterns |
| **AI-06: Complexity-Based Routing** | §3.2 — Escalation Paths; §10.1 Orchestrator |
| **AI-07: Agent-to-Agent Collaboration** | §6 — Agent Communication Protocols; §12 — Collaboration Workflows |
| **AI-08: Model Evaluation & MLOps** | §9.4 — Health Check and Failover; §2 — Capability Specs |

---

## 15. Quality Verification

### Quality Checklist

| Check | Status |
|-------|--------|
| Document ID: ARC-001-AGT-DES-v1.0 | ✅ |
| All Document Control fields populated | ✅ |
| 8 agent categories with full capability specifications | ✅ |
| 16 agent instances with detailed specs | ✅ |
| Interaction model (conversational patterns, escalation paths) | ✅ |
| Memory and state management design (3-tier model) | ✅ |
| Context window and token budget management | ✅ |
| Multi-modal interaction patterns | ✅ |
| Agent-to-agent communication protocols | ✅ |
| Knowledge retrieval patterns (RAG, tool use) | ✅ |
| Performance targets and SLAs | ✅ |
| Model selection rationale and fallback strategies | ✅ |
| Agent orchestration patterns | ✅ |
| Multi-agent collaboration workflows (3 patterns) | ✅ |
| Tool-use patterns | ✅ |
| Guardrail patterns (defence-in-depth) | ✅ |
| Error handling and recovery patterns | ✅ |
| Session management and state persistence | ✅ |
| AGT-INV traceability | ✅ |
| APPINV traceability | ✅ |
| ADR traceability (all 8 ADRs) | ✅ |
| TRANS phase traceability | ✅ |
| BPCM capability traceability | ✅ |
| MagicDelivery context maintained throughout | ✅ |
| ArcKit Version: 5.15.2 | ✅ |
| Date: 2026-07-01 | ✅ |
| Model: Qwen3.6-27B | ✅ |

---

*End of Document*
