# Project Requirements: AgenticEA — MagicDelivery Agent AI Transformation Program

> **Template Origin**: Official | **ArcKit Version**: 5.15.2 | **Command**: `/arckit:requirements`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-REQ-v1.0 |
| **Document Type** | Business and Technical Requirements |
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
| **Distribution** | Executive Leadership, Parcel Business, Digital Technology, Compliance/Legal, Program Delivery Team, Program Analysts, Mobile App Developers |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-07-01 | ArcKit AI | Initial creation from `/arckit:requirements` command — 8 business, 16 functional, 23 non-functional, 8 integration, 10 data requirements; 4 conflict resolutions | PENDING | PENDING |

---

## Document Purpose

This document defines the comprehensive business, functional, non-functional, integration, and data requirements for the **AgenticEA — MagicDelivery Agent AI Transformation Program**. It establishes the authoritative requirements baseline against which all design, development, testing, and delivery decisions are measured. The requirements are derived from stakeholder analysis (ARC-001-STKE-v1.0), enterprise architecture principles (ARC-000-PRIN-v2.0), and international regulatory obligations.

This document serves as the input for vendor RFPs, architecture design, test planning, and benefits realisation tracking.

---

## Executive Summary

### Business Context

MagicDelivery is launching a comprehensive AI transformation to deploy intelligent AI agents within the MagicDelivery Mobile App, serving 10 million international customers. The program targets three capability areas: AI-powered customer service, intelligent parcel tracking, and an AI shopping assistant for e-commerce. Current pain points include 8-minute average call wait times, a Net Promoter Score of 32, fragmented parcel tracking, and competitive pressure from Amazon Logistics and dedicated courier services eroding market share.

The program delivers AI agents progressively through the existing MagicDelivery Mobile App — approximately 3 million active monthly users — with a phased rollout over 12 to 24 months. The approved programme budget is USD $18.5M, with a target of USD $25M incremental annual revenue attributable to AI-enabled features by Month 18 and USD $15M annual operational savings from AI-assisted operations.

### Objectives

- Deploy AI agents in the MagicDelivery Mobile App for customer service, parcel tracking, and shopping assistance within 12 months
- Achieve USD $25M incremental annual revenue from AI-enabled features by Month 18
- Reduce routine call centre volume by 40% through AI agent deflection, with zero net FTE reduction
- Achieve NPS of 42 (up from 32) and CSAT above 80% by Month 12
- Establish privacy-compliant AI architecture with zero Privacy Act breaches
- Upskill 2,000 operations staff in AI-augmented workflows within 18 months

### Expected Outcomes

- **Financial**: USD $25M incremental annual revenue by Month 18; USD $15M operational cost savings; 3.5x ROI on AI investment within 24 months
- **Customer**: NPS improvement from 32 to 42; CSAT above 80%; sub-30-second AI resolution time for common queries
- **Operational**: 40% routine call deflection by AI; staff satisfaction score from 4.2 to 6.5/10; zero net FTE reduction
- **Compliance**: Zero Privacy Act breaches; 100% DPIA completion; AI Governance Framework maturity score of 7/10
- **Platform**: AI platform supporting 50,000 concurrent users; sub-2-second p95 response times; 2-week agent onboarding cycles

### Project Scope

**In Scope**:

- AI Customer Service Agent: Conversational, multi-turn agent for common queries (parcel tracking, delivery status, address changes, fee information)
- AI Parcel Tracking Agent: Real-time status updates, predictive ETAs, proactive notifications
- AI Shopping Assistant: Product discovery, recommendations, personalised offers within the app
- Human-in-the-loop escalation: Seamless handoff to human agents when AI confidence is below threshold
- AI agent platform: Scalable infrastructure supporting model serving, telemetry, governance
- Integration with existing MagicDelivery systems: CRM, e-commerce platform, logistics/tracking, SMS/email services
- Privacy-by-design architecture: APP-compliant data handling, DPIAs, audit trails
- Mobile app UI components: AI agent interaction surfaces within existing app navigation
- Staff AI-augmented tooling: AI co-pilot for call centre and retail staff
- Multi-language support: English plus top community languages (Mandarin, Arabic, Vietnamese)

**Out of Scope**:

- Standalone AI applications outside the MagicDelivery Mobile App
- AI agents for domestic mail services (letters, parcels under 2kg)
- Autonomous delivery vehicles or drone operations
- AI-powered workforce scheduling or logistics route optimisation (future phase)
- International customer-facing AI services (USD-only, international customers)
- Replacement of existing call centre; AI augments, not replaces, human agents
- Direct integration with third-party e-commerce platforms (limited to MagicDelivery's own channels)

---

## Stakeholders

| Stakeholder | Role | Organization | Involvement Level |
|-------------|------|--------------|-------------------|
| Parcel Business GM | Executive Sponsor / Decision Maker | Parcel Business | Strategic direction, scope approval, ROI accountability |
| CEO / Executive Board | Executive Sponsor | Executive Leadership | Board-level governance, investment approval |
| Head of Digital Technology | Enterprise Architect | Digital Technology | Platform architecture, technical governance |
| Programme Director | Delivery Lead | Program Delivery Team | Day-to-day delivery, scope control, milestone tracking |
| Head of Customer Experience | Product Owner | Customer Experience | Customer requirements, UX validation, NPS accountability |
| Privacy Officer / CISO | Compliance Lead | Compliance/Legal | Privacy Act compliance, security governance |
| Head of People & Culture | Workforce Lead | HR | Workforce transition, upskilling programme |
| Operations Staff Representatives | End Users | Call Centre, Retail, Logistics | AI tool co-design, feedback, pilot participation |

---

## Business Requirements

### BR-001: AI-Driven Revenue Growth

**Description**: Achieve USD $25M incremental annual revenue attributable to AI-enabled features in the MagicDelivery Mobile App within 18 months of full launch, measured through feature-attribution modelling against control groups.

**Rationale**: Directly satisfies G-1 (AI-Driven Revenue Growth, SD-1 + SD-9). Parcel Business GM scorecard is weighted 40% on revenue growth; AI features in the app represent the highest-ROI digital channel for capturing at-home delivery and click-and-collect segments.

**Success Criteria**:

- Incremental AI-attributed revenue reaching USD $25M annual run-rate by Month 18
- Customer acquisition rate from AI-driven onboarding exceeding 5% of monthly active users
- Average order value uplift of 10% for AI-engaged customers versus matched control cohort
- Feature adoption rate exceeding 20% of monthly active users by Month 6

**Priority**: MUST_HAVE

**Stakeholder**: Parcel Business GM, Executive Leadership

**Traces To**: G-1 (AI-Driven Revenue Growth), SD-1, SD-9

---

### BR-002: Customer Experience Transformation

**Description**: Reduce average customer query resolution time from 8 minutes (phone) to under 30 seconds (AI agent in-app) by Month 12, while increasing NPS from 32 to 42 and CSAT above 80%.

**Rationale**: Directly satisfies G-2 (Customer Experience Transformation, SD-6 + SD-5). Customer satisfaction drives retention, referrals, and revenue. Faster resolution through AI is the primary differentiator against competitors.

**Success Criteria**:

- Average AI agent resolution time under 30 seconds for first-contact queries
- NPS improvement from baseline of 32 to target of 42 by Month 12
- CSAT score above 80% for AI-handled interactions
- First-contact resolution rate above 85%

**Priority**: MUST_HAVE

**Stakeholder**: Customers, Head of Customer Experience

**Traces To**: G-2 (Customer Experience Transformation), SD-6, SD-5

---

### BR-003: Operational Cost Reduction Through AI

**Description**: Reduce routine call centre query volume by 40% through AI agent deflection within 12 months, delivering USD $12M annual operational cost savings with zero net FTE reduction.

**Rationale**: Directly satisfies G-3 (Operational Efficiency, SD-7 + SD-1). 60% of 120,000 monthly calls are routine queries suitable for AI handling. Cost savings must not come at the cost of workforce reduction per the Board-approved AI Augmentation Charter.

**Success Criteria**:

- 40% routine call volume deflection (48,000 calls per month handled by AI)
- Staff satisfaction score improvement from 4.2 to 6.5/10
- Zero net FTE reduction confirmed through HRIS tracking
- AI deflection accuracy rate above 85% on routine query types

**Priority**: MUST_HAVE

**Stakeholder**: Head of Operations, Executive Leadership, Operations Staff

**Traces To**: G-3 (Operational Efficiency Through AI Augmentation), SD-7, SD-1

---

### BR-004: Privacy-Compliant AI Architecture

**Description**: Achieve full Privacy Act 1988 (APP) compliance for all AI agent data processing by launch, with zero regulatory findings in the first OAIC audit cycle and 100% DPIA completion for each AI agent capability.

**Rationale**: Directly satisfies G-4 (Privacy-Compliant AI Architecture, SD-8 + SD-6). OAIC penalties of up to USD $2.5M per breach and reputational damage create existential risk for the programme. Privacy-by-design eliminates post-hoc compliance rework.

**Success Criteria**:

- Zero Privacy Act breaches attributable to AI operations
- 100% DPIA completion rate before feature launch
- Privacy complaints below 5 per 100,000 AI interactions
- Automated privacy controls covering all data collection points

**Priority**: MUST_HAVE

**Stakeholder**: Privacy Officer, CISO, Compliance/Legal, Customers

**Traces To**: G-4 (Privacy-Compliant AI Architecture), SD-8, SD-6

---

### BR-005: Scalable AI Platform

**Description**: Deliver a production-ready AI agent platform supporting 50,000 concurrent users, sub-2-second response times at p95, 99.9% availability, and the ability to onboard new agent types within 2-week development cycles by Month 12.

**Rationale**: Directly satisfies G-5 (Scalable AI Platform Capability, SD-2 + SD-3). Creates a strategic platform asset reusable for future AI initiatives. Cost-per-interaction target below USD $0.05 ensures economic viability.

**Success Criteria**:

- Platform supporting 50,000 concurrent users
- p95 response time under 2,000 milliseconds
- Platform availability of 99.9% during trading hours
- New agent onboarding cycle time of 2 weeks
- Cost per AI interaction below USD $0.05

**Priority**: MUST_HAVE

**Stakeholder**: Head of Digital Technology, Program Delivery Team

**Traces To**: G-5 (Scalable AI Platform Capability), SD-2, SD-3

---

### BR-006: Workforce Augmentation and Upskilling

**Description**: Upskill 2,000 operations and retail staff in AI-augmented workflows within 18 months, with 80% completion rate, zero net job losses, and staff AI-confidence score increasing from 3.0 to 6.5 (out of 10).

**Rationale**: Directly satisfies G-6 (Workforce Augmentation, SD-7 + SD-9). Essential for union relations, organisational culture, and demonstrating AI as augmentation rather than replacement under the Fair Work Act.

**Success Criteria**:

- 2,000 staff certified in AI-augmented workflows (20% of 10,000 workforce)
- Training completion rate of 80%
- AI confidence score improvement from 3.0 to 6.5/10
- Zero net FTE reduction

**Priority**: MUST_HAVE

**Stakeholder**: Head of People & Culture, Executive Leadership, Operations Staff

**Traces To**: G-6 (Workforce Augmentation and Upskilling), SD-7, SD-9

---

### BR-007: AI Governance Framework

**Description**: Establish an AI Governance Framework aligned with international regulatory expectations (OAIC, ACCC, Treasury AI Regulation Review) by Month 6, including AI risk register, model governance process, and human oversight requirements for all customer-facing AI agents.

**Rationale**: Directly satisfies G-7 (Regulatory Readiness for AI Governance, SD-8 + SD-9). Proactively building governance infrastructure positions MagicDelivery as a regulatory leader and prevents reactive compliance rework.

**Success Criteria**:

- AI Governance Framework achieving maturity score of 7/10
- 100% of customer-facing AI models in governance register
- AI incident response time under 4 hours
- Board-approved AI risk appetite statement published

**Priority**: MUST_HAVE

**Stakeholder**: CISO, Privacy Officer, Compliance/Legal, Executive Leadership

**Traces To**: G-7 (Regulatory Readiness for AI Governance), SD-8, SD-9

---

### BR-008: Delivery Excellence and Scope Control

**Description**: Deliver the AgenticEA programme within the 12-to-24 month window, within 10% of approved budget (USD $18.5M), with all critical features achieving production readiness, and no more than 2 scope-change exceptions per quarter.

**Rationale**: Directly satisfies G-8 (Delivery Excellence, SD-3 + SD-1). Previous digital programmes averaged 22% budget overrun and 4-month timeline slippage. Scope discipline protects investment value.

**Success Criteria**:

- Budget variance under 10%
- Timeline variance under 2 months
- Critical feature delivery rate above 90%
- Scope-change exceptions at or below 2 per quarter
- Stakeholder satisfaction score above 7.5/10

**Priority**: MUST_HAVE

**Stakeholder**: Programme Director, Executive Leadership

**Traces To**: G-8 (Delivery Excellence and Scope Control), SD-3, SD-1

---

## Functional Requirements

### User Personas

#### Persona 1: Everyday Customer (Parcel Sender/Receiver)

- **Role**: international consumer who regularly sends or receives parcels through MagicDelivery
- **Goals**: Track parcels in real-time, get instant answers about delivery, receive proactive notifications, find personalised shipping options
- **Pain Points**: 8-minute phone wait times, fragmented tracking across platforms, limited after-hours service
- **Technical Proficiency**: Medium — comfortable with mobile apps, expects modern experiences

#### Persona 2: E-commerce Seller

- **Role**: Small to medium business owner using MagicDelivery for e-commerce fulfilment
- **Goals**: Efficiently ship orders, track shipments, discover cost-effective shipping options, automate routine tasks
- **Pain Points**: Time-consuming shipping processes, lack of bulk operation tools, inconsistent fee information
- **Technical Proficiency**: High — uses multiple e-commerce tools daily

#### Persona 3: Call Centre Agent

- **Role**: Customer service representative handling inbound queries
- **Goals**: Resolve customer queries efficiently, access AI co-pilot for information, handle complex escalations
- **Pain Points**: Repetitive routine queries (60% of workload), peak period overload, stress from high volume
- **Technical Proficiency**: Medium — proficient with CRM and ticketing tools

#### Persona 4: Retail Staff Member

- **Role**: Counter staff at MagicDelivery retail outlets
- **Goals**: Assist customers with parcel services, access AI tools for lookups, process transactions efficiently
- **Pain Points**: Peak-period queues, knowledge-intensive product inquiries, inconsistent information
- **Technical Proficiency**: Medium — uses point-of-sale and retail systems

---

### Functional Requirements Detail

#### FR-001: AI Customer Service Agent — Conversational Interface

**Description**: The system shall provide an AI-powered conversational agent accessible within the MagicDelivery Mobile App that handles multi-turn natural language interactions for common customer queries including parcel tracking, delivery status, address changes, fee information, and service inquiries.

**Relates To**: BR-002, BR-003, G-2, G-3

**Acceptance Criteria**:

- [ ] Given a customer submits a natural language query, when the AI agent processes it, then the agent returns a relevant response within 2 seconds
- [ ] Given a multi-turn conversation, when context is established, then the agent maintains context across at least 10 consecutive turns
- [ ] Given the AI agent confidence score falls below 70%, when the query is processed, then the agent offers escalation to a human agent
- [ ] Given a customer queries parcel status, when a tracking number is provided, then the agent returns current status, predicted delivery date, and location history
- [ ] Edge case: Given ambiguous input, when the agent cannot determine intent with 80% confidence, then the agent asks clarifying questions rather than guessing

**Data Requirements**:

- **Inputs**: Natural language query, customer authentication token, optional tracking number
- **Outputs**: Text response, structured data (tracking status), confidence score, escalation flag
- **Validations**: Response must not contain PII beyond what is explicitly relevant to the query; confidence score must be logged

**Priority**: MUST_HAVE

**Complexity**: HIGH

**Dependencies**: FR-002, INT-001 (CRM), INT-003 (Logistics/Tracking)

**Assumptions**: AI model achieves 85% first-contact resolution rate on routine queries; customer has authenticated session

---

#### FR-002: AI Parcel Tracking Agent — Real-Time Status and Prediction

**Description**: The system shall provide an AI-powered parcel tracking capability that delivers real-time shipment status, predictive Estimated Times of Arrival (ETA), and proactive push notifications for significant status changes.

**Relates To**: BR-002, G-2, G-1

**Acceptance Criteria**:

- [ ] Given a parcel exists in the logistics system, when the customer queries its status, then the AI agent returns current status within 1 second including location, next milestone, and predicted ETA
- [ ] Given a parcel reaches a scan milestone, when the event is received from the logistics system, then the system pushes a notification to the customer within 30 seconds
- [ ] Given a parcel is delayed beyond predicted ETA, when the delay is detected, then the AI agent proactively informs the customer with revised ETA and cause
- [ ] Given a customer has multiple parcels, when the agent is queried, then the agent presents a consolidated tracking summary with prioritisation by urgency
- [ ] Edge case: Given a tracking system outage, when status data is unavailable, then the agent provides last-known status and advises when next update is expected

**Data Requirements**:

- **Inputs**: Tracking number, customer ID, logistics event stream
- **Outputs**: Real-time status, predicted ETA, notification, historical scan points
- **Validations**: ETA prediction must be derived from historical data; notification delivery confirmed via receipt

**Priority**: MUST_HAVE

**Complexity**: HIGH

**Dependencies**: INT-003 (Logistics/Tracking), INT-004 (SMS/Email), NFR-P-001

**Assumptions**: Logistics/tracking system provides real-time event stream with sub-60-second latency

---

#### FR-003: AI Shopping Assistant — Product Discovery and Recommendations

**Description**: The system shall provide an AI-powered shopping assistant that helps customers discover shipping services, compare options, and receive personalised recommendations based on parcel characteristics, delivery preferences, and historical behaviour.

**Relates To**: BR-001, G-1

**Acceptance Criteria**:

- [ ] Given a customer wants to send a parcel, when they describe the parcel, then the assistant recommends appropriate service tiers with pricing
- [ ] Given customer browsing history, when the assistant identifies a pattern, then it offers relevant promotions or service upgrades
- [ ] Given a comparison request, when the customer asks "what's the best option", then the assistant presents a ranked comparison of available services with cost, speed, and tracking features
- [ ] Given an opt-in for personalisation, when the customer has browsing history, then the assistant tailors recommendations to past behaviour
- [ ] Edge case: Given no purchase history, when the assistant generates recommendations, then it relies on explicit customer inputs only, not inferred preferences

**Data Requirements**:

- **Inputs**: Customer profile (opt-in), parcel dimensions/weight, delivery preferences, browsing history
- **Outputs**: Ranked recommendations, pricing, service descriptions
- **Validations**: Recommendations must comply with ACCC consumer law; no misleading comparisons

**Priority**: MUST_HAVE

**Complexity**: HIGH

**Dependencies**: INT-001 (E-commerce Platform), FR-005 (Personalisation)

**Assumptions**: Customer has explicitly opted in to personalised recommendations

---

#### FR-004: Human-in-the-Loop Escalation

**Description**: The system shall provide seamless handoff from AI agent to human customer service agents when AI confidence is below threshold, the customer explicitly requests a human, or the query involves high-risk topics (security, legal, complaints).

**Relates To**: BR-002, BR-003, G-2, G-3

**Acceptance Criteria**:

- [ ] Given AI confidence score below 70%, when processing a query, then the agent offers "Would you like to speak with a human?" with one-tap escalation
- [ ] Given a customer requests "talk to a person", when the request is received, then escalation occurs within 30 seconds
- [ ] Given an escalation occurs, when the human agent receives the conversation, then the agent is presented with full conversation context including AI confidence scores and attempted responses
- [ ] Given a high-risk topic is detected (security, legal complaint, vulnerability), when the query is received, then the agent escalates automatically without requiring customer prompt
- [ ] Edge case: Given human agent queue is full, when escalation is requested, then the agent provides estimated wait time and option to leave a message

**Data Requirements**:

- **Inputs**: Conversation history, AI confidence scores, customer authentication, escalation reason code
- **Outputs**: Human agent brief, conversation transcript, routing metadata
- **Validations**: Full conversation context transferred; no loss of PII during handoff

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

**Dependencies**: FR-001, INT-002 (CRM/ERP)

**Assumptions**: Call centre routing system supports API-based agent assignment with context injection

---

#### FR-005: Personalisation Engine

**Description**: The system shall maintain a customer preference profile that enables AI agents to provide personalised interactions, including service recommendations, notification preferences, and language selection, based on opt-in data collection.

**Relates To**: BR-001, G-1, G-2

**Acceptance Criteria**:

- [ ] Given a returning authenticated customer, when the agent initiates a conversation, then it addresses the customer by name and references prior interactions where relevant
- [ ] Given customer has set notification preferences, when tracking events occur, then notifications are delivered only via preferred channels
- [ ] Given customer has a preferred language set, when the agent responds, then it responds in that language for supported languages
- [ ] Given a customer changes personalisation settings, when the change is saved, then the change takes effect within the current session
- [ ] Edge case: Given a guest (non-authenticated) user, when they interact with the agent, then the agent provides a standard experience without personalisation

**Data Requirements**:

- **Inputs**: Customer preferences, interaction history, opt-in flags, language selection
- **Outputs**: Personalised responses, targeted notifications, language selection
- **Validations**: Personalisation requires explicit opt-in per APP 3; settings accessible via privacy dashboard

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

**Dependencies**: DR-001, NFR-C-001

**Assumptions**: Customer authentication via existing MagicDelivery account system

---

#### FR-006: Multi-Language Support

**Description**: The system shall support AI agent interactions in English and up to 5 additional community languages (Mandarin, Arabic, Vietnamese, Hindi, Cantonese) with comparable accuracy to English interactions.

**Relates To**: BR-002, G-2

**Acceptance Criteria**:

- [ ] Given a customer selects a supported language, when they submit a query, then the agent responds in that language with accuracy above 80%
- [ ] Given the customer switches languages mid-conversation, when the language changes, then the agent switches seamlessly without losing context
- [ ] Given a language is not yet supported, when the customer queries in that language, then the agent responds in English with an invitation to switch to a supported language
- [ ] Edge case: Given code-mixed input (multiple languages in one message), when the agent detects multiple languages, then it responds in the dominant language

**Data Requirements**:

- **Inputs**: Language selection, multilingual queries
- **Outputs**: Translated responses, language detection metadata
- **Validations**: Translation accuracy above 80% against human evaluation; fallback to English for unsupported languages

**Priority**: SHOULD_HAVE

**Complexity**: HIGH

**Dependencies**: AI model supports multilingual inference

**Assumptions**: Top 5 community languages selected based on MagicDelivery customer demographic data

---

#### FR-007: AI Co-Pilot for Operations Staff

**Description**: The system shall provide an AI co-pilot tool for call centre and retail staff that assists with customer queries by surfacing relevant information, suggesting responses, and automating routine lookups.

**Relates To**: BR-003, BR-006, G-3, G-6

**Acceptance Criteria**:

- [ ] Given a staff member is handling a customer call, when a query is received, then the AI co-pilot displays suggested responses and relevant data within 2 seconds
- [ ] Given the co-pilot suggests a response, when the staff member accepts it, then the response is delivered to the customer with staff approval logged
- [ ] Given a routine tracking query, when the co-pilot detects the pattern, then it auto-fills the tracking lookup and displays results
- [ ] Edge case: Given the co-pilot confidence is below 70%, when a suggestion is made, then it is flagged as "low confidence" for staff review

**Data Requirements**:

- **Inputs**: Customer query context, CRM data, logistics data, staff role
- **Outputs**: Suggested responses, auto-fill data, confidence scores
- **Validations**: All suggestions require staff approval before customer delivery; no autonomous customer-facing output from co-pilot

**Priority**: MUST_HAVE

**Complexity**: HIGH

**Dependencies**: FR-004, INT-002, INT-003

**Assumptions**: Staff terminal environment supports co-pilot overlay with existing CRM interface

---

#### FR-008: AI Interaction Audit Trail

**Description**: The system shall maintain a complete, tamper-evident audit trail of all AI agent interactions including conversation logs, confidence scores, escalation events, and data access records, retained for compliance and forensic purposes.

**Relates To**: BR-004, BR-007, G-4, G-7

**Acceptance Criteria**:

- [ ] Given an AI interaction occurs, when it completes, then the full conversation is logged with timestamp, customer ID, confidence scores, and outcome
- [ ] Given a regulatory audit request, when logs are retrieved, then they can be produced with cryptographic integrity verification
- [ ] Given a privacy access request under APP 12, when the customer requests their data, then their AI interaction logs are included in the response within 30 days
- [ ] Edge case: Given a PII data deletion request under APP 11, when the request is validated, then personal identifiers are removed from logs while preserving the interaction record for governance

**Data Requirements**:

- **Inputs**: Conversation data, confidence scores, user identifiers, outcome codes
- **Outputs**: Encrypted audit log entries, compliance reports, customer data extracts
- **Validations**: Logs must be append-only; integrity verified via cryptographic hashing

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

**Dependencies**: NFR-C-001, NFR-C-002, DR-005

**Assumptions**: Secure log storage with tamper-evident capabilities

---

#### FR-009: In-App Privacy Dashboard

**Description**: The system shall provide customers with a privacy dashboard within the MagicDelivery Mobile App where they can view, manage, and control their personal data, opt-in/opt-out of personalisation, and request data deletion.

**Relates To**: BR-004, G-4

**Acceptance Criteria**:

- [ ] Given an authenticated customer, when they access the privacy dashboard, then they can see all data categories collected and their retention periods
- [ ] Given a customer toggles personalisation off, when the toggle is saved, then AI personalisation ceases within the current session
- [ ] Given a customer requests data deletion, when the request is submitted, then deletion is confirmed within 30 days per APP requirements
- [ ] Edge case: Given a customer requests export of their data, when the export is generated, then it is provided in machine-readable JSON format within 30 days

**Data Requirements**:

- **Inputs**: User identity, consent flags, data categories, retention settings
- **Outputs**: Data inventory, consent status, export files, deletion confirmation
- **Validations**: All consent changes logged with timestamp; deletion requests processed within 30 days

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

**Dependencies**: DR-006, NFR-C-001

**Assumptions**: Existing MagicDelivery authentication supports privacy settings persistence

---

#### FR-010: AI Confidence Monitoring and Feedback

**Description**: The system shall provide post-interaction feedback mechanisms allowing customers to rate AI responses, with feedback data feeding an automated model improvement pipeline.

**Relates To**: BR-002, G-2

**Acceptance Criteria**:

- [ ] Given an AI interaction completes, when the interaction ends, then the customer is prompted to rate the response on a 5-point scale
- [ ] Given a negative rating (below 3/5), when submitted, then a follow-up survey is offered to capture feedback
- [ ] Given accumulated feedback, when the feedback pipeline processes data, then model accuracy is measured and improvement is tracked
- [ ] Edge case: Given a customer declines to rate, when no feedback is provided, then the interaction is still logged but excluded from feedback analytics

**Data Requirements**:

- **Inputs**: Customer ratings, feedback text, interaction IDs
- **Outputs**: Feedback analytics, model improvement metrics, trend reports
- **Validations**: Feedback data classified as INTERNAL; no PII in feedback analytics

**Priority**: SHOULD_HAVE

**Complexity**: LOW

**Dependencies**: NFR-P-003

**Assumptions**: Customer will engage with feedback prompt at a rate above 20%

---

#### FR-011: Multi-Channel Consistency

**Description**: The system shall ensure consistent AI agent behaviour and response quality across the MagicDelivery Mobile App, web portal, and call centre interfaces, with shared conversation context enabling seamless transition between channels.

**Relates To**: BR-002, G-2

**Acceptance Criteria**:

- [ ] Given a conversation initiated on the mobile app, when the customer switches to web, then conversation history is preserved and accessible
- [ ] Given identical queries across channels, when processed by the AI agent, then response content and tone are consistent within acceptable variation
- [ ] Edge case: Given a conversation started via app and escalated to call centre, when the human agent accesses the record, then the full AI interaction history is available

**Data Requirements**:

- **Inputs**: Channel identifiers, session tokens, conversation data
- **Outputs**: Unified conversation records, channel routing metadata
- **Validations**: Cross-channel context preserved within 7-day session window

**Priority**: SHOULD_HAVE

**Complexity**: MEDIUM

**Dependencies**: INT-001, INT-002

**Assumptions**: Web portal integration available as Phase 2 enhancement

---

#### FR-012: AI Agent Administration and Monitoring

**Description**: The system shall provide administrators with a dashboard to monitor AI agent performance, view real-time metrics, manage model versions, configure confidence thresholds, and pause specific agent capabilities.

**Relates To**: BR-007, G-7

**Acceptance Criteria**:

- [ ] Given an administrator accesses the dashboard, when it loads, then real-time metrics are displayed including active sessions, response times, confidence distribution, and error rates
- [ ] Given a model version update is available, when the administrator approves deployment, then the new model is deployed with automatic rollback capability
- [ ] Given an administrator adjusts confidence thresholds, when saved, then the change takes effect within 5 minutes for new interactions
- [ ] Given an administrator pauses an agent capability, when the pause is activated, then all new queries for that capability are redirected to human agents
- [ ] Edge case: Given a critical metric breach (error rate above 5%), when the threshold is exceeded, then an alert is generated and automated pause is triggered after administrator confirmation

**Data Requirements**:

- **Inputs**: Agent metrics, model metadata, threshold settings, admin actions
- **Outputs**: Dashboard displays, alerts, model deployment records, audit logs
- **Validations**: Admin actions logged with identity and timestamp; rollback tested quarterly

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

**Dependencies**: NFR-M-001, NFR-A-001

**Assumptions**: Admin access restricted to authorised Digital Technology personnel via RBAC

---

#### FR-013: Notification Preferences Management

**Description**: The system shall allow customers to configure their notification preferences for AI-driven alerts including push notifications, SMS, and email, with granular control over event types (delivery confirmation, delay alerts, ETA updates).

**Relates To**: BR-002, G-2

**Acceptance Criteria**:

- [ ] Given a customer accesses notification settings, when they view preferences, then all event types and channels are displayed with toggle controls
- [ ] Given a customer disables SMS notifications, when the change is saved, then no SMS is sent for any event type
- [ ] Edge case: Given a delivery exception event occurs, when all notification channels are disabled, then the event is logged and visible in the app history but not pushed

**Data Requirements**:

- **Inputs**: User preferences, event types, channel selection
- **Outputs**: Notification settings record, preference validation
- **Validations**: At least one notification channel must remain enabled for critical events (delivery failures, security alerts)

**Priority**: SHOULD_HAVE

**Complexity**: LOW

**Dependencies**: INT-004 (SMS/Email)

**Assumptions**: Notification preferences persist across app updates and device changes

---

#### FR-014: Proactive Delivery Exception Management

**Description**: The system shall detect delivery exceptions (failed delivery, address issues, customs holds, damaged parcels) and proactively initiate AI conversations with affected customers offering resolution options.

**Relates To**: BR-002, BR-001, G-2, G-1

**Acceptance Criteria**:

- [ ] Given a delivery exception is detected in the logistics system, when it is received, then the AI agent initiates a proactive conversation within 5 minutes
- [ ] Given a customer receives a proactive exception notification, when they respond, then the agent offers available resolution options (redelivery, address correction, collection at retail)
- [ ] Edge case: Given multiple exceptions for one customer, when notifications are generated, then they are consolidated into a single message

**Data Requirements**:

- **Inputs**: Exception events, customer contact data, resolution options
- **Outputs**: Proactive notifications, resolution workflows, exception records
- **Validations**: Exception events correlated to customer within 5 minutes; resolution options validated against service level

**Priority**: SHOULD_HAVE

**Complexity**: MEDIUM

**Dependencies**: INT-003, FR-002

**Assumptions**: Logistics exception events are reliably surfaced within the integration layer

---

#### FR-015: Staff Upskilling Training Module Integration

**Description**: The system shall integrate with the organisational Learning Management System (LMS) to deliver AI-augmented workflow training modules, track completion, and issue certifications to operations staff.

**Relates To**: BR-006, G-6

**Acceptance Criteria**:

- [ ] Given a staff member begins training, when they complete a module, then completion is recorded in the LMS with timestamp and score
- [ ] Given a staff member achieves 80% or above on all modules, when the threshold is met, then an AI-augmented workflow certification is issued
- [ ] Given quarterly AI confidence surveys, when results are collected, then the AI confidence score is calculated and tracked
- [ ] Edge case: Given a staff member fails a module, when resubmission is allowed, then a maximum of 3 attempts is permitted before manager notification

**Data Requirements**:

- **Inputs**: Staff identity, training module IDs, completion data, scores
- **Outputs**: Certification records, LMS updates, confidence score trends
- **Validations**: Training data classified as INTERNAL; linked to HRIS records

**Priority**: SHOULD_HAVE

**Complexity**: LOW

**Dependencies**: Existing LMS provides REST API for training data exchange

**Assumptions**: LMS supports module-based training delivery and completion tracking

---

#### FR-016: AI Hallucination Detection and Mitigation

**Description**: The system shall implement runtime detection of potential AI hallucinations (factually incorrect or misleading responses) through response validation rules, confidence thresholding, and post-response fact-checking against authoritative data sources.

**Relates To**: BR-004, BR-007, G-2, G-4

**Acceptance Criteria**:

- [ ] Given an AI response is generated, when it contains factual claims, then claims are validated against authoritative data sources before delivery
- [ ] Given validation detects a mismatch, when confidence is below threshold, then the response is suppressed and escalation is triggered
- [ ] Given a customer reports an inaccurate response, when reported, then the response is flagged for review and the model is retrained on the correction
- [ ] Edge case: Given a query with no authoritative data source (e.g., opinion-based), when the agent responds, then it includes a disclaimer that the information is AI-generated

**Data Requirements**:

- **Inputs**: Generated responses, authoritative data, customer reports
- **Outputs**: Validated responses, hallucination flags, correction records
- **Validations**: Validation rules maintained in a version-controlled rules database; daily accuracy audits

**Priority**: MUST_HAVE

**Complexity**: HIGH

**Dependencies**: FR-001, INT-001, NFR-SEC-005

**Assumptions**: Authoritative data sources (fee schedules, service terms) are maintained in a queryable format

---

### User Stories Summary

| ID | As a... | I want to... | So that... | Priority |
|----|---------|-------------|-----------|----------|
| US-001 | Customer | Ask my AI agent about my parcel | I get instant answers without calling | MUST_HAVE |
| US-002 | Customer | Receive proactive delivery updates | I stay informed without manual tracking | MUST_HAVE |
| US-003 | E-commerce seller | Compare shipping options | I find the most cost-effective service | MUST_HAVE |
| US-004 | Customer | Switch to a human agent easily | Complex issues are resolved with expertise | MUST_HAVE |
| US-005 | Call centre agent | Use AI co-pilot | I handle fewer routine queries and focus on complex issues | MUST_HAVE |
| US-006 | Customer | Control my data privacy settings | I trust the AI with my information | MUST_HAVE |
| US-007 | Customer | Interact in my preferred language | I receive service I understand | SHOULD_HAVE |
| US-008 | Administrator | Monitor AI performance | I maintain service quality and compliance | MUST_HAVE |
| US-009 | Staff member | Complete AI training | I am confident using AI-augmented tools | MUST_HAVE |
| US-010 | Customer | Rate AI responses | The system improves based on my feedback | SHOULD_HAVE |

---

## Non-Functional Requirements (NFRs)

### Performance Requirements

#### NFR-P-001: AI Agent Response Time

**Requirement**: AI agent response time shall be under 2,000 milliseconds at p95 under normal load conditions and under 5,000 milliseconds at p95 under peak load conditions.

**Rationale**: Supports G-2 (Customer Experience Transformation) — customers expect instant responses; supports G-5 (Platform Capability) — sub-2-second target per STKE goals. Aligns with PRIN Principle 11 (Performance and Efficiency).

**Measurement Method**: APM tooling tracking response time percentiles; distributed tracing with OpenTelemetry; monthly performance reports.

**Load Conditions**:

- Normal load: 10,000 concurrent users, 500 queries per minute
- Peak load: 50,000 concurrent users (Black Friday/Christmas), 2,000 queries per minute
- Burst capacity: 75,000 concurrent users for 30-minute periods

**Priority**: CRITICAL

**Traces To**: G-2, G-5, SD-6, SD-5

---

#### NFR-P-002: Throughput

**Requirement**: The system shall handle a minimum of 2,000 AI interactions per minute at peak load with sustained throughput of 500 interactions per minute under normal conditions.

**Rationale**: Supports G-5 (Platform Capability) and BR-005. Must scale to Black Friday and Christmas peak demand periods.

**Measurement Method**: Load testing at 1.5x peak capacity; production monitoring of throughput metrics; quarterly capacity reviews.

**Priority**: CRITICAL

**Traces To**: G-5, SD-2

---

#### NFR-P-003: Model Inference Latency

**Requirement**: AI model inference latency shall be under 1,500 milliseconds at p95, measured from token input to first token output.

**Rationale**: Direct component of NFR-P-001; ensures AI responses feel instantaneous to users. Aligns with PRIN Principle 11.

**Measurement Method**: Model serving layer metrics; latency breakdown (input processing, inference, output generation); per-model monitoring.

**Priority**: HIGH

**Traces To**: G-2, G-5

---

### Security Requirements

#### NFR-SEC-001: Authentication and Identity

**Requirement**: All AI agent interactions shall require authenticated user sessions via the existing MagicDelivery customer authentication system. Multi-factor authentication (MFA) shall be required for account settings changes and data access operations.

**Rationale**: Supports G-4 (Privacy Compliance) and BR-004. Aligns with PRIN Principle 4 (Security by Design) and APP compliance. Zero-trust architecture per PRIN Principle 4.

**Implementation**:

- Customer authentication: OAuth 2.0 / OpenID Connect via existing MagicDelivery identity provider
- MFA methods: Authenticator app, SMS, biometric (device-dependent)
- Session timeout: 15 minutes of inactivity; absolute timeout 24 hours
- Re-authentication required for: privacy settings changes, data export requests, data deletion

**Priority**: CRITICAL

**Traces To**: G-4, SD-8, SD-6

---

#### NFR-SEC-002: Authorization

**Requirement**: Role-based access control (RBAC) with least privilege principle shall govern all access to AI agent data, administrative functions, and model management.

**Rationale**: Supports G-4 (Privacy Compliance) and G-7 (AI Governance). Aligns with PRIN Principle 4 (Security by Design) zero-trust pillars.

**Roles and Permissions**:

- **Customer**: Access own data and AI interactions; manage own privacy settings
- **Call Centre Agent**: Access customer data for active queries; AI co-pilot usage
- **Administrator**: AI dashboard access, model management, threshold configuration
- **Compliance Officer**: Audit log access, DPIA data review, privacy complaint handling
- **Data Protection Officer**: Full data access for privacy requests, retention management

**Priority**: CRITICAL

**Traces To**: G-4, G-7, SD-8

---

#### NFR-SEC-003: Data Encryption

**Requirement**: All data shall be encrypted in transit and at rest using approved cryptographic standards.

**Implementation**:

- Data in transit: TLS 1.3 minimum with AEAD cipher suites
- Data at rest: AES-256 encryption for all data stores (databases, object storage, log storage)
- Key management: AWS KMS or equivalent with international-resident key management
- Application-level field encryption for PII: Customer names, addresses, phone numbers, email addresses

**Encryption Scope**:

- [x] Database encryption at rest
- [x] Backup encryption
- [x] File storage encryption
- [x] Application-level field encryption for PII

**Priority**: CRITICAL

**Traces To**: G-4, SD-8

---

#### NFR-SEC-004: Secrets Management

**Requirement**: No secrets (API keys, passwords, certificates, model API tokens) shall be stored in code repositories, configuration files, or environment variables accessible to application runtime.

**Implementation**:

- Secrets storage: HashiCorp Vault or AWS Secrets Manager
- Secrets rotation: Automatic rotation every 90 days
- Access logging: All secret access events logged with identity and timestamp
- Emergency access: Break-glass procedure with approval from CISO and Head of Digital Technology

**Priority**: CRITICAL

**Traces To**: G-4, SD-8

---

#### NFR-SEC-005: Vulnerability Management

**Requirement**: Comprehensive vulnerability management covering dependency scanning, static and dynamic application security testing, and regular penetration testing.

**Implementation**:

- Dependency scanning in CI/CD pipeline: No critical or high vulnerabilities permitted in production builds
- SAST: Automated static analysis on every code commit
- DAST: Dynamic testing against staging environment before each release
- Penetration testing: Quarterly by external accredited firm; results reported to CISO and Steering Committee

**Remediation SLA**:

- Critical vulnerabilities: 24 hours
- High vulnerabilities: 7 days
- Medium vulnerabilities: 30 days

**Priority**: CRITICAL

**Traces To**: G-4, G-7, SD-8

---

### Scalability Requirements

#### NFR-S-001: Horizontal Scaling

**Requirement**: The AI agent platform shall support horizontal scaling without code changes to accommodate demand growth.

**Growth Projections**:

- Year 1: 3 million monthly active users; 50,000 concurrent users peak; 25,000 AI interactions per day
- Year 2: 5 million monthly active users; 75,000 concurrent users peak; 50,000 AI interactions per day
- Year 3: 8 million monthly active users; 100,000 concurrent users peak; 100,000 AI interactions per day

**Scaling Triggers**: Auto-scale when CPU above 70% or memory above 80% for 5 consecutive minutes. Scale-out time target: under 3 minutes from trigger to new capacity available.

**Priority**: CRITICAL

**Traces To**: G-5, SD-2

---

#### NFR-S-002: Data Volume Scaling

**Requirement**: The system shall handle data growth to 50 terabytes over 3 years, including conversation logs, telemetry, audit trails, and model training data.

**Data Archival Strategy**:

- Hot storage (active data): Current 90 days; SSD-backed; low-latency access
- Warm storage (recent history): 91 days to 2 years; standard cloud storage; queryable
- Cold storage (archive): Beyond 2 years; low-cost object storage; retrieval within 24 hours

**Priority**: HIGH

**Traces To**: G-5, DR-006

---

### Availability and Resilience Requirements

#### NFR-A-001: Availability Target

**Requirement**: The AI agent platform shall achieve 99.95% availability during trading hours (06:00–23:00 AEST, Monday to Sunday) measured monthly.

**Maximum Downtime**:

- Planned maintenance: 4 hours per month during off-peak windows (02:00–06:00 AEST)
- Unplanned downtime: Maximum 26 minutes per month during trading hours
- Total monthly downtime: 30 minutes equivalent across all maintenance windows

**Maintenance Windows**: Sunday 02:00–06:00 AEST; announced 72 hours in advance

**Priority**: CRITICAL

**Traces To**: G-5, SD-2, SD-5

---

#### NFR-A-002: Disaster Recovery

**Requirement**: The system shall support rapid disaster recovery with defined RTO and RPO targets.

**RPO (Recovery Point Objective)**: Maximum acceptable data loss of 15 minutes

**RTO (Recovery Time Objective)**: Maximum acceptable downtime of 4 hours for full platform recovery; 30 minutes for critical AI agent services

**Backup Requirements**:

- Backup frequency: Continuous for transactional data; hourly snapshots for configuration
- Backup retention: 30 days hot, 12 months warm
- Geographic backup location: Secondary availability zone within international region (sydney-2)

**Failover Requirements**:

- Automatic failover to secondary availability zone: YES
- Failover time: Under 15 minutes
- Data consistency: Guaranteed via synchronous replication for critical stores

**Priority**: CRITICAL

**Traces To**: G-5, G-7

---

#### NFR-A-003: Fault Tolerance

**Requirement**: The system shall gracefully degrade when individual components fail, maintaining core AI agent functionality.

**Resilience Patterns Required**:

- [x] Circuit breaker for external dependencies (logistics API, CRM, SMS gateway)
- [x] Retry with exponential backoff (initial 1 second, max 30 seconds, 5 retries)
- [x] Timeout on all network calls (default 10 seconds, configurable)
- [x] Bulkhead isolation for critical resources (model serving, authentication, data access)
- [x] Graceful degradation: reduce to essential AI features when non-critical services are unavailable

**Priority**: CRITICAL

**Traces To**: G-5, SD-2

---

### Compliance Requirements

#### NFR-C-001: Privacy Act and APP Compliance

**Requirement**: All AI agent operations shall comply with the Privacy Act 1988 (Cth) and all 13 international Privacy Principles (APPs), with particular focus on APP 1 (open management), APP 3 (collection), APP 5 (notice), APP 8 (cross-border disclosure), APP 11 (security), APP 12 (access), and APP 11.2 (deletion).

**Applicable Regulations**: Privacy Act 1988 (Cth), international Privacy Principles, ACCC international Consumer Law

**Compliance Requirements**:

- [x] Data subject rights: Access (APP 12), correction, deletion (APP 11.2), export in machine-readable format
- [x] Consent management and audit trail: Explicit opt-in for personalisation; consent logged with timestamp
- [x] Privacy by design and by default: Architecture embeds privacy controls at each data collection point
- [x] Data breach notification: OAIC notification within 72 hours of breach identification; customer notification if personal information affected
- [x] Data protection impact assessment (DPIA): Completed for each AI feature before launch; registered in compliance system

**Data Residency**: All customer personal data stored and processed within international regions (AWS ap-southeast-2 or equivalent). No cross-border transfer of PII without explicit consent and APP 8 assessment.

**Data Retention**: AI interaction logs retained for 7 years for governance; personal identifiers removed after 2 years with anonymised interaction records retained for model improvement.

**Priority**: CRITICAL

**Traces To**: G-4, G-7, SD-8, SD-6

---

#### NFR-C-002: Audit Logging and Forensic Readiness

**Requirement**: Comprehensive audit trail for all AI agent interactions, administrative actions, and data access events, enabling compliance audits, incident investigation, and forensic analysis.

**Audit Log Contents** (for all sensitive operations):

- **Who**: User/service identity with authentication method
- **What**: Action performed with detailed description
- **When**: Timestamp (UTC, millisecond precision)
- **Where**: System component and geographic location
- **Why**: Request ID, transaction ID, conversation ID
- **Result**: Success/failure with error details

**Log Retention**: 7 years for compliance logs; immutable storage with cryptographic integrity verification (SHA-256 chained hashing)

**Log Integrity**: Tamper-evident logging; write-once storage; integrity verification available for audit

**Priority**: CRITICAL

**Traces To**: G-4, G-7, SD-8

---

#### NFR-C-003: ACCC Consumer Law Compliance

**Requirement**: AI agent responses shall comply with the Competition and Consumer Act 2010 and international Consumer Law, ensuring no misleading or deceptive conduct in AI-generated content.

**Compliance Controls**:

- [x] AI responses regarding fees, terms, and services validated against authoritative data before delivery
- [x] Clear disclosure that AI-generated content may not be fully accurate
- [x] No AI-generated content making claims about product quality, pricing guarantees, or legal rights without human verification
- [x] Post-response fact-checking for regulated topics (fees, legal terms, service promises)
- [x] Customer complaint handling within ACCC-mandated timeframes

**Priority**: CRITICAL

**Traces To**: G-4, G-7, SD-8

---

#### NFR-C-004: Fair Work Act Compliance

**Requirement**: AI agent deployment shall comply with the Fair Work Act 2009 (Cth) obligations regarding workforce impact, with zero net FTE reduction for 24 months post-launch per the Board-approved AI Augmentation Charter.

**Compliance Controls**:

- [x] Board-approved AI Augmentation Charter: Zero net FTE reduction commitment for 24 months
- [x] Union consultation: Quarterly consultation sessions with TWU and Fair Work Commission
- [x] Workforce impact monitoring: Monthly HRIS data reporting on FTE counts by role category
- [x] Upskilling investment: USD $1.8M training programme with clear career pathways
- [x] Transparent communication: Regular workforce updates on AI impact metrics

**Priority**: CRITICAL

**Traces To**: G-6, SD-7, SD-9

---

#### NFR-C-005: AI Governance Framework Compliance

**Requirement**: All customer-facing AI models shall be registered in the AI Governance Framework, with documented risk assessments, human oversight requirements, and model lifecycle management.

**Compliance Controls**:

- [x] AI model register: All deployed models registered with version, purpose, data sources, and risk rating
- [x] Model governance process: Pre-deployment review, post-deployment monitoring, periodic reassessment
- [x] Human oversight requirements: Defined for each model capability; escalation paths documented
- [x] Model transparency reporting: Algorithmic impact assessments for customer-facing models
- [x] Board-approved AI risk appetite statement: Published and referenced in governance framework

**Priority**: CRITICAL

**Traces To**: G-7, SD-8, SD-9

---

### Accessibility Requirements

#### NFR-U-001: WCAG Compliance

**Requirement**: All AI agent UI components within the MagicDelivery Mobile App shall comply with WCAG 2.1 Level AA standards.

**Accessibility Features**:

- [x] Keyboard navigation for all agent functions (where applicable in mobile context)
- [x] Screen reader compatibility (VoiceOver on iOS, TalkBack on Android)
- [x] High contrast mode support
- [x] Adjustable font sizes (minimum 200% scaling without loss of function)
- [x] Alt text for all visual elements in AI responses
- [x] Colour contrast ratio minimum 4.5:1 for text, 3:1 for UI components

**Testing**: Automated accessibility testing in CI/CD pipeline (axe-core); manual accessibility audit quarterly by specialist; user testing with accessibility advocacy groups.

**Priority**: CRITICAL

**Traces To**: G-2, SD-6

---

#### NFR-U-002: Mobile App Performance Standards

**Requirement**: AI agent integration shall not degrade overall MagicDelivery Mobile App performance standards.

**Performance Standards**:

- App crash-free session rate: Above 99.0%
- App Store rating: Maintain above 4.5 stars (iOS) and 4.3 stars (Android)
- App size increase due to AI features: Under 50 MB additional
- First contentful paint for AI screen: Under 1.5 seconds
- Background data usage: Under 50 MB per day of typical use

**Priority**: HIGH

**Traces To**: G-2, G-5, SD-5

---

#### NFR-U-003: UX Consistency

**Requirement**: AI agent interactions shall be consistent with existing MagicDelivery Mobile App design language, navigation patterns, and user experience standards.

**Implementation**:

- Design system compliance: All AI UI components use existing MagicDelivery design system
- Interaction patterns: Swipe, tap, and scroll gestures consistent with app conventions
- Visual identity: MagicDelivery brand colours, typography, and iconography
- Tone of voice: Friendly, professional, and consistent with existing brand voice

**Priority**: HIGH

**Traces To**: G-2, SD-6, SD-5

---

### Maintainability Requirements

#### NFR-M-001: Observability and Telemetry

**Requirement**: Comprehensive instrumentation for monitoring AI agent performance, model accuracy, and system health.

**Telemetry Requirements**:

- **Logging**: Structured JSON logs with correlation IDs; centralized log aggregation
- **Metrics**: RED metrics (Rate, Errors, Duration); AI-specific metrics (confidence distribution, escalation rates, hallucination rates); Prometheus-compatible
- **Tracing**: Distributed tracing with OpenTelemetry; full request flow from app to model to data store
- **Dashboards**: Real-time operational dashboards for key metrics
- **Alerts**: SLO-based alerting with actionable runbooks

**AI-Specific Metrics**:

- First-contact resolution rate
- Confidence score distribution (p10, p50, p90, p99)
- Escalation rate and average escalation time
- Customer satisfaction correlation with confidence scores
- Model accuracy trend (weekly)

**Priority**: CRITICAL

**Traces To**: G-5, G-7, SD-2

---

#### NFR-M-002: Documentation

**Requirement**: Comprehensive documentation for operators, developers, and compliance stakeholders.

**Documentation Types**:

- [x] Architecture documentation (C4 model: Context, Container, Component)
- [x] API documentation (OpenAPI 3.0 specifications for all agent interfaces)
- [x] Runbooks for operational procedures (deployment, rollback, scaling, incident response)
- [x] AI model documentation (training data provenance, version history, known limitations)
- [x] Privacy documentation (DPIA records, data flow diagrams, consent mechanisms)
- [x] Compliance documentation (audit reports, governance framework records)

**Documentation Currency**: Updated within 5 days of code changes or model updates

**Priority**: HIGH

**Traces To**: G-5, G-7, SD-2

---

#### NFR-M-003: Model Lifecycle Management

**Requirement**: AI models shall be managed through a defined lifecycle including versioning, evaluation, deployment, monitoring, and retirement processes.

**Lifecycle Stages**:

1. **Development**: Model training, fine-tuning, prompt engineering
2. **Evaluation**: Accuracy testing, bias assessment, hallucination testing, compliance review
3. **Staging**: Shadow deployment alongside production model; comparison analytics
4. **Production**: Gradual rollout with canary deployment (10% → 50% → 100% over 48 hours)
5. **Monitoring**: Continuous accuracy tracking, drift detection, customer feedback analysis
6. **Retirement**: Phased decommissioning with rollback capability; data archival

**Priority**: HIGH

**Traces To**: G-7, SD-2

---

#### NFR-M-004: AI-Specific Testing

**Requirement**: AI agent interactions shall undergo testing beyond conventional software testing, covering hallucination detection, bias assessment, and edge-case handling.

**Testing Types**:

- Hallucination testing: 1,000 adversarial queries against authoritative data sources
- Bias testing: Demographic and linguistic bias assessment across supported languages
- Adversarial testing: Prompt injection, jailbreak attempts, adversarial inputs
- Regression testing: Model update impact on existing query accuracy
- Red teaming: Quarterly AI red team exercises by independent assessor

**Priority**: HIGH

**Traces To**: G-7, G-2

---

---

## Integration Requirements

### INT-001: MagicDelivery E-Commerce Platform

**Purpose**: Access product catalogue, pricing, service options, and customer order history for AI shopping assistant and customer service queries.

**Integration Type**: Real-time API (REST/JSON)

**Data Exchanged**:

- **From AI Platform to E-Commerce Platform**: Customer ID, service queries, product search criteria
- **From E-Commerce Platform to AI Platform**: Product/service catalogue, pricing data, order history, promotional data

**Integration Pattern**: Request/response via REST API with OAuth 2.0 authentication; event-driven notifications for price changes and promotional updates

**Authentication**: OAuth 2.0 client credentials flow

**Error Handling**: Retry with exponential backoff (max 3 retries); circuit breaker after 5 consecutive failures; fallback to cached catalogue data (max 24-hour staleness)

**SLA**: 99.5% availability; p95 response time under 500ms

**Owner**: E-Commerce Platform Team (Digital Technology)

**Priority**: CRITICAL

**Traces To**: G-1, G-2

---

### INT-002: CRM / ERP System

**Purpose**: Access customer profiles, interaction history, service tickets, and account information for AI customer service and escalation workflows.

**Integration Type**: Real-time API (REST/JSON) + event-driven updates

**Data Exchanged**:

- **From AI Platform to CRM**: Query requests, customer ID, interaction results, escalation requests with context
- **From CRM to AI Platform**: Customer profile data, interaction history, service level agreements, account preferences

**Integration Pattern**: Synchronous REST API for profile lookups; event-driven (webhooks) for profile updates; bidirectional for escalation handoff

**Authentication**: Mutual TLS with client certificates

**Error Handling**: Retry with exponential backoff; dead letter queue for failed CRM updates; manual reconciliation within 24 hours

**SLA**: 99.9% availability; p95 response time under 300ms

**Owner**: CRM System Team (Digital Technology)

**Priority**: CRITICAL

**Traces To**: G-2, G-3, G-4

---

### INT-003: Logistics and Tracking System

**Purpose**: Access real-time parcel tracking data, scan events, ETA predictions, and delivery exceptions for AI parcel tracking agent and proactive notifications.

**Integration Type**: Real-time event stream + REST API

**Data Exchanged**:

- **From AI Platform to Logistics System**: Tracking number queries, event subscription requests
- **From Logistics System to AI Platform**: Real-time scan events, ETA predictions, delivery exceptions, route data

**Integration Pattern**: Event-driven via message broker (Kafka or equivalent) for real-time events; REST API for on-demand tracking queries; bidirectional for status updates

**Authentication**: API key with HMAC-SHA256 signature verification; rotating keys every 90 days

**Error Handling**: Dead letter queue for missed events; replay capability within 7 days; fallback to last-known status with staleness indicator

**SLA**: 99.9% availability for event stream; p95 event delivery latency under 30 seconds

**Owner**: Logistics Operations Team

**Priority**: CRITICAL

**Traces To**: G-2, G-1

---

### INT-004: SMS and Email Notification Services

**Purpose**: Deliver AI-triggered notifications, proactive alerts, and delivery confirmations via SMS and email channels.

**Integration Type**: Real-time API (REST/JSON)

**Data Exchanged**:

- **From AI Platform to Notification Services**: Notification payload (recipient, message, channel, priority), template references
- **From Notification Services to AI Platform**: Delivery confirmations, read receipts, bounce notifications

**Integration Pattern**: Request/response via REST API; asynchronous delivery confirmation callbacks

**Authentication**: API key with rate limiting (10,000 notifications per minute)

**Error Handling**: Retry failed deliveries (max 3 attempts); dead letter for undeliverable notifications; customer notified via app for failed push notifications

**SLA**: 99.5% availability; SMS delivery within 30 seconds; email delivery within 5 minutes

**Owner**: Communications Team (Digital Technology)

**Priority**: HIGH

**Traces To**: G-2, SD-6

---

### INT-005: Payment Gateway

**Purpose**: Process payments for AI-recommended shipping services within the app, including real-time pricing, payment processing, and receipt generation.

**Integration Type**: Real-time API (REST/JSON)

**Data Exchanged**:

- **From AI Platform to Payment Gateway**: Payment amount, customer ID, service reference, currency (USD)
- **From Payment Gateway to AI Platform**: Payment status, transaction ID, receipt data, refund status

**Integration Pattern**: Synchronous request/response for payment authorisation; event-driven for payment status updates and refunds

**Authentication**: PCI-DSS-compliant tokenisation; no raw card data transmitted through AI platform

**Error Handling**: Transaction retry on network timeout; customer notified of payment failure with retry option; refund processing within 5 business days

**SLA**: 99.9% availability; payment authorisation under 3 seconds

**Owner**: Finance / Payments Team

**Priority**: HIGH

**Traces To**: G-1, SD-1

---

### INT-006: Third-Party AI Model APIs

**Purpose**: Access large language model and AI inference capabilities for powering agent conversations, tracking predictions, and shopping recommendations.

**Integration Type**: Real-time API (REST/gRPC)

**Data Exchanged**:

- **From AI Platform to Model Provider**: Tokenised conversation data, prompt templates, system instructions (no raw PII in model API calls)
- **From Model Provider to AI Platform**: Generated responses, confidence scores, token usage metrics

**Integration Pattern**: Request/response via REST API; streaming responses for long-form outputs; multi-provider abstraction layer for failover

**Authentication**: API key with HMAC signing; mutual TLS for enterprise agreements

**Error Handling**: Automatic failover to secondary provider within 4 hours; graceful degradation to cached responses for non-critical queries; circuit breaker for sustained provider outage

**SLA**: Provider SLA minimum 99.5% availability; platform manages multi-provider failover to achieve 99.9% effective availability

**Owner**: AI Engineering Team (Digital Technology)

**Priority**: CRITICAL

**Traces To**: G-5, SD-2

---

### INT-007: Learning Management System (LMS)

**Purpose**: Deliver and track AI-augmented workflow training modules for operations staff; sync completion data, certifications, and confidence scores.

**Integration Type**: REST API (xAPI / LTI 1.3)

**Data Exchanged**:

- **From AI Platform to LMS**: Training module completions, assessment scores, certification records
- **From LMS to AI Platform**: Staff training status, module availability, certification expiry dates

**Integration Pattern**: Bidirectional REST API for training data sync; scheduled sync every 4 hours for non-urgent updates

**Authentication**: OAuth 2.0 client credentials

**Error Handling**: Retry with exponential backoff; queued updates delivered when connectivity restored; HRIS reconciliation monthly

**SLA**: 99.0% availability; training data sync within 4 hours

**Owner**: People & Culture / HR Team

**Priority**: SHOULD_HAVE

**Traces To**: G-6, SD-7

---

### INT-008: AI Governance and Compliance System

**Purpose**: Register AI models, record DPIA outcomes, track compliance audits, and maintain the AI Governance Framework register.

**Integration Type**: REST API + event-driven compliance events

**Data Exchanged**:

- **From AI Platform to Governance System**: Model deployments, accuracy metrics, incident reports, DPIA triggers
- **From Governance System to AI Platform**: Compliance status, model approval decisions, audit findings, policy updates

**Integration Pattern**: Event-driven compliance event publishing; REST API for governance queries; bidirectional for model approval workflow

**Authentication**: Mutual TLS with role-based access (Privacy Officer, CISO, Compliance Officer)

**Error Handling**: Compliance events persisted locally if governance system unavailable; synchronous delivery when system recovers; audit gap alerts if delivery exceeds 24 hours

**SLA**: 99.5% availability; compliance events delivered within 1 hour

**Owner**: Compliance/Legal Team

**Priority**: CRITICAL

**Traces To**: G-7, G-4, SD-8

---

## Data Requirements

### DR-001: Customer Profile Data Model

**Description**: Structured customer profile data supporting AI personalisation, authentication, and service delivery.

**Attributes**:

| Attribute | Type | Required | Description | Constraints |
|-----------|------|----------|-------------|-------------|
| customer_id | UUID | Yes | Unique customer identifier | Primary key; linked to CRM |
| full_name | String(255) | Yes | Customer legal name | Classified: RESTRICTED |
| email | String(255) | Yes | Primary contact email | Classified: RESTRICTED; indexed |
| phone_number | String(20) | No | Mobile phone number | Classified: RESTRICTED |
| address | JSON | Yes | Delivery addresses | Classified: RESTRICTED |
| preferences | JSON | No | Notification and personalisation preferences | Opt-in only |
| personalisation_opt_in | Boolean | No | Explicit consent for personalisation | Default: false |
| language_preference | String(10) | No | Preferred interaction language | Default: en-AU |
| created_at | Timestamp | Yes | Account creation date | Indexed |
| updated_at | Timestamp | Yes | Last profile update | Indexed |
| status | Enum | Yes | Account status | ['active', 'suspended', 'closed'] |

**Data Classification**: RESTRICTED (contains PII per Privacy Act 1988)

**Data Retention**: Active accounts indefinitely; closed accounts retained 7 years then permanently deleted per APP 11.2

**Data Residency**: Australia (AWS ap-southeast-2)

**Priority**: CRITICAL

**Traces To**: G-2, G-4, G-5

---

### DR-002: Transaction and Order History

**Description**: Historical shipping and e-commerce transaction data for AI recommendations, pattern analysis, and revenue attribution.

**Attributes**:

| Attribute | Type | Required | Description | Constraints |
|-----------|------|----------|-------------|-------------|
| transaction_id | UUID | Yes | Unique transaction identifier | Primary key |
| customer_id | UUID | Yes | Customer reference | Foreign key to DR-001 |
| service_type | Enum | Yes | Service category | ['standard', 'express', 'sameday', 'click_collect'] |
| amount | Decimal(10,2) | Yes | Transaction amount (USD) | Classified: CONFIDENTIAL |
| status | Enum | Yes | Transaction status | Indexed |
| created_at | Timestamp | Yes | Transaction date | Indexed |
| parcel_tracking_number | String(50) | No | Associated tracking number | Linked to DR-003 |

**Data Classification**: CONFIDENTIAL (financial data)

**Data Retention**: 7 years per corporate records policy; archived to cold storage after 2 years

**Data Residency**: Australia

**Priority**: CRITICAL

**Traces To**: G-1, G-2

---

### DR-003: Parcel and Shipping Data

**Description**: Real-time and historical parcel tracking data supporting AI parcel tracking agent and predictive analytics.

**Attributes**:

| Attribute | Type | Required | Description | Constraints |
|-----------|------|----------|-------------|-------------|
| tracking_number | String(50) | Yes | Unique parcel identifier | Primary key |
| customer_id | UUID | Yes | Customer reference | Foreign key to DR-001 |
| current_status | Enum | Yes | Current tracking status | Indexed |
| current_location | String(255) | No | Last known location | Classified: INTERNAL |
| predicted_eta | Timestamp | No | AI-predicted delivery time | Updated in real-time |
| actual_delivery | Timestamp | No | Actual delivery timestamp | — |
| scan_events | JSON Array | Yes | Chronological scan history | Appended only |
| exception_data | JSON | No | Delivery exception details | When applicable |

**Data Classification**: INTERNAL (operational data; location data is semi-sensitive)

**Data Retention**: 12 months hot; archived to cold storage for 3 years; then deleted

**Data Residency**: Australia

**Priority**: CRITICAL

**Traces To**: G-1, G-2

---

### DR-004: AI Interaction Logs

**Description**: Complete records of all AI agent interactions for analytics, compliance, model improvement, and audit purposes.

**Attributes**:

| Attribute | Type | Required | Description | Constraints |
|-----------|------|----------|-------------|-------------|
| interaction_id | UUID | Yes | Unique interaction identifier | Primary key |
| customer_id | UUID | Yes | Customer reference | Anonymised after 2 years |
| agent_type | Enum | Yes | Agent category | ['customer_service', 'tracking', 'shopping'] |
| conversation | JSON | Yes | Full conversation turns | Encrypted at rest |
| confidence_scores | JSON | Yes | Per-turn confidence | Encrypted at rest |
| outcome | Enum | Yes | Interaction result | ['resolved', 'escalated', 'abandoned'] |
| escalation_reason | String(500) | No | Reason for human handoff | When escalated |
| customer_rating | Integer | No | 1–5 post-interaction rating | — |
| timestamp | Timestamp | Yes | Interaction timestamp | Indexed |
| model_version | String(50) | Yes | AI model version used | For traceability |

**Data Classification**: RESTRICTED (contains conversation data with potential PII)

**Data Retention**: 7 years for governance; personal identifiers removed after 2 years; anonymised records retained for model improvement

**Data Residency**: Australia

**Priority**: CRITICAL

**Traces To**: G-4, G-7, G-2

---

### DR-005: AI Training Data and Governance Records

**Description**: Records of training data provenance, model version history, evaluation results, and governance approvals for AI model lifecycle management.

**Attributes**:

| Attribute | Type | Required | Description | Constraints |
|-----------|------|----------|-------------|-------------|
| model_id | UUID | Yes | Unique model identifier | Primary key |
| version | String(20) | Yes | Model version | SemVer format |
| training_data_source | String(255) | Yes | Training data provenance | Audit trail |
| evaluation_results | JSON | Yes | Accuracy, bias, hallucination metrics | Immutable |
| governance_status | Enum | Yes | Approval status | ['pending', 'approved', 'rejected'] |
| approved_by | UUID | Yes | Approver identity | Compliance Officer or CISO |
| approved_at | Timestamp | Yes | Approval timestamp | — |
| deployment_status | Enum | Yes | Deployment state | ['staging', 'production', 'retired'] |
| last_updated | Timestamp | Yes | Last model update | Indexed |

**Data Classification**: CONFIDENTIAL (contains proprietary model information)

**Data Retention**: Retained for life of model plus 3 years; governance records retained 7 years

**Data Residency**: Australia

**Priority**: CRITICAL

**Traces To**: G-7, SD-8

---

### DR-006: Data Governance and Classification

**Description**: Data classification and handling policies for all data processed by the AI platform, aligned with PRIN Principle 6 (Data as a Product) and Principle 7 (Data Sovereignty).

**Classification Tiers**:

| Tier | Scope | Handling Requirements | Examples |
|------|-------|------------------------|----------|
| PUBLIC | No restrictions | No encryption required | Service descriptions, public fee schedules |
| INTERNAL | Employee-only access | Standard encryption | Operational metrics, internal analytics |
| CONFIDENTIAL | Need-to-know basis | AES-256 encryption; access logging | Transaction data, model evaluation results |
| RESTRICTED | Highest controls | AES-256 + field-level encryption; MFA required | Customer PII, health-related delivery data |

**PII Handling Rules**:

- PII collection requires explicit consent per APP 3
- PII must not be transmitted to third-party AI model APIs (tokenised before transmission)
- PII field-level encryption via application layer
- Data minimisation: collect only data necessary for the specific AI function
- Right to access (APP 12): Customer can request all held data within 30 days
- Right to correction (APP 12): Errors corrected within 5 business days
- Right to deletion (APP 11.2): Deletion processed within 30 days; legal hold exceptions documented

**Data Lineage**: End-to-end lineage documented for all data flows; system of record identified per entity; derived copies labelled with sync frequency

**Priority**: CRITICAL

**Traces To**: G-4, G-7, SD-8

---

### DR-007: Analytics and Attribution Data

**Description**: Analytics data supporting revenue attribution, customer experience measurement, and benefits realisation tracking.

**Attributes**:

| Attribute | Type | Required | Description | Constraints |
|-----------|------|----------|-------------|-------------|
| analytics_event_id | UUID | Yes | Unique event identifier | Primary key |
| customer_id | UUID | Yes | Anonymised customer reference | Hashed; not reversable |
| event_type | Enum | Yes | Event category | ['page_view', 'agent_query', 'purchase', 'escalation'] |
| ai_attribution | Boolean | No | Whether event occurred in AI context | — |
| revenue_value | Decimal(10,2) | No | Associated revenue (USD) | When applicable |
| timestamp | Timestamp | Yes | Event timestamp | Indexed |
| channel | String(20) | Yes | Interaction channel | ['app', 'web', 'call_centre'] |

**Data Classification**: INTERNAL (anonymised analytics)

**Data Retention**: 3 years for trend analysis; aggregated data retained indefinitely

**Data Residency**: Australia

**Priority**: HIGH

**Traces To**: G-1, G-2

---

### DR-008: Model Telemetry and Performance Data

**Description**: Real-time telemetry data for AI model monitoring, including accuracy metrics, confidence distributions, and performance indicators.

**Attributes**:

| Attribute | Type | Required | Description | Constraints |
|-----------|------|----------|-------------|-------------|
| telemetry_id | UUID | Yes | Unique telemetry record | Primary key |
| model_id | UUID | Yes | Model reference | Foreign key to DR-005 |
| metric_type | Enum | Yes | Metric category | ['accuracy', 'latency', 'confidence', 'escalation_rate'] |
| metric_value | Decimal(10,6) | Yes | Measured value | — |
| percentile | Integer | No | Percentile rank (p50, p95, p99) | When applicable |
| timestamp | Timestamp | Yes | Measurement time | Indexed |
| environment | Enum | Yes | Deployment environment | ['staging', 'production'] |

**Data Classification**: INTERNAL

**Data Retention**: 1 year hot; aggregated monthly summaries retained 5 years

**Data Residency**: Australia

**Priority**: HIGH

**Traces To**: G-5, G-7

---

## Constraints and Assumptions

### Technical Constraints

**TC-1**: All AI model inference must occur within international regions (AWS ap-southeast-2 or equivalent); no PII transmitted to overseas model endpoints.

**TC-2**: The MagicDelivery Mobile App supports iOS 15+ and Android 12+; AI features must be compatible with these minimum versions.

**TC-3**: Integration with existing CRM and logistics systems must use published APIs; direct database access is prohibited per PRIN Principle 9 (Loose Coupling).

**TC-4**: AI agent platform must deploy to existing MagicDelivery cloud infrastructure; no standalone infrastructure purchases.

**TC-5**: The platform must support multi-provider AI model abstraction to prevent vendor lock-in per risk R-6 in STKE.

### Business Constraints

**BC-1**: Programme budget cap of USD $18.5M with maximum 10% variance.

**BC-2**: Zero net FTE reduction for 24 months post-launch per Board-approved AI Augmentation Charter.

**BC-3**: Go-live date constrained by peak trading season; Phase 1 must launch before November 2027 to capture Christmas trading period.

**BC-4**: All AI features require DPIA completion and Compliance/Legal sign-off before production launch.

**BC-5**: Currency for all financial metrics is USD; all pricing and revenue targets denominated in USD.

### Assumptions

**A-1**: Existing MagicDelivery customer authentication system supports OAuth 2.0 / OpenID Connect integration.

**A-2**: Logistics/tracking system provides real-time event stream with sub-60-second latency.

**A-3**: Third-party AI model providers offer international-region inference endpoints or acceptable cross-border arrangements.

**A-4**: Customer adoption of AI features exceeds 20% of monthly active users by Month 6.

**A-5**: Union consultation proceeds constructively with the Board-approved zero FTE reduction commitment.

**A-6**: OAIC engagement on AI-specific guidance occurs within 6 months and does not result in requirements that render the architecture unviable.

**A-7**: Existing CRM system supports API-based agent assignment with context injection for escalation workflows.

**Validation Plan**: Each assumption will be validated during the Architecture Decision phase (Months 1–3). Validation results documented in ADRs with contingency plans for invalidated assumptions.

---

## Success Criteria and KPIs

### Business Success Metrics

| Metric | Baseline | Target | Timeline | Measurement Method |
|--------|----------|--------|----------|-------------------|
| Incremental AI-attributed revenue (USD) | $0 | $25M annual run-rate | Month 18 | Revenue attribution analytics platform |
| NPS | 32 | 42 | Month 12 | Quarterly NPS surveys |
| CSAT (AI interactions) | 72% | 80%+ | Month 12 | Post-interaction surveys |
| Routine call deflection rate | 0% | 40% | Month 12 | Call volume analytics |
| Staff AI-confidence score | 3.0/10 | 6.5/10 | Month 18 | Quarterly confidence surveys |
| Privacy Act breaches | 0 | 0 | Continuous | Compliance audit reports |
| Budget variance | N/A | Under 10% | Programme end | Earned value management |

### Technical Success Metrics

| Metric | Target | Measurement Method |
|--------|--------|-------------------|
| Platform availability (trading hours) | 99.95% | Uptime monitoring |
| p95 response time | Under 2,000ms | APM tooling |
| AI first-contact resolution rate | Above 85% | Interaction analytics |
| Error rate | Under 0.5% | Log aggregation |
| MTTR | Under 30 minutes | Incident tracking |
| Model accuracy (routine queries) | Above 85% | Quarterly accuracy audits |
| Cost per AI interaction | Under USD $0.05 | FinOps dashboards |

### User Adoption Metrics

| Metric | Target | Timeline | Measurement Method |
|--------|--------|----------|-------------------|
| Monthly active AI feature users | 600,000 (20% of 3M MAU) | Month 6 | App analytics |
| Feature adoption rate | Above 20% of MAU | Month 6 | Usage analytics |
| Customer satisfaction (AI) | Above 80% | Month 6 | In-app surveys |
| Staff AI tool adoption | Above 60% of eligible staff | Month 12 | Co-pilot usage analytics |

---

## Dependencies and Risks

### Dependencies

| Dependency | Description | Owner | Target Date | Status | Impact if Delayed |
|------------|-------------|-------|-------------|--------|-------------------|
| D-001 | MagicDelivery customer authentication system API availability | Digital Technology | 2026-09-01 | On Track | HIGH — blocks all AI interactions |
| D-002 | Logistics/tracking real-time event stream | Logistics Operations | 2026-08-15 | On Track | HIGH — blocks parcel tracking agent |
| D-003 | AI model provider contracts executed | Procurement | 2026-07-31 | On Track | CRITICAL — blocks all AI capability |
| D-004 | CRM system API for escalation handoff | CRM System Team | 2026-09-15 | On Track | HIGH — blocks human escalation |
| D-005 | E-Commerce Platform API access | E-Commerce Platform | 2026-08-31 | On Track | MEDIUM — blocks shopping assistant |
| D-006 | Cloud infrastructure provisioning | Digital Technology | 2026-08-01 | On Track | CRITICAL — blocks all platform deployment |
| D-007 | LMS integration for training modules | HR / People & Culture | 2026-10-01 | On Track | MEDIUM — delays upskilling programme |
| D-008 | OAIC AI-specific guidance consultation | Compliance/Legal | 2026-09-30 | At Risk | HIGH — may alter architecture |

### Risks

| Risk ID | Description | Probability | Impact | Mitigation Strategy | Owner |
|---------|-------------|-------------|--------|---------------------|-------|
| R-001 | AI model accuracy below 85% for routine queries | MEDIUM | HIGH | Rigorous evaluation pipeline; staged rollout; confidence thresholding with human escalation | AI Engineering Team |
| R-002 | Third-party AI provider disruption | MEDIUM | HIGH | Multi-provider strategy; failover within 4 hours; on-premise model option for sensitive operations | Head of Digital Technology |
| R-003 | Privacy Act breach from AI data handling | LOW | CRITICAL | Privacy-by-design architecture; 100% DPIA completion; automated privacy controls | CISO / Privacy Officer |
| R-004 | Union opposition to AI implementation | MEDIUM | HIGH | Board-approved zero FTE reduction pledge; quarterly union consultation; co-design involvement | Head of People & Culture |
| R-005 | Budget overrun exceeding 10% variance | MEDIUM | HIGH | Earned value management; monthly budget review; scope change discipline | Programme Director |
| R-006 | Customer trust erosion from poor AI experience | MEDIUM | HIGH | Closed beta (5,000 users); rigorous UX testing; phased feature release | Head of Customer Experience |

---

## Requirement Conflicts & Resolutions

> **Purpose**: Document conflicting requirements that arise from competing stakeholder drivers and show how conflicts were resolved.
>
> **Source**: Conflicts derived from STKE conflict analysis (ARC-001-STKE-v1.0, Section: Conflict Analysis).
>
> **Principle**: Be transparent about trade-offs — don't hide conflicts or pretend both requirements can be fully satisfied.

### Conflict C-1: Speed of Delivery vs Thorough Compliance Testing (G-1 vs G-4)

**Conflicting Requirements**:

- **Requirement A**: BR-001 / FR-001 — Launch AI features rapidly to capture market window and generate early revenue evidence
- **Requirement B**: NFR-C-001 / FR-008 — 100% DPIA completion, legal review at each design gate, compliance sign-off before launch

**Stakeholders Involved**:

- **Executive Leadership / Parcel Business** (SD-9, SD-1): Wants rapid market entry to capture competitive advantage and demonstrate ROI within 6 months
- **Compliance/Legal** (SD-8): Requires thorough Privacy Act testing, DPIAs, and governance sign-offs that extend timelines

**Nature of Conflict**:

Rushing compliance reviews creates regulatory exposure with penalties up to USD $2.5M per breach and reputational damage. Thorough reviews delay market positioning, risking competitive disadvantage. The Executive scorecard demands speed while Compliance cannot legally approve shortcuts.

**Trade-off Analysis**:

| Option | Pros | Cons | Impact |
|--------|------|------|--------|
| **Option 1**: Prioritize Speed (Launch with limited compliance review) | Fast market entry; early revenue | Regulatory risk; potential OAIC penalties; rework | Executive happy; Compliance/Legal at risk |
| **Option 2**: Prioritize Compliance (Full reviews for all features before any launch) | Zero regulatory risk; defensible governance | Missed market window; delayed revenue; executive frustration | Compliance happy; Executive frustrated |
| **Option 3**: Parallel Compliance (Embed Compliance in delivery teams; phased compliance per feature) | Balanced; early features launch with sign-off; compliance continuous | Higher compliance resource cost; coordination complexity | Both partially satisfied |
| **Option 4**: Privacy-by-Design + Phased Rollout (Architect compliance in from start; release features incrementally with individual compliance sign-off) | Compliance built in; no post-hoc delays; features launch as ready | Upfront architecture cost; requires Compliance engagement from inception | Both satisfied with discipline |

**Resolution Strategy**: INNOVATE (Parallel Compliance + Privacy-by-Design)

**Decision**: Adopt Option 4 — embed Compliance/Legal in delivery teams from inception; privacy-by-design architecture eliminates post-hoc compliance burden; phased rollout allows features to launch independently as each passes compliance sign-off.

**Rationale**: Privacy-by-design architecture (PRIN Principle 4) removes the majority of compliance rework by building controls into the architecture. Embedding Compliance within delivery teams eliminates gate bottlenecks. Phased rollout provides early revenue evidence while maintaining compliance discipline.

**Decision Authority**: Programme Director with Steering Committee approval; compliance gate authority rests with Privacy Officer per RACI matrix (ARC-001-STKE-v1.0).

**Impact on Requirements**:

- **Modified**: NFR-C-001 — Compliance review is continuous and embedded, not a final gate
- **Modified**: BR-001 — Revenue target achievable through phased feature release starting Month 4
- **Added**: Compliance resource allocation within programme budget (dedicated Compliance engineer)

**Stakeholder Management**:

- **Executive Leadership**: Weekly progress updates on compliance sign-off status; early feature launches demonstrate speed
- **Compliance/Legal**: Budget allocated for embedded compliance resources; privacy-by-design reduces rework burden

---

### Conflict C-2: Cost Savings vs Feature Richness (G-3 vs G-1)

**Conflicting Requirements**:

- **Requirement A**: BR-003 / NFR-S-001 — Deliver operational efficiency within USD $18.5M budget with disciplined cost control
- **Requirement B**: BR-001 / FR-003 — Comprehensive AI feature set (customer service, tracking, shopping, personalisation, multi-language) requiring significant investment

**Stakeholders Involved**:

- **Executive Leadership** (SD-9): Wants cost optimisation; budget cap of USD $18.5M with 10% variance limit
- **Parcel Business** (SD-1): Wants comprehensive feature set differentiating customer experience and driving revenue

**Nature of Conflict**:

Feature breadth increases infrastructure, model, and development costs. Cost discipline limits capability investment. The Parcel Business GM needs differentiation to capture market share, but Executive Leadership requires investment ROI discipline.

**Trade-off Analysis**:

| Option | Pros | Cons | Impact |
|--------|------|------|--------|
| **Option 1**: Full Feature Set (No scope restrictions) | Maximum differentiation; full revenue potential | Likely budget overrun; investment credibility at risk | Parcel Business satisfied; Executive concerned |
| **Option 2**: Minimum Feature Set (Core tracking and FAQ only) | Budget certainty; focused delivery | Limited differentiation; lower revenue potential | Executive satisfied; Parcel Business disappointed |
| **Option 3**: Prioritised Phased Approach (Phase 1: core features; Phase 2: enhanced features funded by Phase 1 revenue) | Balanced; ROI-driven sequencing; budget discipline | Delayed comprehensive feature availability | Both satisfied with phased discipline |

**Resolution Strategy**: PHASE

**Decision**: Adopt Option 3 — Phase 1 launches with minimum viable AI capability set (parcel tracking, customer service FAQ agent) to generate early revenue evidence within budget. Phase 2 adds shopping assistant, personalisation, multi-language, and proactive features funded by demonstrated Phase 1 revenue. Feature prioritisation weighted 60% revenue impact, 30% implementation cost, 10% strategic alignment.

**Rationale**: Phased approach satisfies both stakeholders by delivering speed and differentiation (Parcel Business) while maintaining budget discipline (Executive). Revenue attribution from Phase 1 validates continued investment. Quarterly ROI review enables data-driven scope decisions.

**Decision Authority**: Executive Steering Committee; feature prioritisation by Product Owners with Parcel Business GM approval per RACI.

**Impact on Requirements**:

- **Modified**: FR-003 (Shopping Assistant) — deferred to Phase 2; classified as SHOULD_HAVE for Phase 1
- **Modified**: FR-006 (Multi-Language) — deferred to Phase 2; classified as SHOULD_HAVE
- **Modified**: BR-001 — USD $25M target achieved through Phase 1 (USD $12M by Month 12) plus Phase 2 (USD $13M by Month 18)

**Stakeholder Management**:

- **Parcel Business GM**: Weekly revenue attribution reporting; competitive positioning through early launch
- **Executive Leadership**: Monthly budget tracking; steering committee scope decisions

---

### Conflict C-3: AI Automation vs Workforce Protection (G-3 vs G-6)

**Conflicting Requirements**:

- **Requirement A**: BR-003 / FR-001 — 40% routine call deflection through AI, delivering USD $12M annual cost savings
- **Requirement B**: BR-006 / NFR-C-004 — Zero net FTE reduction; workforce augmentation model; upskilling investment

**Stakeholders Involved**:

- **Operations Staff / Union** (SD-7): Requires job security; AI as augmentation not replacement; upskilling investment
- **Parcel Business / Executive Leadership** (SD-1, SD-9): Need operational efficiency gains that could be interpreted as workforce reduction

**Nature of Conflict**:

AI achieves cost savings by replacing human labour with automation. The Fair Work Act and union relations require protecting jobs. Operational efficiency gains from AI deflection (40% routine call reduction) naturally raise questions about whether reduced workload justifies reduced headcount.

**Trade-off Analysis**:

| Option | Pros | Cons | Impact |
|--------|------|------|--------|
| **Option 1**: Cost savings via FTE reduction | Maximum cost savings; clear efficiency gains | Union opposition; potential industrial action; reputational damage | Operations unhappy; risk to programme |
| **Option 2**: Zero efficiency gains (preserve all roles) | Full workforce protection; no union issues | Programme loses cost-saving rationale; Executive loses ROI | Operations happy; Executive frustrated |
| **Option 3**: AI Augmentation Charter (Zero net FTE for 24 months; redeploy staff to high-value roles; invest in upskilling) | Balanced; staff focus improves; union satisfied | Requires USD $1.8M upskilling investment; redeployment complexity | Both satisfied with transparent commitment |

**Resolution Strategy**: COMPROMISE with Board-Approved Charter

**Decision**: Adopt Option 3 — Board-approved AI Augmentation Charter committing to zero net FTE reduction for 24 months post-launch. AI handles routine queries; redeployed staff focus on complex, high-value customer interactions. USD $1.8M upskilling investment positions workforce for enhanced roles. Union consultation programme with quarterly progress reports.

**Rationale**: The augmentation model is the only sustainable path — it preserves workforce trust and union relations while delivering genuine efficiency gains through improved staff productivity (fewer routine calls, more high-value interactions). The 24-month commitment provides stability during transition.

**Decision Authority**: CEO with Board approval; union consultation per Fair Work Act obligations.

**Impact on Requirements**:

- **Modified**: BR-003 — Cost savings achieved through productivity improvement (fewer calls, same staff), not headcount reduction
- **Modified**: FR-007 (Staff Co-Pilot) — designed for augmentation; staff approval required for all co-pilot outputs
- **Added**: NFR-C-004 — Fair Work Act compliance with monthly FTE monitoring

**Stakeholder Management**:

- **Operations Staff / Union**: Quarterly consultation sessions; transparent augmentation metrics; co-design involvement
- **Executive Leadership**: Cost savings through productivity gains documented; no industrial disruption

---

### Conflict C-4: Personalisation vs Privacy (G-2 vs G-4)

**Conflicting Requirements**:

- **Requirement A**: BR-002 / FR-005 — Personalised AI experiences driving customer engagement, higher conversion, and satisfaction
- **Requirement B**: BR-004 / NFR-C-001 — Data minimisation, explicit consent, transparent data handling per APP compliance

**Stakeholders Involved**:

- **Customers / Parcel Business** (SD-6, SD-1): Want personalised, proactive AI service that anticipates needs and drives engagement
- **Compliance/Legal** (SD-8): Requires data minimisation, explicit consent, and transparent data handling

**Nature of Conflict**:

Effective personalisation requires extensive data collection and behavioural analysis. APP compliance requires data minimisation and explicit consent. The tension: customers want personalisation but also want privacy; the more personalisation the AI provides, the more data it needs, increasing privacy risk.

**Trade-off Analysis**:

| Option | Pros | Cons | Impact |
|--------|------|------|--------|
| **Option 1**: Maximise personalisation (collect extensive data) | Best customer experience; higher revenue | Privacy risk; potential APP breach; customer trust erosion | Parcel Business happy; Compliance at risk |
| **Option 2**: Minimal data collection (no personalisation) | Maximum privacy protection; compliance certainty | Poor customer experience; lower engagement | Compliance happy; Customers disappointed |
| **Option 3**: Opt-in personalisation (explicit consent; tiered personalisation levels) | Balanced; customer control; compliance met | Some customers decline personalisation; lower engagement for those customers | Both satisfied with customer choice |

**Resolution Strategy**: COMPROMISE with Opt-In Design

**Decision**: Adopt Option 3 — privacy-by-design with explicit opt-in personalisation. Customers choose their personalisation level (basic tracking vs. proactive recommendations vs. full personalisation). All data collection points have clear privacy notices and control mechanisms. Design principle: minimum data needed for core service function, with progressive enhancement through opt-in features.

**Rationale**: Opt-in design satisfies both APP compliance (explicit consent per APP 3) and customer personalisation desires. Customers control their data through the privacy dashboard (FR-009). The default is minimum data collection, protecting privacy while offering enhanced personalisation for those who opt in.

**Decision Authority**: Privacy Officer approval of data collection design; Product Owner approval of personalisation feature design.

**Impact on Requirements**:

- **Modified**: FR-005 (Personalisation Engine) — requires explicit opt-in; default state is minimal personalisation
- **Modified**: FR-009 (Privacy Dashboard) — customer controls personalisation level; data usage transparency
- **Modified**: NFR-C-001 — personalisation data treated separately from core service data; separate consent per tier

**Stakeholder Management**:

- **Customers**: Transparent privacy notices; easy opt-in/opt-out; clear benefit communication
- **Compliance/Legal**: OAIC-engaged approach; privacy-by-design validated through DPIAs
- **Parcel Business**: Personalisation value demonstrated for opt-in cohort; engagement metrics tracked separately

---

## Timeline and Milestones

### High-Level Milestones

| Milestone | Description | Target Date | Dependencies |
|-----------|-------------|-------------|--------------|
| M-001 | Requirements Approval | 2026-07-31 | This document |
| M-002 | Architecture Design Complete | 2026-09-15 | M-001, D-001, D-003 |
| M-003 | AI Platform Infrastructure Live | 2026-10-31 | M-002, D-006 |
| M-004 | Phase 1 Features in Staging (Tracking, FAQ Agent) | 2026-12-15 | M-003, D-002, D-004 |
| M-005 | Phase 1 Production Launch (Closed Beta, 5,000 users) | 2027-02-28 | M-004, Compliance sign-off |
| M-006 | Phase 1 Full Customer Rollout | 2027-04-30 | M-005, performance validation |
| M-007 | Phase 2 Features in Staging (Shopping Assistant, Personalisation) | 2027-07-31 | M-006, D-005 |
| M-008 | Phase 2 Production Launch | 2027-10-01 | M-007, Compliance sign-off |
| M-009 | Multi-Language Support Launch | 2027-12-31 | M-008 |
| M-010 | Full Platform at 50,000 Concurrent Users | 2028-03-31 | M-009, capacity validation |

---

## Budget

### Cost Estimate (Phase 1)

| Category | Estimated Cost (USD) | Notes |
|----------|---------------------|-------|
| AI Engineering Team (FTEs) | $4,800,000 | 12 FTEs over 12 months |
| AI Model API Costs | $1,800,000 | Multi-provider; includes failover capacity |
| Cloud Infrastructure | $2,200,000 | Platform, compute, storage, data transfer |
| Mobile App Development | $1,500,000 | AI UI components, integration, testing |
| Compliance and Governance | $1,200,000 | DPIAs, legal review, audit, framework development |
| Testing and QA | $800,000 | AI-specific testing, load testing, security testing |
| Training Programme | $1,800,000 | 2,000 staff upskilling; curriculum and delivery |
| Project Management | $1,200,000 | Programme director, PMO, delivery coordination |
| Contingency (10%) | $1,530,000 | For approved scope changes |
| **Total** | **$16,830,000** | Within USD $18.5M budget cap |

### Ongoing Operational Costs (Annual)

| Category | Annual Cost (USD) | Notes |
|----------|------------------|-------|
| AI Model Inference | $2,400,000 | Based on 50,000 concurrent users; <USD $0.05 per interaction |
| Cloud Infrastructure | $1,800,000 | Compute, storage, data transfer, backups |
| Platform Operations | $600,000 | Monitoring, incident response, maintenance |
| Model Maintenance | $300,000 | Retraining, evaluation, governance |
| **Total** | **$5,100,000** | |

---

## Approval

### Requirements Review

| Reviewer | Role | Status | Date | Comments |
|----------|------|--------|------|----------|
| Parcel Business GM | Executive Sponsor | Pending | — | — |
| Head of Customer Experience | Product Owner | Pending | — | — |
| Head of Digital Technology | Enterprise Architect | Pending | — | — |
| CISO / Privacy Officer | Security and Compliance | Pending | — | — |
| Programme Director | Delivery Lead | Pending | — | — |

### Sign-Off

By signing below, stakeholders confirm that requirements are complete, understood, and approved to proceed to design phase.

| Stakeholder | Signature | Date |
|-------------|-----------|------|
| Parcel Business GM, Executive Sponsor | — | — |
| Head of Digital Technology, Enterprise Architect | — | — |
| CISO / Privacy Officer, Compliance Lead | — | — |
| Programme Director, Delivery Lead | — | — |
| Head of Customer Experience, Product Owner | — | — |

---

## Appendices

### Appendix A: Requirements Traceability Matrix

| Requirement ID | Goal | Driver | Outcome | Status |
|---------------|------|--------|---------|--------|
| BR-001 | G-1 | SD-1, SD-9 | O-1 | MUST_HAVE |
| BR-002 | G-2 | SD-6, SD-5 | O-2 | MUST_HAVE |
| BR-003 | G-3 | SD-7, SD-1 | O-3 | MUST_HAVE |
| BR-004 | G-4 | SD-8, SD-6 | O-4 | MUST_HAVE |
| BR-005 | G-5 | SD-2, SD-3 | O-5 | MUST_HAVE |
| BR-006 | G-6 | SD-7, SD-9 | O-3 | MUST_HAVE |
| BR-007 | G-7 | SD-8, SD-9 | O-4 | MUST_HAVE |
| BR-008 | G-8 | SD-3, SD-1 | O-6 | MUST_HAVE |
| FR-001 | G-2, G-3 | SD-6, SD-7 | O-2, O-3 | MUST_HAVE |
| FR-002 | G-2, G-1 | SD-6, SD-1 | O-2, O-1 | MUST_HAVE |
| FR-003 | G-1 | SD-1 | O-1 | MUST_HAVE |
| FR-004 | G-2, G-3 | SD-6, SD-7 | O-2, O-3 | MUST_HAVE |
| FR-005 | G-1, G-2 | SD-1, SD-6 | O-1, O-2 | MUST_HAVE |
| FR-006 | G-2 | SD-6 | O-2 | SHOULD_HAVE |
| FR-007 | G-3, G-6 | SD-7, SD-9 | O-3 | MUST_HAVE |
| FR-008 | G-4, G-7 | SD-8 | O-4 | MUST_HAVE |
| FR-009 | G-4 | SD-8, SD-6 | O-4 | MUST_HAVE |
| FR-010 | G-2 | SD-6 | O-2 | SHOULD_HAVE |
| FR-011 | G-2 | SD-6 | O-2 | SHOULD_HAVE |
| FR-012 | G-7 | SD-8, SD-2 | O-4 | MUST_HAVE |
| FR-013 | G-2 | SD-6 | O-2 | SHOULD_HAVE |
| FR-014 | G-2, G-1 | SD-6, SD-1 | O-2, O-1 | SHOULD_HAVE |
| FR-015 | G-6 | SD-7 | O-3 | SHOULD_HAVE |
| FR-016 | G-2, G-4 | SD-6, SD-8 | O-2, O-4 | MUST_HAVE |
| NFR-P-001 | G-2, G-5 | SD-6, SD-2 | O-2, O-5 | CRITICAL |
| NFR-P-002 | G-5 | SD-2 | O-5 | CRITICAL |
| NFR-P-003 | G-2, G-5 | SD-6, SD-2 | O-2, O-5 | HIGH |
| NFR-SEC-001 to 005 | G-4, G-7 | SD-8 | O-4 | CRITICAL |
| NFR-S-001 to 002 | G-5 | SD-2 | O-5 | CRITICAL/HIGH |
| NFR-A-001 to 003 | G-5 | SD-2, SD-5 | O-5 | CRITICAL |
| NFR-C-001 to 005 | G-4, G-7 | SD-8, SD-6 | O-4 | CRITICAL |
| NFR-U-001 to 003 | G-2 | SD-6, SD-5 | O-2 | CRITICAL/HIGH |
| NFR-M-001 to 004 | G-5, G-7 | SD-2, SD-8 | O-5, O-4 | CRITICAL/HIGH |
| INT-001 to 008 | G-1 to G-7 | SD-1 to SD-9 | O-1 to O-6 | Varies |
| DR-001 to 008 | G-1 to G-7 | SD-1 to SD-9 | O-1 to O-6 | Varies |

### Appendix B: Architecture Principle Alignment

| Requirement Category | PRIN Principle | Alignment Notes |
|---------------------|---------------|-----------------|
| All NFRs | Principle 1: Business Outcome Alignment | Every NFR traced to measurable business outcome (revenue, cost, satisfaction, compliance) |
| AI Platform NFRs | Principle 2: Composable Architecture | Platform designed as independently deployable components with published interfaces |
| FR-001 to FR-016 | Principle 3: AI-Augmented Operations | All AI agents expose agent-ready interfaces; decision logic externalised; human-in-the-loop escalation |
| NFR-SEC-001 to 005 | Principle 4: Security by Design | Zero-trust architecture; encryption everywhere; secrets management; vulnerability management |
| NFR-M-001 | Principle 5: Observability and Operational Excellence | Structured telemetry (logs, metrics, traces); SLO-based alerting |
| DR-006 | Principle 6: Data as a Product | Named data product owners; published data contracts; quality metrics |
| DR-001 to DR-008 | Principle 7: Data Sovereignty and Governance | international data residency; data classification; retention policies |
| NFR-S-001 to NFR-S-002 | Principle 11: Performance and Efficiency | Performance targets defined; load testing; capacity planning |
| NFR-A-001 to A-003 | Principle 12: Availability and Reliability | SLA targets; RTO/RPO; redundancy; failover testing |
| INT-001 to INT-008 | Principle 9: Loose Coupling | API-based integration; no shared databases; independent deployment |
| INT-003, INT-004 | Principle 10: Event-Driven Integration | Event stream for logistics; pub/sub for notifications |

### Appendix C: Glossary

| Term | Definition |
|------|-----------|
| AI Agent | Autonomous software system that performs tasks, makes decisions, and interacts with users through natural language |
| APP | international Privacy Principle — one of 13 principles under the Privacy Act 1988 |
| DPIA | Data Protection Impact Assessment — systematic process to identify and minimise privacy risks |
| FTE | Full-Time Equivalent — unit of measurement for workforce headcount |
| NPS | Net Promoter Score — customer loyalty metric (-100 to +100 scale) |
| CSAT | Customer Satisfaction Score — post-interaction satisfaction measurement |
| OAIC | Office of the international Information Commissioner — international privacy regulator |
| ACCC | international Competition and Consumer Commission — consumer protection regulator |
| p95 | 95th percentile — metric representing the value below which 95% of observations fall |
| SLA | Service Level Agreement — commitment to service performance standards |
| RTO | Recovery Time Objective — maximum acceptable downtime during disaster recovery |
| RPO | Recovery Point Objective — maximum acceptable data loss during disaster recovery |
| MTTR | Mean Time to Recovery — average time to restore service after an incident |
| LMS | Learning Management System — platform for delivering and tracking training |
| PII | Personally Identifiable Information — data that can identify an individual |
| RBAC | Role-Based Access Control — access management based on user roles |
| MoSCoW | Must have, Should have, Could have, Won't have — requirement prioritisation method |
| p95/p99 | 95th/99th percentile — performance metric representing upper-bound response times |

---

## External References

| Reference ID | Description | URL |
|-------------|-----------|-----|
| EXT-001 | Privacy Act 1988 (Cth) — international privacy legislation | https://www.legislation.gov.au/C2004A48252 |
| EXT-002 | international Privacy Principles (APPs) — 13 principles for personal information | https://www.oaic.gov.au/privacy/australian-privacy-principles |
| EXT-003 | OAIC AI and Privacy Guidance | https://www.oaic.gov.au/artificial-intelligence/ |
| EXT-004 | ACCC international Consumer Law — consumer protection obligations | https://www.accc.gov.au/consumer-data |
| EXT-005 | Fair Work Act 2009 (Cth) — industrial relations legislation | https://www.legislation.gov.au/C2009A00001 |
| EXT-006 | WCAG 2.1 AA Accessibility Guidelines | https://www.w3.org/WAI/WCAG21/quickref/ |
| EXT-007 | Competition and Consumer Act 2010 (Cth) — ACCC oversight | https://www.legislation.gov.au/C2010A00031 |

---

**Generated by**: ArcKit `/arckit:requirements` command
**Generated on**: 2026-07-01 00:00 GMT
**ArcKit Version**: 5.15.2
**Project**: 001 — AgenticEA: Agent AI Transformation
**AI Model**: Qwen3.6-27B
**Generation Context**: Requirements derived from ARC-001-STKE-v1.0 (9 stakeholder groups, 9 drivers, 8 goals, 6 outcomes, 4 conflicts) and ARC-000-PRIN-v2.0 (17 architecture principles). international regulatory context: Privacy Act 1988, APPs, ACCC, Fair Work Act.
