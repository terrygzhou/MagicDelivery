# Architecture Decision Record: AgenticEA — Key Architecture Decisions

> **Template Origin**: Official | **ArcKit Version**: 5.15.2 | **Command**: `/arckit:adr`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-ADR-v1.0 |
| **Document Type** | Architecture Decision Records (ADR) |
| **Project** | 001 — AgenticEA: Agent AI Transformation |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-07-01 |
| **Last Modified** | 2026-07-01 |
| **Review Cycle** | Quarterly |
| **Next Review Date** | 2026-10-01 |
| **Owner** | Program Delivery Team (Programme Director) |
| **Reviewed By** | PENDING |
| **Approved By** | PENDING |
| **Distribution** | Executive Leadership, Parcel Business, Digital Technology, Compliance/Legal, Program Delivery Team, Enterprise Architecture Review Board |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-01 | ArcKit AI | Initial creation from `/arckit:adr` command — 8 ADRs covering AI deployment, agent-human handoff, data architecture, mobile integration, multi-channel consistency, workforce model, compliance governance, and performance strategy | PENDING | PENDING |

---

## Executive Summary

This document records eight critical architecture decisions for the **AgenticEA — MagicDelivery Agent AI Transformation** programme. Each ADR captures the context, evaluated alternatives, chosen decision, and consequences for a key architectural trade-off. These decisions are grounded in the stakeholder analysis (ARC-001-STKE-v1.0), requirements baseline (ARC-001-REQ-v1.0), and enterprise architecture principles (ARC-000-PRIN-v2.0).

The eight ADRs address:

| ADR | Decision | Status |
|-----|----------|--------|
| ADR-001 | Hybrid AI Agent Model Deployment (Cloud Inference + On-Prem Sensitive Data) | Proposed |
| ADR-002 | Hybrid Agent-Human Handoff with Complexity-Based Routing | Proposed |
| ADR-003 | Event-Driven Data Fabric for AI Agent Consumption | Proposed |
| ADR-004 | SDK Embedding for Mobile App AI Integration | Proposed |
| ADR-005 | Centralized Agent Backend with Multi-Channel UI | Proposed |
| ADR-006 | AI Co-Pilot Augmentation with Gradual Transition | Proposed |
| ADR-007 | Hybrid Compliance Governance (Pre-Deployment + Runtime) | Proposed |
| ADR-008 | Tiers-Based Performance with Predictive Scaling | Proposed |

---

# ADR-001: AI Agent Model Deployment Strategy

## Decision Title

Hybrid AI Agent Model Deployment: Cloud Inference with On-Prem Sensitive Data Processing

## 1. Context and Problem Statement

### 1.1 Problem Description

MagicDelivery must deploy AI agents serving 10 million customers for customer service, parcel tracking, and shopping assistance. The deployment model must balance scalability demands (50,000 concurrent users at peak), cost efficiency (under USD $0.05 per interaction), data privacy obligations under the Privacy Act 1988 (APPs), and international data residency requirements for personally identifiable information (PII).

**Problem statement as a question**: Where should AI agent model inference occur — entirely in the cloud, entirely on-premises, or in a hybrid configuration?

### 1.2 Why This Decision Is Needed

- **Business context**: BR-001 (AI-Driven Revenue Growth) and BR-005 (Scalable AI Platform) require a cost-effective, scalable model serving layer. G-1 targets USD $25M incremental revenue; G-5 targets sub-2-second p95 response times.
- **Technical context**: NFR-P-001 (Response Time), NFR-S-001 (Horizontal Scaling), and NFR-P-003 (Model Inference Latency under 1,500ms) constrain deployment options. PRIN Principle 3 (AI-Augmented Operations) and PRIN Principle 4 (Security by Design) are directly relevant.
- **Regulatory context**: Privacy Act 1988 APP 8 (cross-border disclosure), APP 11 (security), and international data residency expectations require PII to remain within international borders. NFR-C-001 mandates zero cross-border PII transfer without explicit consent.

### 1.3 Supporting Links

- **Requirements**: BR-001, BR-005, NFR-P-001, NFR-S-001, NFR-C-001
- **Stakeholders**: SD-1 (Parcel Business), SD-2 (Digital Technology), SD-6 (Customers), SD-8 (Compliance/Legal)
- **Related ADRs**: ADR-003 (Data Architecture), ADR-007 (Compliance Governance), ADR-008 (Performance Strategy)

---

## 2. Decision Drivers (Forces)

### 2.1 Technical Drivers

- **Scalability**: Platform must scale from 10,000 to 50,000 concurrent users during peak periods (Black Friday, Christmas). Cloud providers offer elastic scaling; on-prem requires significant CAPEX for peak capacity that sits idle 80% of the year.
- **Latency**: NFR-P-003 requires sub-1,500ms inference latency. Cloud-hosted inference in international regions (AWS ap-southeast-2) can achieve this; on-prem model serving adds complexity with limited GPU availability in Australia.
- **Model Diversity**: Multiple model types (conversational LLM, recommendation engine, tracking prediction) benefit from cloud model provider ecosystems and managed services.

### 2.2 Business Drivers

- **Cost Control**: Cloud inference operates on variable OPEX aligned to usage; on-prem requires fixed CAPEX. Target is under USD $0.05 per interaction (BR-005). Cloud API pricing for enterprise contracts ranges USD $0.01–0.04 per interaction.
- **Speed to Market**: Cloud-hosted models can be operational in weeks; on-prem model serving requires procurement, hardware installation, and tuning (3–6 months minimum).
- **Strategic Asset**: G-5 requires the AI platform to be a reusable strategic asset. Cloud infrastructure supports multi-project reuse.

### 2.3 Regulatory & Compliance Drivers

- **Privacy Act 1988 / APP 8**: Cross-border data disclosure requires explicit consent or APP 8 assessment. PII must remain in international data centres.
- **Data Residency**: All customer personal data must be stored and processed within international regions (NFR-C-001, data residency requirement).
- **ACCC Consumer Law**: AI-generated content must not be misleading or deceptive — requires real-time validation against authoritative data sources, more feasible with cloud-hosted validation services.

### 2.4 Alignment to Architecture Principles

| Principle | Alignment | Impact |
|-----------|-----------|--------|
| AI-Augmented Operations (PRIN-3) | Supports | Cloud model serving enables rapid agent deployment and iteration |
| Security by Design (PRIN-4) | Partial | Cloud introduces cross-border risk mitigated by on-prem PII processing |
| Composable Architecture (PRIN-2) | Supports | Cloud API boundaries enable loose coupling and independent deployment |
| Performance and Efficiency (PRIN-11) | Supports | Cloud auto-scaling meets variable demand patterns |
| Data Sovereignty (PRIN-7) | Supports | On-prem PII processing ensures international data residency |
| Legacy Modernization (PRIN-17) | Supports | Strangler pattern applies to model deployment transition |

---

## 3. Considered Options

### Option 1: Fully Cloud-Hosted LLM API (AWS/GCP international Region)

**Description**: Deploy all AI model inference through cloud provider APIs hosted in AWS ap-southeast-2 or GCP australia-southeast region. All data processing, including PII, occurs in international cloud regions.

**Implementation approach**: AWS Bedrock, GCP Vertex AI, or direct LLM provider API with international-region hosting. Tokenised conversations sent to model provider; no raw PII transmitted.

**Wardley Evolution Stage**: Product (Off-the-shelf — mature cloud AI services)

#### Good (Pros)

- ✅ **Rapid deployment**: Operational within 2–4 weeks via managed services
- ✅ **Elastic scaling**: Auto-scales to 75,000 concurrent burst users (NFR-S-001)
- ✅ **Cost efficiency**: Pay-per-use model; estimated USD $0.01–0.04 per interaction
- ✅ **Model diversity**: Access to multiple model providers through abstraction layer (INT-006)

#### Bad (Cons)

- ❌ **Cross-border risk**: Even with international regions, model provider legal entities may be subject to overseas data access laws (US Cloud Act)
- ❌ **Vendor lock-in**: Dependence on single or dual cloud providers
- ❌ **APP 8 compliance**: Requires annual APP 8 assessments for each model provider; ongoing governance burden
- ❌ **Data residency ambiguity**: Customer PII tokenisation must be perfect — any leakage to model API constitutes APP breach

#### Cost Analysis

- **CAPEX**: USD $0.5M (integration layer, tokenisation service)
- **OPEX**: USD $2.5M/year at Year 1 volume (25M interactions); USD $5M/year at Year 3 volume
- **TCO (3-year)**: USD $9.5M

### Option 2: Fully On-Premises Model Serving

**Description**: Host all AI models on MagicDelivery's own infrastructure within international data centres. Models run on dedicated GPU infrastructure procured and managed in-house.

**Implementation approach**: Open-source or self-hosted LLMs (Llama, Mistral, or commercial self-hosted models) on GPU clusters in international data centres.

**Wardley Evolution Stage**: Custom-Built

#### Good (Pros)

- ✅ **Full data sovereignty**: No cross-border data transfer; complete APP 8 compliance
- ✅ **Complete control**: Full model versioning, training data, and inference control
- ✅ **No vendor dependency**: No third-party API risk or pricing changes

#### Bad (Cons)

- ❌ **Prohibititive CAPEX**: USD $15–20M for GPU infrastructure, exceeding total programme budget
- ❌ **Limited model options**: Cannot access cutting-edge commercial models; constrained to open-source or licensed self-hosted models
- ❌ **Scaling limitations**: Peak capacity requires purchasing for 75,000 concurrent users; hardware sits idle 80% of the year
- ❌ **Skills gap**: Requires specialised ML engineering talent for model maintenance and infrastructure
- ❌ **Time-to-market**: 6–12 months for procurement, installation, and model tuning

#### Cost Analysis

- **CAPEX**: USD $18M (GPU infrastructure, data centre expansion)
- **OPEX**: USD $3.5M/year (staff, energy, maintenance, upgrades)
- **TCO (3-year)**: USD $28.5M

### Option 3: Hybrid (Cloud Inference + On-Prem Sensitive Data Processing)

**Description**: Cloud-hosted model inference for general AI operations, with on-premises or air-gapped processing for sensitive customer data. PII is tokenised before cloud transmission; tokenisation and de-tokenisation occur in MagicDelivery-controlled infrastructure.

**Implementation approach**: Two-tier architecture — (1) tokenisation service on MagicDelivery infrastructure converts PII to reversible tokens before cloud model calls; (2) cloud inference layer processes tokenised conversations with no PII exposure; (3) post-inference responses are de-tokenised on-prem before customer delivery. Sensitive workflows (complaints, security, legal) processed entirely on-prem with dedicated model instance.

**Wardley Evolution Stage**: Custom-Built (tokenisation layer) + Product (cloud inference)

#### Good (Pros)

- ✅ **Compliance-safe**: PII never leaves MagicDelivery infrastructure; APP 8 compliance by design
- ✅ **Scalable**: Cloud handles variable inference load; on-prem handles deterministic tokenisation
- ✅ **Cost-effective**: Cloud OPEX for inference; modest CAPEX for tokenisation layer
- ✅ **Flexibility**: Can swap cloud providers; tokenisation layer is provider-agnostic
- ✅ **Performance**: Cloud inference achieves sub-1,500ms latency; tokenisation adds ~50ms overhead

#### Bad (Cons)

- ❌ **Architecture complexity**: Two-tier data flow adds latency and operational overhead
- ❌ **Tokenisation risk**: Any tokenisation failure exposes PII to cloud provider
- ❌ **On-prem model maintenance**: Dedicated on-prem model for sensitive workflows requires model lifecycle management

#### Cost Analysis

- **CAPEX**: USD $2.5M (tokenisation infrastructure, on-prem model instances for sensitive workflows)
- **OPEX**: USD $3.0M/year (cloud inference + on-prem maintenance)
- **TCO (3-year)**: USD $11.5M

### Option 4: Do Nothing (Baseline)

**Description**: Continue with current non-AI customer service model; defer AI deployment decision.

#### Good

- ✅ No immediate investment required
- ✅ No compliance risk from AI deployment

#### Bad

- ❌ **Competitive disadvantage**: Competitors (Amazon Logistics, dedicated couriers) advance AI capabilities
- ❌ **Opportunity cost**: USD $25M incremental revenue target (BR-001) and USD $15M operational savings (BR-003) deferred
- ❌ **Strategic risk**: SD-9 (Executive Leadership) AI transformation mandate cannot be met
- ❌ **Technical debt**: Legacy infrastructure continues to accumulate debt (PRIN-17)

---

## 4. Decision Outcome

### 4.1 Chosen Option

**"Option 3: Hybrid AI Agent Model Deployment (Cloud Inference + On-Prem Sensitive Data Processing)"**

### 4.2 Y-Statement

> **In the context of** deploying AI agents for 10 million MagicDelivery customers across customer service, parcel tracking, and shopping domains,
> **facing** the tension between cloud scalability and Privacy Act data residency requirements,
> **we decided for** a hybrid deployment model with cloud-hosted inference for general operations and on-premises tokenisation for sensitive data processing,
> **to achieve** scalable, cost-effective AI serving that maintains international data sovereignty by design,
> **accepting** increased architectural complexity and tokenisation layer maintenance overhead.

### 4.3 Justification

**Key reasons**:

1. **Compliance-first architecture**: The hybrid model ensures PII never reaches cloud providers, eliminating APP 8 cross-border disclosure risk. This satisfies SD-8 (Compliance/Legal) as a primary stakeholder driver and meets NFR-C-001 without operational exceptions.
2. **Cost-to-value ratio**: At USD $11.5M TCO over 3 years, the hybrid approach delivers 70% lower cost than fully on-prem (USD $28.5M) while maintaining full data sovereignty — a superior value proposition versus fully cloud (USD $9.5M) which carries unacceptable compliance risk.
3. **Scalability with control**: Cloud inference layer scales elastically to meet NFR-S-001 growth projections (50,000 to 100,000 concurrent users over 3 years), while the on-prem tokenisation layer handles predictable, low-variance workloads.

**Stakeholder consensus**: SD-8 (Compliance/Legal) requires data sovereignty; SD-2 (Digital Technology) requires scalability; SD-1 (Parcel Business) requires cost efficiency. Hybrid satisfies all three. No significant dissenting views expected.

**Risk appetite**: Medium — architecture introduces complexity risk mitigated by rigorous tokenisation testing and monitoring (see ADR-007).

---

## 5. Consequences

### 5.1 Positive Consequences

- ✅ **Compliance assurance**: PII never transmitted to cloud providers; APP 8 compliance by design, not by process
- ✅ **Elastic scalability**: Cloud layer scales to 75,000 burst concurrent users; meets NFR-S-001 growth projections
- ✅ **Cost optimisation**: 59% TCO reduction versus fully on-prem; supports BR-005 sub-USD $0.05 cost per interaction
- ✅ **Multi-provider flexibility**: Tokenisation layer is provider-agnostic; can swap cloud providers without re-architecture
- ✅ **Gradual onboarding**: Non-sensitive AI capabilities can go live immediately via cloud; sensitive workflows added on-prem in parallel

**Measurable outcomes**:

- Cost per interaction: Target < USD $0.04 (from cloud pricing at volume)
- Inference latency: p95 < 1,500ms (cloud) + ~50ms (tokenisation) = p95 ~1,550ms
- Compliance incidents: Zero APP 8 findings (PII never leaves MagicDelivery infrastructure)

### 5.2 Negative Consequences (Accepted Trade-offs)

- ❌ **Architecture complexity**: Two-tier data flow increases development and operational complexity
- ❌ **Tokenisation failure risk**: Tokenisation service is a single point of compliance failure
- ❌ **On-prem model lifecycle**: Dedicated sensitive-workflow model requires ongoing maintenance

**Mitigation strategies**:

- **Tokenisation risk**: Cryptographic key management in HashiCorp Vault; automated integrity verification; dual-key redundancy with independent key holders
- **Complexity**: Standardised integration contracts (INT-006); containerised tokenisation microservice; automated testing of tokenisation pipeline
- **Model maintenance**: Model lifecycle management per NFR-M-003; quarterly model reviews; automated accuracy monitoring

### 5.3 Neutral Consequences (Changes Needed)

- Training: AI Engineering team training on tokenisation architecture and secure key management
- Infrastructure: Tokenisation service deployment in two international data centres (active-active)
- Process: Tokenisation pipeline monitoring and alerting integrated into existing observability stack (PRIN-5)
- Vendor relationships: Tokenisation service vendor relationship; cloud provider enterprise agreement

### 5.4 Risks and Mitigations

| Risk | Likelihood | Impact | Mitigation | Owner |
|------|------------|--------|------------|-------|
| Tokenisation service failure exposes PII to cloud | Low | Critical | Dual-key redundancy; automated integrity checks; circuit breaker halts cloud calls on failure | Head of Digital Technology |
| On-prem model capacity insufficient for sensitive workflows | Medium | High | Capacity planning with 2x headroom; auto-scale GPU instances; fallback to human escalation | AI Engineering Lead |
| Cloud provider region outage | Low | High | Multi-region failover (ap-southeast-1); cross-region tokenisation; graceful degradation to cached responses | Head of Digital Technology |
| Tokenisation latency exceeds SLA | Medium | Medium | Performance testing at 1.5x peak; async tokenisation for non-real-time workflows; CDN-level caching for common tokens | Platform Engineering Lead |

---

## 6. Implementation Plan

### 6.1 Dependencies

- ADR-003 (Data Architecture Pattern): Data fabric must support tokenisation service data flows
- ADR-007 (Compliance Governance): Tokenisation compliance requires governance framework
- Infrastructure: Two international data centres with GPU capacity for sensitive-workflow model instances

### 6.2 Implementation Timeline

| Phase | Activities | Duration | Owner |
|-------|-----------|----------|-------|
| Phase 1: Tokenisation Design | Tokenisation service architecture, key management design, security review | 4 weeks | AI Engineering Lead |
| Phase 2: Cloud Integration | Cloud inference layer, multi-provider abstraction, tokenisation pipeline | 8 weeks | Platform Engineering Team |
| Phase 3: On-Prem Model | On-prem sensitive-workflow model setup, GPU infrastructure, model tuning | 6 weeks | AI Engineering Lead |
| Phase 4: Integration Testing | End-to-end tokenisation flow testing, compliance validation, performance testing | 4 weeks | QA / Compliance Team |

### 6.3 Rollback Plan

**Rollback trigger**: Tokenisation service integrity failure; compliance finding on PII exposure; inference latency exceeding 3,000ms p95 for 30 minutes.

**Rollback procedure**:

1. Activate circuit breaker to halt cloud model API calls
2. Redirect all traffic to on-prem model instance (degraded performance, full compliance)
3. Notify Compliance/Legal of incident; begin root cause investigation
4. Tokenisation service repair with key rotation
5. Gradual traffic restoration with monitoring

---

## 7. Review and Updates

**Initial review**: 2027-01-01 (6 months after implementation)
**Periodic review**: Annually, or triggered by events
**Review criteria**: Success metrics on track? Tokenisation architecture still optimal? New compliance requirements?

---

# ADR-002: Agent-Human Handoff Model

## Decision Title

Hybrid Agent-Human Handoff with Complexity-Based Routing

## 1. Context and Problem Statement

### 1.1 Problem Description

AI agents must seamlessly escalate to human agents when they cannot resolve queries confidently. Current call centre model (120,000 inbound queries per month, 60% routine, 40% complex) must integrate with AI handoff without disrupting human agent workflows or customer experience. The handoff model must ensure customers receive the right level of assistance while AI agents handle the maximum volume of routine queries.

**Problem statement as a question**: What handoff model maximises AI deflection while maintaining seamless customer experience when human intervention is required?

### 1.2 Why This Decision Is Needed

- **Business context**: BR-003 targets 40% routine call deflection (48,000 calls/month handled by AI) with zero net FTE reduction (G-3). FR-004 defines handoff requirements including sub-30-second escalation and full context transfer.
- **Technical context**: NFR-P-001 requires sub-2-second response times; handoff latency must not degrade the AI-first experience. INT-002 (CRM) must support context injection during handoff.
- **Regulatory context**: ACCC consumer law requires that AI escalation does not delay resolution of complaints or security concerns (NFR-C-003). Fair Work Act compliance requires that handoff models support staff augmentation (NFR-C-004).

### 1.3 Supporting Links

- **Requirements**: BR-003, FR-004, FR-007, NFR-P-001
- **Stakeholders**: SD-6 (Customers), SD-7 (Operations Staff), SD-8 (Compliance/Legal)
- **Related ADRs**: ADR-001 (Deployment Strategy), ADR-006 (Workforce Augmentation), ADR-005 (Multi-Channel Consistency)

---

## 2. Decision Drivers (Forces)

### 2.1 Technical Drivers

- **Context transfer**: Full conversation history, AI confidence scores, attempted responses, and customer data must transfer during handoff without loss
- **Routing intelligence**: Complexity-based routing must classify queries in real-time and direct to appropriate agent skills/groups
- **Performance**: Handoff must complete within 30 seconds (FR-004) with no perceptible interruption to customer

### 2.2 Business Drivers

- **Cost efficiency**: Maximal AI deflection of routine queries reduces operational cost per interaction
- **Staff augmentation**: SD-7 (Operations Staff) driver requires AI tools that reduce workload, not add complexity
- **Customer experience**: SD-6 driver — seamless handoff preserves trust; jarring handoff degrades CSAT

### 2.3 Regulatory & Compliance Drivers

- **Complaint handling**: Regulatory complaints must escalate immediately to qualified human agents
- **Audit trail**: FR-008 requires complete handoff audit records for compliance
- **Privacy**: PII transfer during handoff must maintain APP 11 security standards

### 2.4 Alignment to Architecture Principles

| Principle | Alignment | Impact |
|-----------|-----------|--------|
| AI-Augmented Operations (PRIN-3) | Supports | Handoff is human-in-the-loop escalation path per principle |
| Composable Architecture (PRIN-2) | Supports | Handoff as independent service with published API |
| Security by Design (PRIN-4) | Supports | Secure context transfer with least privilege access |
| Loose Coupling (PRIN-9) | Supports | Handoff service decoupled from AI agent and CRM systems |

---

## 3. Considered Options

### Option 1: Seamless Warm Handoff (AI-to-Human with Full Context)

**Description**: AI agent detects low confidence or high-risk query, initiates warm handoff transferring full conversation context to an available human agent. Customer experiences continuous interaction with no re-authentication or re-statement.

**Implementation approach**: Real-time handoff via CRM API (INT-002); conversation transcript, confidence scores, AI-generated brief injected into agent workspace; customer transferred to agent queue within 30 seconds.

#### Good (Pros)

- ✅ **Best customer experience**: Zero disruption; customer never needs to repeat information
- ✅ **Agent productivity**: Full context enables immediate resolution; no re-investigation needed
- ✅ **Trust preservation**: Seamless transition reinforces confidence in AI-augmented service

#### Bad (Cons)

- ❌ **Integration complexity**: Requires real-time CRM integration with full context injection
- ❌ **Agent workload**: Warm handoff requires agent to review full transcript before engaging
- ❌ **Cost**: Higher operational cost as handoff is more resource-intensive than cold transfer

### Option 2: Self-Service with Human Fallback (AI-First, Opt-In Escalation)

**Description**: AI agent handles queries independently; customer explicitly requests human agent via "talk to a person" prompt. No proactive escalation by AI.

#### Good (Pros)

- ✅ **Maximal AI deflection**: Only explicit escalations reach human agents
- ✅ **Lower operational cost**: Minimal human resource commitment
- ✅ **Simplest architecture**: No proactive routing complexity

#### Bad (Cons)

- ❌ **Customer frustration**: AI struggling customers forced to request human manually
- ❌ **Trust erosion**: Repeated AI failures without automatic escalation damage brand perception
- ❌ **Compliance risk**: Regulatory complaints may not escalate without explicit customer action
- ❌ **CSAT impact**: SD-6 driver — customers expect AI to know its limits

### Option 3: AI-First with Human Review (All AI Responses Vetted)

**Description**: AI generates responses but all responses undergo human review before delivery to customer. Human can approve, modify, or reject AI-generated responses.

#### Good (Pros)

- ✅ **Quality assurance**: Human oversight prevents hallucination-related errors
- ✅ **Compliance safety**: Human verification satisfies ACCC consumer law for regulated topics

#### Bad (Cons)

- ❌ **Performance bottleneck**: Human review adds significant latency; cannot meet sub-30-second target at scale
- ❌ **Operational cost**: Requires human for every interaction; defeats AI cost-efficiency goal
- ❌ **Scalability**: Cannot handle 50,000 concurrent users with human review per interaction
- ❌ **Staff fatigue**: Reviewing thousands of AI responses creates burnout risk

### Option 4: Hybrid Routing Based on Query Complexity

**Description**: AI classifies queries by complexity level in real-time — routine queries handled autonomously, moderate-complexity queries handled by AI with human review queue, high-complexity/risk queries immediately escalated to human agents. Routing is dynamic based on query content, customer context, and AI confidence scores.

#### Good (Pros)

- ✅ **Optimal balance**: Maximal AI handling of routine queries with intelligent escalation for complex cases
- ✅ **Proactive compliance**: High-risk topics (complaints, security, legal) auto-escalate without customer action
- ✅ **Scalable**: Complexity routing distributes workload efficiently; human agents handle appropriate volume
- ✅ **Customer-centric**: Customer never forced to re-state; complexity detection prevents AI struggling in plain sight
- ✅ **Measurable**: Clear metrics on deflection rate, escalation rate, and resolution quality per complexity tier

#### Bad (Cons)

- ❌ **Classification accuracy**: Requires accurate real-time complexity classification; false positives create unnecessary handoffs, false negatives create customer frustration
- ❌ **Agent skills matching**: Routing to appropriate agent skill groups requires sophisticated workforce management integration
- ❌ **Complexity tuning**: Thresholds require continuous calibration based on feedback data (FR-010)

### Option 5: Do Nothing (Baseline)

**Description**: Continue current call centre model with no AI-augmented handoff.

#### Good

- ✅ No integration risk
- ✅ No workforce transition complexity

#### Bad

- ❌ **No deflection benefit**: BR-003 (40% routine call deflection) not achievable
- ❌ **Customer experience unchanged**: 8-minute wait times persist (BR-002)
- ❌ **Strategic failure**: SD-9 AI transformation mandate unmet
- ❌ **Competitive disadvantage**: Competitors advance AI capabilities

---

## 4. Decision Outcome

### 4.1 Chosen Option

**"Option 4: Hybrid Routing Based on Query Complexity"**

### 4.2 Y-Statement

> **In the context of** integrating AI agents with MagicDelivery's existing call centre serving 120,000 monthly inbound queries,
> **facing** the need to maximise AI deflection while ensuring seamless customer experience and regulatory compliance,
> **we decided for** hybrid routing based on real-time query complexity classification,
> **to achieve** optimal balance between AI efficiency (40% routine deflection target) and human expertise for complex interactions,
> **accepting** complexity classification risk requiring continuous threshold calibration.

### 4.3 Justification

**Key reasons**:

1. **Optimal deflection-to-quality ratio**: Complexity-based routing handles ~60% of queries autonomously (routine: tracking, status, fees) while escalating ~40% (complaints, complex deliveries, account issues) to human agents. This aligns with the 60/40 current query distribution and maximises AI value without sacrificing quality.
2. **Compliance by design**: High-risk topics auto-escalate per FR-004 acceptance criteria and NFR-C-003 (ACCC consumer law). No customer-facing AI response on complaints or security issues without human oversight.
3. **Customer experience preservation**: Sub-30-second handoff (FR-004) with full context transfer maintains seamless experience regardless of routing outcome.

**Stakeholder consensus**: SD-6 (Customers) want seamless transitions; SD-7 (Operations Staff) want reduced workload without quality loss; SD-8 (Compliance) requires auto-escalation for regulated topics. Hybrid routing satisfies all three.

---

## 5. Consequences

### 5.1 Positive Consequences

- ✅ **40% deflection target achievable**: 60% routine query volume handled by AI at >85% accuracy (BR-003)
- ✅ **Proactive compliance**: Auto-escalation for high-risk topics eliminates regulatory gaps
- ✅ **Staff productivity**: Agents focus on complex, high-value interactions; reduced repetitive workload (SD-7)
- ✅ **Customer satisfaction**: CSAT maintained above 80% through seamless handoff (BR-002)
- ✅ **Measurable optimisation**: Complexity classification accuracy tracked and tuned via FR-010 feedback loop

**Measurable outcomes**:

- Deflection rate: Target 40% of 120,000 monthly queries (48,000/month AI-handled)
- Escalation time: p50 < 15 seconds; p95 < 30 seconds
- Complexity classification accuracy: >90% (measured against agent-confirmed routing)
- CSAT for escalated queries: >80%

### 5.2 Negative Consequences (Accepted Trade-offs)

- ❌ **Classification risk**: False classification leads to premature escalation or inadequate AI handling
- ❌ **Routing complexity**: Requires real-time classification engine integrated with CRM and workforce management
- ❌ **Threshold calibration**: Continuous tuning needed as query patterns evolve

**Mitigation strategies**:

- **Classification risk**: Dual-score confidence model (content confidence + topic risk); conservative thresholds for regulated topics
- **Routing complexity**: Published API contract for classification service; containerised microservice with independent deployment
- **Threshold calibration**: Weekly threshold review based on FR-010 feedback data; automated drift detection on classification accuracy

---

## 6. Review and Updates

**Initial review**: 2027-01-01
**Periodic review**: Quarterly, aligned with AI governance review cycle (ADR-007)
**Trigger events**: Classification accuracy below 85%; deflection rate below 30%; CSAT below 75%

---

# ADR-003: Data Architecture Pattern for AI

## Decision Title

Event-Driven Data Fabric for AI Agent Consumption

## 1. Context and Problem Statement

### 1.1 Problem Description

AI agents require real-time access to customer data, parcel tracking events, purchase history, and service catalogue information. The data architecture must support agent consumption (structured, machine-readable formats) while maintaining Privacy Act compliance, sub-second access latency, and consistency across multiple data sources (CRM, logistics, e-commerce, notifications).

**Problem statement as a question**: What data architecture pattern enables AI agents to consume real-time, structured data from multiple MagicDelivery systems while maintaining privacy, consistency, and scalability?

### 1.2 Why This Decision Is Needed

- **Business context**: BR-002 (Customer Experience) requires sub-30-second resolution; BR-005 (Scalable Platform) requires data access within overall 2-second response budget. AI agents need parcel status, customer profiles, and service options within each query cycle.
- **Technical context**: INT-001 (E-Commerce), INT-002 (CRM), INT-003 (Logistics), INT-004 (Notifications) must feed AI agents with consistent, fresh data. NFR-P-001 requires sub-2-second end-to-end response; data layer budget is approximately 500ms.
- **Regulatory context**: NFR-C-001 requires privacy-by-design data handling; APP-compliant data access controls must be enforced at the data layer. DR-001 through DR-005 define data requirements for AI consumption.

### 1.3 Supporting Links

- **Requirements**: BR-002, BR-005, INT-001 through INT-004, NFR-P-001, NFR-C-001
- **Stakeholders**: SD-2 (Digital Technology), SD-6 (Customers), SD-8 (Compliance/Legal)
- **Related ADRs**: ADR-001 (Deployment Strategy), ADR-004 (Mobile Integration), ADR-005 (Multi-Channel Consistency)

---

## 2. Decision Drivers (Forces)

### 2.1 Technical Drivers

- **Real-time access**: FR-002 requires real-time parcel tracking with sub-1-second status lookups
- **Data freshness**: FR-002 requires proactive notifications within 30 seconds of logistics events
- **Structured output**: PRIN-3 (AI-Augmented Operations) requires machine-readable, structured data for agent inference
- **Event-driven integration**: PRIN-10 (Event-Driven Integration) advocates pub/sub patterns for non-real-time interactions

### 2.2 Business Drivers

- **Consistency**: Customers expect consistent data across channels (FR-011 multi-channel consistency)
- **Scalability**: NFR-S-001 requires data architecture supporting 3-year growth to 100,000 concurrent users
- **Cost**: BR-005 targets sub-USD $0.05 per interaction; data access cost must be minimal

### 2.3 Regulatory & Compliance Drivers

- **Privacy Act**: APP-compliant data access controls at the data layer; data classification (PRIN-7)
- **Data as a Product**: PRIN-6 requires data domains treated as products with quality SLAs
- **Single Source of Truth**: PRIN-8 requires authoritative data sources with synchronised derived copies

### 2.4 Alignment to Architecture Principles

| Principle | Alignment | Impact |
|-----------|-----------|--------|
| Data as a Product (PRIN-6) | Supports | Data fabric implements data product ownership and contracts |
| Data Sovereignty (PRIN-7) | Supports | Data classification and residency enforced at fabric layer |
| Event-Driven Integration (PRIN-10) | Supports | Event-driven pattern enables real-time agent data access |
| Loose Coupling (PRIN-9) | Supports | Data fabric abstracts source systems from AI agent consumption |
| AI-Augmented Operations (PRIN-3) | Supports | Agent-ready interfaces with structured data output |

---

## 3. Considered Options

### Option 1: Event-Driven Data Fabric

**Description**: Real-time event stream from all source systems into a central data fabric (Kafka/Kinesis). AI agents subscribe to relevant event topics; materialised views provide point-in-time snapshots for agent inference. Tokenised customer data flows through fabric with embedded privacy controls.

**Implementation approach**: Apache Kafka or AWS MSK for event streaming; schema registry for data contracts; materialised view service for agent-ready data snapshots; event-driven updates to AI agent context windows.

**Wardley Evolution Stage**: Product (Kafka is mature; custom materialised views are Custom-Built)

#### Good (Pros)

- ✅ **Real-time freshness**: Sub-second data updates to AI agents via event streams
- ✅ **Decoupled architecture**: Source systems publish events without AI awareness; AI subscribes independently
- ✅ **Scalable**: Horizontal scaling of event streams and materialised views
- ✅ **Audit trail**: Event streams provide immutable data access records for compliance (NFR-C-002)
- ✅ **Multi-consumer**: Single event stream serves AI agents, analytics, and reporting

#### Bad (Cons)

- ❌ **Complexity**: Event-driven architecture requires schema management, consumer coordination, and dead-letter handling
- ❌ **Eventual consistency**: Materialised views are eventually consistent; staleness window must be bounded
- ❌ **Operational overhead**: Kafka cluster management, monitoring, and disaster recovery

#### Cost Analysis

- **CAPEX**: USD $1.5M (event infrastructure, schema registry, materialised view service)
- **OPEX**: USD $1.2M/year (infrastructure, staffing, maintenance)
- **TCO (3-year)**: USD $5.1M

### Option 2: Real-Time Streaming with Direct Source Access

**Description**: AI agents query source systems directly via REST APIs in real-time. No central event layer; each agent request triggers synchronous calls to CRM, logistics, e-commerce systems.

#### Good (Pros)

- ✅ **Strong consistency**: Data is always current; no staleness risk
- ✅ **Simpler architecture**: No event infrastructure to manage
- ✅ **Lower initial cost**: No event platform investment

#### Bad (Cons)

- ❌ **Latency**: Multiple synchronous calls per query increase response time; difficult to meet sub-2-second target under load
- ❌ **Coupling**: AI agents directly coupled to source system APIs; source changes break agent consumption
- ❌ **Scalability**: Source systems not designed for AI query volumes; risk of overloading CRM/logistics
- ❌ **No audit trail**: Direct queries lack centralised access logging for compliance

### Option 3: Batch + Cache Architecture

**Description**: Data extracted from source systems on scheduled intervals (batch) with caching layer for AI agent consumption. Cache refreshed every 5–15 minutes.

#### Good (Pros)

- ✅ **Simplest architecture**: ETL + cache is well-understood pattern
- ✅ **Source system protection**: Batch extraction does not impact real-time operations

#### Bad (Cons)

- ❌ **Stale data**: 5–15 minute cache refresh cannot support FR-002 (proactive 30-second notifications)
- ❌ **Poor customer experience**: Parcel status updates delayed; tracking queries return outdated information
- ❌ **Compliance risk**: Stale data may provide incorrect information to customers

### Option 4: Lakehouse Architecture

**Description**: Central data lake with structured tables for AI consumption. Real-time ingestion via streaming; historical data in data lake for model training and analytics.

#### Good (Pros)

- ✅ **Unified platform**: Single platform for real-time serving and batch analytics
- ✅ **Model training data**: Historical data in lake supports model improvement pipelines

#### Bad (Cons)

- ❌ **Query latency**: Lake queries typically slower than purpose-built streaming (seconds vs milliseconds)
- ❌ **Over-engineering**: Lakehouse designed for analytics workloads, not sub-second agent inference
- ❌ **Complexity**: Unified platform introduces complexity that doesn't benefit AI agent real-time needs

### Option 5: Do Nothing (Baseline)

**Description**: Continue with existing data access patterns; AI agents query legacy systems directly.

#### Bad

- ❌ Cannot support real-time tracking (FR-002)
- ❌ Source systems not designed for AI query volumes
- ❌ No structured agent-ready interfaces (PRIN-3)

---

## 4. Decision Outcome

### 4.1 Chosen Option

**"Option 1: Event-Driven Data Fabric"**

### 4.2 Y-Statement

> **In the context of** AI agents requiring real-time, structured data from multiple MagicDelivery systems (CRM, logistics, e-commerce, notifications),
> **facing** the need for sub-second data freshness, scalable access patterns, and privacy-compliant data handling,
> **we decided for** an event-driven data fabric with real-time streaming and materialised views,
> **to achieve** decoupled, scalable, real-time data access for AI inference while maintaining audit trails and privacy controls,
> **accepting** increased architectural complexity and operational overhead for event platform management.

### 4.3 Justification

**Key reasons**:

1. **Real-time data freshness**: Event streams deliver sub-second updates to AI agents, enabling FR-002 (30-second proactive notifications) and NFR-P-001 (sub-2-second response). Materialised views provide agent-ready snapshots with bounded staleness (<5 seconds).
2. **Decoupled scalability**: Source systems publish events independently of AI consumer demands. AI agents scale without impacting CRM, logistics, or e-commerce performance. PRIN-9 (Loose Coupling) and PRIN-10 (Event-Driven Integration) are directly satisfied.
3. **Compliance integration**: Event streams provide immutable audit trails (NFR-C-002); privacy controls embedded at publish point; data classification enforced via schema registry. PRIN-6 (Data as a Product) and PRIN-7 (Data Sovereignty) implemented at fabric layer.

---

## 5. Consequences

### 5.1 Positive Consequences

- ✅ **Sub-second data freshness**: Real-time event updates support proactive notifications (FR-002) and fast agent responses (NFR-P-001)
- ✅ **Source system protection**: Decoupled event architecture prevents AI query load from impacting production systems
- ✅ **Compliance audit trail**: Immutable event streams enable forensic data access analysis (NFR-C-002)
- ✅ **Platform reuse**: Data fabric serves future AI initiatives beyond AgenticEA (G-5)

### 5.2 Negative Consequences

- ❌ **Event platform complexity**: Kafka cluster management, schema versioning, consumer coordination
- ❌ **Bounded staleness**: Materialised views not perfectly current; 5-second maximum staleness budget

**Mitigation strategies**:
- **Complexity**: Managed Kafka service (AWS MSK); automated schema validation; schema compatibility policies
- **Staleness**: Critical events (delivery exceptions, security alerts) delivered as real-time push to agents; materialised views for non-critical data only

---

## 6. Review and Updates

**Initial review**: 2027-01-01
**Periodic review**: Quarterly with platform performance metrics
**Trigger events**: Event latency exceeding 5 seconds; materialised view staleness exceeding 5 seconds; consumer throughput below 80% of target

---

# ADR-004: Mobile App Integration Approach

## Decision Title

SDK Embedding for Mobile App AI Agent Integration

## 1. Context and Problem Statement

### 1.1 Problem Description

AI agents must be integrated into the existing MagicDelivery Mobile App (~3 million monthly active users) without disrupting current app experience, performance, or App Store review process. The integration approach must support gradual feature rollout (12–24 month programme), incremental AI capability additions, and maintain app quality standards (4.5-star rating, 99% crash-free sessions).

**Problem statement as a question**: How should AI agent capabilities be integrated into the MagicDelivery Mobile App to balance seamless user experience, development agility, and rollout flexibility?

### 1.2 Why This Decision Is Needed

- **Business context**: BR-002 requires seamless AI experience within existing app; BR-005 requires sub-2-second response times. SD-5 (Mobile App Developers) expects modern tooling and improved developer experience.
- **Technical context**: NFR-U-002 limits AI feature app size increase to under 50 MB; NFR-U-003 requires consistency with existing design system. NFR-U-001 requires WCAG 2.1 AA compliance for AI components.
- **Delivery context**: BR-008 requires 12–24 month delivery; gradual rollout demands integration approach that supports phased feature releases.

### 1.3 Supporting Links

- **Requirements**: BR-002, BR-005, BR-008, NFR-U-001 through NFR-U-003
- **Stakeholders**: SD-5 (Mobile App Developers), SD-6 (Customers), SD-3 (Program Delivery)
- **Related ADRs**: ADR-005 (Multi-Channel Consistency), ADR-008 (Performance Strategy)

---

## 2. Decision Drivers (Forces)

### 2.1 Technical Drivers

- **App performance**: AI integration must not degrade crash-free session rate (<99%) or app Store ratings (>4.5 stars)
- **App size**: Maximum 50 MB additional size from AI features (NFR-U-002)
- **First contentful paint**: AI screen must render in under 1.5 seconds (NFR-U-002)
- **Modularity**: AI features must be independently updatable without full app version bumps

### 2.2 Business Drivers

- **Gradual rollout**: Phased feature release over 12–24 months (BR-008) requires modular integration
- **Speed to market**: AI features must reach customers within weeks, not months (app review cycles)
- **User experience**: AI interactions must feel native to the app; no jarring UI transitions

### 2.3 Alignment to Architecture Principles

| Principle | Alignment | Impact |
|-----------|-----------|--------|
| Composable Architecture (PRIN-2) | Supports | SDK as composable module with published interface |
| Legacy Modernization (PRIN-17) | Supports | Incremental integration via strangler pattern |
| Maintainability (PRIN-13) | Supports | Modular SDK with independent update cycles |
| Performance (PRIN-11) | Supports | Lightweight SDK with lazy loading |

---

## 3. Considered Options

### Option 1: Native Agent Module (Full In-App Integration)

**Description**: AI agent UI and logic built as native components within the app codebase. Tight integration with existing navigation, theming, and state management.

#### Good (Pros)

- ✅ **Most native experience**: AI feels indistinguishable from existing app features
- ✅ **Best performance**: Direct access to device resources; no bridge overhead
- ✅ **Seamless navigation**: Integrated into existing app flow

#### Bad (Cons)

- ❌ **App review dependency**: Every AI feature update requires full app submission to App Store / Google Play (review delay: 1–5 days)
- ❌ **Tight coupling**: AI changes require app rebuild; blocks independent AI iteration
- ❌ **Developer burden**: AI and app teams must coordinate releases; slows both
- ❌ **Size impact**: Native code increases app bundle size; harder to stay under 50 MB limit

### Option 2: Progressive Web Layer (Web-View Embedding)

**Description**: AI agent UI delivered as a web experience embedded within the app via WebView. Logic runs in a separate web service; app hosts the WebView container.

#### Good (Pros)

- ✅ **Independent updates**: Web content updated without app Store submissions
- ✅ **Smaller app size**: WebView is lightweight; minimal app bundle impact
- ✅ **Rapid iteration**: AI UI changes deployed instantly via web service

#### Bad (Cons)

- ❌ **Performance overhead**: WebView rendering slower than native; may violate 1.5-second paint target
- ❌ **UX inconsistency**: WebView experiences feel less native; navigation transitions may feel jarring
- ❌ **Device feature access**: Limited access to device capabilities (push notifications, biometrics) within WebView
- ❌ **WCAG compliance**: WebView accessibility harder to certify than native components

### Option 3: SDK Embedding (Modular AI Agent SDK)

**Description**: AI agent delivered as a lightweight SDK embedded in the app. SDK provides pre-built UI components (chat interface, tracking display, recommendation cards) and a communication layer to cloud AI services. SDK is independently versionable via over-the-air updates for the service layer, with native UI components bundled in app.

#### Good (Pros)

- ✅ **Balanced experience**: Native UI components provide seamless UX; cloud service layer updated independently
- ✅ **Performance**: Native UI components meet 1.5-second paint target; lazy-loaded to minimise size impact
- ✅ **Rollout flexibility**: Service layer updated independently of app; feature toggles control gradual rollout
- ✅ **App Store compliant**: Minimal app updates (SDK baseline bundled); service updates bypass review cycle
- ✅ **Developer experience**: SDK provides clear integration surface; AI team and app team can work independently
- ✅ **Size management**: Modular SDK components loaded on-demand; stays under 50 MB limit

#### Bad (Cons)

- ❌ **SDK maintenance**: SDK lifecycle management; backward compatibility with older app versions
- ❌ **Integration complexity**: SDK contract must be stable; breaking changes require app updates
- ❌ **Dual deployment**: SDK service layer and native components have independent versioning

#### Cost Analysis

- **CAPEX**: USD $1.0M (SDK development, CI/CD, testing infrastructure)
- **OPEX**: USD $0.8M/year (SDK maintenance, compatibility testing, service hosting)
- **TCO (3-year)**: USD $3.4M

### Option 4: Deep-Linking from App (External AI Experience)

**Description**: App provides deep links to a separate AI experience (separate app or web service). AI capabilities accessed via link navigation.

#### Good (Pros)

- ✅ **Zero app impact**: No changes to existing app code or size
- ✅ **Independent AI development**: AI experience developed and deployed entirely separately

#### Bad (Cons)

- ❌ **Fragmented experience**: Users navigate away from app context; jarring transition
- ❌ **Abandonment risk**: Users may not navigate to AI experience; adoption barrier
- ❌ **Branding inconsistency**: Separate experience may not match app design language (NFR-U-003)
- ❌ **Session state loss**: Navigating away from app loses context (cart, tracking session)

### Option 5: Do Nothing (Baseline)

**Description**: No AI integration in mobile app.

#### Bad

- ❌ Cannot achieve BR-002 (customer experience transformation)
- ❌ Cannot achieve BR-005 (scalable platform)
- ❌ Strategic failure against SD-1 (revenue growth) and SD-9 (AI transformation mandate)

---

## 4. Decision Outcome

### 4.1 Chosen Option

**"Option 3: SDK Embedding"**

### 4.2 Y-Statement

> **In the context of** integrating AI agents into the MagicDelivery Mobile App serving 3 million monthly active users,
> **facing** the need for native-quality UX, independent AI iteration, gradual rollout, and App Store compliance,
> **we decided for** SDK embedding with modular native UI components and independently updatable cloud service layer,
> **to achieve** seamless AI integration that balances user experience with development agility,
> **accepting** SDK lifecycle management overhead and dual-versioning complexity.

### 4.3 Justification

**Key reasons**:

1. **Optimal UX-to-agility balance**: SDK delivers native-quality UI (meeting NFR-U-002/003) while cloud service layer enables rapid AI updates without App Store review cycles. Supports BR-008 gradual rollout with feature toggles.
2. **Performance within bounds**: Native UI components achieve sub-1.5-second first contentful paint (NFR-U-002); lazy-loaded SDK modules stay under 50 MB size limit.
3. **Independent team velocity**: AI team and app team can develop independently with SDK as published contract (PRIN-2 Composable Architecture). AI iteration cycles are 2 weeks (BR-005) regardless of app release schedule.

---

## 5. Consequences

### 5.1 Positive Consequences

- ✅ **Native UX**: SDK components indistinguishable from existing app features; maintains 4.5-star rating
- ✅ **Rapid AI iteration**: Service layer updates deployed within hours, not days (App Store review)
- ✅ **Gradual rollout**: Feature toggles control phased release; A/B testing supported at service layer
- ✅ **App quality preserved**: Crash-free rate maintained; size impact controlled via lazy loading

### 5.2 Negative Consequences

- ❌ **SDK version management**: Backward compatibility with older app versions; deprecation timeline needed
- ❌ **Dual deployment coordination**: SDK service and native components must be version-compatible

**Mitigation strategies**:
- **Version management**: SemVer SDK versioning; minimum supported app version policy; automated compatibility testing
- **Dual deployment**: SDK contract frozen after each app release; service layer absorbs all changes; breaking changes scheduled with next app update

---

## 6. Review and Updates

**Initial review**: 2027-01-01
**Trigger events**: SDK size exceeding 40 MB; app Store reviews mentioning AI-related issues; SDK latency exceeding 500ms

---

# ADR-005: Multi-Channel Agent Consistency

## Decision Title

Centralized Agent Backend with Multi-Channel UI

## 1. Context and Problem Statement

### 1.1 Problem Description

Customers expect consistent AI agent experience across the MagicDelivery Mobile App, web portal, call centre, and retail channels. A customer who starts a conversation on the app should be able to continue it on the web without losing context. AI responses must be consistent in content and quality regardless of channel.

**Problem statement as a question**: How should AI agent intelligence be distributed across channels to ensure consistency while supporting channel-specific user experience requirements?

### 1.2 Why This Decision Is Needed

- **Business context**: FR-011 (Multi-Channel Consistency) requires consistent AI behaviour across channels with shared conversation context. BR-002 targets NPS improvement from 32 to 42, requiring consistent experience.
- **Technical context**: Conversation context must be preserved across channels (7-day session window per FR-011). Shared state management across independent channel implementations.
- **Delivery context**: Phase 1 delivers mobile app; Phase 2 expands to web and call centre. Architecture must support incremental channel addition.

### 1.3 Supporting Links

- **Requirements**: FR-011, FR-004, BR-002
- **Stakeholders**: SD-6 (Customers), SD-2 (Digital Technology)
- **Related ADRs**: ADR-002 (Handoff Model), ADR-004 (Mobile Integration)

---

## 2. Decision Drivers (Forces)

### 2.1 Technical Drivers

- **Conversation state management**: Shared conversation history across channels; 7-day session window (FR-011)
- **Response consistency**: Same query on different channels should produce consistent answers
- **Scalability**: Centralised backend must serve all channels at peak load
- **Channel-specific optimisation**: Each channel has unique UI/UX constraints

### 2.2 Business Drivers

- **Customer trust**: Consistent AI behaviour across channels builds trust; inconsistent responses erode trust
- **Operational efficiency**: Single AI backend reduces development and maintenance cost versus per-channel agents
- **Incremental rollout**: New channels can be added without redeveloping AI logic

### 2.3 Alignment to Architecture Principles

| Principle | Alignment | Impact |
|-----------|-----------|--------|
| Composable Architecture (PRIN-2) | Supports | Backend as composable service with published API; channels as independent consumers |
| Loose Coupling (PRIN-9) | Supports | Channels decoupled from AI backend via published interfaces |
| Single Source of Truth (PRIN-8) | Supports | Single AI backend is authoritative source of agent intelligence |
| Maintainability (PRIN-13) | Supports | AI logic maintained in one place; easier to update and test |

---

## 3. Considered Options

### Option 1: Centralized Agent Backend (Single Brain, Multi-Channel UI)

**Description**: Single AI agent platform serves all channels (mobile, web, call centre, retail). Channel-specific UI components consume a shared AI API. Conversation state, model inference, data access, and governance are centralised.

**Implementation approach**: Central AI platform (per ADR-001) exposes REST/gRPC API for agent interactions. Each channel implements its UI layer consuming the API. Conversation state stored centrally with cross-channel session management.

#### Good (Pros)

- ✅ **Consistency guarantee**: Single model, single conversation state ensures identical AI behaviour across channels
- ✅ **Development efficiency**: AI logic developed once; channels focus on UI/UX
- ✅ **Channel agnosticism**: New channels added by implementing UI layer against existing API
- ✅ **Centralised governance**: Model monitoring, compliance, and updates applied to all channels simultaneously
- ✅ **Cross-channel continuity**: Customer conversation seamlessly transitions between channels (FR-011)

#### Bad (Cons)

- ❌ **Single point of failure**: Central backend outage affects all channels simultaneously
- ❌ **Latency to remote channels**: Call centre and retail terminals may experience higher latency to cloud backend
- ❌ **Channel-specific optimisation**: Centralised API may not perfectly serve unique channel constraints

#### Cost Analysis

- **CAPEX**: USD $0.8M (API gateway, session management, cross-channel state)
- **OPEX**: USD $0.5M/year (central platform hosting, monitoring)
- **TCO (3-year)**: USD $2.3M

### Option 2: Channel-Specific Agents with Shared Knowledge Base

**Description**: Each channel runs its own AI agent instance with access to a shared knowledge base (FAQs, policy documents, service data). Agents are independently deployed but share training data.

#### Good (Pros)

- ✅ **Channel isolation**: Channel outage does not affect other channels
- ✅ **Channel optimisation**: Each agent tuned for channel-specific interaction patterns

#### Bad (Cons)

- ❌ **Inconsistency risk**: Independent models produce different responses to same query across channels
- ❌ **Development overhead**: N channels × model maintenance = N× development effort
- ❌ **No cross-channel continuity**: Conversation state not shared; customer must restart on new channel
- ❌ **Governance complexity**: Compliance monitoring must cover all channel instances independently

### Option 3: Federated Agents with Orchestration Layer

**Description**: Distributed AI agents at each channel, coordinated by an orchestration layer that ensures consistency through policy enforcement and model alignment.

#### Good (Pros)

- ✅ **Distributed resilience**: Channel-level fault isolation
- ✅ **Channel optimisation**: Local agents can be tuned for channel patterns

#### Bad (Cons)

- ❌ **Complexity**: Orchestration layer adds architectural complexity without clear benefit over centralised approach
- ❌ **Partial consistency**: Orchestration can enforce alignment but cannot guarantee identical behaviour
- ❌ **Governance burden**: Compliance must verify orchestration effectiveness across distributed agents

### Option 4: Do Nothing (Baseline)

**Description**: AI agents only in mobile app; no cross-channel consistency requirement.

#### Bad

- ❌ FR-011 (Multi-Channel Consistency) not met
- ❌ Customer experience fragmented across channels
- ❌ Higher development cost for future channel expansion

---

## 4. Decision Outcome

### 4.1 Chosen Option

**"Option 1: Centralized Agent Backend with Multi-Channel UI"**

### 4.2 Y-Statement

> **In the context of** delivering AI agent experiences across mobile app, web portal, call centre, and retail channels,
> **facing** the need for consistent AI behaviour, cross-channel conversation continuity, and efficient development,
> **we decided for** a centralized agent backend with channel-specific UI layers,
> **to achieve** guaranteed consistency, cross-channel conversation continuity, and single-source governance,
> **accepting** centralised failure risk mitigated by multi-AZ deployment and circuit breakers.

### 4.3 Justification

**Key reasons**:

1. **Consistency guarantee**: Single model and conversation state ensure identical AI behaviour across all channels. This is essential for customer trust (SD-6) and NPS improvement (BR-002). Inconsistent AI responses across channels would undermine the NPS target of 42.
2. **Development efficiency**: AI logic developed and maintained once. New channels (web, call centre, retail) added by implementing UI layer — estimated 40% reduction in development effort versus per-channel agents.
3. **Governance simplicity**: Centralised compliance monitoring, model updates, and audit trails apply uniformly. Satisfies BR-007 (AI Governance Framework) with a single governance surface.

---

## 5. Consequences

### 5.1 Positive Consequences

- ✅ **Guaranteed consistency**: Identical AI behaviour across channels; customer trust preserved
- ✅ **Cross-channel continuity**: 7-day conversation state enables seamless channel transitions (FR-011)
- ✅ **Governance efficiency**: Single compliance surface; uniform model monitoring and updates
- ✅ **Rapid channel expansion**: New channels onboarded by implementing UI layer against existing API

### 5.2 Negative Consequences

- ❌ **Centralised failure risk**: Backend outage affects all channels
- ❌ **Network latency**: Call centre and retail terminals depend on network connectivity to cloud backend

**Mitigation strategies**:
- **Failure risk**: Multi-AZ deployment; circuit breakers per ADR-001; graceful degradation to cached responses
- **Latency**: Edge caching for common queries; connection pooling; fallback to local search for offline-capable terminals

---

## 6. Review and Updates

**Initial review**: 2027-01-01
**Trigger events**: Cross-channel consistency score below 95%; backend availability below 99.9%; channel-specific latency exceeding 3 seconds

---

# ADR-006: Workforce Augmentation Model

## Decision Title

AI Co-Pilot Augmentation with Gradual Transition and Natural Attrition

## 1. Context and Problem Statement

### 1.1 Problem Description

AI agents handling 60% of routine call centre queries (approximately 72,000 of 120,000 monthly queries) create significant workforce impact for MagicDelivery's 10,000-person operational workforce. The workforce augmentation model must deliver AI efficiency gains without mass layoffs, while addressing union concerns, maintaining operational continuity, and positioning staff for higher-value roles.

**Problem statement as a question**: How should AI agent deployment impact the workforce — through replacement, augmentation, or a transition model — and what is the responsible approach for 10,000 staff under the Fair Work Act?

### 1.2 Why This Decision Is Needed

- **Business context**: BR-003 targets 40% routine call deflection with zero net FTE reduction. BR-006 targets 2,000 staff upskilled in AI-augmented workflows within 18 months. G-3 and G-6 are directly relevant.
- **Technical context**: FR-007 defines AI co-pilot for operations staff; FR-015 defines LMS integration for training. AI co-pilot requires staff terminal integration with existing CRM.
- **Regulatory context**: NFR-C-004 (Fair Work Act Compliance) mandates zero net FTE reduction for 24 months per Board-approved AI Augmentation Charter. Union consultation required quarterly. SD-7 (Operations Staff) driver centres on genuine workload reduction, not displacement anxiety.

### 1.3 Supporting Links

- **Requirements**: BR-003, BR-006, FR-007, FR-015, NFR-C-004
- **Stakeholders**: SD-7 (Operations Staff), SD-9 (Executive Leadership), Fair Work Commission / TWU
- **Related ADRs**: ADR-002 (Handoff Model), ADR-007 (Compliance Governance)

---

## 2. Decision Drivers (Forces)

### 2.1 Technical Drivers

- **Co-pilot capability**: FR-007 requires AI co-pilot tool for call centre and retail staff — surfacing suggestions, auto-filling lookups, reducing routine workload
- **Training integration**: FR-015 requires LMS integration for AI-augmented workflow training and certification
- **Workload redistribution**: AI handles routine queries; staff shift to complex queries requiring human expertise

### 2.2 Business Drivers

- **Zero FTE commitment**: Board-approved AI Augmentation Charter prohibits net headcount reduction for 24 months
- **Union relations**: TWU actively monitoring AI impact; industrial action risk if workforce feels threatened
- **Staff morale**: SD-7 driver — staff want tools that reduce workload, not replace them. AI confidence score must improve from 3.0 to 6.5/10.
- **Cost efficiency**: AI delivers USD $12M operational savings through efficiency, not headcount reduction

### 2.3 Regulatory & Compliance Drivers

- **Fair Work Act**: Workforce changes require consultation; significant changes require genuine redundancy processes
- **AI Augmentation Charter**: Board commitment to zero net FTE reduction for 24 months is a governance requirement
- **Union consultation**: Quarterly sessions with TWU and Fair Work Commission (NFR-C-004)

### 2.4 Alignment to Architecture Principles

| Principle | Alignment | Impact |
|-----------|-----------|--------|
| AI-Augmented Operations (PRIN-3) | Supports | Co-pilot is human-in-the-loop augmentation per principle |
| Business Outcome Alignment (PRIN-1) | Supports | Workforce model aligned to operational efficiency and cost savings |
| Security by Design (PRIN-4) | Supports | Co-pilot requires staff approval before customer delivery (FR-007) |

---

## 3. Considered Options

### Option 1: AI Co-Pilot for Staff (Augmented Workers)

**Description**: AI agents serve as co-pilots for existing staff, handling routine queries while staff focus on complex interactions. Staff retain their roles and receive upskilling for higher-value work. No headcount reduction; AI efficiency gained through productivity improvement.

**Implementation approach**: AI co-pilot tool (FR-007) integrated with staff CRM; AI handles routine queries autonomously, co-pilots staff on complex queries, and staff approve AI suggestions before customer delivery. Training programme (BR-006) upskills 2,000 staff in 18 months.

#### Good (Pros)

- ✅ **Zero FTE reduction**: Satisfies AI Augmentation Charter and NFR-C-004
- ✅ **Staff morale**: AI reduces repetitive workload; staff focus on complex, rewarding interactions
- ✅ **Union relations**: Transparent augmentation approach; no displacement anxiety
- ✅ **Operational continuity**: Existing staff retain expertise; no capability loss during transition
- ✅ **Measurable efficiency**: AI handles 60% of routine queries; staff productivity increases by handling higher-value interactions

#### Bad (Cons)

- ❌ **Slower efficiency gains**: Augmentation alone does not reduce headcount; efficiency gains come through productivity, not cost-of-headroom reduction
- ❌ **Training investment**: USD $1.8M training programme (NFR-C-004) required for 2,000 staff
- ❌ **Change management**: Staff must adopt new AI-augmented workflows; resistance risk

### Option 2: AI Replacement with Reskilling Programme

**Description**: AI replaces staff in routine query roles; displaced staff enter reskilling programme for new roles within MagicDelivery (digital operations, quality assurance, AI training).

#### Good (Pros)

- ✅ **Maximum efficiency**: Direct cost reduction from headcount reduction
- ✅ **Clear transition**: Defined reskilling pathway for displaced staff

#### Bad (Cons)

- ❌ **Violates Augmentation Charter**: Zero net FTE reduction commitment would be breached
- ❌ **Union conflict**: Direct replacement creates industrial relations risk; potential industrial action
- ❌ **Reputational damage**: MagicDelivery branded as AI job-replacement organisation
- ❌ **Capability loss**: Institutional knowledge and customer service expertise lost

### Option 3: AI Augmentation with Hiring Freeze

**Description**: AI handles increased query volume; no new hiring as positions become vacant. Headcount gradually reduces through natural attrition over 3–5 years.

#### Good (Pros)

- ✅ **Gradual transition**: No forced redundancies; staff departures managed through natural attrition
- ✅ **Predictable workforce change**: Gradual reduction aligns with workforce planning cycles

#### Bad (Cons)

- ❌ **Partial charter breach**: Hiring freeze is functionally equivalent to headcount reduction; may violate spirit of AI Augmentation Charter
- ❌ **Staff morale**: Hiring freeze signals job insecurity; may affect productivity and retention
- ❌ **Skill gaps**: New capabilities (AI-augmented workflows) require new skills that attritioning staff may not have

### Option 4: AI Co-Pilot Augmentation with Gradual Transition and Natural Attrition

**Description**: AI co-pilots existing staff on routine queries (immediate augmentation). Concurrently, AI handles routine queries independently (deflection). Over 24 months, workforce transitions through natural attrition — positions vacated through retirement, resignation, and redeployment are not backfilled at same headcount, while remaining staff are upskilled to handle higher-value AI-augmented roles. The 24-month zero-net-FTE commitment is maintained; post-24-month workforce planning considers efficiency gains.

#### Good (Pros)

- ✅ **Augmentation-first**: Immediate workload reduction for existing staff; builds AI confidence and trust
- ✅ **Compliance**: Zero net FTE reduction maintained for 24 months (AI Augmentation Charter)
- ✅ **Natural transition**: Post-24-month attrition-based workforce adjustment is non-disruptive
- ✅ **Staff agency**: Staff choose to upskill and transition; no forced displacement
- ✅ **Efficiency realised**: AI handles 60% of routine queries; staff focus on 40% complex queries + new value-adding activities
- ✅ **Union alignment**: Transparent, consultative approach with TWU engagement

#### Bad (Cons)

- ❌ **Transition planning complexity**: Requires careful workforce planning with union consultation
- ❌ **Post-24-month uncertainty**: After charter expiry, workforce decisions become more complex
- ❌ **Training delivery timeline**: 18-month upskilling programme must complete while AI goes live

#### Cost Analysis

- **CAPEX**: USD $1.8M (training programme per NFR-C-004)
- **OPEX**: USD $0.5M/year (ongoing training, LMS maintenance, certification)
- **TCO (3-year)**: USD $3.3M
- **Efficiency gains**: USD $12M/year operational savings through AI deflection (BR-003)

### Option 5: Do Nothing (Baseline)

**Description**: No workforce model change; AI defers to existing call centre model.

#### Bad

- ❌ Cannot achieve BR-003 (40% deflection)
- ❌ Cannot achieve BR-006 (2,000 staff upskilled)
- ❌ Operational inefficiency persists; 8-minute wait times continue
- ❌ Strategic AI mandate unfulfilled (SD-9)

---

## 4. Decision Outcome

### 4.1 Chosen Option

**"Option 4: AI Co-Pilot Augmentation with Gradual Transition and Natural Attrition"**

### 4.2 Y-Statement

> **In the context of** deploying AI agents that automate 60% of routine call centre queries for MagicDelivery's 10,000-person operational workforce,
> **facing** the tension between AI-driven efficiency and workforce security under the Fair Work Act and Board-approved AI Augmentation Charter,
> **we decided for** AI co-pilot augmentation with gradual workforce transition through natural attrition,
> **to achieve** immediate staff workload reduction, zero net FTE reduction for 24 months, and sustainable long-term efficiency gains,
> **accepting** transition planning complexity and the need for ongoing union consultation.

### 4.3 Justification

**Key reasons**:

1. **Responsible transition**: Augmentation-first approach respects workforce dignity while delivering efficiency gains. Staff experience AI as a tool that reduces their workload, not threatens their jobs. This directly addresses SD-7 driver concerns and SD-8 union relations requirements.
2. **Compliance adherence**: Zero net FTE reduction for 24 months satisfies the Board-approved AI Augmentation Charter and NFR-C-004. Post-24-month natural attrition approach is non-disruptive and aligns with Fair Work Act obligations.
3. **Efficiency realisation**: AI handles 60% of routine queries independently (48,000/month); staff focus on 40% complex queries plus AI-augmented high-value activities. USD $12M operational savings delivered through productivity improvement, not headcount reduction (BR-003).

**Stakeholder consensus**: SD-7 (Operations Staff) — augmentation preferred over replacement; SD-9 (Executive Leadership) — efficiency gains delivered; SD-8 (Compliance) — charter compliance maintained. TWU engagement through quarterly consultation (NFR-C-004).

---

## 5. Consequences

### 5.1 Positive Consequences

- ✅ **Zero FTE reduction**: AI Augmentation Charter honoured for 24 months
- ✅ **Staff morale improvement**: AI reduces repetitive workload; staff confidence grows (target: 3.0 to 6.5/10)
- ✅ **Operational savings**: USD $12M/year through AI efficiency, not layoffs (BR-003)
- ✅ **Union alignment**: Transparent augmentation approach reduces industrial relations risk
- ✅ **Upskilling delivered**: 2,000 staff certified in AI-augmented workflows within 18 months (BR-006)

**Measurable outcomes**:
- Staff AI confidence score: 3.0 → 6.5/10
- Staff satisfaction score: 4.2 → 6.5/10
- Training completion rate: 80% of targeted 2,000 staff
- Zero net FTE reduction verified through HRIS tracking

### 5.2 Negative Consequences

- ❌ **Training programme delivery risk**: 18-month timeline for 2,000 staff certification is aggressive
- ❌ **Post-24-month workforce planning complexity**: Charter expiry creates decision point for headcount management
- ❌ **Change management burden**: Staff adoption of AI co-pilot requires sustained change management

**Mitigation strategies**:
- **Training delivery**: Phased rollout with 500 staff per 6-month wave; dedicated training team allocation
- **Post-24-month planning**: Early workforce planning initiated at 18-month mark; union consultation on long-term strategy
- **Change management**: Town halls, pilot participation, feedback channels per SD-7 engagement strategy

---

## 6. Review and Updates

**Initial review**: 2027-01-01
**Periodic review**: Quarterly with workforce metrics; annual with union consultation outcomes
**Trigger events**: FTE reduction detected via HRIS; training completion below 60%; staff satisfaction below 5.0/10; TWU industrial action

---

# ADR-007: Compliance and Governance for AI Agents

## Decision Title

Hybrid Compliance Governance: Pre-Deployment Gates with Runtime Monitoring and Audit

## 1. Context and Problem Statement

### 1.1 Problem Description

AI agent deployment must comply with the Privacy Act 1988 (APPs), ACCC consumer law, Fair Work Act obligations, and emerging AI-specific regulatory frameworks. A governance model is required that catches compliance issues before deployment while continuously monitoring runtime behaviour for emerging compliance risks (hallucinations, data privacy violations, consumer law breaches).

**Problem statement as a question**: What compliance governance model ensures AI agents remain within regulatory boundaries throughout their lifecycle — from design through deployment to continuous operation?

### 1.2 Why This Decision Is Needed

- **Business context**: BR-004 (Privacy-Compliant Architecture) requires zero Privacy Act breaches and 100% DPIA completion. BR-007 (AI Governance Framework) requires maturity score of 7/10 within 6 months. G-4 and G-7 are critical success factors.
- **Technical context**: FR-008 (AI Interaction Audit Trail) requires tamper-evident logging of all AI interactions. FR-012 (Agent Administration) requires real-time monitoring of AI performance and compliance metrics. FR-016 (Hallucination Detection) requires runtime validation.
- **Regulatory context**: Privacy Act 1988 penalties up to USD $2.5M per breach. ACCC consumer law prohibits misleading AI-generated content. OAIC enforcement is active; regulatory ambiguity around AI-specific obligations requires proactive governance.

### 1.3 Supporting Links

- **Requirements**: BR-004, BR-007, FR-008, FR-012, FR-016, NFR-C-001 through NFR-C-005
- **Stakeholders**: SD-8 (Compliance/Legal), SD-6 (Customers), SD-9 (Executive Leadership)
- **Related ADRs**: ADR-001 (Deployment Strategy), ADR-002 (Handoff Model), ADR-003 (Data Architecture)

---

## 2. Decision Drivers (Forces)

### 2.1 Technical Drivers

- **Runtime monitoring**: AI models can produce unpredictable outputs (hallucinations); runtime monitoring required for compliance
- **Audit trails**: FR-008 requires complete, tamper-evident audit of all AI interactions
- **Automated controls**: Manual compliance checks cannot scale to 10M customer interactions
- **Model governance**: NFR-M-003 requires defined model lifecycle with pre-deployment review and post-deployment monitoring

### 2.2 Business Drivers

- **Time to market**: Compliance process must not block 12-month delivery target (BR-008)
- **Cost**: Compliance overhead must be factored into programme budget (USD $18.5M)
- **Customer trust**: Compliance failures damage brand; proactive governance preserves trust

### 2.3 Regulatory & Compliance Drivers

- **Privacy Act 1988**: APP-compliant data handling at design time (pre-deployment) and operation time (runtime)
- **ACCC Consumer Law**: AI-generated content validated against authoritative data (FR-016)
- **OAIC**: Data breach notification within 72 hours (NFR-C-001)
- **Fair Work Act**: AI Augmentation Charter compliance monitoring (NFR-C-004)
- **AI Governance Framework**: Model register, risk assessments, human oversight (NFR-C-005)

### 2.4 Alignment to Architecture Principles

| Principle | Alignment | Impact |
|-----------|-----------|--------|
| Security by Design (PRIN-4) | Supports | Compliance controls embedded in architecture |
| Data Sovereignty (PRIN-7) | Supports | Data classification enforced through governance |
| AI-Augmented Operations (PRIN-3) | Supports | Governance enables safe AI deployment |
| Observability (PRIN-5) | Supports | Runtime monitoring requires structured telemetry |

---

## 3. Considered Options

### Option 1: Pre-Deployment Compliance Gates

**Description**: All AI capabilities must pass defined compliance gates before deployment — DPIA completion, security review, consumer law validation, accuracy testing, and governance registration. No runtime monitoring beyond standard operational alerting.

#### Good (Pros)

- ✅ **Strong pre-launch assurance**: Comprehensive review catches design-time compliance issues
- ✅ **Clear accountability**: Gate ownership assigned; sign-off required from Compliance/Legal
- ✅ **Regulatory defensibility**: Audit trail of pre-deployment assessments

#### Bad (Cons)

- ❌ **Blind to runtime drift**: Model behaviour can change with new data, prompts, or adversarial inputs
- ❌ **Cannot detect hallucinations**: Pre-deployment testing cannot anticipate all runtime scenarios
- ❌ **Slow iteration**: Compliance gates add review time to model update cycles (impacts 2-week onboarding target)
- ❌ **False sense of security**: Passing gates does not guarantee runtime compliance

### Option 2: Runtime Monitoring Only

**Description**: Deploy AI agents with minimal pre-deployment review; rely on runtime monitoring, alerting, and automated controls to catch compliance issues.

#### Good (Pros)

- ✅ **Fastest time to market**: Minimal pre-deployment review overhead
- ✅ **Real-time compliance**: Runtime monitoring catches actual compliance issues

#### Bad (Cons)

- ❌ **Compliance risk**: No pre-deployment assurance; regulatory findings possible before monitoring catches issues
- ❌ **Audit gap**: Runtime-only monitoring cannot demonstrate pre-deployment diligence to OAIC
- ❌ **Reactive posture**: Compliance issues detected after they affect customers; reputational damage

### Option 3: Hybrid Governance (Pre-Deployment Gates + Runtime Monitoring)

**Description**: Pre-deployment compliance gates for design-time assurance combined with continuous runtime monitoring for operational compliance. Pre-deployment gates cover DPIA, security review, model registration, accuracy testing, and consumer law validation. Runtime monitoring covers hallucination detection, PII leakage detection, confidence threshold monitoring, and automated alerting.

**Implementation approach**:
- **Pre-deployment**: Compliance gates in CI/CD pipeline; automated DPIA checklist; model accuracy and bias testing; legal sign-off before staging
- **Runtime**: FR-016 hallucination detection; FR-008 tamper-evident audit trail; real-time compliance dashboard (FR-012); automated circuit breakers for compliance violations
- **Periodic**: Quarterly governance reviews; annual regulatory assessment; model re-evaluation

#### Good (Pros)

- ✅ **Comprehensive coverage**: Pre-deployment catches design issues; runtime catches operational drift
- ✅ **Balanced time-to-market**: Pre-deployment gates automated in CI/CD; minimal manual review overhead
- ✅ **Regulatory defensibility**: Full audit trail from design to runtime; OAIC-ready
- ✅ **Continuous improvement**: Runtime data feeds model improvement and compliance refinement
- ✅ **Automated enforcement**: Circuit breakers halt non-compliant AI behaviour in real-time

#### Bad (Cons)

- ❌ **Highest complexity**: Both pre-deployment and runtime systems to design, implement, and maintain
- ❌ **Resource requirements**: Dedicated compliance engineering team required for both layers
- ❌ **Integration complexity**: CI/CD gates, runtime monitoring, audit trails, and governance dashboard must integrate

#### Cost Analysis

- **CAPEX**: USD $1.5M (compliance tooling, audit infrastructure, monitoring dashboards)
- **OPEX**: USD $1.0M/year (compliance team, tooling maintenance, regulatory engagement)
- **TCO (3-year)**: USD $4.5M

### Option 4: Self-Certification with Annual Review

**Description**: AI team self-certifies compliance through internal checklist; annual external review validates compliance posture.

#### Good (Pros)

- ✅ **Lowest upfront cost**
- ✅ **Simplicity**

#### Bad (Cons)

- ❌ **Inadequate assurance**: Self-certification lacks independent validation
- ❌ **Regulatory risk**: Annual review gap means 12 months of potential undetected compliance issues
- ❌ **Not sufficient for OAIC**: Self-certification unlikely to satisfy regulatory scrutiny

### Option 5: Do Nothing (Baseline)

**Description**: No formal AI compliance governance.

#### Bad

- ❌ Zero Privacy Act breaches (BR-004) impossible without governance
- ❌ AI Governance Framework (BR-007) cannot be established
- ❌ OAIC penalties up to USD $2.5M per breach
- ❌ Reputational damage from compliance failures

---

## 4. Decision Outcome

### 4.1 Chosen Option

**"Option 3: Hybrid Governance (Pre-Deployment Gates + Runtime Monitoring)"**

### 4.2 Y-Statement

> **In the context of** deploying AI agents for 10 million MagicDelivery customers under the Privacy Act 1988, ACCC consumer law, and Fair Work Act obligations,
> **facing** the need for comprehensive compliance assurance from design through continuous operation,
> **we decided for** hybrid governance with automated pre-deployment compliance gates and continuous runtime monitoring with automated enforcement,
> **to achieve** zero Privacy Act breaches (BR-004), AI Governance Framework maturity of 7/10 (BR-007), and regulatory defensibility,
> **accepting** increased complexity and resource requirements for compliance engineering.

### 4.3 Justification

**Key reasons**:

1. **Comprehensive compliance coverage**: Pre-deployment gates ensure design-time compliance (DPIA, security, accuracy, consumer law); runtime monitoring catches operational drift (hallucinations, PII leakage, confidence degradation). Neither approach alone is sufficient for the compliance risk profile.
2. **Regulatory defensibility**: Full audit trail from design to runtime demonstrates regulatory diligence to OAIC. Pre-deployment gates show proactive compliance; runtime monitoring shows operational commitment. BR-004 zero-breach target requires both.
3. **Automation-enabled speed**: CI/CD-integrated compliance gates automate much of pre-deployment review, maintaining 2-week model onboarding target (BR-005) while ensuring compliance. Runtime monitoring provides continuous assurance without blocking operations.

**Stakeholder consensus**: SD-8 (Compliance/Legal) — comprehensive coverage required; SD-3 (Program Delivery) — automation enables speed; SD-9 (Executive) — regulatory defensibility protects organisation.

---

## 5. Consequences

### 5.1 Positive Consequences

- ✅ **Zero Privacy Act breaches**: Comprehensive governance enables BR-004 target achievement
- ✅ **AI Governance Framework maturity**: Hybrid model achieves 7/10 maturity score (BR-007) within 6 months
- ✅ **Real-time enforcement**: Circuit breakers halt non-compliant AI behaviour; automated remediation
- ✅ **Regulatory leadership**: Proactive governance positions MagicDelivery as AI governance leader; potential regulatory consultation role

**Measurable outcomes**:
- Compliance incidents: Zero Privacy Act breaches
- DPIA completion rate: 100% before feature launch
- AI incident response time: <4 hours (BR-007)
- Governance framework maturity: 7/10 by Month 6

### 5.2 Negative Consequences

- ❌ **Complexity**: Dual-layer compliance requires dedicated compliance engineering capability
- ❌ **Resource commitment**: Compliance team needed for gate design, runtime monitoring, and regulatory engagement
- ❌ **Pipeline overhead**: Pre-deployment gates add time to model update cycles (mitigated by automation)

**Mitigation strategies**:
- **Complexity**: Standardised compliance templates; automated gate execution; shared tooling across AI initiatives
- **Resource commitment**: Dedicated compliance engineering team within Digital Technology; skills development programme
- **Pipeline overhead**: Automated gate execution in CI/CD; parallel gate execution; target <2 hours added per model update

---

## 6. Review and Updates

**Initial review**: 2027-01-01
**Periodic review**: Quarterly aligned with AI governance review cycle; annual regulatory assessment
**Trigger events**: Privacy Act breach detected; compliance incident response time exceeding 4 hours; DPIA completion rate below 100%

---

# ADR-008: Performance Target Strategy

## Decision Title

Tiers-Based Performance with SLOs, Circuit Breakers, and Predictive Scaling

## 1. Context and Problem Statement

### 1.1 Problem Description

AI agent platform must serve 10 million customers with defined performance targets under varying load conditions — from 10,000 normal concurrent users to 75,000 burst concurrent users during Black Friday and Christmas. Performance strategy must balance AI response quality (first-contact resolution, accuracy) with latency targets (sub-2-second p95), availability (99.95% trading hours), and graceful degradation under extreme load.

**Problem statement as a question**: What performance target strategy ensures reliable AI agent service under variable demand while maintaining customer experience and cost efficiency?

### 1.2 Why This Decision Is Needed

- **Business context**: BR-005 requires 50,000 concurrent user capacity, sub-2-second p95 response times, 99.9% availability, and 2-week agent onboarding. BR-002 requires sub-30-second resolution times for customer satisfaction. G-5 defines platform capability targets.
- **Technical context**: NFR-P-001 (sub-2-second p95 normal load, sub-5-second p95 peak load), NFR-P-002 (2,000 interactions/minute peak throughput), NFR-P-003 (sub-1,500ms inference latency), NFR-A-001 (99.95% availability), NFR-S-001 (horizontal scaling).
- **Operational context**: Black Friday and Christmas create 5x demand spikes. Performance strategy must handle predictable peak loads and unpredictable bursts.

### 1.3 Supporting Links

- **Requirements**: BR-002, BR-005, NFR-P-001 through NFR-P-003, NFR-A-001 through NFR-A-003, NFR-S-001
- **Stakeholders**: SD-2 (Digital Technology), SD-5 (Mobile App Developers), SD-6 (Customers)
- **Related ADRs**: ADR-001 (Deployment Strategy), ADR-003 (Data Architecture), ADR-008 (this decision)

---

## 2. Decision Drivers (Forces)

### 2.1 Technical Drivers

- **Variable demand**: Normal load (10,000 concurrent) to peak load (50,000 concurrent) to burst load (75,000 concurrent for 30 minutes)
- **Latency budgets**: End-to-end response budget of 2,000ms (p95); inference budget 1,500ms; data access budget 500ms; tokenisation budget 50ms
- **Scaling requirements**: Auto-scale within 3 minutes from trigger to new capacity (NFR-S-001)
- **Graceful degradation**: NFR-A-003 requires circuit breakers, retry patterns, and bulkhead isolation

### 2.2 Business Drivers

- **Customer experience**: NPS target of 42 (from 32) requires consistent performance even under peak load
- **Cost efficiency**: BR-005 targets sub-USD $0.05 per interaction; over-provisioning for peak loads is wasteful
- **Revenue protection**: AI features contribute to USD $25M revenue target (BR-001); performance failures directly impact revenue

### 2.3 Alignment to Architecture Principles

| Principle | Alignment | Impact |
|-----------|-----------|--------|
| Performance and Efficiency (PRIN-11) | Supports | SLOs enforce performance targets |
| Availability (PRIN-12) | Supports | Circuit breakers and graceful degradation maintain availability |
| Observability (PRIN-5) | Supports | SLO-based alerting requires structured telemetry |

---

## 3. Considered Options

### Option 1: Strict SLO with Circuit Breakers

**Description**: Define strict performance SLOs with hard enforcement via circuit breakers. When SLO thresholds are breached, circuit breakers automatically activate to protect system health — failing fast rather than degrading slowly.

#### Good (Pros)

- ✅ **Clear performance boundaries**: Hard SLOs provide unambiguous performance expectations
- ✅ **System protection**: Circuit breakers prevent cascading failures under extreme load
- ✅ **Predictable behaviour**: System either meets SLO or fails cleanly

#### Bad (Cons)

- ❌ **Customer experience cliff**: When circuit breaks activate, customers receive error messages or are redirected abruptly
- ❌ **Revenue risk**: Sudden service interruption during peak periods (Black Friday) directly impacts revenue
- ❌ **Too rigid**: Does not account for query priority; all queries treated equally when breaking

### Option 2: Best-Effort with Graceful Degradation

**Description**: System operates on best-effort performance; no strict SLO enforcement. Under load, response quality degrades gradually — slower responses, reduced feature set, fallback to cached answers.

#### Good (Pros)

- ✅ **Always available**: System continues serving queries even under extreme load
- ✅ **No hard failure cliff**: Customer experience degrades gracefully rather than breaking

#### Bad (Cons)

- ❌ **Unpredictable experience**: Customer cannot rely on consistent performance
- ❌ **Quality risk**: Slow or inaccurate responses at peak load damage CSAT and NPS
- ❌ **Compliance risk**: ACCC consumer law — slow responses may include stale or incorrect information

### Option 3: Tiers-Based Performance (Premium vs Standard)

**Description**: AI agent interactions classified into performance tiers. Critical queries (parcel tracking, delivery exceptions, security) receive premium performance guarantees with reserved capacity. Standard queries (general information, shopping) receive best-effort performance with shared capacity. Tier classification is automatic based on query type and customer context.

#### Good (Pros)

- ✅ **Prioritised reliability**: Critical queries always meet SLA; standard queries degrade gracefully
- ✅ **Cost optimisation**: Premium tier sized for critical query volume only; standard tier benefits from shared capacity
- ✅ **Customer-centric**: Customers who need urgent help (delivery exceptions) always get priority service
- ✅ **Measurable**: Tier-specific SLOs enable precise monitoring and capacity planning

#### Bad (Cons)

- ❌ **Tier classification overhead**: Real-time query classification required; false classification possible
- ❌ **Perceived unfairness**: Customers may notice different response times for different query types
- ❌ **Complexity**: Tier-based capacity management requires sophisticated resource allocation

### Option 4: Predictive Scaling with Auto-Rollback

**Description**: Historical demand patterns used to predict peak load periods; capacity pre-provisioned before expected demand. Automatic rollback to normal capacity when predicted peak passes. Anomaly detection for unexpected spikes.

#### Good (Pros)

- ✅ **Proactive capacity**: No cold-start delay for scaling; capacity available before demand arrives
- ✅ **Cost efficiency**: Over-provisioning only during predicted peak periods; minimised idle capacity
- ✅ **Predictable performance**: Pre-provisioned capacity meets SLO targets during known peaks

#### Bad (Cons)

- ❌ **Cannot handle unexpected spikes**: Anomalous demand beyond prediction cannot be pre-provisioned
- ❌ **Prediction accuracy**: Historical patterns may not predict novel demand patterns
- ❌ **Wasted capacity**: If prediction overestimates, capacity sits idle; if underestimates, SLO breach

### Option 5: Do Nothing (Baseline)

**Description**: No formal performance strategy; best-effort scaling with no SLOs.

#### Bad

- ❌ Cannot meet NFR-P-001, NFR-S-001, or NFR-A-001
- ❌ Peak load failures during Black Friday/Christmas
- ❌ Revenue risk from service degradation

---

## 4. Decision Outcome

### 4.1 Chosen Option

**"Option 3: Tiers-Based Performance, combined with Option 4: Predictive Scaling"**

The chosen strategy combines tiers-based performance prioritisation with predictive scaling and auto-rollback as the capacity management mechanism.

### 4.2 Y-Statement

> **In the context of** AI agents serving 10 million MagicDelivery customers with demand ranging from 10,000 normal to 75,000 burst concurrent users,
> **facing** the need to balance guaranteed performance for critical queries, cost efficiency, and graceful degradation for non-critical interactions,
> **we decided for** tiers-based performance with predictive scaling and circuit breakers,
> **to achieve** guaranteed SLA for critical queries (parcel tracking, delivery exceptions), graceful degradation for standard queries, and cost-efficient capacity management,
> **accepting** tier classification overhead and complexity in capacity management.

### 4.3 Justification

**Key reasons**:

1. **Guaranteed critical service**: Premium tier ensures parcel tracking (FR-002), delivery exceptions (FR-014), and security queries always meet sub-2-second p95 response times even at peak load. This protects the most customer-impacting interactions and directly supports BR-002 CSAT and NPS targets.
2. **Cost-efficient scaling**: Standard queries consume shared capacity with graceful degradation under extreme load. Premium tier reserved capacity sized only for critical query volume (estimated 20% of total interactions). Standard tier benefits from predictive scaling during known peaks (Black Friday, Christmas).
3. **Predictive capacity management**: Historical demand patterns pre-provision capacity for known peak periods (NFR-S-001 growth projections). Auto-rollback prevents idle capacity costs. Anomaly detection with circuit breakers (NFR-A-003) handles unexpected spikes.

---

## 5. Consequences

### 5.1 Positive Consequences

- ✅ **Guaranteed critical performance**: Premium tier SLOs protect customer-impacting queries at all load levels
- ✅ **Cost optimisation**: Tiered capacity sizing reduces over-provisioning cost by ~40% versus uniform sizing
- ✅ **Predictable peak handling**: Predictive scaling ensures capacity is ready before demand arrives
- ✅ **Graceful degradation**: Standard tier degrades gracefully rather than breaking under extreme load
- ✅ **Measurable SLOs**: Tier-specific metrics enable precise performance monitoring and capacity planning

**Measurable outcomes**:
- Premium tier (critical queries): p95 < 1,000ms; availability > 99.99%
- Standard tier (non-critical): p95 < 2,000ms normal, < 5,000ms peak; availability > 99.5%
- Platform availability: 99.95% during trading hours (NFR-A-001)
- Scaling trigger-to-capacity: < 3 minutes (NFR-S-001)
- Cost per interaction: < USD $0.05 (BR-005)

### 5.2 Negative Consequences

- ❌ **Tier classification risk**: Incorrect tier assignment leads to poor performance for critical queries or wasted premium capacity
- ❌ **Perceived inconsistency**: Customers may observe variable response times across query types
- ❌ **Capacity complexity**: Tier-based resource allocation requires sophisticated orchestration

**Mitigation strategies**:
- **Tier classification**: Content-based classification with conservative rules; security/complaint queries always premium; continuous refinement via FR-010 feedback
- **Perceived inconsistency**: Transparent communication about service levels; standard tier performance remains good (sub-5-second at peak)
- **Capacity complexity**: Cloud-native orchestration (Kubernetes HPA/VPA); automated tier capacity management; quarterly capacity reviews

---

## 6. Implementation Plan

### 6.1 Dependencies

- ADR-001 (Deployment Strategy): Cloud infrastructure for tiered capacity
- ADR-003 (Data Architecture): Event fabric for real-time tier classification
- ADR-002 (Handoff Model): Tier classification integrated with complexity-based routing

### 6.2 Implementation Timeline

| Phase | Activities | Duration | Owner |
|-------|-----------|----------|-------|
| Phase 1: Tier Definition | Tier classification rules, SLO definitions, capacity models | 2 weeks | Platform Engineering Lead |
| Phase 2: Infrastructure | Multi-tier capacity allocation, predictive scaling, circuit breakers | 4 weeks | Platform Engineering Team |
| Phase 3: Testing | Load testing at 1.5x peak; tier SLO validation; graceful degradation verification | 3 weeks | QA Team |
| Phase 4: Production Rollout | Gradual tier enablement; Black Friday dry run; auto-rollback validation | 3 weeks | Platform Engineering Team |

### 6.3 Rollback Plan

**Rollback trigger**: Premium tier SLO breach; circuit breaker activation exceeding threshold; tier classification accuracy below 85%.

**Rollback procedure**:

1. Suspend tier differentiation; revert to uniform capacity
2. Activate maximum scaling (all capacity reserved)
3. Investigate tier classification or capacity allocation issue
4. Repair and re-enable tiered performance with monitoring

---

## 7. Review and Updates

**Initial review**: 2027-01-01
**Periodic review**: Quarterly with performance metrics; pre-peak reviews before Black Friday and Christmas
**Trigger events**: Premium tier SLO breach; standard tier p95 exceeding 5,000ms for 15 minutes; predictive scaling error exceeding 20%

---

# Cross-ADR Dependency Map

The following diagram shows the dependency relationships between the eight ADRs:

```text
ADR-001: Deployment Strategy
├──→ ADR-002: Handoff Model (cloud/on-prem determines handoff architecture)
├──→ ADR-003: Data Architecture (deployment model determines data flow)
├──→ ADR-005: Multi-Channel (deployment determines backend architecture)
└──→ ADR-008: Performance (deployment determines scaling model)

ADR-002: Handoff Model
├──→ ADR-006: Workforce (handoff model determines staff impact)
└──→ ADR-005: Multi-Channel (handoff consistency across channels)

ADR-003: Data Architecture
└──→ ADR-007: Compliance (data fabric determines audit trail architecture)

ADR-004: Mobile Integration
├──→ ADR-005: Multi-Channel (SDK enables mobile channel)
└──→ ADR-008: Performance (SDK impacts app performance)

ADR-006: Workforce Model
└──→ ADR-007: Compliance (workforce model requires Fair Work Act compliance)

ADR-007: Compliance Governance
└──→ ADR-008: Performance (compliance monitoring impacts performance budget)
```

## ADR Inter-Dependencies Summary

| ADR | Depends On | Influences |
|-----|-----------|-----------|
| ADR-001 (Deployment) | — | ADR-002, ADR-003, ADR-005, ADR-008 |
| ADR-002 (Handoff) | ADR-001 | ADR-005, ADR-006 |
| ADR-003 (Data) | ADR-001 | ADR-007 |
| ADR-004 (Mobile) | ADR-001 | ADR-005, ADR-008 |
| ADR-005 (Multi-Channel) | ADR-001, ADR-002, ADR-004 | — |
| ADR-006 (Workforce) | ADR-002 | ADR-007 |
| ADR-007 (Compliance) | ADR-003, ADR-006 | ADR-008 |
| ADR-008 (Performance) | ADR-001, ADR-004, ADR-007 | — |

---

# ADR Index and Status Summary

| ADR ID | Title | Status | Decision Date | Next Review |
|--------|-------|--------|---------------|-------------|
| ADR-001 | Hybrid AI Agent Model Deployment | Proposed | 2026-07-01 | 2027-01-01 |
| ADR-002 | Hybrid Agent-Human Handoff with Complexity-Based Routing | Proposed | 2026-07-01 | 2027-01-01 |
| ADR-003 | Event-Driven Data Fabric for AI Agent Consumption | Proposed | 2026-07-01 | 2027-01-01 |
| ADR-004 | SDK Embedding for Mobile App AI Integration | Proposed | 2026-07-01 | 2027-01-01 |
| ADR-005 | Centralized Agent Backend with Multi-Channel UI | Proposed | 2026-07-01 | 2027-01-01 |
| ADR-006 | AI Co-Pilot Augmentation with Gradual Transition | Proposed | 2026-07-01 | 2027-01-01 |
| ADR-007 | Hybrid Compliance Governance | Proposed | 2026-07-01 | 2027-01-01 |
| ADR-008 | Tiers-Based Performance with Predictive Scaling | Proposed | 2026-07-01 | 2027-01-01 |

---

**Generated by**: ArcKit `/arckit:adr` command
**Generated on**: 2026-07-01
**ArcKit Version**: 5.15.2
**Project**: AgenticEA — MagicDelivery Agent AI Transformation (Project 001)
**Model**: Qwen3.6-27B
