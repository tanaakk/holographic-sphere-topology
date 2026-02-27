# 00_HST_Basic_Concepts_EN — Holographic Sphere Topology: Basic Concepts

**Translation from the canonical Japanese version** (`00_HST_Basic_Concepts.md`). The Japanese version is the authoritative source.

**Holographic Sphere Topology (HST)** is a new guideline and neologism proposed by TANAAKK for the AI era.

**Definition of this repository**: By following the rules of this repository, it outputs answers to queries about **how to organize the external and internal boundaries of business as a complex system**.

---

## Conclusion, Theme, and Proposition (Claim)

**All things, life, and systems can be defined, verified, and predicted solely by their boundaries (In/Out).** Without opening the interior, certification of purpose alignment is possible by inferring from types, contracts, and protocols on the boundary. Business can be wrapped into a black-box sphere of capital Input → net profit Output. System development is reduced to a **design problem of Objects and Morphisms**. The act of writing code is a fossil except for legacy maintenance.

This proposition will be proven in the future through the grounds and metaphors presented below.

---

## Grounds and Metaphors

### 1. Organ Metaphor: Separation of Frontend and Backend

### 1.1 The Liver = Database Principle

| Organ | System Equivalent | Role |
|-------|-------------------|------|
| **Liver** | Database (backend) | Metabolism, storage. Does not receive raw data directly |
| **Mouth, stomach, intestines** | Frontend, API layer | Chew and digest input, convert to **processable form** before passing to backend |

**Principle**: No one directly puts food into the liver. After processing by the frontend (mouth, stomach), data is passed to the backend only when it is in a **form that can be easily processed**.

### 1.2 The Fallacy of Modern ERP: The "Single Giant" Illusion

Traditional apps such as Oracle and SAP attempt to build **one large giant**.

- **Reality**: Business is composed of **10 or more organs**
- **Between organs**: Separated by **boundaries (holography)**
- **Problem**: Monolithic design lacking boundary definitions confuses organ roles and creates technical debt

### 1.3 The Slaughtered-Cow Fallacy: Toward a Combination of Lightweight Processing

**Every application should become a combination of lightweight processing.**

A common mistake in modern systems is **bringing a freshly slaughtered cow and trying to throw it whole into the mouth**.

| Stage | Processing | System Equivalent |
|-------|------------|-------------------|
| **Before entering mouth** | Contamination check, cooking, seasoning, cutting, plating | Classification, validation, format conversion in frontend |
| **After eating** | Chewing, saliva, stomach, pancreatic juice, intestinal digestion | Normalization and transformation in API layer, middleware |
| **Handoff** | To liver, kidneys | To backend (DB). Processed data only |

**If unclassified data flows from frontend to backend, it is natural that digestion takes time inside the body. Modern core systems are in this state.**

→ Decomposing each stage into **lightweight processing** and completing preprocessing before data enters the "mouth" is the design HST aims for.

---

### 2. Holographic Principle: Definition of Boundaries

### 2.1 https:// as Event Horizon

As software grows in mass and complexity, the `https://` boundary functions as an **event horizon**.

| Physical Metaphor | Software Reality | GAAS Implementation |
|-------------------|------------------|---------------------|
| **Inside black hole** | Server, Docker internals | Unobservable (abstracted). Executes automatically as singularity |
| **Event horizon (boundary)** | The only reality users touch | TypeScript types, SolidJS Signals, Tailwind class names |
| **Boundary vibration** | Reactive updates | SolidJS (Signals) |
| **Observation (access)** | Protocol | https:// (PWA) |

### 2.2 Organ = Object, Boundary = Morphism

| Concept | Mathematical Correspondence | Description |
|---------|----------------------------|-------------|
| **Organ** | Object | Liver, stomach, mouth… Each functional unit. 10+ independent modules |
| **Boundary** | Morphism | Interface between organs. Defined by types, contracts, protocols |
| **Information flow** | Arrow (morphism) | Mouth → stomach → intestines → liver. Raw data is transformed before crossing boundaries |

**Definition of holography**: Organs are separated by boundaries; **only information on the boundary surface is exchanged**. Internal implementation is unobservable (abstracted).

**All things and life are established at a boundary that is highly compressed and easy to decode.** 3D internal structure is compressed and encoded onto the boundary (2D); it can be decoded via queries from the boundary. The essence of things, life, and systems is condensed on the boundary surface.

To know what the Earth is like, no one digs into the ground and observes cores first—**looking at the surface is sufficient**. Observing the boundary (surface) allows understanding without digging into the interior. The same principle applies.

When getting to know someone romantically, no one asks for health check data first. One relies on **face, expression, and conversation**—boundary interaction. Understanding the other through In/Out on the boundary (expression, words) without opening internal data (blood tests, X-rays).

### 2.3 Boundary Violation Between Internal and External Systems: The Poison Principle

| Domain | Role Example | System Equivalent |
|--------|--------------|-------------------|
| **External system** | Heating, cooking, cutting | Frontend, API layer. Input preprocessing |
| **Internal system** | Metabolism, storage, absorption | Database, backend. Receives only processed data |

**Principle**: Trying to make the internal system do external tasks, or the external system do internal tasks, is **impossible** and yields **the same result as eating poison**.

| Violation Pattern | Example | Result |
|-------------------|---------|--------|
| Internal responsibility in external | Complex aggregation/join logic in UI | Performance collapse, consistency breakdown |
| External responsibility in internal | Input validation, format conversion in DB | Raw meat fed directly to liver. Poison |

Design that does not respect boundaries leads to **system destruction** in either direction.

### 2.4 Definition of Human: Computing Device with Externalized Storage

**Humans can be defined as computing devices with externalized storage.**

| Component | Role | Note |
|-----------|------|------|
| **Memory** | Used only for external interaction as CPU | Cannot store binary data |
| **Bones, muscles, brain** | Temporary media for processing | All replaced within weeks to months |
| **Storage** | Externalized | No persistent binary storage in the body |

The human "interior" has no persistent storage. Memory is used only for processing at the boundary (external interaction); it is not suited for binary data storage. Bones, muscles, and brain are all replaced within weeks to months. **Persistent information resides outside the boundary (external storage)**. This aligns with HST's principle that "information aggregates on the boundary."

**Whether to make the database part of the body is the same as evolutionary history.** Humans reduced nails, hair, and muscle mass—abandoning strength as storage—to maintain survival advantage by becoming a processor-based system. Similarly, the decision to use Shopify instead of building an EC site in-house, or to use serverless instead of owning servers, OS, and database, reflects the judgment that **using external black boxes causes entropy to converge more effectively than using internal black boxes**. Evolution toward processor specialization and the decision to delegate to external black boxes are isomorphic.

**For humans too, the history of past interactions can be referenced almost entirely through surface information—responses to queries.** Access to past interaction history is possible through boundary queries and responses alone, without opening the interior. This is isomorphic to Zero Knowledge Proof–type certification and In/Out verification.

---

### 3. Mathematization of System Development

### 3.1 Reduction to Objects and Morphisms

Under the above definitions, **system development is largely replaced by a mathematical problem of Objects and Morphisms**.

| Traditional Development | HST Development |
|------------------------|-----------------|
| Writing code | Defining Objects (organs) and designing Morphisms (boundaries) |
| Writing raw SQL | Describing boundaries via types (Drizzle). Internal state is uniquely determined |
| Locking down environment with Docker | Execution at boundary (edge). Containers unnecessary |
| Monolithic giant | Combination of 10+ organs. Each organ is self-contained |

### 3.2 The Role of Code Writing

**The act of writing code has become a fossil except for legacy maintenance.**

| Task | Role |
|------|------|
| **New development** | Object/Morphism design. Definition of types, contracts, boundaries. AI generates boundary code |
| **Legacy maintenance** | Fixing fossilized existing code. Paying down technical debt |
| **Engineer's essential role** | Inscribing information on boundaries. Guaranteeing correctness of Morphisms between organs |

**What matters for the engineer's role is understanding the landscape, organizing hierarchical relationships through ontology, and making topology explainable.** Explainability is synonymous with reproducibility and extensibility. Designing boundaries, Objects, and Morphisms is nothing other than constructing this explainable topology.

**Engineering has shifted from stacking bricks to creating substantial black boxes that integrate with the surrounding environment and return correct In/Out.** The essence lies not in internal implementation (how bricks are stacked) but in behavior at the boundary (integration with environment, correct In/Out).

The selection of **appropriate 3rd-party black boxes** as the internal structure of the system, so that enterprise Output is legitimate, is itself evidence that **engineers have been elevated to authority over the landscape**. Choices such as Shopify, serverless, Drizzle, and SolidJS are the design of the landscape itself.

**All specialists across domains that were previously separated in organizations—finance, sales, marketing, design, development, quality management, audit—will be classified by whether they hold root authority to observe the higher-level In/Out through this HST landscape, or not.**

### 3.2.1 Scope of Impact: Existing Infrastructure, Personnel, and Careers

HST theory clarifies **the scope of impact—what effects will occur on existing infrastructure, personnel, and careers**.

| Impact Area | Content |
|-------------|---------|
| **Existing infrastructure** | Monolithic giant-type systems, ERPs lacking boundaries, in-house DBs and servers become legacy. Migration toward organ separation, boundary design, and external black-box selection is required |
| **Personnel** | Reclassification by presence or absence of root authority. Value diverges between those capable of boundary design and Object/Morphism design, and those specialized in traditional internal implementation |
| **Careers** | Code-writing work becomes fossilized. Understanding the landscape, organizing ontology, and topology explainability become the central axis of careers. Advancement to positions with 3rd-party black-box selection authority becomes a new career path |

### 3.3 The Next Era: Black-Box Spherification of Business

**Every application should become a combination of lightweight processing.** The database, long a sanctuary, becomes serverless and **almost free—no longer a source of profit**.

What becomes important in the next era is possessing the following wisdom:

| Activity | Content |
|----------|---------|
| **Define boundaries** | Make interfaces between organs explicit via types and contracts |
| **Categorize and package Objects** | Organize functional units as independent modules |
| **Define as Morphisms** | Describe information exchange between different Objects as morphisms |
| **Optimize processing order** | Design the flow of lightweight processing combinations |

**Purpose**: To wrap the larger Object—**business**—into a simple black-box sphere of **capital Input** and **net profit Output**.

```
Capital (Input) → [ Object₁ ⟷ Object₂ ⟷ … ⟷ Objectₙ ] → Net Profit (Output)
                    ↑ Connected by Morphisms, order optimized
```

With correct design of internal Objects and Morphisms, the entire business is expressed as a **sphere observable only via Input/Output**. This is the abstraction of the business model HST aims for.

**In this context, the enterprise as a black box can be said to be a broader box composed of combined systems.** To judge whether the internal complexity of the enterprise black box is legitimate, verification is possible through In/Out alone without observing internal structure.

| Verification Level | In | Out | Question |
|--------------------|-----|-----|----------|
| **From outside** | Capital deployment | ROIC | Is the returned output correct? |
| **Internal systems** | What was invested | Operating cash flow | Does it flow out? |
| **Competitiveness** | — | Above output | Is it competitive? |

Whether capital invested in internal systems is output as operating cash flow, and whether that output is competitive—**verifiable through In/Out alone without observing internal structure.**

### 3.4 Acceptance of Black Boxes and Predictability Through Inference

What becomes important in the next era is possessing the wisdom to **not study the internal system**, **accept black boxes**, and **achieve predictability of results through inference**.

| Traditional Approach | HST Approach |
|---------------------|--------------|
| Open and understand the interior | Accept the black box |
| Depend on implementation details | Depend only on boundary (Input/Output) |
| Debug to trace causes | Infer to predict results |

The internal system is unobservable (abstracted). Result predictability is ensured by inferring from **types, contracts, and protocols on the boundary**, enabling control from outside without opening the interior.

### 3.5 Zero Knowledge Proof–Type Certification

Whether the black-boxed sphere interior aligns with its purpose can be **entirely defined by In and Out at the boundary**. This is **Zero Knowledge Proof–type certification**.

| Traditional Certification | HST Certification |
|-------------------------|-------------------|
| Inspect interior to confirm compliance | Certify compliance only via types and contracts of boundary Input/Output |
| Implementation disclosure and audit required | Prove without opening interior, via In/Out consistency only |

Without knowing internal implementation, **In and Out at the boundary satisfying the specification** certifies that the sphere aligns with its purpose. Verifiable from outside while preserving internal secrets.

**When expected Out does not result from In, the Input data is wrong in most cases.** Every system outputs according to some rule. When unexpected Out is obtained, first suspect In at the boundary (type, format, value of input data). Verify correctness of In before suspecting bugs in the internal system.

---

### 4. Correspondence with GAAS Standard Stack

| Domain | HST Position |
|--------|--------------|
| **SolidJS (Signals)** | Boundary vibration. Partial changes do not propagate to whole |
| **Tailwind CSS v4** | Surface pattern. Boundary description complete within HTML |
| **Drizzle ORM** | Boundary via types. Govern via types, not raw SQL |
| **SQLite (LibSQL)** | Liver (DB). Single file, complete. Serverless/edge, fast |
| **Bun** | Singularity. Executes automatically in background. No Docker |
| **https:// (PWA)** | Event horizon. Single URL delivers to all devices |

---

## Detailed Expansion of the Proposition (Conclusion Checklist)

0. **Definition of this repository**: By following the rules of this repository, it outputs answers to queries about how to organize the external and internal boundaries of business as a complex system
1. **Organ metaphor**: Business is composed of 10+ organs; organs are separated by boundaries
2. **Slaughtered-cow fallacy**: Complete preprocessing before putting in mouth, not throwing in whole. Apps become combinations of lightweight processing
3. **DB commoditization**: The long-sanctified database becomes serverless; almost free, no longer profitable
4. **Holographic principle**: Only information on the boundary is exchanged. Interior unobservable. All things and life are established at a highly compressed, easily decodable boundary
5. **Definition of human**: Computing device with externalized storage. Memory used only for external interaction; bones, muscles, brain replaced in weeks to months. Past interaction history can be referenced almost entirely via surface information of query responses
6. **Evolution and external black boxes**: Isomorphic to evolution reducing nails, hair, muscle for processor specialization. Using Shopify, serverless instead of owning DB—external black boxes converge entropy more
7. **Poison principle**: Reversing responsibilities of internal and external systems is impossible; same result as eating poison
8. **Mathematization**: Development is reduced to a design problem of Objects and Morphisms
9. **Business black-box sphere**: Design boundaries, Objects, Morphisms; optimize processing order; wrap business into a simple sphere of capital Input → net profit Output
10. **Enterprise black box**: Enterprise is a broader box of combined systems. Legitimacy of internal complexity verifiable via ROIC, operating CF, Competitive In/Out
11. **Acceptance of black boxes**: Do not study internal system; accept black boxes; achieve predictability through inference
12. **Zero Knowledge Proof–type certification**: Whether sphere interior aligns with purpose is defined by boundary In and Out. Certifiable without opening interior
13. **In-first verification**: When expected Out does not appear, Input data is wrong in most cases. Every system outputs by some rule
14. **Engineer's role**: Understand landscape; organize hierarchical relationships via ontology; make topology explainable. Selection of appropriate 3rd-party black boxes elevates engineers to authority over the landscape
15. **Specialist reclassification**: Specialists in finance, sales, marketing, design, development, quality management, and audit are classified by presence or absence of root authority to observe higher-level In/Out through the HST landscape
16. **Scope of impact**: Impact on existing infrastructure (legacy, migration), personnel (reclassification by root authority), and careers (landscape understanding and black-box selection authority as central axis) is clarified
17. **Engineering shift**: Not stacking bricks but creating substantial black boxes that integrate with environment and return correct In/Out
18. **Role of code**: In new development, boundary description is primary. "Writing code" is a fossil except for legacy maintenance

---

## Revision History

| Date | Changes |
|------|---------|
| 2026-02-27 | English translation created from canonical Japanese (00_HST_Basic_Concepts.md) |
| 2026-02-27 | Conclusion, theme, proposition placed at top; restructured as grounds and metaphors (thesis-first) |
| 2026-02-27 | 3.2.1 Scope of impact (existing infrastructure, personnel, careers) added |
| 2026-02-27 | Definition of this repository (outputs answers to queries about organizing external/internal boundaries of business as complex system) added |
