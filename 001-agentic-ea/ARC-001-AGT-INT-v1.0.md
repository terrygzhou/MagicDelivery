# Agent Integration: AgenticEA — MagicDelivery Agent AI Transformation

> **Template Origin**: Official | **ArcKit Version**: 5.15.2 | **Command**: `/arckit:agentintegration`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-AGT-INT-v1.0 |
| **Document Type** | Agent Integration (AGT-INT) |
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
| 1.0 | 2026-07-01 | ArcKit AI | Initial creation — Multi-agent orchestration patterns, 4 integration layers, cross-agent communication protocols, security & compliance framework, full traceability to AGT-INV, AGT-DES, APPINV, ADR, TRANS | PENDING | PENDING |

---

## Executive Summary

### Purpose

This Agent Integration (AGT-INT) document defines the **multi-agent orchestration patterns, integration layers, and cross-agent communication protocols** for the **AgenticEA — MagicDelivery Agent AI Transformation** programme. It provides the authoritative integration architecture for connecting 16 AI agents across 8 categories operating on the centralised AI Agent Platform (TAPP-02) to existing MagicDelivery systems, customer channels, and compliance frameworks.

This document operationalises the agent inventory (ARC-001-AGT-INV-v1.0), agent design (ARC-001-AGT-DES-v1.0), and architecture decisions (ARC-001-ADR-v1.0) into concrete integration specifications that engineering teams use to implement the agent-to-agent, agent-to-system, and agent-to-channel connectivity required for the 5-year transformation programme.

### Scope

| Aspect | Detail |
|--------|--------|
| **Agent Portfolio** | 16 agent instances across 8 categories |
| **Integration Layers** | 4 (Customer-facing Orchestration, Agent-to-Agent Collaboration, Backend Integration, Analytics & Observability) |
| **Orchestration Patterns** | 6 (Intent Routing, Conversation State Management, Multi-Agent Consensus, Load Balancing, Session Continuity, Cross-Agent Context Sharing) |
| **Communication Protocols** | Event-Driven Agent Bus, Synchronous Tool Calls, Consensus Voting, Handoff Streams |
| **Backend Systems** | 12 existing MagicDelivery systems (CRM, ERP, GCP Event Manager, Pricing, Products, etc.) |
| **Design Horizon** | 5 years (Foundation → Scale → Mature phases) |

### Key Integration Decisions

| Decision | Choice | Rationale |
|----------|--------|-----------|
| **Agent Bus** | Event-Driven (Kafka/Pub-Sub) | Loose coupling; PRIN-09; AI-07 capability |
| **Orchestration Model** | Centralised Agent Orchestrator with Complexity Router | ADR-002; single control plane; consistent experience |
| **Cross-Agent Protocol** | Structured JSON over internal event bus | Schema registry; versioned contracts; auditability |
| **Backend Integration** | API Gateway + Anti-Corruption Layers | PRIN-02 (Composable); PRIN-17 (Legacy Modernization) |
| **Security Model** | mTLS + Token-Based Auth + Consent Verification | PRIN-04 (Security by Design); Zero Trust |
| **Observability** | OpenTelemetry + Custom Agent Telemetry | PRIN-05; structured logs, metrics, traces per agent |

### Architecture Overview

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                      LAYER 1: Customer-Facing Orchestration                      │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐   │
│  │ Mobile   │ │  Web    │ │Call Ctr  │ │ Retail  │ │Self-Svc │ │API Gateway│   │
│  │  App     │ │ Portal  │ │ (Co-Pilot)│ │ Kiosks  │ │  UI     │ │ (INT-001) │   │
│  └────┬─────┘ └────┬─────┘ └────┬─────┘ └────┬─────┘ └────┬─────┘ └────┬──────┘   │
│       │            │            │           │            │           │           │
│       └────────────┴────────────┴───────────┴────────────┴───────────┘           │
│                              │                                                   │
│                    ┌───────▼───────┐                                             │
│                    │   Agent Orch │ ←── Complexity Router (ADR-002)             │
│                    │  estrator    │ ←── Session Manager + Intent Classifier    │
│                    └───────┬───────┘                                             │
└────────────────────┼──────────────────────────────────────────────────────────────┘
                     │
┌────────────────────┼──────────────────────────────────────────────────────────────┐
│           LAYER 2: Agent-to-Agent Collaboration (Event-Driven Bus)                │
│                                                                                    │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────────┐       │
│  │  CSA Agents  │  │  PTA Agents  │  │  SA Agents   │  │  RSA/OPA/ANA/COM│       │
│  │  (3 agents)  │  │  (2 agents)  │  │  (2 agents)  │  │  Agents (9)      │       │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘  └────────┬─────────┘       │
│         │                  │                  │               │                 │
│         └──────────────────┴──────────────────┴───────────────┘                 │
│                              │                                                   │
│                    ┌───────▼───────┐                                           │
│                    │  Agent Bus    │  Intent Handoff | Data Request | Tool Call │
│                    │  (Event-Driven)│  Result | Escalation | Status | Consensus  │
│                    └───────┬───────┘                                           │
└────────────────────┼──────────────────────────────────────────────────────────────┘
                     │
┌────────────────────┼──────────────────────────────────────────────────────────────┐
│           LAYER 3: Backend Integration (API Gateway + Anti-Corruption)             │
│                                                                                    │
│  ┌────────────┐  ┌────────────┐  ┌─────────────┐  ┌───────────┐ ┌──────────────┐  │
│  │ CRM (INT-02)│ │  ERP      │  │ Pricing/Prod │  │ GCP Event │ │ SMS/Email    │  │
│  │            │  │ (INT-005) │  │ Systems       │  │ Manager   │ │ Services     │  │
│  └─────┬──────┘  └─────┬──────┘  └──────┬────────┘  │(INT-003) │ │(INT-004)    │  │
│        │              │               │           └─────┬─────┘ └──────┬───────┘ │
│        └──────────────┴───────────────┴────────────────┴──────────────┘         │
│                              │                                                   │
│                    ┌───────▼───────┐                                            │
│                    │ API Gateway   │ ←── Anti-Corruption Layers (PRIN-17)       │
│                    │ + Schema      │ ←── Published API Contracts (PRIN-02)     │
│                    │   Registry    │ ←── Strangler-Fig Pattern (PRIN-17)        │
│                    └──────────────┘                                            │
└───────────────────────────────────────────────────────────────────────────────────┘
┌──────────────────────────────────────────────────────────────────────────────────────┐
│           LAYER 4: Analytics & Observability                                          │
│  ┌─────────────────────┐  ┌────────────────────┐  ┌───────────────────────────────┐  │
│  │ Agent Telemetry      │  │ Compliance         │  │ Business Metrics              │  │
│  │ (Accuracy, Latency,  │  │ Monitoring          │  │ (FC Resolution, Deflection,   │  │
│  │  Confidence, Tokens) │  │ (Hallucination,     │  │   Revenue, CSAT)              │  │
│  └──────────┬──────────┘  │  DPIA, Audit Trail) │  └──────────┬────────────────────┘ │
│             │             └────────────────────┘              │                     │
│             └───────────────┬────────────────────────────────┘                     │
│                       ┌─────▼─────┐                                              │
│                       │ Dashboard │ ←── OpenTelemetry + Custom Metrics            │
│                       └──────────┘                                              │
└──────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 1. Integration Layer Specifications

### 1.1 Layer 1: Customer-Facing Orchestration Layer

**Purpose**: Provide a unified entry point for all customer-facing AI interactions across 5 engagement channels, managing session lifecycle, intent classification, and agent routing.

#### 1.1.1 Unified Agent Interface

| Attribute | Specification |
|-----------|---------------|
| **Interface Type** | RESTful API + WebSocket (real-time streaming) |
| **API Versioning** | Semantic versioning (v1.x.x); backward-compatible within major version |
| **Content Negotiation** | JSON (primary); SSE for streaming responses |
| **Rate Limiting** | 100 requests/minute per customer session; 10,000 RPM global per agent |
| **Circuit Breaker** | 50% failure threshold; 30-second recovery window |

**API Contract (Unified Agent Interface)**:

```json
{
  "$schema": "https://magicdelivery.io/schemas/agent-interface/v1",
  "type": "object",
  "properties": {
    "session": {
      "session_id": "uuid",
      "customer_id": "tokenised_id",
      "channel": "mobile_app|web_portal|call_centre|retail|self_service",
      "correlation_id": "uuid"
    },
    "interaction": {
      "input": { "text": "string", "language": "en|zh|ar|vi|hi|yue", "modality": "text|push|email|sms" },
      "context": { "previous_intent": "string", "turn_count": "integer", "prior_agents": ["agent_id"] },
      "consent": { "personalisation": "boolean", "marketing": "boolean", "tracking": "boolean" }
    },
    "routing": {
      "detected_intent": "string",
      "intent_confidence": "number (0-1)",
      "complexity_score": "number (0-100)",
      "risk_level": "routine|moderate|high|critical",
      "target_agent": "string (agent_id)"
    }
  }
}
```

#### 1.1.2 Channel Adapters

Each engagement channel has a channel-specific adapter that normalises input to the unified interface:

| Channel | Adapter | Technology | Key Responsibilities |
|---------|---------|-----------|---------------------|
| **Mobile App** | Mobile SDK (ADR-004) | Native iOS/Android (Swift/Kotlin) | Offline buffering, push notification handling, session persistence |
| **Web Portal** | Web Widget SDK | JavaScript/TypeScript | Embedded chat UI, real-time WebSocket connection, SSR compatibility |
| **Call Centre** | CTI Integration Module | SIP/RTP + CRM API | Real-time speech transcription, agent workspace injection, co-pilot mode |
| **Retail Kiosks** | Kiosk Adapter | Kiosk OS + POS API | Session isolation, barcode/QR input handling, printer integration |
| **Self-Service** | Self-Service UI Adapter | React/Next.js | Accessibility compliance (WCAG 2.1 AA), language selection, form input handling |

#### 1.1.3 API Gateway Integration

| Attribute | Specification | Traceability |
|-----------|---------------|-------------|
| **Gateway Technology** | Kubernetes Ingress + API Management Layer | APPINV TAPP-02; ADR-005 |
| **Authentication** | OAuth 2.0 / JWT for customer sessions; mTLS for service-to-service | PRIN-04 |
| **Rate Limiting** | Per-channel quotas; burst handling for peak events (Black Friday, Christmas) | NFR-S-001 |
| **Caching** | Edge caching for static responses; token-level caching for tokenised queries | NFR-P-001 |
| **Routing** | Intent-based routing to agent orchestrator; complexity-based routing (ADR-002) | AI-06 |
| **Anti-Corruption Layer** | Strangler pattern isolation between legacy and AI systems | PRIN-17; APPINV |

### 1.2 Layer 2: Agent-to-Agent Collaboration Layer

**Purpose**: Enable structured communication between the 16 agents through event-driven collaboration patterns, supporting intent handoffs, data requests, tool calls, escalation routing, and consensus patterns.

#### 1.2.1 Agent Communication Bus Architecture

| Attribute | Specification | Traceability |
|-----------|---------------|-------------|
| **Transport** | Apache Kafka / Google Pub-Sub (managed service) | ADR-003; PRIN-09 |
| **Message Format** | JSON with Avro schema registry validation | AI-07 |
| **Delivery Guarantee** | At-least-once with idempotent consumers; deduplication via message ID | PRIN-09 |
| **Latency Target** | <500ms for agent-to-agent communication; <100ms for bus routing | NFR-P-003 |
| **Encryption** | TLS 1.3 for all bus communication | PRIN-04; NFR-SEC-003 |
| **Authentication** | mTLS between agent services; RBAC-scoped subscriptions | NFR-SEC-002 |
| **Retention** | 72-hour event retention; dead letter queue for failed messages | PRIN-09 |
| **Schema Registry** | Versioned event schemas; backward-compatible evolution | PRIN-02 |

#### 1.2.2 Agent Communication Protocol

```
┌─────────────────────────────────────────────────────────────────────────┐
│                        Agent Communication Bus                          │
│    (Event-Driven, Structured Messages via Platform Event Bus)           │
│                                                                        │
│  ┌──────────────┐     ┌──────────────────┐     ┌──────────────┐        │
│  │ Agent A       │────→│  Agent Bus       │────→│ Agent B      │        │
│  │ (Publisher)  │     │  (Event Router)  │     │ (Subscriber) │        │
│  └──────────────┘     └──────────────────┘     └──────────────┘        │
│         │                    │                      │                    │
│         │   Message Types:   │                      │                    │
│         │   • Intent Handoff │                      │                    │
│         │   • Data Request   │                      │                    │
│         │   • Tool Call      │                      │                    │
│         │   • Escalation      │                      │                    │
│         │   • Consensus Vote │                      │                    │
│         │   • Status Update  │                      │                    │
└─────────────────────────────────────────────────────────────────────────┘
```

**Event Schema (Agent Communication Protocol)**:

```json
{
  "event_id": "uuid",
  "event_type": "intent_handoff|data_request|tool_call|escalation|consensus|status",
  "source_agent": "string (agent_id)",
  "target_agent": "string (agent_id) | string[] (multi-target)",
  "timestamp": "ISO-8601",
  "correlation_id": "uuid (session-level)",
  "session_id": "uuid",
  "priority": "routine|elevated|urgent|critical",
  "payload": {
    "data": "object (event-specific)",
    "context": {
      "conversation_summary": "string",
      "entities": "object (tokenised)",
      "confidence": "number (0-1)",
      "language": "string"
    },
    "metadata": {
      "retry_count": "integer",
      "ttl_seconds": "integer",
      "requires_ack": "boolean"
    }
  },
  "consent_boundary": {
    "data_sharing_permitted": "boolean",
    "pii_tokenised": "boolean",
    "compliance_verified": "boolean"
  }
}
```

#### 1.2.3 Agent Collaboration Registry

| Collaboration ID | Source Agent | Target Agent(s) | Pattern | Trigger | Message Type | Latency SLA |
|-----------------|-------------|----------------|---------|---------|------------|-------------|
| **ACR-001** | CSA-01 | PTA-01 | Intent Handoff | Customer requests parcel status | `intent_handoff:parcel_tracking` | <300ms |
| **ACR-002** | PTA-01 | SA-01 | Intent Handoff | Customer inquires about shipping options | `intent_handoff:shipping_recommendation` | <300ms |
| **ACR-003** | CSA-01 | CSA-02 | Intent Handoff | Complaint pattern detected | `intent_handoff:complaint_triage` | <200ms |
| **ACR-004** | Any Agent | COMPA-01 | Data Request | Personalisation or marketing data access | `data_request:consent_check` | <100ms |
| **ACR-005** | Any Agent | COMPA-02 | Tool Call | Response contains factual claims | `tool_call:compliance_validate` | <200ms |
| **ACR-006** | CSA-01 | CSA-03 | Intent Handoff | Customer switches language mid-conversation | `intent_handoff:language_switch` | <200ms |
| **ACR-007** | PTA-02 | MIA-03 | Intent Handoff | Exception event triggers proactive engagement | `intent_handoff:proactive_engagement` | <500ms |
| **ACR-008** | CSA-01, PTA-01, SA-01 | ANA-01 | Data Feed | Interaction data feeds customer insights | `data_feed:interaction_events` | <1s (async) |
| **ACR-009** | CSA-01, PTA-01 | OPA-02 | Status | Operational status changes | `status_update:operational` | <500ms |
| **ACR-010** | MIA-01 | MIA-02 | Data Request | Segmentation data for campaign targeting | `data_request:segment_data` | <500ms |
| **ACR-011** | SA-01 | OPA-02 | Data Feed | Shipping pattern data for operations | `data_feed:shipping_patterns` | <1s (async) |
| **ACR-012** | OPA-01 | CSA-01 | Tool Call | Co-pilot queries customer service context | `tool_call:customer_context` | <300ms |
| **ACR-013** | RSA-01 | CSA-01 | Data Request | Retail staff queries service information | `data_request:service_info` | <500ms |
| **ACR-014** | CSA-02 | COMPA-02 | Tool Call | Complaint validation for compliance | `tool_call:complaint_validation` | <200ms |
| **ACR-015** | ANA-01 | MIA-01 | Data Feed | Customer insights feed segmentation | `data_feed:customer_insights` | <1s (async) |
| **ACR-016** | Any Agent | CSA-01 | Escalation | Agent cannot resolve; fallback to general service | `escalation:fallback_service` | <300ms |

#### 1.2.4 Cross-Agent Context Sharing

When agents collaborate, they share context through the **Context Sharing Protocol**:

| Context Element | Shared By | Shared With | Format | Privacy Control |
|----------------|-----------|------------|--------|----------------|
| **Conversation Summary** | Source agent | Target agent | JSON (abridged) | Tokenised PII; consent-bound |
| **Detected Entities** | Source agent | Target agent | Structured (tokenised) | Tokenised; purpose-limited |
| **Intent Classification** | Orchestrator | All agents | Intent label + confidence | No PII |
| **Customer Consent Flags** | COMPA-01 | Requesting agent | Boolean flags | Consent records only |
| **Resolution Status** | Target agent | Source agent | Status code + summary | No PII |
| **Escalation Reason** | Any agent | Orchestrator | Escalation code | Audit-only |

### 1.3 Layer 3: Backend Integration Layer

**Purpose**: Connect AI agents to existing MagicDelivery systems through standardised API patterns, anti-corruption layers, and event-driven integration.

#### 1.3.1 Backend Integration Inventory

| Integration ID | Backend System | APPINV ID | Agents Using | Integration Pattern | Protocol | Data Direction | Latency Target |
|---------------|---------------|-----------|-------------|-------------------|----------|---------------|----------------|
| **INT-001** | API Gateway | TAPP-02 | All Agents | REST + GraphQL | HTTPS/TLS | Bidirectional | <100ms |
| **INT-002** | CRM System | Retained | CSA-01, CSA-02, CSA-03, PTA-01, PTA-02, RSA-01, RSA-02, OPA-01, OPA-02, COMPA-01, COMPA-02 | REST API + Anti-Corruption Layer | HTTPS/REST | Bidirectional | <200ms |
| **INT-003** | GCP Event Manager | APP-22 | PTA-01, PTA-02, OPA-02 | Event Subscription + Streaming | gRPC/Protobuf | Inbound (stream) | <50ms |
| **INT-004** | SMS/Email Services | Retained | PTA-01, PTA-02, MIA-02, MIA-03 | REST API + Queue | HTTPS/REST | Outbound | <500ms |
| **INT-005** | ERP System | APP-24 | CSA-01, SA-02, OPA-01, OPA-02, RSA-02, ANA-01, ANA-02 | REST API + Anti-Corruption Layer | HTTPS/REST | Bidirectional | <500ms |
| **INT-006** | Model Serving Abstraction | TAPP-02 | All Agents | gRPC + Multi-Provider | gRPC/TLS | Bidirectional | <1500ms |
| **INT-007** | Pricing Systems | APP-25 | CSA-01, SA-01, SA-02, RSA-01, RSA-02, OPA-01 | REST API | HTTPS/REST | Inbound (query) | <200ms |
| **INT-008** | Product Systems | APP-26 | CSA-01, SA-01, SA-02, RSA-01, RSA-02, OPA-01 | REST API | HTTPS/REST | Inbound (query) | <200ms |
| **INT-009** | Customer Data Platform | TAPP-04 | SA-01, SA-02, MIA-01, MIA-02, MIA-03, ANA-01, ANA-02 | REST API + Event Streaming | HTTPS + gRPC | Bidirectional | <300ms |
| **INT-010** | Consent Service | TAPP-05 | All Customer-Facing Agents | REST API (synchronous) | HTTPS/REST | Outbound (verify) | <50ms |
| **INT-011** | Retail POS Systems | APP-27 | RSA-01, RSA-02 | REST API + Anti-Corruption Layer | HTTPS/REST | Bidirectional | <500ms |
| **INT-012** | Inventory Management | APP-28 | RSA-01, RSA-02 | REST API | HTTPS/REST | Inbound (query) | <200ms |

#### 1.3.2 Integration Patterns

**Pattern 1: API Gateway with Anti-Corruption Layer (Synchronous)**

Used for: INT-002 (CRM), INT-005 (ERP), INT-007 (Pricing), INT-008 (Products), INT-011 (POS)

```
Agent → API Gateway → Anti-Corruption Layer → Legacy System
                     (Domain Translation)    (Legacy Protocol)
```

| Attribute | Specification |
|-----------|---------------|
| **Purpose** | Isolate agents from legacy system complexity and protocol differences |
| **Translation** | Agent-domain JSON → Legacy protocol (SOAP, legacy REST, database calls) |
| **Caching** | Read-through cache for reference data (pricing, products); TTL: 1 hour |
| **Circuit Breaker** | 3 consecutive failures → fallback to cached data; 60-second recovery |
| **Versioning** | Independent versioning from legacy system; backward-compatible |
| **Traceability** | PRIN-17 (Legacy Modernization); PRIN-02 (Composable); STRAT |

**Pattern 2: Event-Driven Integration (Asynchronous)**

Used for: INT-003 (GCP Event Manager), INT-009 (CDP), agent-to-agent communication

```
Source System → Event Bus → Schema Registry → Agent Subscriber
(GCP Events)    (Kafka)     (Validation)     (Processing)
```

| Attribute | Specification |
|-----------|---------------|
| **Purpose** | Decouple agents from source systems; enable real-time event processing |
| **Schema Registry** | Versioned schemas; consumer compatibility mode (BACKWARD) |
| **Dead Letter Queue** | Failed events routed to DLQ; alert on DLQ depth > 100 |
| **Replay** | Event replay capability for agent reprocessing; 72-hour retention |
| **Consumer Groups** | Separate consumer groups per agent category for independent scaling |
| **Traceability** | PRIN-09 (Event-Driven Integration); ADR-003 |

**Pattern 3: Synchronous Tool Call**

Used for: INT-010 (Consent Service), ACR-005 (Compliance Validation), ACR-012 (Co-Pilot Queries)

```
Agent → Tool Call Service → Target Service → Response
       (synchronous)        (low-latency)    (structured)
```

| Attribute | Specification |
|-----------|---------------|
| **Purpose** | Low-latency, blocking calls for real-time validation or data retrieval |
| **Timeout** | Configurable per tool: 50ms (consent), 200ms (validation), 500ms (lookup) |
| **Caching** | Aggressive caching for idempotent queries; cache-aside pattern |
| **Circuit Breaker** | 2 consecutive failures → circuit open; 15-second half-open test |
| **Traceability** | AGT-DES §6.3 |

#### 1.3.3 Data Synchronization Patterns

| Sync Pattern | Use Case | Direction | Frequency | Consistency Model |
|-------------|----------|-----------|-----------|-------------------|
| **Real-Time Sync** | Parcel tracking events (GCP → PTA-01/02) | Inbound stream | Event-driven (sub-second) | Strong (at-least-once) |
| **Near-Real-Time Sync** | Customer profile updates (CDP → Agents) | Bidirectional | <60 seconds | Eventual (eventual consistency) |
| **Batch Sync** | Marketing segment updates (MIA-01 → MIA-02) | Unidirectional | Hourly/daily | Batch (idempotent) |
| **On-Demand Sync** | Consent verification (Agent → COMPA-01) | Outbound query | Per-interaction | Strong (synchronous) |
| **Caching Sync** | Pricing/product data (Systems → Agent cache) | Inbound | TTL-based refresh | Stale-while-revalidate |

#### 1.3.4 Service Mesh Integration

| Attribute | Specification | Traceability |
|-----------|---------------|-------------|
| **Service Mesh** | Istio / Linkerd sidecar pattern | APPINV TAPP-02 |
| **Traffic Management** | mTLS between all agent services; traffic splitting for canary deployments | PRIN-04 |
| **Observability** | Distributed tracing (OpenTelemetry); access logs; traffic metrics | PRIN-05 |
| **Policy Enforcement** | RBAC at mesh level; quota management; rate limiting per agent | NFR-SEC-002 |
| **Resilience** | Retry policies; timeout policies; circuit breakers; connection pooling | PRIN-12 |

### 1.4 Layer 4: Analytics and Observability Layer

**Purpose**: Provide real-time visibility into agent performance, accuracy, compliance, and business outcomes across the entire agent portfolio.

#### 1.4.1 Telemetry Architecture

```
┌───────────────────────────────────────────────────────────────────────┐
│                   Agent Telemetry Pipeline                            │
│                                                                       │
│  ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌─────────┐    │
│  │ Agent A  │  │ Agent B  │  │ Agent C  │  │ Agent D  │  │ Agent E  │    │
│  │ Telemetry│  │ Telemetry│  │ Telemetry│  │ Telemetry│  │ Telemetry│    │
│  └────┬─────┘  └────┬─────┘  └────┬─────┘  └────┬─────┘  └────┬─────┘   │
│       │              │              │              │              │     │
│       └──────────────┴──────────────┴──────────────┴──────────────┘     │
│                              │                                           │
│                    ┌───────▼───────┐                                      │
│                    │ Telemetry Bus │ (OpenTelemetry-compatible)           │
│                    └───────┬───────┘                                      │
│                            │                                             │
│        ┌───────────────────┼───────────────────┐                           │
│        │                    │                  │                           │
│  ┌─────▼──────┐   ┌───────▼──────┐   ┌────────▼────────┐                   │
│  │ Metrics      │   │ Distributed    │   │ Structured    │                   │
│  │ (Prometheus) │   │ Traces         │   │ Logs          │                   │
│  │              │   │ (Jaeger/OTLP)  │   │ (ELK/LOKI)    │                   │
│  └─────┬───────┘   └───────┬──────┘   └────────┬────────┘                   │
│        │                      │                    │                         │
│        └──────────────────────┼──────────────────┘                           │
│                              │                                               │
│                    ┌───────▼───────┐                                          │
│                    │ Dashboards &  │ ←── Grafana/Custom Agent Dashboards     │
│                    │ Alerting      │ ←── PagerDuty/Custom Alerting            │
│                    └──────────────┘                                           │
└─────────────────────────────────────────────────────────────────────────────────┘
```

#### 1.4.2 Agent-Specific Telemetry

| Telemetry Category | Metrics | Agents | Frequency | Owner |
|-------------------|---------|--------|-----------|-------|
| **Performance** | Response latency (p50/p95/p99), throughput (RPM), error rate, token consumption | All agents | Real-time | Platform Engineering |
| **Accuracy** | First-contact resolution rate, confidence scores, hallucination rate, human escalation rate | Customer-facing agents (CSA, SA, PTA, RSA) | Per-interaction | AI Engineering |
| **Business** | Call deflection rate, revenue attribution, CSAT contribution, cost per interaction | All customer-facing agents | Real-time | Business Analytics |
| **Compliance** | Consent violation rate, audit trail completeness, DPIA coverage, PII exposure incidents | All agents (via COMPA-02) | Real-time | Compliance/Legal |
| **Model** | Model accuracy drift, prompt hit rate, cache hit rate, fallback rate | All agents | Hourly | AI Engineering |
| **Infrastructure** | CPU/memory utilisation, GPU utilisation (on-prem), API quota consumption, network I/O | All agents | Real-time | Platform Engineering |

#### 1.4.3 Alerting and SLO Framework

| SLO | Target | Measurement | Alert Threshold | Response |
|-----|--------|------------|----------------|----------|
| **Agent Availability** | 99.9% uptime | Heartbeat monitoring | >1 minute unavailable | Auto-failover + page on-call |
| **Response Time (p95)** | <2 seconds (Foundation) | Distributed traces | p95 >2s for 5 minutes | Scale + investigate |
| **First-Contact Resolution** | ≥85% (Foundation) | Agent outcome logging | FC rate <80% for 24h | Model review + prompt tuning |
| **Hallucination Rate** | <2% | COMPA-02 validation | Rate >2% for 1 hour | Circuit breaker + model review |
| **Consent Compliance** | 100% | COMPA-01 audit | Any violation | Immediate halt + investigation |
| **Cost per Interaction** | <USD $0.05 | Token accounting | Cost >$0.06 average | Budget review + optimisation |
| **Tokenisation Integrity** | 100% | Cryptographic verification | Any tokenisation failure | Emergency cloud halt |
| **Cross-Agent Handoff Time** | <500ms | Bus latency tracking | p99 >1s for 5 minutes | Bus investigation |

### 1.5 Layer Dependency Map

```
Layer 1 (Customer-Facing Orchestration)
  └── Depends on: Layer 2 (Agent Collaboration) for agent routing
  └── Depends on: Layer 4 (Observability) for health checks
  └── Depends on: INT-010 (Consent Service) for pre-routing consent verification

Layer 2 (Agent-to-Agent Collaboration)
  └── Depends on: Layer 3 (Backend Integration) for data access
  └── Depends on: Layer 4 (Observability) for inter-agent metrics
  └── Depends on: INT-010 (Consent Service) for cross-agent consent boundaries

Layer 3 (Backend Integration)
  └── Depends on: PRIN-02 (Composable), PRIN-17 (Legacy Modernization)
  └── Depends on: PRIN-04 (Security by Design) for mTLS/auth
  └── Depends on: Layer 4 (Observability) for integration health

Layer 4 (Analytics & Observability)
  └── Independent (consumes from all layers)
  └── Feeds back to: Layer 1 (health-based routing), Layer 2 (performance-aware collaboration),
                       Layer 3 (circuit breakers), all agents (adaptive behaviour)
```

---

## 2. Orchestration Patterns

### 2.1 Intent Routing Across Agent Specialisations

**Purpose**: Route customer interactions to the most appropriate specialised agent based on detected intent, complexity, and customer context.

#### 2.1.1 Intent Classification Engine

| Attribute | Specification | Traceability |
|-----------|---------------|-------------|
| **Classification Model** | Multi-class intent classifier (lightweight ML model) | AGT-DES §2.1; CSA-01 capabilities |
| **Intent Taxonomy** | 24 primary intents, 48 sub-intents | AI-06 |
| **Confidence Threshold** | ≥85% for autonomous routing; <85% triggers multi-agent consultation | ADR-002 |
| **Routing Strategy** | Primary intent → fallback intent → general agent cascade | AGT-INV §8.2 |

**Intent Routing Matrix**:

| Detected Intent | Primary Agent | Fallback Agent | Confidence Threshold | Handoff Pattern |
|----------------|-------------|----------------|-------------------|-----------------|
| Parcel tracking | PTA-01 | CSA-01 | ≥85% | Direct route |
| Shipping recommendation | SA-01 | CSA-01 | ≥80% | Direct route |
| Complaint | CSA-02 | CSA-01 → Human | ≥90% | Priority route |
| Fee inquiry | CSA-01 | SA-01 | ≥85% | Direct route |
| Address change | CSA-01 | CSA-02 | ≥85% | Direct route |
| Product inquiry | SA-01 | CSA-01 | ≥80% | Direct route |
| Delivery exception | PTA-02 | PTA-01 → CSA-01 | ≥90% | Priority route |
| Privacy/consent | COMPA-01 | CSA-01 | 100% | Priority route |
| General inquiry | CSA-01 | — | Any | Direct route |
| Language-specific query | CSA-03 | CSA-01 | ≥80% | Language-aware route |
| Business shipping | SA-02 | SA-01 | ≥80% | Segment-aware route |
| Retail service query | RSA-02 (kiosk) / RSA-01 (staff) | CSA-01 | ≥80% | Channel-aware route |

#### 2.1.2 Complexity-Based Routing (ADR-002)

| Complexity Tier | Criteria | Routing Decision | Max Resolution Time | Traceability |
|----------------|----------|-----------------|-------------------|-------------|
| **Routine** (score 0-30) | Standard queries; high confidence (≥85%); no PII risk | Autonomous agent handling | <2 seconds | ADR-002; FR-004 |
| **Moderate** (score 31-69) | Multi-faceted queries; moderate confidence (70-85%) | Agent handles + human review queue | <30 seconds | ADR-002; FR-004 |
| **High-Complexity** (score 70-89) | Complex multi-step queries; low confidence (<70%) | Agent attempts + auto-escalation if unresolved | <30 seconds to handoff | ADR-002; FR-004 |
| **High-Risk** (any score with risk keywords) | Complaints, security, legal, regulatory | Immediate human escalation; agent only acknowledges | <15 seconds to handoff | ADR-002; NFR-C-003 |

### 2.2 Conversation State Management and Handoff Protocols

#### 2.2.1 Session State Model

| Attribute | Specification | Traceability |
|-----------|---------------|-------------|
| **Session Store** | Redis cluster (in-memory with persistence) | AGT-DES §4.2 |
| **Session TTL** | 30 minutes idle timeout; 24 hour max session | AGT-DES §4.2 |
| **State Size** | 10+ turns; up to 40K tokens per session | AGT-DES §4.2 |
| **State Persistence** | AOF persistence; RDB snapshots every 5 minutes | PRIN-12 |
| **Cross-Channel State** | Session correlation ID (UUID) shared across channels | AGT-DES §5.3 |

**Session State Transfer on Agent Handoff**:

```json
{
  "handoff": {
    "session_id": "uuid",
    "correlation_id": "uuid",
    "from_agent": "CSA-01",
    "to_agent": "PTA-01",
    "handoff_reason": "intent_handoff",
    "state": {
      "conversation_summary": "Tokenised summary of conversation to date",
      "active_entities": {"tracking_number": "tok_abc123"},
      "conversation_language": "en",
      "turn_count": 7,
      "customer_context": {"consent_flags": {...}, "channel": "mobile_app"},
      "prior_outcomes": ["intent:general_inquiry → resolved", "intent:parcel_tracking → handoff"]
    },
    "metadata": {
      "handoff_timestamp": "ISO-8601",
      "expected_response_time": "<300ms",
      "continuity_required": true
    }
  }
}
```

#### 2.2.2 Handoff Protocols

| Handoff Type | Trigger | Protocol | Max Time | Context Transfer | Traceability |
|-------------|---------|----------|----------|-----------------|-------------|
| **Warm Handoff** | Agent-to-agent within platform | Event bus (intent_handoff) | <300ms | Full session state + entities | ACR-001 to ACR-016 |
| **AI-to-Human Handoff** | Low confidence / high risk | CRM API (INT-002) | <30 seconds | Transcript + confidence + context | ADR-002; FR-004 |
| **Channel Handoff** | Customer switches channel | Session Store lookup | <1 second | Session retrieval via correlation ID | AGT-DES §5.3 |
| **Emergency Handoff** | System failure / security event | Direct escalation | <10 seconds | Minimal context + alert | NFR-C-003 |
| **Complaint Handoff** | Complaint pattern detected | Priority event + CRM | <15 seconds | Complaint context + compliance flags | ACR-003 |

### 2.3 Multi-Agent Decision Consensus Patterns

#### 2.3.1 Consensus Voting Protocol

Used when multiple agents must agree on a decision (e.g., intent classification disagreement, ambiguous queries):

```
Orchestrator → Broadcast Query → [Agent A votes, Agent B votes, Agent C votes]
       │                                         │
       │                                Aggregate Votes
       │                                         │
       │                    ┌────┬────────────────┴────────────────┐
       │                    │     │                               │
       │               Majority (≥2/3)    No Majority            Unanimous
       │               → Accept vote      → Human escalation    → Accept decision
       │
       └──→ Customer response with consensus decision
```

| Attribute | Specification | Use Cases |
|-----------|---------------|-----------|
| **Voting Threshold** | ≥2/3 majority for acceptance; <2/3 triggers human review | Intent classification disputes |
| **Vote Timeout** | 200ms per agent vote | Real-time decisioning |
| **Vote Weighting** | Configurable per agent specialisation (domain-weighted) | Cross-domain decisions |
| **Consensus Log** | Tamper-evident record of all votes and outcomes | Compliance (FR-008) |

#### 2.3.2 Decision Consensus Registry

| Decision Type | Participating Agents | Consensus Method | Fallback | Traceability |
|--------------|-------------------|-----------------|----------|-------------|
| **Intent Classification Disagreement** | CSA-01, PTA-01, SA-01 | Majority vote with domain weighting | Orchestrator decides | AI-06 |
| **Complaint Severity Rating** | CSA-01, CSA-02, COMPA-02 | CSA-02 authoritative; COMPA-02 validates | Human escalation | CSA-02 capabilities |
| **Personalisation Eligibility** | SA-01, COMPA-01, MIA-01 | COMPA-01 authoritative on consent | Deny personalisation | COMPA-01 |
| **Routing Decision** | Orchestrator, Complexity Router | Orchestrator authoritative | CSA-01 (general agent) | ADR-002 |
| **Exception Resolution** | PTA-02, CSA-01, MIA-03 | PTA-02 authoritative on logistics | Human escalation | PTA-02 |

### 2.4 Load Balancing and Failover Strategies

#### 2.4.1 Agent Instance Scaling

| Attribute | Specification | Traceability |
|-----------|---------------|-------------|
| **Scaling Model** | Horizontal pod autoscaling (Kubernetes) | NFR-S-001 |
| **Scale Trigger** | CPU >70% OR active sessions > threshold per agent type | NFR-P-001 |
| **Min Instances** | 2 per agent type (high availability) | PRIN-12 |
| **Max Instances** | 50 per agent type (capacity ceiling) | NFR-S-001 |
| **Scale-Up Time** | <30 seconds (warm start); <5 seconds (cold start from cache) | NFR-P-001 |
| **Load Distribution** | Consistent hashing by session ID; sticky sessions for conversation continuity | AGT-DES §4.2 |

#### 2.4.2 Agent-Specific Load Targets

| Agent Category | Min Instances | Max Instances | Scale Threshold | Target Utilisation | Foundation |
|---------------|-------------|-------------|-----------------|-------------------|------------|
| CSA (Customer Service) | 4 | 30 | 200 RPM per instance | 65-75% | Foundation |
| PTA (Parcel Tracking) | 4 | 25 | 500 RPM per instance | 60-70% | Foundation |
| SA (Shopping Assistant) | 2 | 15 | 100 RPM per instance | 60-70% | Foundation/Scale |
| RSA (Retail Support) | 2 | 10 | 50 RPM per instance | 50-60% | Scale |
| OPA (Operations) | 2 | 10 | 200 RPM per instance | 50-60% | Foundation |
| MIA (Marketing Intelligence) | 2 | 8 | 50 RPM per instance | 40-50% | Scale |
| ANA (Analytics) | 1 | 5 | Batch queue depth > 100 | 30-40% | Scale |
| COMPA (Compliance) | 2 | 4 | 100 RPM per instance | 30-40% | Foundation |

#### 2.4.3 Failover Strategies

| Failure Type | Detection | Response | Recovery Time | Traceability |
|-------------|-----------|----------|---------------|-------------|
| **Single Agent Instance Failure** | Health check (15s interval) | Route to healthy instance; session continuity via Redis | <5 seconds | PRIN-12 |
| **Agent Category Failure (All Instances)** | Health check + circuit breaker | Route to fallback agent (CSA-01); degrade non-critical features | <30 seconds | NFR-S-001 |
| **Model Provider Failure** | API health check + error rate monitoring | Failover to secondary model provider | <60 seconds | ADR-001; R-002 |
| **Tokenisation Service Failure** | Cryptographic integrity check | Circuit breaker → halt cloud inference → on-prem fallback | <10 seconds | ADR-001 |
| **Agent Bus Failure** | Bus health check + dead letter monitoring | Agents operate independently with cached context; queue events for replay | <30 seconds | PRIN-09 |
| **Consent Service Failure** | API health check | Deny personalisation/marketing; allow basic service interactions | <5 seconds | COMPA-01 |
| **Platform-Wide Failure** | Multi-layer health check | Graceful degradation → static responses → human-only mode | <2 minutes | NFR-S-001 |

### 2.5 Session Continuity Across Channels

#### 2.5.1 Cross-Channel Session Model

| Attribute | Specification | Traceability |
|-----------|---------------|-------------|
| **Session Correlation** | UUID generated at first interaction; persists across all channels | AGT-DES §5.3 |
| **Identity Resolution** | Tokenised customer ID; federated identity provider | TAPP-01; PRIN-02 |
| **State Portability** | Session state retrievable from Redis via correlation ID | AGT-DES §4.2 |
| **Channel Handoff** | Customer switches channels without losing conversation context | ADR-005 |
| **Privacy** | Tokenised IDs only; no raw PII in cross-channel state | PRIN-04; APP 11 |

#### 2.5.2 Continuity Flow

```
Mobile App (initiated) ──→ Session ID: abc-123 ──→ Session Store (Redis)
Web Portal (resumed)     ──→ Session ID: abc-123 ──→ State restored (last turn, entities, intent)
Call Centre (resumed)    ──→ Session ID: abc-123 ──→ Co-pilot receives context via CRM injection
```

| Continuity Scenario | Implementation | Max Context Loss | Traceability |
|--------------------|----------------|------------------|-------------|
| Same device, different channel | Session ID in cookie + SDK; Redis lookup | None | ADR-005 |
| Different device, same customer | Federated identity + Redis lookup | Last 2 turns (summary) | ADR-005 |
| Inactive session resumed (<30 min idle) | Redis TTL alive; full state restore | None | AGT-DES §4.2 |
| Expired session resumed (>30 min idle) | Customer re-authentication; summary restore from vector DB | Full context (summary only) | AGT-DES §4.3 |

### 2.6 Cross-Agent Context Sharing

#### 2.6.1 Context Sharing Protocols

| Protocol | Use Case | Mechanism | Data Shared | Privacy Guardrails |
|----------|----------|-----------|------------|-------------------|
| **Event Bus Handoff** | Agent-to-agent context transfer | Structured event with context payload | Conversation summary, entities, intent | Tokenised PII; consent-bound |
| **Session Store Reference** | Shared session state across agents | Redis key reference (shared session ID) | Full session state | Session-scoped; TTL-limited |
| **Tool Call Result** | Request-response data exchange | Synchronous tool call | Specific data field | Purpose-limited; minimum necessary |
| **Vector Memory Query** | Cross-agent knowledge retrieval | Vector search (semantic similarity) | Knowledge chunks | Aggregated; no PII |
| **Consent Boundary Check** | Cross-agent privacy enforcement | COMPA-01 validation | Consent flags only | Boolean only; no raw data |

#### 2.6.2 Context Sharing Governance

| Governance Rule | Description | Enforcement | Traceability |
|----------------|-------------|-------------|-------------|
| **PII Never Shared in Raw Form** | All shared context uses tokenised identifiers | Tokenisation layer (ADR-001) | PRIN-04; APP 11 |
| **Purpose-Limited Sharing** | Context shared only for the specific handoff purpose | Event schema validation | PRIN-02 |
| **Consent-Gated Sharing** | No context sharing if customer consent not granted | COMPA-01 pre-check | COMPA-01; APP 3 |
| **Retention-Limited** | Shared context automatically expires with session | Redis TTL; vector DB policy | AGT-DES §4.2 |
| **Audit-Logged Sharing** | All context sharing events recorded | Tamper-evident audit trail | FR-008; COMPA-02 |

---

## 3. Integration Requirements

### 3.1 API Gateway Integration

| Requirement | Specification | Traceability |
|------------|---------------|-------------|
| **API Gateway** | Central API gateway (Kubernetes Ingress + API Management) | TAPP-02; ADR-005 |
| **Unified Endpoint** | Single API surface for all agent interactions | PRIN-02 |
| **Protocol Support** | REST (JSON), WebSocket (streaming), gRPC (internal) | AGT-DES §6.2 |
| **Request Validation** | Schema validation at gateway level; input sanitisation | PRIN-04 |
| **Authentication** | JWT/OAuth 2.0 for customer requests; mTLS for service calls | PRIN-04 |
| **Rate Limiting** | Per-customer, per-channel, per-agent limits with burst allowance | NFR-S-001 |
| **API Versioning** | Semantic versioning; deprecation notices 6 months minimum | PRIN-02 |
| **Documentation** | OpenAPI 3.1 specification; developer portal | PRIN-02 |

### 3.2 Event-Driven Architecture

| Requirement | Specification | Traceability |
|-------------|---------------|-------------|
| **Event Bus** | Apache Kafka / Google Pub-Sub (managed) | ADR-003; PRIN-09 |
| **Event Schema Registry** | Confluent Schema Registry / equivalent | PRIN-02 |
| **Event Types** | Intent events, context events, tool call events, result events, status events | AGT-DES §6.1 |
| **Message Durability** | At-least-once delivery; idempotent consumers | PRIN-09 |
| **Dead Letter Queue** | Failed events routed to DLQ; monitoring and replay | PRIN-09 |
| **Event Replay** | 72-hour retention; replay capability for debugging | PRIN-09 |
| **Event Versioning** | Schema evolution with backward compatibility | PRIN-02 |
| **Event Observability** | Message-level tracing; consumer lag monitoring | PRIN-05 |

### 3.3 Real-Time Streaming vs Batch Processing

| Processing Mode | Use Cases | Latency Target | Agents | Traceability |
|----------------|-----------|---------------|--------|-------------|
| **Real-Time Streaming** | Conversational responses, parcel tracking updates, proactive notifications | <2 seconds (conversational); <30 seconds (notifications) | CSA, PTA, SA | NFR-P-001; NFR-P-003 |
| **Near-Real-Time** | Agent-to-agent handoffs, consent verification, compliance validation | <500ms | All agents | AGT-DES §6.2 |
| **Near-Batch** | Customer profile updates, consent sync, segment refresh | <60 seconds | SA, MIA, ANA | INT-009 |
| **Batch Processing** | Analytics aggregation, model retraining, reporting | Hourly/daily | MIA, ANA, COMPA-02 | AGT-DES §2.4, §2.7 |
| **Eventual Consistency** | Cross-system data sync, marketing segment propagation | <5 minutes | MIA, SA | INT-009 |

### 3.4 Service Mesh Integration

| Requirement | Specification | Traceability |
|-------------|---------------|-------------|
| **Sidecar Pattern** | Envoy/Istio sidecar per agent service | TAPP-02 |
| **mTLS** | Mutual TLS between all agent-to-agent and agent-to-backend calls | PRIN-04 |
| **Traffic Splitting** | Canary deployments; blue-green agent versioning | PRIN-02 |
| **Observability** | Distributed tracing, access logs, traffic metrics | PRIN-05 |
| **Policy Enforcement** | RBAC at mesh level; quota enforcement; rate limiting | NFR-SEC-002 |
| **Resilience** | Retry policies, timeout policies, circuit breakers | PRIN-12 |

---

## 4. Security & Compliance

### 4.1 Agent Authentication and Authorization

| Control | Implementation | Scope | Traceability |
|---------|---------------|-------|-------------|
| **Service Authentication** | mTLS with short-lived certificates (24h rotation) | All agent services | PRIN-04; NFR-SEC-001 |
| **Customer Authentication** | OAuth 2.0 / JWT with federated identity | Customer-facing agents | TAPP-01; PRIN-04 |
| **Role-Based Access Control** | RBAC with agent-specific roles (e.g., agent_read_crm, agent_write_tracking) | All agents | NFR-SEC-002 |
| **Attribute-Based Access Control** | ABAC for fine-grained access (agent category, data classification, purpose) | Sensitive data access | PRIN-04 |
| **API Key Management** | Vault-managed API keys with automatic rotation | Backend integrations | PRIN-04 |
| **Session Tokens** | Short-lived session tokens (15 min TTL) with refresh | Customer sessions | PRIN-04 |
| **Audit Logging** | All authentication/authorization events logged | All agents | FR-008; COMPA-02 |

### 4.2 Data Privacy Boundaries Between Agents

| Boundary Rule | Description | Enforcement | Traceability |
|--------------|-------------|-------------|-------------|
| **PII Tokenisation Boundary** | PII tokenised before cloud transmission; tokens only in agent context | Tokenisation service (ADR-001) | APP 8; PRIN-04 |
| **Cross-Agent Data Boundary** | Agents may share tokenised entities only for handoff purposes | Event schema validation | COMPA-01 |
| **Category-Level Isolation** | Marketing agents (MIA) cannot access customer service conversation content | ABAC policy enforcement | PRIN-02 |
| **Consent Boundary** | No personalisation or marketing data access without explicit consent | COMPA-01 real-time verification | APP 3; COMPA-01 |
| **Complaint Data Boundary** | Complaint data (CSA-02) isolated to on-prem; never routed to cloud models | Deployment boundary (ADR-001) | APP 11 |
| **Analytics Anonymisation** | Analytics agents (ANA) receive only aggregated/anonymised data | Data pipeline transformation | ANA-01 capabilities |

### 4.3 Audit Trail for Agent-to-Agent Communication

| Audit Requirement | Implementation | Retention | Traceability |
|------------------|----------------|-----------|-------------|
| **Inter-Agent Events** | All agent bus events logged with source, target, timestamp, event type | 7 years | FR-008; COMPA-02 |
| **Context Transfers** | Context payload metadata (not full payload) logged | 7 years | FR-008 |
| **Escalation Events** | Full escalation context logged including reason, timestamps, target | 7 years | FR-008; CSA-02 |
| **Consent Checks** | Consent verification results logged | Indefinite (regulatory) | COMPA-01 |
| **Tamper-Evident Logging** | Hash chain for log integrity verification | 7 years | COMPA-02 |
| **Access Logs** | All data access events logged with agent identity | 7 years | PRIN-04 |

### 4.4 Consent Management Integration

| Integration Point | Consent Check | Enforcement | Agent Impact | Traceability |
|------------------|--------------|------------|-------------|-------------|
| **Pre-Interaction** | COMPA-01 verifies consent for personalisation | Block personalisation if not consented | SA-01, SA-02 | COMPA-01 |
| **Pre-Notification** | COMPA-01 verifies consent for push/SMS/email | Suppress notification if not consented | PTA-01, PTA-02, MIA-03 | COMPA-01 |
| **Pre-Cross-Agent Sharing** | COMPA-01 verifies consent for context sharing | Block context sharing if not consented | All agents | COMPA-01 |
| **Pre-Cloud Inference** | Tokenisation service verifies consent for cloud model usage | Route to on-prem model if consent not granted | All agents | ADR-001 |
| **Pre-Campaign Targeting** | COMPA-01 verifies marketing consent | Exclude from campaign targeting | MIA-01, MIA-02, MIA-03 | COMPA-01 |
| **Consent Withdrawal** | COMPA-01 propagates withdrawal to all agents in real-time | Immediate cessation of affected activities | All agents | COMPA-01 |

### 4.5 PII Handling Across Agent Boundaries

| PII Data Type | Handling Rule | Tokenisation | Cross-Agent Policy | Traceability |
|--------------|--------------|-------------|-------------------|-------------|
| **Customer Name** | Tokenised before cloud inference; de-tokenised at point of output | Reversible tokenisation | Token only; purpose-limited | ADR-001; APP 11 |
| **Tracking Number** | Tokenised; used for status lookups only | Reversible tokenisation | Token only; handoff-bound | PTA-01 |
| **Delivery Address** | Tokenised; classified as PII | Reversible tokenisation | Token only; no marketing agents | APP 11 |
| **Contact Details** | Tokenised; used for notifications only | Reversible tokenisation | Token only; consent-gated | PTA-01, PTA-02 |
| **Payment Information** | Never stored by agents; processed by payment systems only | N/A (no agent exposure) | No agent exposure | RSA-01, RSA-02 |
| **Complaint Content** | On-prem only; never transmitted to cloud | N/A (on-prem isolation) | CSA-02 only; no cross-agent sharing | CSA-02; ADR-001 |
| **Consent Records** | Encrypted storage (AES-256); immutable history | N/A (structured data) | COMPA-01 authoritative; flags only | COMPA-01 |

---

## 5. Agent Integration Phasing

### 5.1 Foundation Phase (Year 1) — Core Orchestration

| Deliverable | Description | Agents Enabled | Dependencies |
|------------|-------------|----------------|-------------|
| **Agent Orchestrator MVP** | Intent classification, complexity routing, session management | CSA-01, PTA-01, OPA-01 | WP-ARC-001 |
| **Agent Bus v1** | Core event types (handoff, data request, escalation) | All Foundation agents | WP-ARC-003 |
| **API Gateway Integration** | Unified endpoint, mTLS, rate limiting | All Foundation agents | WP-ARC-004 |
| **Tokenisation Service** | PII tokenisation, on-prem boundary enforcement | CSA-01, CSA-02, PTA-01 | WP-ARC-002; WP-SEC-002 |
| **Consent Service Integration** | Real-time consent verification | CSA-01, PTA-01, COMPA-01 | WP-SEC-001 |
| **CRM Integration (INT-002)** | Anti-corruption layer, context injection for handoffs | CSA-01, CSA-02, OPA-01 | WP-ARC-004 |
| **Telemetry Pipeline v1** | Performance, accuracy, compliance monitoring | All Foundation agents | WP-SEC-004 |

### 5.2 Scale Phase (Years 2–3) — Expanded Collaboration

| Deliverable | Description | Agents Enabled | Dependencies |
|------------|-------------|----------------|-------------|
| **Agent Bus v2** | Consensus protocol, cross-agent context sharing, event replay | All Scale agents | WP-ARC-008 |
| **CDP Integration (INT-009)** | Real-time profile sync, event streaming | SA-01, MIA-01, ANA-01 | WP-DAT-005 |
| **Consensus Pattern** | Multi-agent voting for intent disputes | CSA-01, PTA-01, SA-01 | WP-ARC-009 |
| **Advanced Handoff Protocols** | Complaint handoff, language switching, proactive outreach | CSA-02, CSA-03, PTA-02, MIA-03 | WP-APP-009 |
| **Service Mesh Integration** | mTLS, traffic splitting, resilience patterns | All agents | WP-ARC-009 |
| **Marketing Integration** | Segment data exchange, campaign triggers | MIA-01, MIA-02, MIA-03 | WP-APP-009 |

### 5.3 Mature Phase (Years 3–5) — Optimised Integration

| Deliverable | Description | Agents Enabled | Dependencies |
|------------|-------------|----------------|-------------|
| **Agent Bus v3** | Self-optimising routing, predictive collaboration patterns | All agents | WP-ARC-010 |
| **Cross-Channel Continuity** | Full session portability across all 5 channels | All customer-facing agents | WP-APP-014 |
| **Advanced Observability** | Self-optimising SLOs, automated remediation | All agents | WP-ARC-011 |
| **Full Consent Awareness** | Real-time consent boundary enforcement at all integration points | All agents | WP-SEC-012 |
| **Autonomous Integration** | AI-driven integration optimisation, self-healing pipelines | All agents | WP-ARC-011 |

---

## 6. Traceability Matrix

### 6.1 Agent Inventory (AGT-INV) Traceability

| AGT-INV Reference | This Document Reference | Coverage |
|-------------------|------------------------|----------|
| AGT-INV §8.2: Agent-to-Agent Collaboration | §1.2.3: Agent Collaboration Registry (ACR-001 to ACR-016) | Full |
| AGT-INV §8.1: Agent-to-System Integration | §1.3.1: Backend Integration Inventory (INT-001 to INT-012) | Full |
| AGT-INV §5.2: Agent Interaction Patterns | §2.2: Conversation State Management; §2.6: Cross-Agent Context Sharing | Full |
| AGT-INV §7: Maturity Roadmap | §5: Agent Integration Phasing | Full |
| AGT-INV §9: Privacy/Security Framework | §4: Security & Compliance | Full |
| AGT-INV §12: Lifecycle Management | §5: Phasing; §1.4: Telemetry | Partial |

### 6.2 Agent Design (AGT-DES) Traceability

| AGT-DES Reference | This Document Reference | Coverage |
|-------------------|------------------------|----------|
| AGT-DES §1.2: Architecture Layers | §1: Integration Layer Specifications | Full |
| AGT-DES §3.1: Conversational Patterns | §2.1: Intent Routing; §2.2: Conversation State | Full |
| AGT-DES §3.2: Escalation Paths | §2.2: Handoff Protocols | Full |
| AGT-DES §4: Memory and State Management | §2.2: Session State Model | Full |
| AGT-DES §5.3: Cross-Channel Continuity | §2.5: Session Continuity Across Channels | Full |
| AGT-DES §6: Agent-to-Agent Communication | §1.2: Agent-to-Agent Collaboration Layer | Full |

### 6.3 Application Inventory (APPINV) Traceability

| APPINV Reference | This Document Reference | Coverage |
|-----------------|------------------------|----------|
| TAPP-02: AI Agent Platform | §1.1: Orchestration Layer; §1.4: Observability | Full |
| TAPP-03: Composable AI Services | §1.3: Backend Integration Layer | Full |
| TAPP-04: Customer Data Platform | §1.3.1: INT-009; §3.4: Service Mesh | Partial |
| TAPP-05: Privacy & Consent Management | §1.3.1: INT-010; §4.4: Consent Integration | Full |
| TAPP-08: Enhanced Mobile App | §1.1.2: Mobile SDK Adapter | Partial |
| TAPP-09: Retail Digital Integration | §1.3.1: INT-011; §1.1.2: Kiosk Adapter | Partial |

### 6.4 Architecture Decisions (ADR) Traceability

| ADR Reference | This Document Reference | Coverage |
|---------------|------------------------|----------|
| ADR-001: Hybrid AI Agent Model Deployment | §1.2.1: Agent Bus; §4.2: Privacy Boundaries; §4.5: PII Handling | Full |
| ADR-002: Agent-Human Handoff with Complexity-Based Routing | §2.1.2: Complexity-Based Routing; §2.2: Handoff Protocols | Full |
| ADR-003: Event-Driven Data Fabric | §1.2.1: Agent Communication Bus; §3.2: Event-Driven Architecture | Full |
| ADR-004: SDK Embedding for Mobile App | §1.1.2: Mobile SDK Adapter; §2.5: Session Continuity | Partial |
| ADR-005: Centralised Agent Backend with Multi-Channel UI | §1.1: Orchestration Layer; §1.3.1: INT-001 | Full |
| ADR-007: Hybrid Compliance Governance | §4.1: AuthN/AuthZ; §4.3: Audit Trail; §4.4: Consent | Partial |

### 6.5 Transition Architecture (TRANS) Traceability

| TRANS Reference | This Document Reference | Coverage |
|-----------------|------------------------|----------|
| WP-ARC-001: AI Agent Platform Core | §5.1: Foundation Phase deliverables | Full |
| WP-ARC-002: Tokenisation Service | §5.1: Tokenisation Service | Full |
| WP-ARC-003: Event Bus Foundation | §5.1: Agent Bus v1 | Full |
| WP-ARC-004: API Gateway | §5.1: API Gateway Integration | Full |
| WP-ARC-006: Composable Commerce | §5.2: Scale Phase deliverables | Partial |
| WP-ARC-009: Integration Architecture at Scale | §5.2: Service Mesh Integration | Partial |
| WP-SEC-001: Consent Service | §5.1: Consent Service Integration | Full |
| WP-SEC-004: AI Governance Framework | §1.4: Telemetry; §4.3: Audit Trail | Partial |

---

## 7. Quality Attributes and Non-Functional Requirements

### 7.1 Performance Requirements

| Requirement | Target | Measurement | Agents | Traceability |
|------------|--------|------------|--------|-------------|
| **Intent Classification Latency** | <50ms | Distributed traces | All agents | NFR-P-001 |
| **Agent-to-Agent Bus Latency** | <500ms p99 | Bus metrics | All agents | AGT-DES §6.2 |
| **Cross-Agent Handoff Time** | <300ms | Handoff telemetry | All agents | ACR-001 to ACR-016 |
| **Consent Verification Latency** | <50ms | COMPA-01 metrics | All customer-facing agents | COMPA-01 |
| **Session State Retrieval** | <10ms | Redis metrics | All agents | AGT-DES §4.2 |
| **Compliance Validation** | <200ms | COMPA-02 metrics | All agents | COMPA-02 |

### 7.2 Scalability Requirements

| Requirement | Target | Measurement | Traceability |
|------------|--------|------------|-------------|
| **Concurrent Sessions** | 50,000 (Y1) → 100,000 (Y3) | Session count | NFR-S-001 |
| **Bus Throughput** | 100,000 events/minute | Bus metrics | PRIN-09 |
| **Agent Instances** | Auto-scale to 50 per agent type | K8s HPA | NFR-S-001 |
| **Cross-Channel Sessions** | Session retrieval from any channel | Redis lookup time | AGT-DES §5.3 |

### 7.3 Reliability Requirements

| Requirement | Target | Measurement | Traceability |
|------------|--------|------------|-------------|
| **Platform Availability** | 99.9% (Foundation) → 99.95% (Mature) | Uptime monitoring | PRIN-12 |
| **Agent Instance Availability** | 99.99% per instance | Health checks | PRIN-12 |
| **Bus Availability** | 99.95% | Bus monitoring | PRIN-09 |
| **Data Durability** | 99.999999% (Redis + event logs) | Persistence checks | PRIN-12 |
| **Recovery Time Objective (RTO)** | <2 minutes (full platform) | Disaster recovery tests | PRIN-12 |
| **Recovery Point Objective (RPO)** | <30 seconds (session data) | Backup verification | PRIN-12 |

---

## 8. Document Quality Verification

### Quality Checklist

| Check | Status |
|-------|--------|
| Document ID: ARC-001-AGT-INT-v1.0 | ✅ |
| All Document Control fields populated | ✅ |
| 4 Integration Layers fully specified | ✅ |
| Customer-facing orchestration layer | ✅ |
| Agent-to-agent collaboration layer | ✅ |
| Backend integration layer | ✅ |
| Analytics and observability layer | ✅ |
| 6 Orchestration Patterns defined | ✅ |
| Intent routing across agent specialisations | ✅ |
| Conversation state management and handoff protocols | ✅ |
| Multi-agent decision consensus patterns | ✅ |
| Load balancing and failover strategies | ✅ |
| Session continuity across channels | ✅ |
| Cross-agent context sharing | ✅ |
| API Gateway integration | ✅ |
| Event-driven architecture | ✅ |
| Real-time streaming vs batch processing | ✅ |
| Data synchronization patterns | ✅ |
| Service mesh integration | ✅ |
| Observability and monitoring | ✅ |
| Agent authentication and authorization | ✅ |
| Data privacy boundaries between agents | ✅ |
| Audit trail for agent-to-agent communication | ✅ |
| Consent management integration | ✅ |
| PII handling across agent boundaries | ✅ |
| AGT-INV traceability | ✅ |
| AGT-DES traceability | ✅ |
| APPINV traceability | ✅ |
| ADR traceability | ✅ |
| TRANS traceability | ✅ |
| MagicDelivery context maintained throughout | ✅ |
| ArcKit Version: 5.15.2 | ✅ |
| Date: 2026-07-01 | ✅ |
| Model: Qwen3.6-27B | ✅ |

---

*End of Document*
