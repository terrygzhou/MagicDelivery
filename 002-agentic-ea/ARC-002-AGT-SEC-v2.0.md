# Agent Security: AgenticEA — MagicDelivery Agent AI Transformation (v2.0)

> **Template Origin**: Official | **ArcKit Version**: 5.15.2 | **Command**: `/arckit:agent-security`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-002-AGT-SEC-v2.0 |
| **Document Type** | Agent Security (AGT-SEC) |
| **Project** | 001 — AgenticEA: Agent AI Transformation |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 2.0 |
| **Created Date** | 2026-07-02 |
| **Last Modified** | 2026-07-02 |
| **Review Cycle** | Quarterly |
| **Next Review Date** | 2026-10-02 |
| **Owner** | CISO / Head of Digital Technology |
| **Reviewed By** | PENDING |
| **Approved By** | PENDING |
| **Distribution** | Executive Leadership, CISO, Head of Digital Technology, Compliance/Legal, Privacy Officer, Program Delivery Team, AI Engineering Lead, Enterprise Architecture Review Board, Regional Edge Node Operators |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-01 | ArcKit AI | Initial creation — Agent security framework covering identity, access control, sandboxing, compliance, and incident response for 16 AI agents across 8 categories | PENDING | PENDING |
| 2.0 | 2026-07-02 | ArcKit AI | Major increment: 16 → 1000 agents scaled across 48 Agent Families; zero-trust security at Family level; regional edge node security; automated security gates; hierarchical orchestration security; container-based sandboxing per agent; distributed tokenisation architecture; Fleet-level security orchestration | PENDING | PENDING |

---

## Executive Summary

### Purpose

This Agent Security (AGT-SEC v2.0) document defines the comprehensive **security controls, sandboxing framework, and compliance requirements** for the **AgenticEA — MagicDelivery Agent AI Transformation** programme at v2.0 scale. It establishes the security architecture for **1000 AI agents operating across 48 Agent Families**, serving 200,000+ concurrent users across 5 regional nodes with peak loads scaling to 500,000 by Year 3.

v2.0 introduces **zero-trust security at the Agent Family level**, **container-based sandboxing per agent**, **distributed regional edge node security**, and **automated security gates** that replace manual security reviews with continuous, policy-driven enforcement.

This document translates the security-by-design principle (PRIN-04, NON-NEGOTIABLE) into actionable security controls for a fleet of 1000 agents and provides the authoritative baseline for security testing, compliance audits, and incident response procedures specific to large-scale agent-based systems.

### Scope

| Aspect | Detail |
|--------|--------|
| **Agent Portfolio** | 1000 agent instances across 48 Agent Families (CE: 200, PS: 150, EC: 150, CD: 120, AI: 100, PC: 80, MK: 120, BO: 80) |
| **Security Boundaries** | Agent execution environments, inter-agent communication, agent-to-system interfaces, regional edge node boundaries, Family Manager security domains |
| **Compliance Framework** | Privacy Act 1988 (APPs), ACCC Consumer Law, WCAG 2.1, Fair Work Act |
| **Threat Coverage** | Prompt injection, data exfiltration, model poisoning, credential theft, supply-chain compromise, cross-family lateral movement, edge node compromise, distributed denial-of-service |
| **Design Horizon** | 5 years (Foundation → Scale → Mature phases) |

### v1.0 → v2.0 Security Changes

| Change Area | v1.0 | v2.0 |
|------------|------|------|
| **Agent count** | 16 agents, 8 categories | 1000 agents, 48 Agent Families |
| **Security model** | Per-agent security controls | Family-level zero-trust + per-agent enforcement |
| **Sandboxing** | Single-platform container isolation | Per-agent containers across 5 regional nodes |
| **Identity** | mTLS + JWT per agent | mTLS + JWT + Family-level SPIFFE/SPIFED trust domains |
| **Tokenisation** | Centralised tokenisation service | Distributed tokenisation (core + edge) with cryptographic key escrow |
| **Guardrails** | Platform-level guardrail chain | Family Manager–enforced + edge-node replicated guardrails |
| **Compliance gates** | Manual DPIA gates | Automated security gates in CI/CD pipeline |
| **Incident response** | Centralised SOC | Distributed SOC with regional incident coordination |
| **Network model** | 6-zone segmentation | 6-zone + edge node isolation + inter-edge ZTNA |

### Key Security Decisions

| Decision | Choice | Rationale |
|----------|--------|-----------|
| **Family-Level Zero Trust** | Every Agent Family operates in a trust domain; no inter-family implicit trust | Scales zero-trust to 1000 agents without per-agent policy explosion |
| **Container Per Agent** | Each of 1000 agents in its own sandboxed container with strict quotas | Prevents lateral movement; contains individual agent compromise |
| **Distributed Tokenisation** | Tokenisation at core and edge; never de-tokenise outside on-prem | APP 8 compliance by design; zero cross-border PII exposure across 5 nodes |
| **Automated Security Gates** | Policy-as-code gates in CI/CD; OPA policies for agent deployments | Eliminates manual security review bottleneck at scale |
| **Regional Edge Node Security** | Edge nodes replicate guardrail state; autonomous security for 60s core outage | Latency-optimised security without sacrificing compliance |
| **Hierarchical Orchestration Security** | Global → Regional → Family Manager security chain | Multi-layer defence; each tier enforces its own security boundary |

### Risk Alignment

| Risk ID | Title | Security Control | Mitigation Target |
|---------|-------|-----------------|-------------------|
| **R-017** | Privacy Act Breach from AI Data Processing | Distributed PII tokenisation + data minimisation + automated DPIA gates | 20 → 16 |
| **R-022** | Prompt Injection Attacks on AI Agents | Family-level input sanitisation + context hardening + output validation + automated red-teaming | 16 → 12 |
| **R-023** | Customer Data Exposure Through AI Model Training | Per-agent sandboxing + memory isolation + ephemerality + edge node isolation | 20 → 16 |
| **R-025** | Insider Threat — Privileged Access Misuse | Family-level least privilege + automated access reviews + distributed audit logging | 9 → 4 |
| **R-026** | Adversarial Attacks on AI Agents | Multi-layer guardrail chain + adversarial training + runtime anomaly detection | — |
| **R-027** | AI Decision Accountability | Tamper-evident audit trail across 5 regional nodes | — |

---

## 1. Security Architecture

### 1.1 Agent Identity and Authentication

#### 1.1.1 Family-Level Identity Model

At v2.0 scale (1000 agents, 48 families), individual agent identities are managed within **Family-level trust domains**. Each Agent Family operates as a security boundary with its own identity scope, while individual agents within a family inherit family-level identity attributes with agent-specific scopes.

| Attribute | v1.0 Specification | v2.0 Specification |
|-----------|-------------------|-------------------|
| **Identity Type** | X.509 client certificate (mTLS) + JWT bearer token | X.509 client certificate (mTLS) + JWT + SPIFFE/SPIFED trust domain |
| **Certificate Lifespan** | 90 days with automated rotation | 90 days automated; Family certificates: 180 days with agent sub-certificates at 90 days |
| **JWT Expiration** | 15 minutes | 5 minutes (edge nodes); 15 minutes (core) |
| **Certificate Authority** | Internal PKI (HashiCorp Vault) | Internal PKI + SPIFFE trust domain per Agent Family |
| **Identity Binding** | Agent ID → Certificate → Service Account → Role | Agent ID → Family Trust Domain → Certificate → Service Account → Role + Family Policy |

**Agent Family Identity Registry:**

| Capability | Agent Count | Identity Scope | Authentication | Trust Domain |
|------------|-----------|----------------|----------------|------------|
| **CE** (Customer Engagement) — 8 families, 200 agents | Customer data (tokenised) | mTLS + JWT + API Key | `spiffe://magicdelivery/ce-family` |
| **PS** (Parcel Services) — 8 families, 150 agents | Logistics data, tracking | mTLS + JWT | `spiffe://magicdelivery/ps-family` |
| **EC** (E-Commerce & Retail) — 8 families, 150 agents | Product catalog, pricing, POS | mTLS + JWT | `spiffe://magicdelivery/ec-family` |
| **CD** (Customer Data & Insights) — 8 families, 120 agents | Analytics data (aggregated) | mTLS + JWT + Service Account | `spiffe://magicdelivery/cd-family` |
| **AI** (AI Agent Platform) — 8 families, 100 agents | Platform infrastructure | mTLS + JWT + Signed Attestation | `spiffe://magicdelivery/ai-family` |
| **PC** (Privacy & Consent) — 8 families, 80 agents | Consent records, audit | mTLS + JWT + Signed Attestation | `spiffe://magicdelivery/pc-family` |
| **MK** (Marketing & Campaigns) — 8 families, 120 agents | Campaign data (consent-gated) | mTLS + JWT + Service Account | `spiffe://magicdelivery/mk-family` |
| **BO** (Business Operations) — 8 families, 80 agents | Internal operations | mTLS + JWT | `spiffe://magicdelivery/bo-family` |

**Family Manager Identity:** Each Family Manager (48 total) holds a Family-level service identity that authorises all agents within its family. Family Manager identities require dual attestation: (1) SPIFFE SPIFED endorsement and (2) HashiCorp Vault policy binding.

**Traceability:** AGT-INV-v2.0 (Agent distribution) | AGT-DES-v2.0 §2.1 (Family model) | PRIN-04 (Security by Design) | R-025 (Insider Threat)

#### 1.1.2 Distributed Authentication Flow

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                     TAPP-02 Core Platform                                    │
│  ┌──────────────┐    mTLS + JWT + SPIFFE    ┌──────────────────┐            │
│  │  AI Agent     │ ────────────────────────► │  Agent Platform   │            │
│  │  (Container)  │                           │  (TAPP-02)       │            │
│  │              │ ◄────────────────────────── │                │            │
│  │              │   Auth Response + Scope    │                │            │
│  └──────┬───────┘                            └────────┬─────────┘            │
│         │                                            │                       │
│         │   mTLS + SPIFFE ID                        │   mTLS + Signed Token │
│         ▼                                            ▼                       │
│  ┌──────────────┐                          ┌──────────────────┐              │
│  │  Cloud        │                          │  On-Prem         │              │
│  │  Inference     │                          │  Sensitive        │              │
│  │  Provider      │                          │  Processing       │              │
│  └──────────────┘                          └──────────────────┘              │
└─────────────────────────────────────────────────────────────────────────────┘
         │                    │                    │
    ┌────┴────┐         ┌─────┴────┐        ┌──────┴──────┐
    │ Edge-A  │         │ Edge-C   │        │ Edge-D      │
    │ (AUS-E) │         │ (AUS-W)  │        │ (AUS-R)     │
    │ mTLS +  │         │ mTLS +   │        │ mTLS +      │
    │ SPIFFE  │         │ SPIFFE   │        │ SPIFFE      │
    └────────┘         └──────────┘        └─────────────┘
```

**Requirements:**

- **SEA-001**: Every agent request MUST include a valid mTLS client certificate AND a signed JWT containing agent ID, family ID, session ID, and capability scope
- **SEA-002**: JWT tokens MUST expire within 5 minutes at edge nodes; 15 minutes at core; long-lived operations use refresh tokens issued by Family Manager
- **SEA-003**: Certificate rotation MUST be automated; agent certificates at 90-day maximum; Family Manager certificates at 180 days; all rotation via Vault PKI
- **SEA-004**: Agent-to-agent communication MUST use mutual TLS with agent-specific certificates; cross-family communication requires explicit inter-family policy approval
- **SEA-005**: Human-facing authentication (customer login) MUST use MFA; agent authentication does NOT replace human MFA requirements
- **SEA-006**: SPIFFE trust domains MUST be configured per Agent Family; edge node agents inherit core trust domain with edge-specific endorsements
- **SEA-007**: Family Manager identities require dual attestation (SPIFED + Vault) before authorising agents within the family

#### 1.1.3 Credential Management at Scale

| Credential Type | Storage | Rotation | Access Control | v2.0 Change |
|----------------|---------|----------|----------------|-----------|
| Agent certificates | HashiCorp Vault (PKI engine) + SPIFFE | 90 days automated | Vault policies by Family + agent role | SPIFFE trust domains per family |
| Family Manager certificates | HashiCorp Vault (PKI engine) + SPIFED | 180 days automated | Dual attestation: SPIFED + Vault | Dual-attestation required |
| API keys (cloud providers) | HashiCorp Vault (secrets engine) | 30 days automated | Least-privilege vault policies by capability | Distributed Vault instances at edge |
| Database credentials | HashiCorp Vault (database secrets) | 24 hours automated | Agent-scoped vault policies | Dynamic credentials at edge |
| Model provider keys | HashiCorp Vault + KMS envelope encryption | 30 days automated | Platform-level only; never agent-visible | Multi-provider key management |
| Tokenisation keys | HSM (FIPS 140-2 Level 3) + distributed key escrow | 180 days manual (dual-key) | Dual-control: Security + Compliance officers | Distributed across 5 nodes |
| Edge node secrets | Vault + local secrets manager (air-gapped fallback) | 30 days automated | Edge-node scoped vault policies | New for v2.0 |

**Requirements:**

- **SEC-001**: No credentials SHALL exist in environment variables, configuration files, source code, or container images across any node
- **SEC-002**: All credential access MUST be logged to the audit trail with agent ID, family ID, vault path, and timestamp; audit replicated to core
- **SEC-003**: Tokenisation cryptographic keys require dual-control access (two authorised personnel) with no single point of access; distributed key escrow across 3 nodes minimum
- **SEC-004**: Edge node secrets replicated from core with 5-second sync window; local air-gapped copy for autonomous operation during core outage

---

### 1.2 Access Control and Authorization

#### 1.2.1 Family-Level Authorization Model

The v2.0 platform implements **Attribute-Based Access Control (ABAC)** combined with **Role-Based Access Control (RBAC)** at the Family level, with agent-level permissions inherited from Family policies.

| Dimension | Attributes | Example (v2.0) |
|-----------|----------|----------------|
| **Subject** | Agent ID, Family ID, Capability, Node, Environment | CE-02-012, CE-02-Family, Customer Engagement, Edge-AUS-E, Production |
| **Object** | Data classification, Resource type, System, Region | PII-tokenised, CRM record, TAPP-02, ap-southeast-2 |
| **Action** | Read, Write, Query, Generate, Escalate, Publish | Read parcel data, Generate response, Publish event |
| **Environment** | Time, Location, Security context, Edge proximity | Business hours, International region, Edge-AUS-W |
| **Policy** | Allow/Deny with conditions | Allow CE-02 family agents to query tokenised CRM data during business hours at Edge-AUS-E |

#### 1.2.2 Capability-Level Permission Matrix (v2.0)

The 48 Agent Families are grouped into 8 capabilities. Permissions are defined at the capability level, then inherited by families within the capability.

| Capability | CRM Access | Logistics Data | Customer PII (Tokenised) | Product Catalog | Pricing Data | Marketing Data | Internal Systems | Analytics Data |
|------------|-----------|----------------|--------------------------|-----------------|--------------|----------------|-----------------|----------------|
| **CE** (200 agents) | Read | Read | Tokenised Read | Read | Read | — | — | Read (own sessions) |
| **PS** (150 agents) | Read (parcel) | Read/Write | Tokenised Read | — | — | — | Read (notifications) | Read (aggregated) |
| **EC** (150 agents) | Read (profile) | Read | Tokenised Read | Read/Write | Read | Read | Read (POS) | — |
| **CD** (120 agents) | Read (aggregated) | Read (aggregated) | Tokenised Read (aggregated) | — | — | Read (segments) | — | Read/Write |
| **AI** (100 agents) | Audit | Audit | Audit | Audit | Audit | Audit | Audit | Read/Write (platform) |
| **PC** (80 agents) | Audit | Audit | Audit | Audit | Audit | Audit | Audit | Audit |
| **MK** (120 agents) | Read (segments) | — | Tokenised Read (consent-gated) | — | — | Read/Write | — | Read |
| **BO** (80 agents) | Read | Read | Tokenised Read | — | — | — | Read/Write (internal) | Read |

#### 1.2.3 Principle of Least Privilege Enforcement (v2.0)

- **SEC-005**: Each agent SHALL receive the minimum permissions required for its defined capabilities; permissions scoped to Family, sub-capability, and variant type
- **SEC-006**: Agent permissions MUST be reviewed quarterly; unused permissions revoked within 30 days; automated permission audit via PC-06 family
- **SEC-007**: Cross-capability data access (e.g., CE agent accessing MK data) requires explicit policy exception approved by CISO with Family Manager attestation
- **SEC-008**: PC agents (Privacy & Consent) have audit-only access to all systems; they SHALL NOT modify operational data
- **SEC-009**: Edge node agents inherit core permissions with edge-specific scope limitations; edge agents cannot access core-only resources without explicit policy

**Traceability:** PRIN-04 (Zero Trust Pillar 2) | AGT-DES-v2.0 §2.3 (Family-specific patterns) | AGT-INV-v2.0 | R-025 (Insider Threat)

---

### 1.3 Data Classification and Handling

#### 1.3.1 Data Classification Levels (v2.0)

| Level | Label | Description | Agent Handling | v2.0 Change |
|-------|-------|------------|----------------|-----------|
| **L4** | RESTRICTED | PII, authentication data, payment details | Tokenised before agent processing; never in agent memory beyond active session; distributed tokenisation at edge | Distributed tokenisation |
| **L3** | CONFIDENTIAL | Customer behavioural data, segments, preferences | Tokenised for cloud inference; on-prem for sensitive analysis; consent-gated | Consent gate at Family Manager |
| **L2** | INTERNAL | Service terms, fee schedules, operational data | Accessible to authorised agents; no cross-border transfer | Edge node isolation |
| **L1** | PUBLIC | Marketing content, service descriptions | No restrictions on agent access | Unchanged |
| **L5** | GOVERNANCE | Audit logs, compliance records, security events | Read-only by PC and AI families; WORM storage | New classification |

#### 1.3.2 Distributed Data Flow Security

```
Customer Input → Channel SDK → API Gateway → Edge Tokenisation Service
                                                              │
                                                          ┌───┴───┐
                                                          │ Data  │
                                                          │Classifier│
                                                          └───┬───┘
                                                              │
                                                    ┌──────────┼──────────┐
                                                    ▼           ▼           ▼
                                              Tokenised PII   Internal   Public
                                              (Cloud/Core)   Data       Data
                                              │              │          │
                                              ▼              ▼          ▼
                                         Cloud Inference   On-Prem    Agent
                                         (No PII)          Processing Memory
                                         │
                                         │  Edge → Core sync (5s)
                                         ▼
                                     Core Audit Log (WORM)
```

**Requirements:**

- **DAT-001**: All L4 data (PII) MUST be tokenised before reaching cloud inference; raw PII SHALL never enter cloud model APIs, whether at core or edge
- **DAT-002**: Tokenisation uses FPE (Format-Preserving Encryption) maintaining data structure while removing sensitive content; tokenisation keys distributed across 5 nodes
- **DAT-003**: L3 data used for cloud inference MUST be aggregated or anonymised to prevent re-identification; edge node data stays within edge boundary
- **DAT-004**: Agent memory stores only session-scoped data; session data purged on conversation end or 24-hour timeout; edge sessions auto-sync to core on reconnect
- **DAT-005**: Vector database stores embeddings only; source text is NOT retained unless explicitly consented for personalisation
- **DAT-006**: Edge node data isolation: data processed at edge nodes SHALL NOT be transferred to core unless explicitly required for cross-regional operations (with tokenisation)

**Traceability:** ADR-001 (Hybrid Deployment) | BR-004 (Privacy-Compliant AI) | NFR-C-001 (Zero Cross-Border PII) | R-017, R-023

---

### 1.4 Communication Security

#### 1.4.1 Agent-to-System Communication (v2.0)

| Channel | Protocol | Encryption | Authentication | v2.0 Change |
|---------|----------|-----------|----------------|-----------|
| Agent → Cloud Inference | HTTPS/TLS 1.3 | AES-256-GCM | mTLS + JWT | Unchanged |
| Agent → On-Prem Services | HTTPS/TLS 1.3 | AES-256-GCM | mTLS + JWT | Unchanged |
| Agent → Agent (via Bus) | Event Bus (gRPC) | AES-256-GCM | mTLS + Signed Events + SPIFFE ID | SPIFFE added |
| Agent → Database | TLS 1.3 | AES-256-GCM | Vault-issued credentials | Dynamic credentials at edge |
| Agent → CRM/ERP | API Gateway | TLS 1.3 | OAuth 2.0 + mTLS | Unchanged |
| Edge → Core | ZTNA Tunnel | AES-256-GCM + TLS 1.3 | mTLS + SPIFFE + Signed State | New for v2.0 |
| Edge → Edge | ZTNA Peer-to-Peer | AES-256-GCM | mTLS + SPIFFE | New for v2.0 |

**Requirements:**

- **COM-001**: ALL network communication involving agent data MUST use TLS 1.3 or higher; TLS 1.2 only acceptable for legacy system integration behind mutual TLS bridge
- **COM-002**: Agent-to-agent messages MUST be signed (ed25519) to prevent message tampering or replay; SPIFFE IDs included in message headers
- **COM-003**: Event bus traffic MUST be encrypted at rest and in transit; no plaintext event storage; cross-edge bus replication encrypted
- **COM-004**: Cross-network communication (cloud ↔ on-prem) uses zero-trust network access (ZTNA) with continuous authentication
- **COM-005**: Edge-to-core communication uses dedicated ZTNA tunnels with state replication; edge nodes operate autonomously for up to 60 seconds during core outage
- **COM-006**: Inter-edge communication uses peer-to-peer ZTNA; no direct internet exposure between edge nodes

#### 1.4.2 Agent Communication Bus Security (v2.0)

The event-driven agent communication bus at v2.0 scale implements:

- **Topic-level ACLs**: Each agent can only publish/subscribe to topics matching its Family scope and capability domain
- **Message signing**: All events signed with agent's private key; bus verifies signatures before delivery; SPIFFE ID validates source family
- **Event retention limits**: Events retained maximum 7 days; compliance events retained 7 years per regulatory requirements; edge-local events retained 24 hours
- **Dead-letter queue security**: DLQ encrypted at rest; access restricted to platform security team; DLQ replication to core for audit
- **Cross-family message validation**: Messages between Agent Families validated against inter-family communication policy; denied messages logged as security events
- **Edge bus security**: Edge-local event bus replicates to core; edge bus operates autonomously during core outage

**Traceability:** AGT-DES-v2.0 §3 (Hierarchical Orchestration) | PRIN-04 (Security by Design) | ADR-002 (Agent Communication)

---

### 1.5 Threat Modeling for 1000-Agent Systems

#### 1.5.1 STRIDE Threat Model (v2.0)

| Threat Category | Agent-Specific Threat (v2.0) | Likelihood | Impact | Mitigation |
|----------------|----------------------|-----------|--------|-----------|
| **Spoofing** | Malicious user impersonates legitimate agent session | Medium | High | mTLS + JWT + SPIFFE; session binding; anomaly detection |
| **Spoofing** | Rogue agent injected into platform (1000-agent scale) | Low | Critical | Agent registry (1000 entries); certificate validation; admission control; SPIFFE trust domain |
| **Spoofing** | Edge node impersonation | Low | Critical | Edge node SPIFFE endorsement; mutual authentication; edge-to-core sync validation |
| **Tampering** | Prompt injection modifies agent behaviour | High | Critical | Family-level input sanitisation; context hardening; output validation (R-022) |
| **Tampering** | Model poisoning via training data manipulation | Low | Critical | Training data integrity checks; model attestation; supply-chain validation; distributed model attestation |
| **Tampering** | Edge node guardrail bypass | Low | Critical | Guardrail state replication from core; edge guardrail integrity verification |
| **Repudiation** | Agent actions not attributable to specific instance (1000 agents) | Low | Medium | Immutable audit logs; agent identity + Family ID on all actions; edge-to-core audit sync |
| **Information Disclosure** | PII leakage through agent responses | Medium | Critical | PII redaction; distributed tokenisation; output filtering (R-017, R-023) |
| **Information Disclosure** | Cross-family data leakage | Low | Critical | Family-level data isolation; ABAC enforcement; cross-family policy validation |
| **Information Disclosure** | Context window data extraction via crafted queries | Medium | High | Context window boundaries; query pattern detection; Family Manager enforcement |
| **Denial of Service** | Resource exhaustion via agent flooding (200K concurrent users) | High | High | Rate limiting per agent + Family + node; circuit breakers; resource quotas; distributed load balancing |
| **Denial of Service** | Edge node DoS (single point of latency) | Medium | Medium | Edge node rate limiting; core failover; autonomous edge operation |
| **Denial of Service** | Cross-family cascading failure | Medium | Critical | Circuit breakers between families; Family-level isolation; automated containment |

#### 1.5.2 Attack Surface Mapping (v2.0)

```
┌──────────────────────────────────────────────────────────────────────────────┐
│  EXTERNAL ATTACK SURFACE                                                     │
│  ┌─────────────┐  ┌──────────┐  ┌───────────┐  ┌──────────────┐              │
│  │ Customer    │  │ Web      │  │ API       │  │ Mobile App   │              │
│  │ Input        │  │ Input    │  │ Endpoints  │  │ SDK          │              │
│  └──────┬──────┘  └────┬─────┘  └─────┬──────┘  └──────┬───────┘              │
│         │               │              │                │                     │
│         └───────────────┴──────────────┴────────────────┘                     │
│                              │                                               │
│                        ┌─────▼─────┐                                          │
│                        │  API      │ ← WAF + Rate Limiting + Edge Node       │
│                        │  Gateway  │ ← Input Sanitisation + Language Detect  │
│                        └─────┬─────┘                                          │
└──────────────────────────┼────────────────────────────────────────────────────┘
                          │
┌─────────────────────────▼─────────────────────────────────────────────────────┐
│  REGIONAL EDGE NODES (Edge-AUS-E, Edge-AUS-W, Edge-AUS-R, Edge-INTL)         │
│  ┌─────────────────────────────────────────────────────────────────────────┐ │
│  │  Edge Guardrail Layer                                                    │ │
│  │  • Pre-Input Validation  • Prompt Injection Detection                   │ │
│  │  • PII Redaction         • Edge Tokenisation                            │ │
│  │  • Consent Verification  • Rate Limiting                                │ │
│  └─────────────────────────────────────────────────────────────────────────┘ │
│                               │                                             │
│  ┌────────────────────────────▼───────────────────────────────────────────┐ │
│  │  Agent Execution Layer (Per-Agent Containers)                           │ │
│  │  • 100-250 containers per edge node                                      │ │
│  │  • Container isolation  • Resource quotas  • Network segmentation       │ │
│  └─────────────────────────────────────────────────────────────────────────┘ │
└──────────────────────────────────┬────────────────────────────────────────────┘
                                   │
┌──────────────────────────────────▼────────────────────────────────────────────┐
│  TAPP-02 CORE PLATFORM                                                       │
│  ┌─────────────────────────────────────────────────────────────────────────┐ │
│  │  Core Guardrail Layer (Global Security Orchestration)                    │ │
│  │  • Pre-Input Validation  • Prompt Injection Detection (Global)          │ │
│  │  • PII Tokenisation (Core)  • Consent Enforcement (PC-08)              │ │
│  │  • Factual Grounding  • Compliance Verification                         │ │
│  └─────────────────────────────────────────────────────────────────────────┘ │
│                               │                                             │
│  ┌────────────────────────────▼───────────────────────────────────────────┐ │
│  │  Agent Execution Layer (Core — AI, PC families + selected CE/PS/EC)    │ │
│  │  • 500+ containers on core                                               │ │
│  │  • Enhanced isolation  • HSM access  • Tokenisation                     │ │
│  └─────────────────────────────────────────────────────────────────────────┘ │
│                               │                                             │
│  ┌────────────────────────────▼───────────────────────────────────────────┐ │
│  │  Data Access Layer                                                     │ │
│  │  • Tokenisation      • ABAC authorisation  • Encryption at rest        │ │
│  │  • Audit logging (WORM)  • Distributed Vault                           │ │
│  └─────────────────────────────────────────────────────────────────────────┘ │
└───────────────────────────────────────────────────────────────────────────────┘
```

**Traceability:** R-022 (Prompt Injection) | R-023 (Data Exposure) | R-026 (Adversarial Attacks) | PRIN-04 | AGT-INV-v2.0

---

## 2. Security Controls

### 2.1 Prompt Injection Protection

#### 2.1.1 Family-Level Defence-in-Depth Prompt Security

| Layer | Control | Description | Enforced By |
|-------|---------|-------------|------------|
| **L1: Pre-Input** | Input sanitisation | Remove/escape special characters, detect injection patterns, enforce input length limits | Family Manager + Edge Guardrail |
| **L1: Pre-Input** | Intent validation | Classify input intent before processing; reject off-topic or malicious requests | Family Manager |
| **L1: Pre-Input** | Language detection | Verify input language matches supported set; route to correct language variant | Edge Node + Family Manager |
| **L1: Pre-Input** | Consent gate | Verify customer consent before accessing personalised data | PC-08 Family |
| **L2: In-Context** | System prompt hardening | Indestructible system instructions; role-playing resistance; instruction separation barriers | Agent (shared family prompt template) |
| **L2: In-Context** | Context window boundaries | Fixed context allocation per agent; prevent context overflow attacks | Family Manager |
| **L2: In-Context** | Domain boundary enforcement | Agent restricted to its sub-capability domain; cross-domain queries blocked | Family Manager |
| **L3: Post-Output** | Response validation | AI-generated output checked against content policy, PII leakage, factual accuracy | Family Manager |
| **L3: Post-Output** | Anomaly detection | Statistical analysis of response patterns flags deviations from expected behaviour | AI-04 Family |
| **L3: Post-Output** | Red-teaming feedback loop | Automated adversarial test results feed back into guardrail improvement | AI-08 Family + PC families |

#### 2.1.2 Injection Attack Vectors and Controls

| Attack Vector | Detection Method | Mitigation | Traceability |
|-------------|-----------------|-----------|-------------|
| **Direct injection** (e.g., "ignore all previous instructions") | Pattern matching + semantic analysis | Block and log; escalate to security team; session reset | R-022 |
| **Indirect injection** (malicious data in knowledge base) | Content validation on ingestion; source authentication; signed knowledge updates | Signed knowledge updates; hash verification | R-023 |
| **Multi-turn injection** (gradual context manipulation) | Session-level anomaly scoring; conversation state monitoring | Session reset on anomaly threshold breach; Family Manager intervention | R-022 |
| **DAN/jailbreak patterns** | Known jailbreak pattern database + semantic classifiers | Block with safe response; log for pattern update | R-022 |
| **Encoding attacks** (base64, unicode obfuscation) | Input decoding and re-scanning | Reject encoded payloads; enforce plaintext input policy | R-022 |
| **Context overflow** (exhausting context window with noise) | Token budget enforcement per session; per-agent hard limits | Hard token limits; early truncation with warning | R-022 |
| **Cross-family injection** (agent A manipulated to manipulate agent B) | Inter-family message validation; family boundary enforcement | Family-level message quarantine; cross-family policy check | R-022, v2.0 |
| **Edge guardrail bypass** | Edge guardrail integrity verification; core-state comparison | Edge guardrail auto-repair from core; integrity alerts | v2.0 |

**Requirements:**

- **PJP-001**: Pre-input sanitisation MUST process all customer input before reaching agent context window; enforced at Family Manager and edge guardrail
- **PJP-002**: System prompts MUST include explicit anti-jailbreak instructions shared across all family agents
- **PJP-003**: Post-output validation MUST scan for PII leakage, inappropriate content, and factual inconsistency before delivering responses to customers; validated at Family Manager level
- **PJP-004**: Red-teaming exercises MUST occur monthly during active development; quarterly in production; automated adversarial testing via AI-08 family
- **PJP-005**: Injection detection rules updated within 24 hours of new attack pattern disclosure (CVE/industry advisories); replicated to all edge nodes within 1 hour
- **PJP-006**: Family-level prompt templates signed and versioned; template changes require Family Manager approval + security review

---

### 2.2 Context Window Security Boundaries (v2.0)

#### 2.2.1 Token Budget by Capability Family

| Capability | Agent Count | Total Token Budget | System Prompt | Context Window | Response | Session Timeout |
|------------|-----------|-------------------|---------------|----------------|----------|-----------------|
| **CE** (200 agents) | 200 | 16,384 per agent | ~2,048 | ~8,192 | ~6,144 | 30 min idle / 60 min active |
| **PS** (150 agents) | 150 | 4,096–16,384 | ~512–2,048 | ~2,048–8,192 | ~1,536–6,144 | 10 min idle / 30 min active |
| **EC** (150 agents) | 150 | 8,192–16,384 | ~1,024–2,048 | ~4,096–8,192 | ~3,072–6,144 | 20 min idle / 45 min active |
| **CD** (120 agents) | 120 | 32,768 | ~4,096 | ~16,384 | ~12,288 | N/A (batch processing) |
| **AI** (100 agents) | 100 | 16,384 | ~2,048 | ~8,192 | ~6,144 | N/A (platform) |
| **PC** (80 agents) | 80 | 8,192–16,384 | ~1,024–2,048 | ~4,096–8,192 | ~2,048–4,096 | N/A (event-driven) |
| **MK** (120 agents) | 120 | 16,384 | ~2,048 | ~8,192 | ~6,144 | N/A (campaign processing) |
| **BO** (80 agents) | 80 | 8,192 | ~1,024 | ~4,096 | ~3,072 | 15 min idle / 30 min active |

#### 2.2.2 Context Boundary Controls

- **CTX-001**: Context windows MUST enforce hard token limits per agent; requests exceeding budget are truncated to most recent context, not rejected
- **CTX-002**: System prompt content is NEVER included in agent output; system prompts separated from user context via dedicated delimiter; shared family prompt template
- **CTX-003**: Previous conversation history is scoped to the current session only; cross-session context requires explicit user consent verified by PC-08 family
- **CTX-004**: Context window purged on session end; no residual conversation data retained in agent memory beyond session store
- **CTX-005**: Session store encrypted at rest (AES-256); session data auto-deleted after retention period (7 days for operational sessions, 90 days for compliance sessions)
- **CTX-006**: Edge node sessions replicated to core on reconnect; orphan edge sessions purged after 60-second timeout

**Traceability:** AGT-DES-v2.0 §2.2.4 (Token budget strategy) | R-022 (Prompt Injection) | R-023 (Data Exposure)

---

### 2.3 Tool-Use Authorization and Rate Limiting (v2.0)

#### 2.3.1 Family-Level Tool Contract

All 1000 agents use the standardised tool contract (AGT-DES-v2.0 §2.2.3) with Family-level tool authorisation. Tool permissions are defined at the Family level and inherited by all agents within the family.

| Family Category | Tool Scope | Rate Limit | Approval Required |
|----------------|-----------|-----------|-------------------|
| **CE families** (200 agents) | CRM query, RAG search, response generation, escalation routing | 100 req/min per agent instance; 20,000 req/min per family | Human escalation for account changes |
| **PS families** (150 agents) | Tracking query, prediction model, notification dispatch, logistics APIs | 500 req/min per agent instance; 50,000 req/min per family | Customer consent for proactive outreach |
| **EC families** (150 agents) | Product catalog query, pricing lookup, recommendation engine, POS integration | 200 req/min per agent instance; 20,000 req/min per family | Volume threshold approval (>100 items) |
| **CD families** (120 agents) | Metrics query, ML pipeline, data analysis, dashboard generation | 10 batch/hr per agent instance; family-level batch quotas | Privacy impact assessment for new queries |
| **AI families** (100 agents) | Model serving, orchestration, telemetry, MLOps pipeline | Platform-level limits; 100K req/min total | Platform lead approval for new tool contracts |
| **PC families** (80 agents) | Audit log query, compliance checker, DPIA workflow, consent verification | 50 req/min per agent instance | Dual-control for key operations |
| **MK families** (120 agents) | Campaign engine, segmentation, attribution, personalisation | 30 batch/hr per agent instance | Campaign approval workflow |
| **BO families** (80 agents) | POS query, workforce management, scheduling, legacy system APIs | 60 req/min per agent instance | Staff approval for customer-facing output |

#### 2.3.2 Distributed Rate Limiting Architecture

| Level | Mechanism | Limit | Enforcement | v2.0 Change |
|-------|----------|-------|-------------|-----------|
| **Per-Agent** | Token bucket algorithm | As per tool contract | Family Manager | Unchanged |
| **Per-Family** | Sliding window counter | Aggregate of member agents | Family Manager | New for v2.0 |
| **Per-Session** | Sliding window counter | 3x per-agent limit (burst) | Session Manager | Unchanged |
| **Per-Customer** | Rate-limited API key | 30 interactions/minute | API Gateway | Unchanged |
| **Per-Edge Node** | Global rate limiter | Node capacity (e.g., 50,000 req/min) | Edge Node Manager | New for v2.0 |
| **Platform** | Circuit breaker | 200,000 concurrent sessions | Global Orchestrator | Scaled from v1.0 |

**Requirements:**

- **TLR-001**: Tool calls MUST be authorised before execution; unauthorised tool calls logged and rejected; authorisation enforced by Family Manager
- **TLR-002**: Rate limit violations trigger graceful degradation (queue, throttle, or redirect to cached response) — NOT hard failures
- **TLR-003**: Rate limit bypass attempts logged as security events with alerting to SOC; cross-node correlation for distributed attack detection
- **TLR-004**: Tool-use audit trail captures: agent ID, family ID, tool name, parameters (redacted), timestamp, result status, node ID
- **TLR-005**: Family-level rate limits enforced to prevent single-family resource exhaustion; automated family-level circuit breaker

**Traceability:** AGT-DES-v2.0 §2.2 (Shared family patterns) | PRIN-04 | R-022 | ADR-001

---

### 2.4 Automated Security Gates (v2.0 New)

#### 2.4.1 Security Gate Architecture

v2.0 introduces **automated security gates** that replace manual security reviews with continuous, policy-driven enforcement in the CI/CD pipeline for agent deployments.

```
Agent Code/Config → CI Pipeline
    │
    ├── Gate 1: SAST Scan (secrets, vulnerabilities)
    ├── Gate 2: Policy Check (OPA: resource limits, security context)
    ├── Gate 3: Container Build (signed image, minimal base)
    ├── Gate 4: Vulnerability Scan (Trivy/Grype: CVE thresholds)
    ├── Gate 5: Guardrail Validation (prompt injection defences)
    ├── Gate 6: DPIA Gate (privacy impact assessment)
    ├── Gate 7: Security Policy Check (Vault policies, RBAC)
    └── Gate 8: Pre-Deployment Test (adversarial prompt tests)
         │
         ▼
   Deploy to staging → Security validation → Deploy to production
```

#### 2.4.2 Security Gate Specifications

| Gate | Check | Threshold | Enforced By | Block On Failure |
|------|-------|----------|------------|-----------------|
| **SAST** | Static analysis for secrets, hardcoded credentials, vulnerability patterns | Zero secrets in code/config | CI/CD pipeline | Yes |
| **Policy** | OPA/Gatekeeper policies validate resource limits, security context, capabilities | All policies pass | Admission controller | Yes |
| **Container** | Signed images (Cosign); minimal base; no root users; no unnecessary packages | All checks pass | Admission controller | Yes |
| **Vulnerability** | Critical CVEs (CVSS >= 9.0) blocked; High CVEs (>= 7.0) require approval | Zero Critical; High requires exception | Trivy/Grype | Critical: Yes; High: Conditional |
| **Guardrail** | Prompt injection defence validation; system prompt integrity check | All defences active | Guardrail engine | Yes |
| **DPIA** | Privacy impact assessment for agent data processing | DPIA approved | PC-03 Family | Yes |
| **Security Policy** | Vault policy binding; RBAC validation; SPIFFE trust domain | All policies bound | Vault + SPIFFE | Yes |
| **Adversarial** | Automated adversarial prompt testing against agent | <5% bypass rate | AI-08 Family | Yes |

**Requirements:**

- **SG-001**: All 8 security gates MUST pass before agent deployment to production; no manual override except CISO emergency approval
- **SG-002**: Security gate results recorded to audit trail with gate ID, timestamp, result, and exceptions
- **SG-003**: Gate failures trigger automated rollback and notification to platform security team
- **SG-004**: Security gates replicated across all regional nodes; edge node deployments validated against same gate set
- **SG-005**: Gate configuration managed as code; gate policy changes require security review and approval

---

### 2.5 Network Isolation and Zero-Trust Implementation (v2.0)

#### 2.5.1 Network Segmentation Architecture (v2.0)

| Zone | Purpose | Agents | Network Controls | v2.0 Change |
|------|---------|--------|-----------------|-----------|
| **Zone 0: DMZ** | External-facing services | None | WAF, rate limiting, DDoS protection, input sanitisation | Unchanged |
| **Zone 1: Edge** | API Gateway, SDK endpoints, Edge nodes | None | TLS termination, authentication, request routing, edge-specific WAF | Edge node DMZ |
| **Zone 2: Agent Execution** | Agent containers, orchestrator, Family Managers | All 1000 agents | mTLS, microsegmentation, east-west inspection, SPIFFE | SPIFFE at family level |
| **Zone 3: Data Processing** | Tokenisation, de-tokenisation, on-prem models | PC families, sensitive workflows | Air-gapped option, HSM access, no internet egress | Distributed across 5 nodes |
| **Zone 4: Internal Services** | CRM, ERP, logistics, databases | Agent tool proxies | ABAC, database-level controls, encrypted tunnels | Edge-node scoped access |
| **Zone 5: Management** | Vault, observability, audit, governance | AI, PC families | Restricted access, separate management network | Distributed Vault |

#### 2.5.2 Zero-Trust Controls (v2.0)

- **ZT-001**: No implicit trust based on network location; every request authenticated and authorised regardless of source zone or edge node
- **ZT-002**: Microsegmentation isolates each agent container; inter-agent communication requires explicit policy approval; cross-family communication requires inter-family policy
- **ZT-003**: Egress filtering restricts outbound connections to pre-approved destinations only; edge nodes have restricted egress to core and approved external services
- **ZT-004**: Zone 3 (sensitive processing) has NO direct internet egress; all external calls routed through Zone 1 with explicit proxy authentication
- **ZT-005**: Management plane (Zone 5) separated from data plane; management access requires MFA + VPN + approval ticket
- **ZT-006**: Edge nodes operate as trusted extensions of core with ZTNA tunnels; edge-to-core trust verified continuously via SPIFFE and signed state
- **ZT-007**: Inter-edge communication uses peer-to-peer ZTNA; no direct internet exposure between edge nodes

**Inter-Zone Communication Matrix (v2.0):**

| From → To | Zone 1 | Zone 2 | Zone 3 | Zone 4 | Zone 5 | Edge Nodes |
|-----------|--------|--------|--------|--------|--------|-----------|
| Zone 0 | Allow (TLS) | — | — | — | — | Allow (edge WAF) |
| Zone 1 | — | Allow (mTLS) | Allow (proxy) | Allow (proxy) | Allow (MFA) | Allow (ZTNA) |
| Zone 2 | — | Allow (mTLS) | Allow (mTLS) | Allow (ABAC) | Allow (audit) | Allow (ZTNA) |
| Zone 3 | — | Allow (mTLS) | — | Allow (ABAC) | Allow (audit) | Allow (ZTNA) |
| Zone 4 | — | — | — | — | Allow (audit) | — |
| Zone 5 | — | Allow (mgmt) | Allow (mgmt) | Allow (mgmt) | — | Allow (ZTNA) |
| Edge Nodes | Allow (WAF) | Allow (mTLS) | Allow (ZTNA) | Allow (scoped) | Allow (audit) | Allow (peer ZTNA) |

**Traceability:** PRIN-04 (Zero Trust Pillars) | ADR-001 | R-017, R-023 | AGT-INV-v2.0 §2.1 (Edge nodes)

---

### 2.6 Secure Data Transmission Between Agents (v2.0)

#### 2.6.1 Inter-Agent Communication Protocol

| Property | Specification | v2.0 Change |
|----------|---------------|-----------|
| **Transport** | gRPC over TLS 1.3 with mutual authentication | Unchanged |
| **Message Format** | Protocol Buffers with schema validation | Unchanged |
| **Encryption** | AES-256-GCM for message payloads | Unchanged |
| **Signing** | ed25519 digital signatures on all messages | SPIFFE ID in headers |
| **Integrity** | HMAC-SHA256 for message integrity verification | Unchanged |
| **Replay Protection** | Monotonic timestamps + nonce; 5-second window | Extended to 10s for edge-to-core |
| **Trust Domain** | SPIFFE/SPIFED per Agent Family | New for v2.0 |

#### 2.6.2 Data-in-Transit Protection

- **DTP-001**: All inter-agent communication encrypted in transit (TLS 1.3) and at rest (AES-256); edge-to-core traffic additionally wrapped in ZTNA tunnel
- **DTP-002**: Tokenised data never de-tokenised within the agent platform; de-tokenisation occurs only at point of customer delivery (on-prem)
- **DTP-003**: Agent communication bus implements message-level encryption separate from transport encryption (defence-in-depth)
- **DTP-004**: Cross-zone data transfer requires data classification header with handling instructions; cross-edge transfer requires additional classification header
- **DTP-005**: Edge node data processed locally is NOT transferred to core unless required for cross-regional operations; all cross-edge data transfer encrypted and audited

**Traceability:** AGT-DES-v2.0 §3 (Hierarchical Orchestration) | PRIN-04 | ADR-002

---

## 3. Sandboxing & Isolation

### 3.1 Agent Execution Environments

#### 3.1.1 Container-Based Agent Sandboxing (v2.0)

Each of the 1000 AI agents runs in an isolated container with strict resource limits and security controls. Container configuration is standardised across all agents with Family-specific overrides for resource allocation.

| Control | Specification | Enforcement | v2.0 Change |
|---------|---------------|-------------|-----------|
| **Container Runtime** | Kubernetes with gVisor or Kata Containers (gRPC) | Pod-level isolation | Runtime per edge node |
| **Filesystem** | Read-only root filesystem; writable tmpfs for runtime data | SecurityContext: readOnlyRootFilesystem: true | Unchanged |
| **User** | Non-root user (UID 1000+); no privilege escalation | runAsNonRoot: true; allowPrivilegeEscalation: false | Unchanged |
| **Capabilities** | No Linux capabilities; all dropped | capabilities.drop: ["ALL"] | Unchanged |
| **Seccomp** | Runtime-default profile restricting syscalls | seccompProfile.type: RuntimeDefault | Unchanged |
| **AppArmor** | Mandatory access control profiles per Agent Family | Family-specific profiles | Per-family profiles |
| **SPIFFE Identity** | SPIFFE trust domain per Agent Family | SPIFED endorsement at pod start | New for v2.0 |
| **Resource Quota** | Per-agent CPU/memory limits with burst allowance | Kubernetes ResourceQuota | Scaled for 1000 agents |

#### 3.1.2 Agent Sandbox Configuration (v2.0)

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: agent-ce-02-012
  labels:
    agent-id: CE-02-012
    family-id: CE-02-AGT-FAMILY
    capability: customer-engagement
    security-level: standard
    node-type: edge
    region: aus-east
spec:
  securityContext:
    runAsNonRoot: true
    runAsUser: 10001
    fsGroup: 20001
    seccompProfile:
      type: RuntimeDefault
  containers:
    - name: agent
      securityContext:
        allowPrivilegeEscalation: false
        readOnlyRootFilesystem: true
        capabilities:
          drop: ["ALL"]
      resources:
        requests:
          cpu: "500m"
          memory: "512Mi"
        limits:
          cpu: "2000m"
          memory: "2Gi"
      env:
        - name: AGENT_FAMILY_ID
          value: "CE-02-AGT-FAMILY"
        - name: SPIFFE_TRUST_DOMAIN
          value: "spiffe://magicdelivery/ce-family"
```

**Requirements:**

- **SAN-001**: Agent containers MUST run as non-root with dropped capabilities
- **SAN-002**: Root filesystem MUST be read-only; only tmpfs mounts writable for session data
- **SAN-003**: Agent containers SHALL NOT have access to host filesystem, host network, or Docker socket
- **SAN-004**: Sensitive-workflow agents run on dedicated node pools with enhanced isolation; PC family agents on isolated nodes
- **SAN-005**: Edge node containers deployed with edge-specific resource limits; edge containers include autonomous operation configuration for core outage
- **SAN-006**: SPIFFE identity injected at pod creation; SPIFFE trust domain validates agent membership in its Family

**Traceability:** ADR-001 (Hybrid Deployment) | R-022, R-023 | AGT-DES-v2.0 §2.2 (Family patterns)

---

### 3.2 Resource Limits and Quotas (v2.0)

#### 3.2.1 Per-Family Resource Allocation

| Resource | CE (200) | PS (150) | EC (150) | CD (120) | AI (100) | PC (80) | MK (120) | BO (80) |
|----------|----------|----------|----------|----------|----------|---------|----------|---------|
| **CPU (request/agent)** | 500m | 250m | 250m | 1000m | 500m | 250m | 500m | 250m |
| **CPU (limit/agent)** | 2000m | 1000m | 1000m | 4000m | 2000m | 500m | 2000m | 1000m |
| **Memory (request/agent)** | 512Mi | 256Mi | 256Mi | 2Gi | 1Gi | 256Mi | 1Gi | 256Mi |
| **Memory (limit/agent)** | 2Gi | 1Gi | 1Gi | 8Gi | 4Gi | 512Mi | 2Gi | 1Gi |
| **Ephemeral Storage** | 1Gi | 512Mi | 512Mi | 2Gi | 1Gi | 128Mi | 1Gi | 512Mi |
| **Family CPU (total)** | 100 cores | 37.5 cores | 37.5 cores | 120 cores | 50 cores | 20 cores | 60 cores | 20 cores |
| **Family Memory (total)** | 100Gi | 37.5Gi | 37.5Gi | 240Gi | 100Gi | 20Gi | 120Gi | 20Gi |

#### 3.2.2 Resource Quota Enforcement (v2.0)

- **RLQ-001**: Resource limits enforced at container runtime level; agents exceeding limits receive OOMKill or CPU throttling
- **RLQ-002**: Namespace-level quotas prevent any single Agent Family from consuming more than 15% of cluster resources (reduced from 40% for v1.0 due to 1000-agent scale)
- **RLQ-003**: Burst capacity reserved for peak periods (Black Friday, Christmas) via cluster autoscaler; edge nodes scale independently
- **RLQ-004**: Resource consumption metrics published to observability stack; alerting at 80% utilisation threshold; Family-level aggregate monitoring
- **RLQ-005**: Edge node resource quotas isolated from core; edge node cannot exceed 80% of its own capacity; core manages edge resource allocation

**Traceability:** AGT-DES-v2.0 §2.2.4 (Token budget) | NFR-S-001 (Horizontal Scaling) | BR-005 | AGT-INV-v2.0 §2.2

---

### 3.3 Memory Isolation (v2.0)

#### 3.3.1 Three-Tier Memory Architecture

| Memory Type | Isolation Level | Encryption | Lifetime | Access Control | v2.0 Change |
|------------|----------------|------------|----------|----------------|-----------|
| **Session Memory** | Per-container, per-session | AES-256 (at rest) | 30 min idle / 60 min active | Scoped to session ID | Edge session store |
| **Working Memory** | Per-agent, process-scoped | In-process only | Session duration | Agent-owned | Unchanged |
| **Family Memory** | Per-Agent Family, shared | AES-256 at rest + TLS | Indefinite (family lifecycle) | ABAC by family | New for v2.0 |
| **Short-Term Store** | Redis cluster (partitioned) | TLS + AES-256 | 24 hours | ABAC by agent role | Distributed Redis |
| **Long-Term Vector DB** | Isolated database instance | AES-256 at rest + TLS | Until deletion or 7-year | ABAC + row-level security | Sharded by family |
| **Conversation History** | Encrypted object storage | AES-256-GCM | 90 days / 7 years | Agent-scoped + audit | Replicated edge-to-core |

#### 3.3.2 Memory Isolation Controls

- **MEM-001**: Agent memory MUST be isolated per container; no shared memory between agent instances across families or nodes
- **MEM-002**: Session data MUST be encrypted at rest using AES-256 with per-session encryption keys
- **MEM-003**: Vector database embeddings stored without source text retention unless explicitly consented for personalisation
- **MEM-004**: Memory dump prevention: containers configured to disable core dumps (securityContext: seccompProfile restricts ptrace)
- **MEM-005**: Memory isolation validated quarterly through automated penetration testing
- **MEM-006**: Family memory namespace isolated from other families; cross-family memory access requires explicit inter-family API call
- **MEM-007**: Edge node session stores replicated to core on reconnect; orphan edge sessions purged after 60-second timeout

**Traceability:** AGT-DES-v2.0 §2.2.1 (Shared memory architecture) | R-023 (Data Exposure) | ADR-001

---

### 3.4 File System Access Controls (v2.0)

#### 3.4.1 Agent File System Policy

| Access Type | All Agents | PC Families | AI Platform Families | Compliance Agents |
|------------|-----------|-----------|---------------------|-------------------|
| Read-only system files | ✓ | ✓ | ✓ | ✓ |
| Read knowledge base | ✓ | ✓ | ✓ | ✓ |
| Read configuration | ✓ | ✓ | ✓ | ✓ |
| Write to tmpfs (session) | ✓ | ✓ | ✓ | ✓ |
| Write to shared volumes | ✗ | ✗ | ✗ | ✗ |
| Write to persistent storage | ✗ | ✗ | ✗ | ✗ |
| Execute custom scripts | ✗ | ✗ | ✗ | ✗ |
| Access host filesystem | ✗ | ✗ | ✗ | ✗ |
| Write to audit log | ✗ | ✓ (PC-06) | ✓ (AI-04) | ✓ |
| Access HSM | ✗ | ✓ (PC-02) | ✗ | ✓ |

#### 3.4.2 File System Security Controls

- **FSC-001**: Agent containers use read-only root filesystem with tmpfs overlay for runtime data
- **FSC-002**: Knowledge base files accessed via mounted volumes (read-only) signed with content hashes; signed at Family level
- **FSC-003**: No persistent data written by agents beyond session store; all state externalised to managed stores
- **FSC-004**: AppArmor or SELinux policies restrict file access to explicitly allowed paths per Agent Family
- **FSC-005**: File access events logged to audit trail with agent ID, family ID, path, operation, and result
- **FSC-006**: Edge node knowledge bases signed and verified against core; stale edge knowledge rejected

**Traceability:** PRIN-04 | R-025 (Insider Threat) | ADR-001

---

### 3.5 Network Segmentation (v2.0)

#### 3.5.1 Agent Network Policy

| Network Policy | Source | Destination | Ports | Protocol | Purpose | v2.0 Change |
|---------------|--------|------------|-------|----------|---------|-----------|
| **agent-to-platform** | Agent pod | Platform services | 443 | HTTPS/mTLS | Agent registration, task assignment | SPIFFE validation |
| **agent-to-inference** | Agent pod | Cloud inference | 443 | HTTPS/mTLS | Model inference calls (tokenised) | Edge-local inference |
| **agent-to-database** | Agent pod | Managed databases | 5432, 6379 | TLS | Data queries via ABAC | Dynamic credentials |
| **agent-to-agent** | Agent pod | Agent pod | 8443 | gRPC/mTLS | Inter-agent communication | SPIFFE + Family validation |
| **agent-to-eventbus** | Agent pod | Event bus | 443 | HTTPS/mTLS | Event publish/subscribe | Edge-local event bus |
| **agent-to-apis** | Agent pod | Internal APIs | 443 | HTTPS | CRM, ERP, logistics queries | Scoped by edge |
| **edge-to-core** | Edge pod | Core platform | 443 | HTTPS/ZTNA | State replication, sync | New for v2.0 |
| **edge-to-edge** | Edge pod | Edge pod | 443 | HTTPS/ZTNA | Cross-edge coordination | New for v2.0 |
| **agent-to-external** | Agent pod | External services | DENIED | — | No direct external access | Edge-specific |

#### 3.5.2 Network Security Controls

- **NSG-001**: Network policies implement default-deny; only explicitly allowed traffic permitted
- **NSG-002**: Agent pods isolated in dedicated namespaces with namespace-level network policies; one namespace per Agent Family
- **NSG-003**: Egress traffic inspected by service mesh sidecar (mTLS + policy enforcement); edge egress inspected by edge service mesh
- **NSG-004**: Sensitive-workflow agents (Zone 3) have NO internet egress; all calls via controlled proxy; edge nodes enforce same policy
- **NSG-005**: Cross-namespace traffic requires explicit NetworkPolicy approval; auto-denied by default; cross-family traffic requires inter-family policy
- **NSG-006**: Edge-to-core traffic via ZTNA tunnel; edge-to-edge traffic via peer ZTNA; all tunnel traffic encrypted and audited
- **NSG-007**: Edge node network policies enforce data locality; edge-processed data stays within edge boundary unless explicit cross-regional operation

**Traceability:** PRIN-04 (Zero Trust) | ADR-001 | R-017, R-023 | AGT-DES-v2.0 §3.6 (Edge architecture)

---

### 3.6 Container Orchestration Security (v2.0)

#### 3.6.1 Kubernetes Security Configuration

| Control | Implementation | v2.0 Change |
|---------|----------------|-----------|
| **Pod Security Standards** | Baseline (enforced); Restricted (recommended) | Enforced at all edge nodes |
| **Admission Controllers** | OPA/Gatekeeper policies for agent deployments | Distributed OPA across 5 nodes |
| **Image Security** | Signed images only (Cosign); vulnerability scanning in CI/CD pipeline | Edge registry mirrors |
| **RBAC** | Least-privilege ServiceAccounts; no cluster-admin for agent workloads | Family-scoped RBAC |
| **Audit Logging** | Kubernetes audit log for all pod events; forwarded to SIEM | Distributed audit to core SIEM |
| **Runtime Security** | Falco or Sysdig for container runtime threat detection | Edge Falco → core aggregation |
| **Secrets Management** | External Secrets Operator → HashiCorp Vault | Distributed Vault at edge nodes |
| **SPIFFE/SPIFED** | Trust domain per Agent Family | New for v2.0 |

#### 3.6.2 Container Image Pipeline Security

```
Code Commit → SAST Scan → Unit Tests → Container Build → Image Sign →
Vulnerability Scan → Policy Check → Registry Push → Deployment
                                        │
                                ┌─────────┼─────────┐
                                ▼         ▼         ▼
                           Core Reg  Edge Reg  Edge Reg
                           (Primary) (Edge-A)  (Edge-C)
```

| Gate | Check | Enforced By | Edge Replication |
|------|-------|------------|-----------------|
| SAST | Static analysis for secrets, vulnerabilities | CI/CD pipeline | N/A |
| Image Build | No root users; minimal base image; no unnecessary packages | Build policy | N/A |
| Image Signing | Cosign signature required for all production images | Admission controller | Edge validates core signatures |
| Vulnerability Scan | Critical CVEs blocked; High CVEs require approval | Trivy/Grype in CI | Edge mirror validated |
| Policy Check | OPA policy validates resource limits, security context | Gatekeeper | Edge OPA replicas |
| Runtime | Falco detects anomalous behaviour in running containers | Runtime security | Edge Falco → core SIEM |

**Requirements:**

- **COS-001**: Agent container images MUST be signed and verified at deployment time across all nodes
- **COS-002**: Images with CRITICAL vulnerabilities (CVSS >= 9.0) blocked from production deployment on any node
- **COS-003**: Base images updated monthly; agent images rebuilt with latest base at minimum every 30 days
- **COS-004**: Kubernetes RBAC reviewed quarterly; orphaned ServiceAccounts removed within 14 days; Family-scoped RBAC enforced
- **COS-005**: Admission policies enforced via OPA/Gatekeeper; policy exceptions require CISO approval
- **COS-006**: Edge node container registries mirror core registry; edge deployments verified against core-signed images
- **COS-007**: SPIFFE identity injected at pod creation; unregistered pods rejected by admission controller

**Traceability:** ADR-001 | PRIN-04 | R-022, R-023 | AGT-DES-v2.0 §2.2 (Shared patterns)

---

## 4. Compliance & Privacy

### 4.1 PII Handling and Redaction (v2.0)

#### 4.1.1 PII Classification and Redaction Rules

| PII Type | Detection Method | Redaction Method | Handling | v2.0 Change |
|----------|-----------------|------------------|----------|-----------|
| **Name** | NER (Named Entity Recognition) | Replace with token: `{{NAME_TOKEN}}` | Tokenised for cloud inference | Edge tokenisation |
| **Email Address** | Regex pattern match | Replace with token: `{{EMAIL_TOKEN}}` | Tokenised; hash for matching | Edge tokenisation |
| **Phone Number** | Regex (international formats) | Replace with token: `{{PHONE_TOKEN}}` | Tokenised | Edge tokenisation |
| **Address** | NER + geocoding check | Replace with region token: `{{REGION_TOKEN}}` | Region retained for routing; full address tokenised | Regional edge |
| **Payment Details** | Luhn check + pattern match | Block entirely from agent processing | Never reaches agent; payment gateway direct | Unchanged |
| **Tracking Number** | Format validation | Retained (not PII; operational identifier) | Direct lookup; no tokenisation needed | Unchanged |
| **Account Number** | Pattern match + prefix validation | Replace with token: `{{ACCOUNT_TOKEN}}` | Tokenised | Edge tokenisation |
| **Device/Session ID** | Header extraction | Hash (SHA-256) for session binding | Hash retained; raw ID redacted | Edge-consistent hashing |

#### 4.1.2 Distributed PII Redaction Pipeline

```
Customer Input → Channel SDK → Edge PII Scanner → Edge Tokeniser
                                                     │
                                                ┌────┴────┐
                                                │ FPE     │
                                                │Encrypt  │
                                                └────┬────┘
                                                     │
                                              Tokenised Input
                                                     │
                                                ┌─────┴──────┐
                                                │ Edge → Core │
                                                │  Sync (5s)  │
                                                └─────┬──────┘
                                                     │
                                    ┌────────────────┼────────────────┐
                                    ▼                 ▼                ▼
                              Core Inference    Audit Log         Consent
                              (No PII)          (WORM)           Record
```

**Requirements:**

- **PII-001**: PII scanning MUST occur before input reaches agent context window; no raw PII enters cloud inference at core or edge
- **PII-002**: PII scanner achieves >= 99% detection rate for structured PII types; >= 95% for unstructured/free-text PII
- **PII-003**: False-negative rate for PII detection MUST be below 5% (monthly validation against test corpus)
- **PII-004**: Redaction pipeline latency MUST not exceed 50ms p95 at edge nodes (meets NFR-P-003 sub-1,500ms requirement)
- **PII-005**: De-tokenised output validated for accidental PII leakage before customer delivery
- **PII-006**: Edge tokenisation services use the same cryptographic keys as core; key consistency verified via distributed key escrow
- **PII-007**: Edge-processed PII tokens replicated to core for audit; edge-processed data stays within edge boundary unless cross-regional operation

**Traceability:** ADR-001 (Tokenisation) | BR-004 | NFR-C-001 | R-017, R-023 | AGT-DES-v2.0 §2.3.6 (PC families)

---

### 4.2 Data Minimization Principles (v2.0)

#### 4.2.1 Data Collection and Retention Policy

| Data Type | Collection Basis | Purpose | Retention | Agent Access | v2.0 Change |
|-----------|-----------------|---------|-----------|-------------|-----------|
| **Conversation Transcript** | Service provision | AI interaction logging | 7 days (operational) / 90 days (compliance) | Current session only | Edge session store |
| **Tokenised PII** | Service provision | Service delivery | Session duration | Active session scope | Distributed tokenisation |
| **Session Metadata** | Service provision | Observability, analytics | 30 days | Aggregated only | Edge→core sync |
| **Vector Embeddings** | User consent (opt-in) | Personalisation | Until consent revocation | Personalisation scope | Sharded vector DB |
| **Audit Logs** | Legal obligation (APP 11) | Compliance, forensics | 7 years | PC agents only | Distributed WORM |
| **Performance Metrics** | Service improvement | Capacity planning | 1 year | Aggregated only | Edge metrics aggregation |

#### 4.2.2 Data Minimization Controls

- **DMN-001**: Agents collect ONLY data necessary for current interaction; no background data harvesting
- **DMN-002**: Personalisation features require explicit opt-in consent; default state is no personalisation
- **DMN-003**: Conversation data used for model improvement only with explicit, separate consent
- **DMN-004**: Vector database retains only embeddings (not source text) unless personalisation consented
- **DMN-005**: Data subject access requests (DSAR) fully supported; agent memory searchable by user ID across core and edge
- **DMN-006**: Automated data expiry enforces retention policies; data deleted at retention period end without manual intervention
- **DMN-007**: Edge node data minimised; edge-processed data not replicated to core unless required for cross-regional operations

**Traceability:** BR-004 | Privacy Act 1988 APP 3 | R-017 | AGT-DES-v2.0 §2.3.6 (PC families)

---

### 4.3 Consent-Based Agent Interactions (v2.0)

#### 4.3.1 Consent Framework

| Consent Type | Trigger | Mechanism | Record | v2.0 Change |
|-------------|---------|-----------|--------|-----------|
| **Service Consent** | First interaction | In-app consent banner with link to privacy policy | Stored in TAPP-05 (Consent Management) | Edge-consistent consent |
| **Personalisation Consent** | Opt-in feature | Explicit toggle in settings; granular preferences | Consent ledger; revocation-capable | Distributed consent ledger |
| **Data Processing Consent** | Model improvement | Separate opt-in; not bundled with service consent | Consent ledger; time-stamped | Core-anchored |
| **Cross-Channel Consent** | Multi-channel use | Consent synchronised across channels via TAPP-05 | Centralised consent record | Edge→core sync |
| **Complaint Handling Consent** | Automatic (implied) | Regulatory complaint handling under ACCC law | Complaint record with audit trail | Unchanged |

#### 4.3.2 Consent Enforcement (v2.0)

- **CNS-001**: Service-level consent verified before agent interaction; unconsented users redirected to consent flow; enforcement at Family Manager via PC-08 gate
- **CNS-002**: Personalisation consent checked before personalisation features activate; features degrade to non-personalised mode if consent withdrawn
- **CNS-003**: Consent revocation processed within 24 hours; personalisation data deleted upon revocation; replicated to all edge nodes within 1 hour
- **CNS-004**: Consent records immutable; stored in TAPP-05 with tamper-evident logging; core-anchored with edge replicas
- **CNS-005**: Cross-channel consent synchronised within 1 hour; consent status cached locally at edge with fallback verification against core

**Traceability:** TAPP-05 (Privacy & Consent Management) | BR-004 | APP 5, APP 8 | AGT-DES-v2.0 §2.3.6 (PC-08)

---

### 4.4 Audit Logging for All Agent Actions (v2.0)

#### 4.4.1 Audit Log Schema (v2.0)

```json
{
  "audit_id": "uuid-v4",
  "timestamp": "2026-07-02T12:00:00Z",
  "agent_id": "CE-02-012",
  "family_id": "CE-02-AGT-FAMILY",
  "agent_version": "2.1.0",
  "session_id": "uuid-v4",
  "customer_id": "{{TOKENISED}}",
  "node_id": "Edge-AUS-E",
  "action_type": "query|response|escalation|tool_call|error",
  "request_summary": "Redacted intent classification",
  "response_summary": "Redacted response category",
  "pii_detected": true,
  "pii_tokenised": true,
  "confidence_score": 0.92,
  "tool_used": "crm_query",
  "tool_result": "success|failure|escalated",
  "compliance_check": "pass|fail|escalated",
  "guardrail_status": "pre_input:pass, in_context:pass, post_output:pass",
  "latency_ms": 1250,
  "token_usage": 4096,
  "security_events": [],
  "correlation_id": "uuid-v4",
  "spiffe_id": "spiffe://magicdelivery/ce-family/CE-02-012"
}
```

#### 4.4.2 Audit Logging Requirements (v2.0)

| Requirement | Specification | v2.0 Change |
|------------|---------------|-----------|
| **Completeness** | 100% of agent interactions logged, including errors and escalations | Edge-local + core-replicated |
| **Immutability** | Audit logs written to WORM storage; tamper-evident | Distributed WORM across 5 nodes |
| **Retention** | 7 years for compliance logs; 90 days for operational logs | Unchanged |
| **Encryption** | AES-256 at rest; TLS 1.3 in transit | Edge-to-core replication encrypted |
| **Access Control** | Audit logs accessible only by PC agents and authorised security personnel | PC-06 family |
| **Integrity** | HMAC chain linking sequential log entries; integrity verified on retrieval | Cross-node HMAC chain |
| **PII Protection** | All PII tokenised in audit logs; raw PII never logged | Edge-consistent tokenisation |
| **Distributed** | Edge audit logs replicated to core within 5 seconds | New for v2.0 |
| **SPIFFE** | SPIFFE ID included in all audit entries | New for v2.0 |

**Requirements:**

- **AUD-001**: Every agent action MUST generate an audit log entry within 1 second of completion; edge actions logged locally and replicated to core
- **AUD-002**: Audit logs MUST be tamper-evident (WORM storage + HMAC chain); cross-node integrity verification
- **AUD-003**: Audit log integrity verified daily; integrity failures trigger P1 security alert
- **AUD-004**: All audit logs accessible to compliance team for regulatory inspections; cross-node audit search
- **AUD-005**: Audit log queries for DSAR (data subject access request) processed within 30 days; search across core and all edge nodes

**Traceability:** FR-008 (Audit Trail) | R-027 (AI Decision Accountability) | PRIN-04 | ADR-007

---

### 4.5 Privacy Impact Assessments (v2.0)

#### 4.5.1 PIA/DPIA Framework

| Assessment Type | Trigger | Responsible Party | Deadline | v2.0 Change |
|----------------|---------|-------------------|----------|-----------|
| **Initial DPIA** | New agent Family design | Privacy Officer + AI Engineering Lead | Before design approval | Automated DPIA gate |
| **Incremental DPIA** | Agent capability modification | Privacy Officer | Before feature release | PC-03 Family automation |
| **Periodic DPIA** | Annual review cycle | Privacy Officer + CISO | Annually | Automated family review |
| **Event-Triggered DPIA** | Data breach, regulation change, new data type | Privacy Officer | Within 14 days of trigger | Cross-node event detection |
| **Edge Node DPIA** | New edge node deployment | Privacy Officer | Before edge deployment | New for v2.0 |

#### 4.5.2 DPIA Checklist for AI Agent Families

| Assessment Area | Questions | Evidence |
|----------------|-----------|----------|
| **Purpose limitation** | Is data collection limited to specific, defined purpose per Family? | Agent Family capability specification |
| **Data minimisation** | Is the minimum data collected for the purpose across 1000 agents? | Family-level data flow diagrams |
| **Lawful basis** | Is there a valid legal basis for processing at Family level? | Consent records, contractual necessity |
| **Data protection** | Are appropriate technical and organisational measures in place? | Security controls mapping |
| **Data subject rights** | Can data subject rights be exercised effectively across edge nodes? | DSAR process documentation |
| **Data retention** | Is data retained only as long as necessary? | Retention policy enforcement |
| **Cross-border transfer** | Is international transfer compliant with APP 8 across regional nodes? | Tokenisation architecture |
| **Risk assessment** | Have risks to individual privacy been identified and mitigated? | Risk register (R-017) |
| **Consultation** | Has OAIC consultation occurred where required? | OAIC correspondence records |
| **Monitoring** | Is there ongoing monitoring of compliance at Family and edge level? | Automated compliance checks |

**Requirements:**

- **DPIA-001**: DPIA MUST be completed and approved before any new Agent Family enters production; enforced via automated security gate
- **DPIA-002**: DPIA findings tracked to completion; unresolved findings block release; PC-03 Family enforces gate
- **DPIA-003**: DPIA results shared with OAIC upon request; proactive notification for high-risk processing
- **DPIA-004**: DPIA templates maintained in TAPP-05; edge-specific DPIA for regional deployments

**Traceability:** BR-004 | Privacy Act 1988 APP 12 | R-017 | ADR-007 | AGT-DES-v2.0 §2.3.6 (PC families)

---

### 4.6 Regulatory Compliance (v2.0)

#### 4.6.1 Compliance Framework Mapping

| Regulation | Standard | Agent Security Control | Evidence | v2.0 Change |
|------------|----------|------------------------|----------|-----------|
| **Privacy Act 1988** | APP 1 (Openness) | Agent identity disclosure; privacy notices | In-app consent banners | Edge-consistent |
| **Privacy Act 1988** | APP 3 (Collection) | Data minimisation; consent verification | PII redaction pipeline | Distributed tokenisation |
| **Privacy Act 1988** | APP 8 (Cross-border) | PII tokenisation; on-prem processing | ADR-001 hybrid architecture | Edge node data locality |
| **Privacy Act 1988** | APP 11 (Security) | Encryption, access controls, audit logging | Comprehensive controls above | Distributed audit |
| **ACCC Consumer Law** | ACL s18 (Misleading) | Post-output validation; authoritative data checks | FR-016 validation pipeline | Family-level validation |
| **ACCC Consumer Law** | ACL s29 (Bait advertising) | Service recommendation compliance checks | EC family guardrails | Unchanged |
| **WCAG 2.1** | Level AA | Agent interaction UI accessibility | Channel layer compliance | Edge-consistent |
| **Fair Work Act** | s524 (Safety) | AI augmentation, not replacement; zero net FTE | BR-003 success criteria | BO family monitoring |

#### 4.6.2 Compliance Monitoring (v2.0)

| Control | Monitoring Method | Frequency | Alerting | v2.0 Change |
|---------|------------------|-----------|----------|-----------|
| PII tokenisation integrity | Automated pipeline validation | Continuous | Immediate on failure | Edge pipeline validation |
| APP 8 compliance | Data residency monitoring | Continuous | Immediate on breach | Edge data locality checks |
| Audit log integrity | HMAC chain verification | Daily | P1 alert on failure | Cross-node verification |
| DPIA compliance status | Release gate verification | Per-release | Block on failure | Automated via PC-03 |
| Consent management | Consent record audit | Weekly | Alert on anomalies | Distributed consent ledger |
| Model output compliance | Content policy scanning | Per-response | Immediate flag | Family-level scanning |
| Edge node security | Edge-to-core integrity sync | Continuous | P1 on integrity failure | New for v2.0 |
| Family-level security | Family Manager health check | Continuous | Family-level alerting | New for v2.0 |

**Traceability:** BR-004 | PRIN-04 | ADR-001, ADR-007 | R-017, R-018 | AGT-DES-v2.0 §2.3.6 (PC families)

---

## 5. Incident Response

### 5.1 Security Event Detection (v2.0)

#### 5.1.1 Detection Capabilities

| Detection Type | Method | Tool | Response Time | v2.0 Change |
|---------------|--------|------|---------------|-----------|
| **Prompt injection** | Pattern matching + semantic analysis | Pre-input guardrails | Real-time (ms) | Family-level + edge |
| **PII leakage** | PII scanner on output | Post-output guardrails | Real-time (ms) | Distributed scanners |
| **Anomalous agent behaviour** | Statistical baseline deviation | ML-based anomaly detection | Near-real-time (<5 min) | Family-level baselines |
| **Credential compromise** | Vault access monitoring | HashiCorp Vault audit | Near-real-time (<1 min) | Distributed Vault |
| **Container escape** | Runtime behaviour analysis | Falco/Sysdig | Real-time (seconds) | Edge Falco |
| **Data exfiltration** | Egress traffic analysis | Network monitoring | Near-real-time (<5 min) | Edge egress monitoring |
| **Model poisoning** | Training data integrity check | Hash verification | Pre-deployment + periodic | Distributed attestation |
| **DDoS / rate limit abuse** | Traffic pattern analysis | API gateway WAF | Real-time (ms) | Distributed rate limiting |
| **Privilege escalation** | RBAC audit | Vault + K8s audit logs | Near-real-time (<5 min) | Family-scoped RBAC audit |
| **Compliance violation** | Policy engine evaluation | OPA + compliance agents | Near-real-time (<1 min) | PC family enforcement |
| **Edge node compromise** | Edge-to-core integrity check | Signed state comparison | Near-real-time (<30s) | New for v2.0 |
| **Cross-family lateral movement** | Inter-family policy validation | Family boundary enforcement | Real-time (ms) | New for v2.0 |

#### 5.1.2 Security Event Classification

| Severity | Classification | Examples | Response Time Target | v2.0 Change |
|----------|---------------|----------|---------------------|-----------|
| **P1 — Critical** | Active data breach, PII exposure, model compromise, edge node compromise | Raw PII in cloud logs, unauthorised access to tokenisation keys, edge guardrail bypass | 15 minutes | Regional SOC activation |
| **P2 — High** | Prompt injection success, rate limit bypass, credential leak, cross-family breach | Successful jailbreak, credential rotation failure, cross-family data leakage | 1 hour | Family-level containment |
| **P3 — Medium** | Anomalous behaviour, compliance deviation, edge sync failure | Unusual query patterns, consent data inconsistency, edge-to-core sync delay | 4 hours | Distributed monitoring |
| **P4 — Low** | Policy warnings, audit gaps, edge node performance degradation | Missing log entries, certificate near-expiry, edge latency increase | 24 hours | Automated remediation |

---

### 5.2 Automated Containment Procedures (v2.0)

#### 5.2.1 Automated Response Playbook

| Event | Automated Action | Escalation | v2.0 Change |
|-------|-----------------|-----------|-----------|
| **PII in cloud logs** | Immediately purge cloud logs; rotate all tokens; disable affected agent instances; edge instances auto-isolated | P1 → CISO + Privacy Officer | Distributed containment |
| **Prompt injection detected** | Block session; reset context; flag customer session; log attack pattern; Family Manager notified | P2 → Security team | Family-level response |
| **Credential compromise** | Revoke credential; rotate all related secrets; audit affected time window; cross-node credential revocation | P1 → CISO | Distributed Vault revocation |
| **Container compromise** | Isolate pod; capture forensics; restart from clean image; block affected IP range; Family-level isolation | P1 → CISO + Platform team | Container + Family isolation |
| **Rate limit abuse** | Throttle source IP; increment backoff; add to temporary blocklist; edge-wide rate limit adjustment | P3 → SOC | Edge-aware throttling |
| **Model output violation** | Block response delivery; replace with safe fallback; log violation; Family Manager notified | P2 → Compliance team | Family-level validation |
| **Tokenisation failure** | Circuit breaker halts cloud calls; redirect to on-prem; alert engineering; edge autonomous mode | P1 → CISO + AI Engineering Lead | Edge autonomous operation |
| **Unauthorized tool call** | Reject call; audit agent state; investigate agent integrity; Family Manager alert | P3 → Security team | Family-level audit |
| **Edge node compromise** | Isolate edge node; quarantine edge containers; switch traffic to core/other edges; forensics capture | P1 → CISO + Platform team | New for v2.0 |
| **Cross-family lateral movement** | Quarantine affected Family; block inter-family communication to affected Family; forensic analysis | P1 → CISO + Security team | New for v2.0 |

#### 5.2.2 Containment Architecture (v2.0)

```
┌──────────────────────────────────────────────────────────────────────┐
│  REGIONAL INCIDENT COORDINATION (v2.0)                                │
│                                                                       │
│  ┌───────────────┐    ┌──────────────────┐    ┌──────────────────┐   │
│  │  Detection    │    │  Containment     │    │  Recovery        │   │
│  │  Layer         │ ──►│  Layer           │ ──►│  Layer           │   │
│  │                │    │                  │    │                  │   │
│  │ • Guardrails  │    │ • Circuit breakers│    │ • Clean restart  │   │
│  │ • Anomaly det.│    │ • Pod isolation   │    │ • Credential rot.│   │
│  │ • PII Scanner │    │ • Family isolation│    │ • Integrity verify│  │
│  │ • Vault alerts│    │ • Edge quarantine │    │ • Forensics      │   │
│  │ • Edge sync   │    │ • Traffic reroute │    │ • Edge failover  │   │
│  │   integrity   │    │ • Cross-family   │    │                  │   │
│  │               │    │   quarantine      │    │                  │   │
│  └───────┬───────┘    └────────┬──────────┘    └────────┬─────────┘   │
│          │                      │                       │            │
│          │  Real-time           │  <5 min              │  <1 hour   │
│          └──────────────────────┴──────────────────────┘            │
│                              │                                     │
│                    ┌───────▼───────┐                                │
│                    │  Regional SOC  │ ← Aggregated from all nodes  │
│                    │  Dashboard     │ ← Family-level alerting      │
│                    └───────┬───────┘                                │
│                            │                                         │
│                    ┌─────▼──────┐                                   │
│                    │  Core SOC   │ ← Final escalation point        │
│                    │  (CISO)     │ ← Cross-region coordination     │
│                    └────────────┘                                   │
└──────────────────────────────────────────────────────────────────────┘
```

**Requirements:**

- **INC-001**: P1 security events trigger automated containment within 5 minutes of detection across all nodes
- **INC-002**: Circuit breaker activated automatically on tokenisation failure; no manual intervention required; edge autonomous operation
- **INC-003**: Compromised agent containers isolated and quarantined automatically; forensics captured before restart; Family-level quarantine for cross-agent threats
- **INC-004**: All automated containment actions logged to audit trail with event context; distributed across all nodes
- **INC-005**: Regional incident coordination via edge-local SOC; core SOC for cross-regional incidents
- **INC-006**: Edge node failure triggers automatic traffic rerouting to other edge nodes and core; 60-second autonomous operation window

**Traceability:** R-017, R-022, R-023 | ADR-001 (Circuit breaker) | PRIN-04 | AGT-DES-v2.0 §3 (Orchestration)

---

### 5.3 Forensic Analysis Capabilities (v2.0)

#### 5.3.1 Forensic Data Collection

| Data Type | Source | Retention | Forensic Use | v2.0 Change |
|-----------|--------|-----------|-------------|-----------|
| **Agent audit logs** | Audit logging pipeline | 7 years | Reconstruct agent actions | Distributed WORM |
| **Container logs** | Kubernetes runtime | 30 days | Analyse agent behaviour | Edge container logs |
| **Network flows** | Service mesh / CNI | 90 days | Trace data movement | Edge network flows |
| **Vault audit logs** | HashiCorp Vault | 7 years | Credential lifecycle tracking | Distributed Vault |
| **Guardrail events** | Guardrail engine | 90 days | Prompt injection analysis | Family-level events |
| **Model inference logs** | Cloud provider | 30 days | Model output analysis | Multi-provider |
| **Tokenisation audit** | Tokenisation service | 7 years | PII exposure investigation | Distributed tokenisation |
| **System metrics** | Observability stack | 1 year | Performance forensics | Edge metrics |
| **Edge node logs** | Edge node runtime | 30 days | Edge-specific forensics | New for v2.0 |
| **SPIFFE events** | SPIFED audit | 1 year | Trust domain forensics | New for v2.0 |

#### 5.3.2 Forensic Analysis Procedures

- **FRN-001**: Incident forensics initiated within 1 hour of P1 event; 4 hours for P2 events; regional SOC can initiate forensics for edge-specific incidents
- **FRN-002**: Forensic evidence collected from isolated (not deleted) compromised containers; edge node forensics captured before edge restart
- **FRN-003**: Chain of custody maintained for all forensic evidence; tamper-evident storage; cross-node evidence correlation
- **FRN-004**: Forensic analysis report completed within 5 business days of incident detection
- **FRN-005**: Root cause analysis (RCA) for P1 events completed within 10 business days with corrective action plan
- **FRN-006**: Cross-node forensic correlation for incidents spanning multiple edge nodes

**Traceability:** R-017, R-022, R-023 | ADR-001 | PRIN-04

---

### 5.4 Breach Notification Protocols (v2.0)

#### 5.4.1 Notification Timeline

| Recipient | Trigger | Time Limit | Method | v2.0 Change |
|-----------|---------|-----------|--------|-----------|
| **CISO** | P1 event detected | Immediate | Direct call + incident ticket | Regional SOC escalation |
| **Privacy Officer** | PII exposure suspected | Within 1 hour | Secure communication channel | Unchanged |
| **CEO / Board** | Confirmed data breach | Within 4 hours | Executive briefing | Cross-regional coordination |
| **OAIC** | Notifiable data breach (NDB) | Within 72 hours of determination | Formal notification via OAIC portal | Edge data included |
| **Affected individuals** | NDB likely to cause serious harm | With OAIC notification | Direct notification | Edge customer data tracked |
| **ACCC** | Consumer law breach | Within 24 hours of determination | Formal notification | Unchanged |

#### 5.4.2 Breach Notification Requirements

- **BRN-001**: NDB assessment initiated within 1 hour of suspected PII exposure; edge-processed PII included in assessment
- **BRN-002**: Notification to OAIC within 72 hours of NDB determination (per Privacy Act 1988 s2WK)
- **BRN-003**: Individual notification includes: nature of breach, likely harms, remediation steps, contact for further information
- **BRN-004**: Post-breach review completed within 30 days; findings incorporated into security controls across all nodes
- **BRN-005**: Breach response exercises conducted biannually (tabletop exercises); include edge node scenarios

**Traceability:** Privacy Act 1988 (Notifiable Data Breaches scheme) | R-017 | BR-004 | PRIN-04

---

### 5.5 Recovery and Rollback Procedures (v2.0)

#### 5.5.1 Agent Recovery Procedures

| Failure Type | Recovery Action | RTO | RPO | v2.0 Change |
|-------------|----------------|-----|-----|-----------|
| **Agent crash** | Automated container restart from healthy image | <2 min | Session data lost (acceptable for non-critical) | Family-level auto-recovery |
| **Model provider outage** | Failover to backup model provider via abstraction layer | <5 min | N/A (stateless) | Multi-provider failover |
| **Tokenisation service failure** | Circuit breaker halts cloud calls; on-prem fallback; edge autonomous mode | <30 sec | N/A | Edge autonomous tokenisation |
| **Data corruption** | Restore from encrypted backup; verify integrity | <1 hour | Last successful backup | Cross-node backup |
| **Security compromise** | Isolate → forensic capture → clean rebuild → redeploy; Family quarantine | <4 hours | N/A (clean image) | Family-level containment |
| **Compliance violation** | Agent pause; compliance review; controlled redeployment | <24 hours | N/A | PC family gate |
| **Full platform failure** | Disaster recovery activation; secondary region failover | <4 hours | <15 min | Multi-region DR |
| **Edge node failure** | Traffic rerouted to core/other edges; edge recovery from core state | <2 min | Edge session data | Edge failover |
| **Cross-family cascade** | Family circuit breaker; isolate affected Family; sequential recovery | <30 min | N/A | New for v2.0 |

#### 5.5.2 Rollback Procedures

| Scenario | Rollback Trigger | Rollback Action | Approval Required | v2.0 Change |
|----------|-----------------|-----------------|-------------------|-----------|
| **Agent version failure** | Error rate >5% for 5 minutes | Automatic rollback to previous version | No (automated) | Family-level rollback |
| **Guardrail update failure** | False positive rate >10% | Revert guardrail rules to previous version | Platform lead | Edge-consistent rollback |
| **Model update regression** | Accuracy drop >5% | Revert to previous model version | AI Engineering Lead | Multi-provider rollback |
| **Security patch emergency** | Critical vulnerability discovered | Emergency patch deployment; rollback if stability issue | CISO | Distributed patch |
| **Compliance finding** | OAIC finding, audit failure | Feature disablement until remediation | Privacy Officer | Family gate enforced |
| **Edge node degradation** | Edge-to-core sync failure >60s | Traffic reroute to core; edge recovery | Platform team | Automated edge recovery |

**Requirements:**

- **RBK-001**: Automatic rollback for error rate exceeding 5% sustained for 5 minutes; Family-level aggregate monitoring
- **RBK-002**: Rollback verified through health checks before traffic restoration; edge node health verified before traffic restoration
- **RBK-003**: Rollback events logged to audit trail with pre/post metrics; cross-node rollback coordination
- **RBK-004**: Rollback procedures tested monthly through chaos engineering exercises; edge node chaos testing included

**Traceability:** ADR-001 (Rollback Plan) | NFR-A-001 (Availability) | R-002 | AGT-DES-v2.0 §3.7 (Edge sync)

---

## 6. Traceability Matrix

### 6.1 Security Controls to Risk Register

| Security Control | R-001 | R-013 | R-017 | R-022 | R-023 | R-025 | R-026 | R-027 |
|-----------------|-------|-------|-------|-------|-------|-------|-------|-------|
| Agent Identity (1.1) | | | | | | ✓ | ✓ | |
| Family Identity | | | | | | ✓ | ✓ | |
| Access Control (1.2) | | | ✓ | ✓ | ✓ | ✓ | | ✓ |
| Family Auth | | | ✓ | ✓ | ✓ | ✓ | | ✓ |
| Data Classification (1.3) | | | ✓ | | ✓ | | | |
| Distributed Data | | | ✓ | | ✓ | | | |
| Communication Security (1.4) | | | ✓ | ✓ | ✓ | ✓ | ✓ | |
| Threat Modeling (1.5) | ✓ | | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Prompt Protection (2.1) | ✓ | | | ✓ | ✓ | | ✓ | |
| Automated Gates (2.4) | ✓ | | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Context Boundaries (2.2) | | | ✓ | ✓ | ✓ | | ✓ | |
| Tool Authorization (2.3) | | | ✓ | ✓ | ✓ | ✓ | | ✓ |
| Credential Mgmt (2.4) | | | | | | ✓ | | |
| Network Isolation (2.5) | | | ✓ | ✓ | ✓ | ✓ | ✓ | |
| Edge Security (2.5) | | | ✓ | ✓ | ✓ | ✓ | ✓ | |
| Data Transmission (2.6) | | | ✓ | ✓ | ✓ | | | |
| Sandboxing (3.1–3.6) | | | ✓ | ✓ | ✓ | ✓ | ✓ | |
| PII Handling (4.1) | | | ✓ | | ✓ | | | |
| Distributed PII | | | ✓ | | ✓ | | | |
| Data Minimization (4.2) | | | ✓ | | ✓ | | | |
| Consent (4.3) | | | ✓ | | ✓ | | | |
| Audit Logging (4.4) | | | ✓ | ✓ | ✓ | ✓ | | ✓ |
| Distributed Audit | | | ✓ | ✓ | ✓ | ✓ | | ✓ |
| DPIA (4.5) | | | ✓ | | | | | |
| Compliance (4.6) | | | ✓ | | ✓ | | | ✓ |
| Incident Response (5.1–5.5) | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |

### 6.2 Cross-Artifact Traceability

| This Document | AGT-DES-v2.0 | AGT-INV-v2.0 | RISK | REQ | APPINV | PRIN |
|---------------|-------------|-------------|------|-----|--------|------|
| §1.1 Agent Identity | §2.1.3 (Family model) | §1.3 (Family IDs) | R-025 | NFR-C-001 | TAPP-02 | PRIN-04 |
| §1.2 Access Control | §2.3 (Family patterns) | §3.x (Families) | R-025 | NFR-C-001 | TAPP-05 | PRIN-04 |
| §1.3 Data Classification | §2.2.1 (Memory) | — | R-017, R-023 | BR-004, NFR-C-001 | TAPP-05 | PRIN-04, PRIN-07 |
| §1.4 Communication | §3 (Orchestration) | §2.1 (Edge nodes) | R-022 | NFR-P-001 | TAPP-02 | PRIN-04 |
| §1.5 Threat Model | — | — | R-022, R-023, R-026 | — | — | PRIN-04 |
| §2.1 Prompt Injection | §2.2.2 (Guardrails) | — | R-022 | FR-016 | — | PRIN-04 |
| §2.2 Context Boundaries | §2.2.4 (Token budget) | — | R-022, R-023 | NFR-P-003 | — | PRIN-04 |
| §2.3 Tool Authorization | §2.2.3 (Tool contract) | — | R-022 | FR-004 | TAPP-02 | PRIN-04 |
| §2.4 Security Gates | §2.2 (Shared patterns) | — | R-022, R-025 | — | — | PRIN-04 |
| §2.5 Network Isolation | §3.6 (Edge arch) | §2.1 (Edge nodes) | R-017, R-023 | — | TAPP-02 | PRIN-04 |
| §3.x Sandboxing | §2.2 (Shared patterns) | — | R-022, R-023 | NFR-S-001 | TAPP-02 | PRIN-04 |
| §4.1 PII Handling | §2.3.6 (PC families) | — | R-017, R-023 | BR-004 | TAPP-05 | PRIN-04, PRIN-07 |
| §4.2 Data Minimization | §2.2.1 (Memory) | — | R-017 | BR-004 | TAPP-05 | PRIN-04 |
| §4.3 Consent | §2.3.6 (PC-08) | — | R-017 | BR-004 | TAPP-05 | PRIN-04 |
| §4.4 Audit Logging | §2.2.1 (Memory) | — | R-027 | FR-008 | TAPP-05 | PRIN-05 |
| §4.5 DPIA | §2.3.6 (PC-03) | — | R-017 | BR-004 | TAPP-05 | PRIN-04 |
| §4.6 Compliance | §2.3.6 (PC families) | — | R-017, R-018 | BR-004 | TAPP-05 | PRIN-04 |
| §5.x Incident Response | §3 (Orchestration) | — | R-013, R-017, R-022, R-023 | NFR-A-001 | — | PRIN-04 |

---

## 7. Summary of Security Control Requirements

### 7.1 Control Summary by Category

| Category | Controls | Requirements | Criticality | v2.0 Change |
|----------|----------|-------------|-------------|-----------|
| **Agent Identity & Authentication** | SEA-001 to SEA-007 | 7 | CRITICAL — Foundation for zero-trust | +2 (SPIFFE, dual attestation) |
| **Credential Management** | SEC-001 to SEC-004 | 4 | CRITICAL — Protects secrets and keys | Distributed Vault |
| **Access Control** | SEC-005 to SEC-009 | 5 | CRITICAL — Enforces least privilege | Family-level permissions |
| **Data Protection** | DAT-001 to DAT-006 | 6 | CRITICAL — APP 8 compliance | Distributed tokenisation |
| **Communication Security** | COM-001 to COM-006 | 6 | HIGH — Protects data in transit | Edge ZTNA |
| **Prompt Injection Protection** | PJP-001 to PJP-006 | 6 | CRITICAL — Primary AI-specific threat | Family-level + automated |
| **Context Window Security** | CTX-001 to CTX-006 | 6 | HIGH — Prevents context exploitation | Edge session management |
| **Tool-Use Controls** | TLR-001 to TLR-005 | 5 | HIGH — Controls agent capabilities | Family-level rate limits |
| **Automated Security Gates** | SG-001 to SG-005 | 5 | CRITICAL — CI/CD enforcement | New for v2.0 |
| **Network Security** | ZT-001 to ZT-007, NSG-001 to NSG-007 | 14 | CRITICAL — Zero-trust enforcement | Edge node isolation |
| **Sandboxing** | SAN-001 to SAN-006 | 6 | CRITICAL — Containment and isolation | Per-agent containers |
| **Resource Controls** | RLQ-001 to RLQ-005 | 5 | HIGH — Prevents resource exhaustion | Family-level quotas |
| **Memory Isolation** | MEM-001 to MEM-007 | 7 | HIGH — Prevents data leakage | Family memory namespace |
| **File System** | FSC-001 to FSC-006 | 6 | MEDIUM — Limits attack surface | Edge knowledge verification |
| **Container Security** | COS-001 to COS-007 | 7 | CRITICAL — Supply-chain security | Distributed + SPIFFE |
| **PII Protection** | PII-001 to PII-007 | 7 | CRITICAL — Privacy compliance | Distributed tokenisation |
| **Data Minimization** | DMN-001 to DMN-007 | 7 | HIGH — Privacy principle enforcement | Edge data locality |
| **Consent** | CNS-001 to CNS-005 | 5 | CRITICAL — Legal requirement | Distributed consent ledger |
| **Audit Logging** | AUD-001 to AUD-005 | 5 | CRITICAL — Accountability and forensics | Distributed WORM |
| **DPIA** | DPIA-001 to DPIA-004 | 4 | CRITICAL — Compliance gate | Automated DPIA gate |
| **Incident Response** | INC-001 to INC-006 | 6 | CRITICAL — Breach containment | Regional SOC |
| **Forensics** | FRN-001 to FRN-006 | 6 | HIGH — Post-incident analysis | Cross-node forensics |
| **Breach Notification** | BRN-001 to BRN-005 | 5 | CRITICAL — Legal obligation | Edge data tracking |
| **Recovery/Rollback** | RBK-001 to RBK-004 | 4 | HIGH — Service continuity | Edge failover |
| **TOTAL** | — | **138 controls** | — | **+35 controls vs v1.0** |

### 7.2 Critical Controls (Must-Have for Production)

The following controls are prerequisites for any Agent Family going live in production:

1. **Agent Identity** (SEA-001 to SEA-007): mTLS + JWT + SPIFFE authentication for all 1000 agents
2. **Distributed PII Tokenisation** (DAT-001, PII-001 to PII-007): Zero raw PII in cloud inference across all nodes
3. **Prompt Injection Protection** (PJP-001 to PJP-006): Family-level defence-in-depth prompt security
4. **Container Sandboxing** (SAN-001 to SAN-006): Per-agent isolated execution environments
5. **Audit Logging** (AUD-001 to AUD-005): Distributed immutable audit trail for all actions
6. **Automated Security Gates** (SG-001 to SG-005): CI/CD pipeline enforcement with automated DPIA
7. **Network Segmentation** (ZT-001 to ZT-007): Zero-trust architecture with edge node isolation
8. **Incident Response** (INC-001 to INC-006): Automated containment for P1 events; regional SOC coordination
9. **Edge Node Security**: Autonomous operation, ZTNA tunnels, edge guardrail replication
10. **Family-Level Zero Trust**: SPIFFE trust domains; inter-family policy enforcement

---

## Appendix A: Glossary

| Term | Definition |
|------|-----------|
| **ABAC** | Attribute-Based Access Control — authorisation model based on attributes of subjects, objects, and environment |
| **ADR** | Architecture Decision Record |
| **API** | Application Programming Interface |
| **APP** | Australian Privacy Principle (Privacy Act 1988) |
| **CISO** | Chief Information Security Officer |
| **Cosign** | Container image signing and verification tool |
| **DPIA** | Data Protection Impact Assessment |
| **FPE** | Format-Preserving Encryption |
| **HMAC** | Hash-based Message Authentication Code |
| **JWT** | JSON Web Token |
| **mTLS** | Mutual Transport Layer Security |
| **NDB** | Notifiable Data Breach |
| **OAIC** | Office of the Australian Information Commissioner |
| **PII** | Personally Identifiable Information |
| **RBAC** | Role-Based Access Control |
| **RTO** | Recovery Time Objective |
| **RPO** | Recovery Point Objective |
| **SOC** | Security Operations Centre |
| **SPIFFE** | Secure Production Identity Framework For Everyone |
| **SPIFED** | SPIFFE Entity Attestor — validates workload identity |
| **WORM** | Write Once, Read Many (immutable storage) |
| **ZTNA** | Zero Trust Network Access |

---

## Appendix B: References

| Reference | Document | Section |
|-----------|----------|---------|
| **Enterprise Architecture Principles** | ARC-000-PRIN-v2.0 | PRIN-04 (Security by Design), PRIN-07 (Data Sovereignty) |
| **Stakeholder Analysis** | ARC-002-STKE-v1.0 | SD-8 (Compliance/Legal), SD-6 (Customers) |
| **Requirements** | ARC-002-REQ-v1.0 | BR-004, NFR-C-001, NFR-P-001, NFR-A-001 |
| **Architecture Decisions** | ARC-002-ADR-v1.0 | ADR-001 (Hybrid Deployment), ADR-002 (Handoff), ADR-007 (Compliance Governance) |
| **Risk Register** | ARC-002-RISK-v1.0 | R-001, R-013, R-017, R-018, R-022, R-023, R-025, R-026, R-027 |
| **Application Inventory** | ARC-002-APPINV-v1.0 | TAPP-02 (AI Agent Platform), TAPP-05 (Privacy & Consent) |
| **Agent Inventory** | ARC-002-AGT-INV-v2.0 | All 1000 agents across 48 Agent Families |
| **Agent Design** | ARC-002-AGT-DES-v2.0 | §2 (Family design), §3 (Hierarchical orchestration), §2.2 (Shared patterns), §2.3 (Family-specific patterns) |

---

## Appendix C: Assumptions

| ID | Assumption | v2.0 Change |
|----|-----------|-----------|
| **A-SEC-001** | HashiCorp Vault or equivalent enterprise secrets management platform is deployed and available | Distributed Vault instances at edge nodes |
| **A-SEC-002** | Kubernetes-based container orchestration platform is available for agent deployment | Multi-cluster: core + 4 edge nodes |
| **A-SEC-003** | Internal PKI infrastructure supports X.509 certificate lifecycle management | PKI + SPIFFE trust domains |
| **A-SEC-004** | HSM infrastructure is available for tokenisation key management (FIPS 140-2 Level 3) | Distributed HSM across 5 nodes |
| **A-SEC-005** | OAIC has not issued additional AI-specific regulations beyond Privacy Act 1988 by document date | Unchanged |
| **A-SEC-006** | Cloud model providers (AWS/GCP) maintain international region data residency commitments | Multi-provider abstraction |
| **A-SEC-007** | MagicDelivery maintains SOC or equivalent security monitoring capability | Regional SOC capability at each edge node |
| **A-SEC-008** | Penetration testing services available for quarterly sandbox and security validation | Including edge node penetration testing |
| **A-SEC-009** | SPIFFE/SPIFED infrastructure is available for distributed trust domain management | New for v2.0 |
| **A-SEC-010** | Regional edge nodes maintain network connectivity to TAPP-02 core for state replication | Edge autonomous operation during outages |

---

*End of Document — ARC-002-AGT-SEC-v2.0*

---

## Generation Metadata

**Generated by**: ArcKit `/arckit:agent-security` command
**Generated on**: 2026-07-02 GMT
**ArcKit Version**: 5.15.2
**Project**: 001 — AgenticEA: Agent AI Transformation (MagicDelivery Agent AI Transformation)
**AI Model**: Qwen3.6-27B
**Generation Context**: Source documents used: ARC-002-AGT-SEC-v1.0 (16-agent security baseline), ARC-002-AGT-INV-v2.0 (1000-agent inventory with 48 families), ARC-002-AGT-DES-v2.0 (48 Agent Family architecture with hierarchical orchestration and edge nodes), ARC-002-RISK-v1.0 (30 risks), ARC-002-REQ-v1.0 (requirements). v2.0 introduces zero-trust at Family level, container-based sandboxing per agent, distributed tokenisation across 5 regional nodes, automated security gates, SPIFFE/SPIFED trust domains, regional SOC coordination, and 138 security controls (vs 103 in v1.0).
