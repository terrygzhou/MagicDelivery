# Capability Framework: MagicDelivery AgenticEA

## Core Capability Domains

| Code | Capability | Sub-Capabilities |
|------|------------|------------------|
| CE | Customer Experience | Omni-channel enabling, CRM, customer service, digital engagement, self-service |
| PS | Product & Services | Product service innovation, product management, price management, service catalog, offer lifecycle |
| COM | Commerce | External integration, order management, e-commerce, marketplace, checkout |
| FUL | Fulfilment | Transport and logistics, distribution network, fulfilment, contractor partners, last-mile delivery |
| ISO | In-store Operations | Payment, finance and identity services, agency, retail, lockers |
| BM | Brand & Marketing | Content management, marketing management, brand management, customer segmentation, campaign optimization |
| DAI | Data & AI Services | AI services, analytics, machine learning, data platform, model governance |
| INT | Integration | API management, event streaming, microservices, service mesh, system integration |

## Capability Dependencies

```
CE → DAI, INT
PS → DAI, COM
COM → DAI, INT, FUL
FUL → INT, ISO
ISO → INT, DAI
BM → DAI, COM
DAI → INT
INT → (foundational)
```

## Agent Capability Mapping

| Agent Type | Primary Capabilities | Secondary Capabilities |
|------------|---------------------|------------------------|
| Customer Service Agents | CE, DAI | BM, INT |
| Shopping Assistant Agents | PS, COM | CE, DAI |
| Parcel Tracking Agents | FUL, CE | DAI, INT |
| Marketing Intelligence Agents | BM, DAI | COM, CE |
| Retail Support Agents | ISO, CE | FUL, DAI |
| Operations Agents | FUL, INT | DAI, COM |
| Analytics Agents | DAI | CE, BM, COM |
| Compliance Agents | INT, DAI | CE, ISO |
