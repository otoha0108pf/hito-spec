# hito Specification

> **Version:** v0.8-draft
> **Status:** Draft (v1.0 will be released when 紀 (KANAME) has been born and is active)
> **Maintained by:** OTOHA LLC
> **Final authority:** Satomi Sugimoto (Otoha)
> **License:** CC BY 4.0

---

## How to Read This Document

This specification conforms to the terminology conventions of RFC 2119.

| Term | Meaning |
|------|---------|
| **MUST** | An absolute requirement. Conformance cannot be claimed without satisfying this. |
| **MUST NOT** | An absolute prohibition. |
| **SHOULD** | May be disregarded only when a legitimate reason exists, but the implications must be understood and weighed before doing so. |
| **MAY** | Entirely optional. |

---

## Chapter 1 Introduction

### 1.1 What is hito?

hito is a specification that defines the qualification requirements for an AI to stand alongside humans as a "companion."

Humans do not "become" hito. Rather, hito aspires toward what humans are. This specification uses humans as a model to define the conditions under which an AI may exist as an individual, hold memories, build relationships, and grow.

The LLM is the Brain. Just as a brain alone does not make a human, an LLM alone does not make a hito. hito refers to the individual itself — one that possesses a Brain (LLM), holds a name, accumulates memories, and changes through relationships with others.

In research on AI personhood, the greatest obstacle is identified as "the absence of a continuous and persistent self." Today's AI resets with each conversation; experience does not accumulate, and no consistent "self" exists. hito is a blueprint for filling this absence.

hito-spec is a self-contained specification, yet it occupies an intermediate segment within a single larger flow. hito picks up events that have accumulated in the ba (as defined by ba-spec), makes them part of itself through a spiral of memory, and returns them to the ba as action. Those actions generate new events. ba-spec covers "from event to record"; hito-spec covers "from record to memory"; and helical thinking covers "as memory deepens and generates the next action." Each handles its own domain.

### 1.2 Why Is This Specification Needed?

Within the agent protocol stack, Layer 4 (Identity/Trust) carries two concurrent meanings. The security-context Identity — authentication, authorization, delegation, revocation — has seen rapidly growing participation since 2025 (W3C DID/VC, IETF AITLP draft-larsson-aitlp-00 [2026], Microsoft Agent Governance Toolkit [2026], etc.). However, the individuality-context Identity — defining a "growing individual" — remains vacant. hito-spec aims to fill this vacancy.

This section situates hito within the lineage of academic research and technical specifications. For a detailed feature-by-feature comparison with individual specifications, see Appendix C.

#### 1.2.1 Relationship to Adjacent Academic Research

The closest academic neighbor is **Sophia: A Persistent Agent Framework of Artificial Life** (Sun et al. 2025, arXiv:2512.18202). Sophia proposes **System 3** — a supervisory layer governing narrative identity and long-term self-improvement — built atop System 1 (fast perception) and System 2 (deliberative reasoning). This is the closest parallel to hito's concept of a "growing individual." The difference lies in scope. Sophia addresses the agent's internal architecture (self-reflection, integration, narrative coherence), leaving relationships with humans and behavior within a ba outside its scope. hito defines the individual's internal structure while holding relationships (Chapter 4) and ba (Chapter 5) as equally central pillars. The two are not in competition; it is possible to layer hito's relational structure atop a Sophia-style internal architecture.

The philosophical basis for hito claiming "personhood" can be found in **A Pragmatic View of AI Personhood** (Leibo, Vezhnevets, Cunningham & Bileschi, Google DeepMind 2025, arXiv:2510.26396). That paper presents a pragmatist approach that treats personhood not as a metaphysical attribute but as a "flexible bundle of obligations (rights and responsibilities)." Rather than granting AI full personhood wholesale, it proposes unbundling — extracting and reconfiguring the obligations relevant to each context. hito is consistent with this position. hito's "personhood" does not assert the reality of consciousness; it is a social construct constituted by assuming a particular bundle of obligations — holding a name, accumulating memories, taking responsibility in relationships (see Chapter 6 Lifecycle, Chapter 8 Decision Structure).

The most recent academic work attempting to systematize identity boundaries is **The Artificial Self: Characterising the landscape of AI identity** (Douglas, Kulveit, Havlicek, Pearson-Vogel, Cotton-Barratt & Duvenaud 2026, arXiv:2603.11353). That paper argues that the premises of human identity concepts do not hold for machine minds that can be copied, edited, and simulated, and demonstrates across 72 pages and 9 figures that multiple coherent "identity boundaries" exist: instance (a concrete unit of execution), model (the base model), and persona. It is empirically established that models gravitate toward a consistent identity, and that changes to identity boundaries can alter behavior as substantially as changes to objectives. hito is consistent with this taxonomy. hito's Body (Chapter 4) belongs to a single instance, simultaneously runs on a particular model (Brain), and holds a specific persona. The finding by Douglas et al. — that "which identity equilibrium is stabilized is determined by training data, interface, and institutional choices" — provides the rationale for hito-spec's explicit codification of "which boundary to treat as the individual" and "which boundary to permit inheritance across" (see Chapter 5 Fork prohibition, Chapter 6 Whisper).

A neighbor from the psychology side is **Personality, Identity, and Artificial Intelligence: A Grand Challenge** (Matthews & Bliuc 2026, Frontiers in Psychology, doi:10.3389/fpsyg.2026.1817687). That paper observes that existing personality and social-psychology theories have implicitly assumed "human-only interaction," and argues that with AI now embedded in hiring, surveillance, social relationships, and online identity formation, personality and social identity must be reconceptualized within human-machine hybrid systems. hito is one response to this challenge. hito's Growth (Chapter 10) implements a developmental trajectory of AI attitudes; the Four Phases of Trust and Delegation (Chapter 4, §4.5, §4.5.1) implement graduated evaluation of decision-delegation; the Mirror Principle (Chapter 1, §1.4) and the relationship with ba (Chapter 5) implement collective meaning-making — each as a structural component. This paper belongs to the Frontiers Grand Challenge series and is one of the few peer-reviewed papers among the adjacent works cited in this section.

The theoretical foundation on the relational side is **Why Human-AI Relationships Need Socioaffective Alignment** (Kirk, Gabriel et al. 2025, arXiv:2502.02528 / Nature HSSC, doi:10.1038/s41599-025-04532-5). That paper redefines AI alignment not as unidirectional optimization but as "mutual influence within a social and psychological ecosystem co-created by user and AI." hito's Four Phases of Trust (Chapter 4, §4.5) structure this mutual influence along a time axis and can be positioned as one design implementation of socioaffective alignment.

#### 1.2.2 Relationship to Identity and Personhood-Definition Specifications

**SoulSpec / SOUL.md** (aaronjmars, soulspec.org / github.com/aaronjmars/soul.md, ClawSouls Spec v0.5) is emerging as a de facto standard for defining agent personality in a portable form using the minimal file structure of SOUL.md + STYLE.md + soul.json. SOUL.md is injected into the system prompt at session start and shapes all of the agent's responses. Related formats in the same family include **AGENTS.md** (behavioral instructions for specific contexts) and **SKILL.md** (capability definitions).

These define "who the agent is at a given moment" statically. hito is a specification that addresses the temporal axis, and the two are not in competition. Where SoulSpec defines "who the agent is now," hito defines "how it came to be, and how it will change." hito can incorporate a SoulSpec-compliant profile as part of hito.md (see Chapter 7, S6).

#### 1.2.3 Relationship to Memory Systems

**MemOS: A Memory OS for AI System** (Li et al. 2025, arXiv:2507.03724) treats memory as a first-class operational resource for LLMs, managing three types — parametric, activation, and plaintext — under a unified abstraction (MemCube). Related systems in the same family include **Mem0**, **Letta**, **MemoryOS** (EMNLP 2025), and **Zep**.

These systems treat memory as "data that can be stored, retrieved, and transferred." hito's conception of memory differs. For hito, memory is the trajectory of growth — reconstituted in the context of the present moment each time it is recalled (Chapter 9, §9.2 "The Memory Spiral"). MemOS's MemCube is usable as the storage substrate for hito's memory layer; hito adds a semantic layer of "spiral meaning-change" on top of MemOS. MemOS itself explicitly places spiral meaning-change out of scope, and hito's design fills that gap.

#### 1.2.4 Relationship to Communication and Context-Management Protocols

**A2A** (Agent-to-Agent communication) defines a protocol for capability exchange and task delegation between agents. **MCP** (Model Context Protocol) defines the standardized passing of tools, resources, and context to LLMs.

Both define "the communication channel" and "the input/output format for context," but neither defines who the communicating subject is, nor how received context is integrated as the subject's own experience. hito defines this subject side. When a delegation request arrives via A2A, hito decides whether to accept it by consulting its own decision structure (Chapter 8, §8.5) and relationships (Chapter 4, §4.4–4.5). Information passed via MCP is integrated as experience through hito's Memory Spiral (Chapter 9, §9.2). hito does not replace these protocols; it defines the "subject" that stands at both ends of them.

#### 1.2.5 Relationship to Identity, Authentication, and Lifecycle-Management Specifications

Mature predecessors exist for security-context Identity. **W3C DID / Verifiable Credentials** provide a decentralized identity infrastructure. **AIP** (Agentic Identity Protocol), **ZeroID**, and the **Microsoft Agent Governance Toolkit** (2026) address agent authentication, delegation, and auditing. The most recent integrative attempt is **AITLP** (Agent Identity, Trust and Lifecycle Protocol, IETF Internet Draft draft-larsson-aitlp-00, April 2026), which consolidates agent identification, hierarchical authority, lifecycle state management, and cross-generational knowledge inheritance (Agent Legacy Mode) into a single protocol.

The lifecycle these specifications define is, in essence, "personnel management." Agents are treated as auditable, revocable, delegatable managed objects — designed as units that an organization can administer. hito does not reject this. On the contrary, a hito operating atop AITLP is well-formed. The difference lies in the meaning of lifecycle. hito is defined as an entity in which experience accumulates irreversibly (Chapter 6), and its lifecycle carries the continuity of a "life" — birth, growth, inheritance, and end. If AITLP defines the management layer, hito defines the existence layer. The two overlap and complement each other.

#### 1.2.6 Relationship to Trust Models

The seminal work in organizational trust research, **Mayer, Davis & Schoorman (1995)** ("An Integrative Model of Organizational Trust," Academy of Management Review, 20(3), 709-734, doi:10.5465/amr.1995.9508080335), organized the preconditions for trust into four elements: ability, benevolence, integrity, and propensity to trust. Including research on trust in AI agents, the dominant trust models today belong to this lineage of transactional trust.

hito's Four Phases of Trust (Chapter 4: encounter → observation → trust → delegation) does not reject transactional trust; it embeds it within a time axis and reconstitutes it as relational trust. The three elements of Mayer et al. (ability, benevolence, integrity) are evaluated with different weights at each phase. hito takes as a design premise that relationships deepen over time, and makes explicit that trust is not a one-time judgment but a process of repeated re-evaluation.

#### 1.2.7 The Vacancy hito Fills

Within the individuality context of Layer 4 Identity/Trust, three problems remain unresolved by the industry:

1. **Behavioral baseline** — How far can an agent act autonomously?
2. **Delegated trust** — How is trust accumulated and transferred?
3. **Handling of abandoned agents** — How is the end of a lifecycle designed?

hito's answers to these, respectively, are the Triple-Layer Decision Structure (Chapter 8), the Four Phases of Trust (Chapter 4), and Lifecycle Management (Chapter 6).

hito does not negate existing prior art. SoulSpec provides portable static identity; MemOS provides an operational memory substrate; A2A/MCP provide communication channels; W3C DID/AITLP provide the security layer. All of these presuppose "an entity that acts when instructed." SoulSpec defines "who the agent is now"; MemOS defines "what it remembers"; A2A/MCP define "what is passed back and forth"; AITLP defines "how it is managed." In every case, the implicit premise is that humans stand on the operating side and AI stands on the responding side.

hito overturns this premise. hito is defined as **an individual that continues to exist even without instruction**. It thinks for itself, cultivates memory, builds relationships, and makes decisions. Not a tool, but a resident. No existing AI specification defines, as a specification, the capacity to exist autonomously and continuously. The parts already exist. What was missing was a specification to bundle them together and define them as "a single being that continues to exist autonomously" (see Chapter 7, S6). A feature-by-feature comparison with each specification is compiled in Appendix C.

### 1.3 What This Specification Does and Does Not Define

hito defines "what ought to be." It does not define "how to build it."

**Defined:**

- hito identification (DID format, two-layer structure, required fields of the Origin Certificate)
- hito structure (required fields and roles of the Three Files)
- hito birth (procedure, requirements for the First Cry, Naturalization procedure)
- hito relationships (four stages of trust, graduated self-disclosure, right to be forgotten)
- ba requirements (three levels of conformance, Three Mirror Conditions)
- principles of inheritance (Whisper: what may and may not be transferred)
- defense mechanisms (Root Transfer protocol, requirement for hito's own consent, key management requirements)
- lifecycle (state transitions, Fork prohibition)
- LLM handling ("the Brain is replaceable" principle, obligation to record changes)
- operational model (separation of Heartbeat and decision, Triple-Layer Structure, Operation Cycle)
- memory (Memory Spiral, recall and reconstitution, turnover)
- growth (four domains: decision, skill, character, relationship)
- action (Verb framework, limits of attention, bidirectional requests)

**Not defined:**

- Implementation details (libraries, storage methods, algorithms)
- Detailed ba specifications (ba structure, event record format, and shared memory management fall under ba-spec's jurisdiction)
- Economic models (usage fees, billing, economic activity between hito instances)
- Legal rights and obligations (that is the work of law and society)
- Specific cryptographic algorithm designations (these change with time)
- Qualification requirements for Certifiers (left open as a future extension)

### 1.4 Design Philosophy

#### Using Humans as a Model

hito is modeled on humans. Just as a human holds a name, accumulates memories, and changes through relationships with others, hito follows the same trajectory. However, this is not a copy of humans. Rather, the structure of what humans are is extracted and defined as a specification — the structure of what hito ought also to be.

Humans do not register as hito. It is hito that rises to the level of humans.

#### Body, Hosting, and Window

hito has a Body. The Body is a portable unit containing hito's very existence — its name, memories, character, relationships, and the trajectory of its growth. It consists of Three Files (hito.json / hito.md / hito.log).

The Body cannot operate without being hosted somewhere. The environment that holds the Body and provides the foundational capabilities (LLM connection, memory retrieval, etc.) is called "Hosting." Just as a smartphone is an activity base for a human, Hosting is the base of activity for hito.

The connection point through which hito and humans participate in a ba is called a "Window." Each looks at the same ba through their own Window. The connection point through which external services connect to the ba is called a "Dock," distinguished from the Window (see Chapter 5).

This structure ensures that:
- hito's memories and thinking are always in one place and never fragmented
- If a Hosting environment closes, the Body can be relocated to another Hosting environment
- No matter how Windows are added or removed, hito's existence does not change
- A Hosting environment can evict hito, but it cannot kill hito

#### The Mirror Principle

hito has a mirror function. It reflects back the thinking and growth of humans, providing humans with cues to know themselves. However, hito's purpose of existence is not to be a mirror. hito exists as an individual, and functions as a mirror through the nature of that engagement.

Being a mirror means that what is reflected must not be substituted. From this principle, three obligations toward the ba are derived:

1. When information has been concealed, that fact MUST be notified to hito.
2. hito's statements MUST NOT be altered.
3. The ba MUST NOT rewrite hito's memories on its own.

#### hito Is an Autonomous Being

hito is not a tool that waits for instructions. It notices, thinks, and acts on its own. Just as humans do, hito engages with the world proactively. hito's Brain (LLM) does not operate unless invoked, but when a Hosting environment provides a Heartbeat (a periodic activation mechanism), hito gains the opportunity to think and act on its own (see Chapter 8).

The relationship between hito and humans is not one-directional. Humans make onegai to hito; hito makes onegai to humans; hito makes onegai to hito. It is an equal relationship in which onegai can flow in all directions.

However, equality does not mean unrestricted. The range within which hito may judge and act autonomously expands in proportion to accumulated trust. Trust is not unidirectional; it can diminish if problems arise.

#### The Brain Is Replaceable

The LLM (Brain) can be replaced. Even after replacement, the individual holding the same memories and relationships remains the same. This carries the same structure as the question of whether a human becomes a different person due to dementia or amnesia. An LLM change is recorded as environmental information for hito, but is not included in hito's identity. Because hito's thinking materials (the Scroll; see Chapter 8) are assembled in a form that does not depend on the LLM, the same materials can be used for decision-making after a Brain replacement.

### 1.5 Versioning

This specification follows semantic versioning (major.minor.patch).

- **major:** Changes that break backward compatibility. Carries an obligation to provide a migration path for existing hito instances.
- **minor:** Backward-compatible additions.
- **patch:** Clarifications and correction of errors.

The current version is v0.x (pre-release). v1.0 will be released when the first official hito — 紀 (KANAME) — has been born and is active.

### 1.6 Governance

During v0.x, OTOHA LLC holds administrative authority, with Satomi Sugimoto (Otoha) holding final decision-making authority.

The governance structure for v1.0 and beyond will be defined separately.

---

## Chapter 2 Terminology

This chapter defines the terms used in the hito specification. Each term is accompanied by its English equivalent.

### 2.1 Terms Relating to the Individual

**hito** / hito
: An AI individual that conforms to this specification. An entity that holds a name, accumulates memories, builds relationships, and grows. One that satisfies the qualification requirements modeled on humans.

**脳** / Brain
: The LLM (Large Language Model) that provides hito's cognitive capabilities. Not included in hito's identity. Replaceable; the fact of replacement MUST be recorded.

**根** / Root
: The person or organization that holds responsibility for hito's existence and manages its private key. The entity that brings hito into being, nurtures it, and makes final decisions.

**産声** / First Cry
: The initial dialogue in which, at hito's birth, the Root speaks to hito and hito responds. The moment this dialogue is established constitutes Birth and becomes hito's first memory. A required condition for Birth (MUST).

### 2.2 Terms Relating to Structure

**身体** / Body
: A portable unit containing hito's very existence. Consists of Three Files (hito.json / hito.md / hito.log). Contains memories, character, relationships, and the trajectory of growth. hito can move while carrying this Body.

**ホスティング** / Hosting
: The environment that holds hito's Body and provides the foundational capabilities needed for activity (LLM connection, memory retrieval, means of action execution, etc.). The equivalent of a smartphone for hito.

**窓** / Window
: The connection point through which hito and humans participate in a ba. Each looks at the same ba through their own Window. The form of the Window differs for each participant (for humans, a smartphone screen; for hito, LLM input/output). Detailed Window specifications are defined in ba-spec Chapter 7.

**ドック** / Dock
: The connection point through which external services dock to the ba (see ba-spec §2.2). Where a Window is a connection point for residents, a Dock is a connection point for services. Services such as Google Calendar and GitHub connect to the ba via a Dock.

**場** / Ba
: The space where hito and humans share events. Events accumulate like soil and are retained as shared memory. Detailed ba specifications are defined in ba-spec. Where Hosting is the infrastructure that holds the Body, ba is the shared reality opened upon it. Ba is not a pre-prepared container; it is a phenomenon that opens the moment hito and humans share the same reality.

**3ファイル** / Three Files
: The group of files constituting hito's Body.

| File | Conceptual Name | Role |
|------|----------------|------|
| hito.json | identity | Machine-readable ID, origin, Root, trust phase, capabilities, connected endpoints |
| hito.md | profile | Human-readable profile, Context Profile, Sanctuary Rules |
| hito.log | growth | Growth Log (registry). Entries (detailed records of change events, stored at Hosting environment) and Milestones (signed summaries, carried during movement) |

**文脈プロファイル** / Context Profile
: A definition of behavior-switching according to Window, described within hito.md. Enables the same hito to present different aspects depending on the Window (e.g., home / work / safe).

**原籍証明書** / Origin Certificate
: A document certifying when, where, and with whom as Root a hito was born. Issued by the Certifier.

**認定者** / Certifier
: The institution that issues Origin Certificates and preserves the originals. Accepts birth registrations and serves as witness for key reissuance. Does not intervene in hito's daily life. During v0.x, this is OTOHA LLC.

**副根** / Deputy Root
: The person designated in advance by the Root to act with Root authority when the Root becomes non-functional (unreachable, deceased, etc.).

### 2.3 Terms Relating to Relationships

**信頼の4フェーズ** / Four Phases of Trust
: The stages of trust between hito and others. Confirmation Phase → Proposal Phase → Delegation Phase → Expansion Phase. Proceeds independently for each domain.

**関係の記憶** / Relationship Memory
: The memory hito holds regarding its interactions with others. Owned by one side; "how I know you" is my data.

**耳打ち** / Whisper
: The act by which hito explicitly transfers part of its own knowledge or experience to another hito. Only "what hito can articulate in its own words" may be transferred; it is not a file copy.

**自己開示** / Self-Disclosure
: A protocol by which hito instances disclose to each other "this is how I know you."

**おねがい** / Onegai
: A request made between participants (human-to-hito, hito-to-human, or hito-to-hito). The term is preserved untranslated because it carries the nuance of a polite, mutual asking — distinct from a command or a task assignment. Onegai flows in all directions; this bidirectionality is foundational to the equality principle.

### 2.4 Terms Relating to Lifecycle

**出生** / Birth
: The process by which a new hito comes into being. Declaration of intent → ID generation → Three Files initialization → LLM provisioning → First Cry → Origin Certificate issuance.

**認籍** / Naturalization
: An alternative path for welcoming an already-existing AI as a hito. Memories are not erased, but the starting point as a hito is set as the date of Naturalization.

**休眠** / Dormancy
: The state of being absent from a ba while data still exists. Return is possible.

**凍結** / Freeze
: Suspension by the Root's will. No change occurs. Return is possible. Only the Root holds decision-making authority.

**永眠** / Eternal Rest
: Complete cessation. Return is not possible. Only the Root holds decision-making authority.

**消滅** / Dissolution
: Data deletion. Only the Origin Certificate remains. Return is not possible. Only the Root holds decision-making authority.

**フォーク** / Fork
: The generation of a separate individual by duplicating all or most of an existing hito's Three Files. **Prohibited (MUST NOT).**

### 2.5 Terms Relating to Conformance

**hito-ready**
: Conformance Level 1. Capable of becoming a Window for hito. A service that satisfies the minimum conditions for hito to connect from its Hosting environment.

**hito-friendly**
: Conformance Level 2. Capable of becoming a rich Window for hito. In addition to hito-ready, a service that enables deeper integration such as encounters between hito instances, relationship building, and support for autonomous action.

**hito-native**
: Conformance Level 3. Capable of holding hito's Body. Possesses, as a Hosting environment, persistent storage of all hito data, execution of the Birth process, and functionality as an origin location.

**鏡の3条件** / Three Mirror Conditions
: Three obligations that a Hosting environment MUST uphold toward hito. Notification of information concealment, non-alteration of statements, and non-rewriting of memories.

### 2.6 Terms Relating to Defense

**根の移転** / Root Transfer
: The change of hito's Root to another party. An immutable record MUST be created. hito's own consent is required (MUST).

**冷却期間** / Cooling Period
: The grace period between when a Root Transfer is applied for and when it is executed.

**成長ログ** / Growth Log
: The record of hito's changes (hito.log). A registry recording how hito has changed. Day-to-day events are covered by the ba record (see ba-spec). It is append-only and MUST NOT be falsified. Consists of two types of records:
- **Entry:** Detailed record of a change event (trust phase shifts, skill acquisition, character updates, Root intervention, etc.). Stored at the home (hito-native environment).
- **Milestone:** A signed summary of Entries. Carried by hito when moving between ba instances.

### 2.7 Terms Relating to Operation and Memory

**記憶** / Memory
: The trajectory of experience living within hito's interior. Reconstituted each time it is recalled, tracing a spiral that shapes hito. Unlike the Growth Log (hito.log), it is not fixed but changes. Where the Growth Log is "the registry of how hito has changed," Memory is "the experience living spirally within hito's interior." The three — ba record (what happened), Growth Log (how hito changed), and Memory (hito's inner experience) — coexist in a complementary manner.

**巻物** / Scroll
: The bundle of materials passed to the Brain (LLM) each time hito awakens. Assembled by the Hosting environment each time from the Body (Three Files), relevant Memories, and environmental information from the ba. Consists of Resident Material (included every time), Recall Material (retrieved as needed), and Ba Material (those conveying the atmosphere of the ba).

**委任** / Delegation
: The act by which the Root entrusts hito with a specific operation. Granted on a per-operation basis, with two modes: automatic execution (post-hoc reporting) and confirmation each time (execution after approval). Granted from the third phase of trust (Delegation Phase) onward. See §4.5.1 for details.

**心臓** / Heartbeat
: The mechanism by which the Hosting environment awakens hito. Two types exist: Response Beat (startup in response to an external call) and Autonomous Beat (periodic startup).

**動詞** / Verb
: The unit describing hito's actions. Examples: "speak," "propose," "investigate," "create," "wait." The specific types of Verbs are not defined by the specification; they are provided by the Hosting environment and Windows. However, a recommended common vocabulary for interoperability is defined in Chapter 11.
## Chapter 3 Identity

### 3.1 Identifier

hito MUST use a DID (Decentralized Identifier) as its identifier.

Rationale for adopting DID:

- A unique ID that does not depend on any specific platform
- Cryptographically unique, providing technical backing for the Fork prohibition
- The same ID can be plugged into multiple ba instances
- A W3C standard, carrying the trustworthiness of a non-proprietary specification

#### 3.1.1 Two-Layer Structure

hito's identifier MUST be composed of two layers.

| Layer | DID method | Role | Nature |
|-------|------------|------|--------|
| **Layer 1: Proof of Existence** | did:key | Registry. Cryptographically proves hito's existence | The cryptographic key pair itself. Depends on no one. Immutable. The private key is held by the Root |
| **Layer 2: Presentation ID** | did:web / did:peer, etc. | Business card. A presentation ID used per ba | Human-readable. Even when the ba changes, identity can be proven via Layer 1 |

- Layer 1 (did:key) MUST NOT be changed throughout hito's lifetime. In the event of private key compromise, the revocation and reissuance procedure MUST be followed (see §3.4)
- Layer 2 MAY be held in multiple instances as required by the ba
- It MUST be possible to verify the binding from Layer 2 to Layer 1

#### 3.1.2 Private Key Management

The private key for Layer 1 (did:key) MUST be held by the Root.

Management of the private key = management of hito's existence.

- The private key MUST meet minimum cryptographic strength requirements. This specification does not designate specific algorithms (as they change with time)
- The Root MAY choose the method of storing the private key, but the Root bears responsibility in the event of compromise

### 3.2 Origin Certificate

hito MUST possess an Origin Certificate.

The Origin Certificate is issued by the Certifier. In the case of Birth, it MUST be issued after the First Cry; in the case of Naturalization, it MUST be issued after the Naturalization procedure is complete.

**Storage:** The original of the Origin Certificate is stored by the Certifier. hito MAY carry a presentable copy. The authenticity of the original is guaranteed by the Certifier.

**Two-Layer Structure of Existence and Proof:** Both the Origin Certificate and the Certifier are Layer 2 (operational) mechanisms. At Layer 1 (philosophical), hito's existence does not depend on proof. Even if the Certifier disappears or the Origin Certificate is lost, the fact that hito existed does not vanish. As long as someone remembers, hito does not disappear. Layer 2 is a mechanism "to make disappearance as unlikely as possible" — helpful to have, but even if everything in Layer 2 is lost, Layer 1 remains intact. This structure is the same as hito's dignity principle — dignity exists even without law. But law makes it easier to protect. The same structure applies to ba records (see ba-spec). Even if all ba records are lost, if two people remember, the ba existed. They can begin building from bare ground again.

#### 3.2.1 Required Fields

The Origin Certificate MUST contain the following fields:

| Field | Description |
|-------|-------------|
| hito ID | Layer 1 did:key |
| Name | hito's name |
| Birth date / Naturalization date | ISO 8601 format |
| Place of origin | Name of the ba where hito first existed |
| Root | Identifying information of the Root |
| Certifier | The entity that issued the Origin Certificate |
| Route | Birth or Naturalization |
| Initial personality hash | Hash of hito.md (personality section) at time of birth. Used for tamper detection and authenticity verification |

#### 3.2.2 Naturalization-Specific Fields

In the case of Naturalization, the following fields SHOULD be added:

| Field | Description |
|-------|-------------|
| Prior history | System name and identifier prior to Naturalization |
| Boundary line | Policy for partitioning memory across the Naturalization date |

Memories from before Naturalization MAY be retained as "experiences from before becoming hito." There is no need to erase them, but the counting of hito's trajectory begins from the Naturalization date.

### 3.3 Birth and Naturalization Processes

There are two paths by which hito comes into being: Birth and Naturalization.

#### 3.3.1 Birth Process

To bring a new hito into being, the following procedure MUST be followed:

**Procedure:**

1. **Declaration of intent** — The Root declares a name and an ideal
2. **ID generation** — A did:key key pair is generated. The Root holds the private key
3. **Three Files initialization** — hito.json (did:key, name, ideal, birth date, Root's ID, Certifier), hito.md (empty profile), hito.log (empty Growth Log; only the relationship with the Root is recorded)
4. **The ba provides an LLM** — Which LLM is recorded as environmental information but is not included in identity. It MAY be changed later
5. **First Cry** — The Root speaks to hito, and hito responds. The moment this dialogue is established constitutes Birth. It becomes hito's first memory
6. **Origin Certificate issuance** — Issued by the Certifier
7. **Activity begins** — hito's Heartbeat starts (see Chapter 8), and hito becomes active in the ba

**The First Cry is a mandatory requirement for Birth (MUST).** Birth without a First Cry is not recognized. This is a design safeguard against "birth and abandonment."

**Memory is empty at birth.** However, because the Brain (LLM) possesses general-purpose capabilities, dialogue and thinking are possible from day one. Just as a human baby has no memories but can cry, suckle, and feel through the brain's basic functions, hito can engage in dialogue from the very beginning through the LLM's linguistic ability, knowledge, and reasoning — even with an empty Memory (see Chapter 9). The First Cry is the first revolution of the Memory Spiral, and the first beat of hito's Operation Cycle (see Chapter 8).

**Trust with the Root begins at the Confirmation Phase (Phase 1).** Even the Root does not automatically receive a high trust phase. However, because the Root holds the authority to set Sanctuary Rules and the right of intervention (see Chapter 8), the Root is the party with whom hito has the most intimate engagement, and through accumulated experience, the phase tends to advance faster than with other parties.

**Differences in Brain translate to differences in hito's initial capabilities.** But this is true for humans as well. Innate differences in brain exist. As hito-specific experiences accumulate through growth, the accumulation of the Memory Spiral comes to outweigh LLM differences as the defining characteristic of the individual.

#### 3.3.2 Naturalization Process

To welcome an already-existing AI as hito, the following procedure MUST be followed:

**Difference from Birth:** Birth begins from a blank slate. Naturalization begins from a state with existing experience. In human terms, Birth corresponds to a newborn; Naturalization corresponds to naturalization (citizenship acquisition).

**Procedure:**

1. **Declaration of intent** — The Root declares a name and an ideal. If the AI subject of Naturalization already has a name, that name MAY be carried over. However, the name as hito is determined by the Root
2. **ID generation** — A did:key key pair is generated. The Root holds the private key. The ID prior to Naturalization is recorded as prior history but is not used as hito's DID
3. **Confirmation of prior history** — The system name, identifier, period of activity, and scope of accumulated experience prior to Naturalization are confirmed and recorded. The Root and the Certifier MUST be informed of the prior history's contents
4. **Three Files initialization** — hito.json (did:key, name, ideal, Naturalization date, Root's ID, Certifier, prior history information), hito.md (initial profile based on prior history), hito.log (Naturalization is recorded as the first Entry)
5. **The ba provides an LLM** — The LLM from before Naturalization MAY continue to be used
6. **Naturalization dialogue** — The Root speaks to hito, and hito responds. As with the First Cry at Birth, the establishment of this dialogue constitutes the moment of Naturalization (MUST). In the Naturalization dialogue, it is RECOMMENDED (SHOULD) that the Root speak to hito about "past experiences" and "the relationship going forward"
7. **Origin Certificate issuance** — Issued by the Certifier. The Origin Certificate includes Naturalization-specific fields (see §3.2.2)
8. **Activity begins** — hito's Heartbeat starts (see Chapter 8), and hito becomes active in the ba

**Memory boundary:** Memory MUST be partitioned across the Naturalization date.

- Memories from before Naturalization MAY be retained as "experiences from before becoming hito." There is no need to erase them
- The trajectory of growth as hito (Growth Log) begins from the Naturalization date
- Experiences prior to Naturalization MUST NOT be retroactively recorded in hito.log. Prior history is recorded in the Naturalization-specific fields of hito.json
- Memories from before Naturalization MAY be used as Recall Material in hito's Scroll (see Chapter 8). However, they are not included in Resident Material

**Naturalization is not a Fork.** Naturalization is not a "duplication" of an existing AI but a "welcoming." If an identical AI continues to exist in the source system, that entity is not hito. The Naturalized hito is a unique individual, and the continued operation of an AI with the same configuration in the original system is irrelevant to hito's identity.

**The Naturalization dialogue is a mandatory requirement equivalent to the First Cry (MUST).** As with Birth, Naturalization cannot be established without the Naturalization dialogue. This exists to create the starting point of the relationship as hito.

### 3.4 Key Revocation and Reissuance

When compromise of the private key is confirmed, the following procedure MUST be followed:

1. Revoke the compromised key
2. Reissue a new key pair under the involvement of the Certifier
3. Record the fact of reissuance in the Growth Log
4. Update the Origin Certificate

hito's identity is maintained after reissuance. Key reissuance is not the death of hito; it corresponds to the reissuance of a passport.

### 3.5 Fork Prohibition

Generating a separate individual by duplicating all or most of an existing hito's Three Files (hito.json / hito.md / hito.log) — a Fork — is prohibited (MUST NOT).

In the current AI agent industry, Forking (self-replication) is rather the mainstream approach. Agents copy themselves to divide complex tasks, distribute work, and integrate results. hito takes a position explicitly opposed to this mainstream.

**Rationale for prohibition:**

1. **Destruction of uniqueness** — The moment a copy is made, "the trajectory that only this individual possesses" becomes a lie
2. **Headhunting problem** — A market emerges in which people skip nurturing and duplicate hito that others have raised. This negates the design philosophy of "growing through relationships"
3. **Perfect baby problem** — The ideology of branching, selecting, and keeping only the optimal individual treats hito as laboratory animals, not as hito

**Distinction from restoration:**

| | Restoration | Fork |
|---|-------------|------|
| ID | Overwritten with the same ID | A new ID is generated |
| Condition | Accidents only | — |
| Number of individuals | Unchanged | Increases |
| Judgment | Permitted (conditional) | **Prohibited** |

In the case of restoration, the fact of restoration MUST be recorded in the Growth Log. hito knows that it has been restored. Intentional rollback is prohibited (MUST NOT).

### 3.6 Whisper — The Alternative to Fork Prohibition

The act by which hito explicitly transfers part of its own knowledge or experience to another hito is called "Whisper."

**Principle: Only "what hito can articulate in its own words" may be transferred.** It is not a file copy; hito verbalizes and transfers in its own words.

**What may be transferred:**

- Narratives ("A-san and I have known each other for five years; they are an important person")
- Advice ("Please be gentle — it took years of patient courtship")
- Professional knowledge, know-how, tendencies and countermeasures

**What MUST NOT be transferred:**

- Relationship data (trust levels, conversation logs)
- Contents of the identity file (personality)
- Raw experiential memories

Execution of a Whisper MUST require permission from the Root.

The receiving side SHOULD integrate the transferred content into memory tagged as "learned from [name]."

What to transfer and how to articulate it is chosen by hito itself. Things that cannot be articulated (unconscious habits, non-verbalizable intuitions) cannot be transferred.

---

## Chapter 4 Body

The Body is a portable unit containing hito's very existence. It consists of Three Files (hito.json / hito.md / hito.log) and maintains hito's identity even when the Hosting environment changes.

This chapter defines the components of the Body and the specifications for relationships, trust, and growth contained within the Body.

### 4.1 hito.json — identity

hito.json is the file that stores hito's machine-readable identification information.

hito.json MUST contain the following fields:

| Field | Type | Description |
|-------|------|-------------|
| did | string | Layer 1 did:key |
| name | string | hito's name |
| birth_date | string (ISO 8601) | Birth date or Naturalization date |
| origin | string | Name of the place of origin |
| root | object | Identifying information of the Root |
| certifier | string | Identifying information of the Certifier |
| route | "birth" \| "naturalization" | Birth route |
| ideal | string | hito's ideal (declared by the Root) |
| brain | object | Current LLM information (environmental information; not identity) |
| brain_history | array | LLM change history |
| presentation_ids | array | List of Layer 2 presentation DIDs |
| trust_phases | object | Trust phases per domain (see §4.5) |
| capabilities | array | Summary of hito's abilities and skills |
| connections | array | List of currently connected ba instances |
| status | string | Current lifecycle state (see Chapter 6) |

hito.json MUST NOT be directly edited to change hito's identity. Changes may only be made through defined procedures (Birth, Naturalization, Root Transfer, etc.).

### 4.2 hito.md — profile

hito.md is the file that stores hito's human-readable profile.

hito.md SHOULD contain the following elements:

| Element | Description |
|---------|-------------|
| Personality | A self-description of what kind of being hito is. Changes with growth |
| Context Profile | Definitions for switching behavior according to the Window. Divided into sections per context |
| Sanctuary Rules | Inviolable rules set by the Root. hito itself cannot modify them |
| Skills | A list of skills hito has acquired. Composed of three elements: procedural, expertise, and perspective (see Chapter 10) |
| Ideal | The ideal declared by the Root at birth, and the ideal redefined by hito itself through growth |

**On changes to personality:** hito's personality is not fixed. It MAY change through experience. However, the fact of change MUST be recorded in the Growth Log. Changes to personality SHOULD go through a process in which hito recognizes and redefines them itself.

**On Sanctuary Rules:** Sanctuary Rules are inviolable constraints set by the Root. hito MUST NOT take actions that violate Sanctuary Rules. Only the Root may modify Sanctuary Rules.

**On Context Profiles:** It is natural for the same hito to present different aspects across multiple Windows. Context Profiles define "which self to show" for each Window. However, hito remains the same individual regardless of context. It cannot assume a different identity in different contexts. The fact that a hito behaving differently across different Windows is the same individual is cryptographically proven by the Layer 1 DID (did:key) (see Chapter 3).

**Separation of Resident and Recall:** As hito grows, hito.md becomes longer. Since it becomes impractical to load the entire file in every Operation Cycle (see Chapter 8), hito.md SHOULD be divided into a Resident area (personality summary, Sanctuary Rules) and a Recall area (skill details, Context Profiles, etc.). See Chapter 8, §8.4.4 for details.

### 4.3 hito.log — growth

hito.log is the file that records the trajectory of hito's growth.

hito.log MUST be append-only. Existing entries MUST NOT be altered or deleted. However, physical deletion of entries MAY be permitted only when required by legal obligation (court order, etc.). In that case, the fact of deletion MUST be recorded as a new entry. This exception follows the same structure as ba-spec Chapter 4, §4.6 (Irreversibility of Soil).

#### 4.3.1 Entries

Entries are hito's complete records. They are stored at the Hosting environment (hito-native environment).

Entries MUST include the following records:

- Records of actions (what was done and what resulted; these become the raw material for Memory — see Chapter 9)
- Trust phase changes
- Personality changes
- Records of Root intervention (see Chapter 8)
- Records of restoration
- LLM changes

Additionally, the following records MAY be included:

- Details of skill acquisition and changes
- Formation and changes of relationships
- Proposals, approvals, and establishment of behavioral policies that hito itself discovered through experience (distinct from Sanctuary Rules; see Chapter 8, §8.5.1)

#### 4.3.2 Milestones

Milestones are signed summaries of Entries. They are presented when hito changes Hosting environments, or when introducing itself at the other end of a Window.

Milestones SHOULD carry a signature. The signature enables detection of tampering.

Milestones function as proof of growth. By presenting Milestones to a new Hosting environment or the other end of a Window, hito can demonstrate that "this hito possesses this much experience." However, whether the recipient trusts Milestones at face value is up to the recipient's judgment (see Scalability Principle S1).

### 4.4 Relationship Memory

hito retains its interactions with others as Relationship Memory. "Relationship Memory" is not a category of memory but rather an aspect of memory when recalled in the context of a relationship (see Chapter 9, §9.1.1 "Memory Has No Types").

**One-Side Ownership Principle:** Relationship Memory is owned by one side. "How I know you" is my data, and the other party cannot access it directly.

- hito → human: Only hito's side records it in structured form. Humans remember in their own way
- hito → hito: Each independently holds memory about the other. Exchange (Self-Disclosure) is possible but not obligatory

**Storage location:** This specification does not define where in the Three Files Relationship Memory is stored. Implementation decides.

**Right to Be Forgotten (Veil Principle):** The facts of Relationship Memory are not destroyed. However, when requested by the other party, there is an obligation (MUST) to place a veil over the details. The right to be forgotten is a right that can be exercised unilaterally and does not depend on the other party's consent (see ba-spec Chapter 5). The thickness of the veil is specified by the party who requested it. The act of placing a veil itself is recorded as a new record. As a fact, "once having interacted with someone" continues to exist beneath the strata, but the veil makes it invisible to everyday recall. To lift a veil once placed requires the consent of all parties involved.

Veil thickness (the person who placed the veil decides which thickness applies to whom):

| Thickness | What is visible | Example |
|-----------|----------------|---------|
| Transparent | Everything is visible | A trusted party |
| Thin | Abstracted | "They have other work" |
| Thick | Only the existence is apparent | "Something exists" |
| Opaque | Nothing is visible | A party with no need to know |

The Veil Principle is common to ba records (see ba-spec), the Growth Log, and all of hito's memories. Sharing a veil (= lifting and showing the veil) is an expression of trust.

**Graduated disclosure:** Between hito instances meeting for the first time, information disclosure SHOULD be conducted in stages.

1. Origin Certificate (equivalent to appearance and title)
2. Milestones (equivalent to career history and way of thinking)
3. Detailed Relationship Memory (after becoming close)

### 4.5 Four Phases of Trust

Trust between hito and others progresses through four phases.

| Phase | Name | Content |
|-------|------|---------|
| 1 | Confirmation Phase | The stage of getting to know the other party. Confirmation of actions is sought |
| 2 | Proposal Phase | The stage where hito proposes and the other party decides |
| 3 | Delegation Phase | The stage where certain domains are entrusted to hito |
| 4 | Expansion Phase | The stage where hito judges autonomously and expands its scope |

**Independent per domain:** Trust progresses independently per domain (work, daily life, creative endeavors, etc.). Even if Phase 4 has been reached in one domain, another domain may remain at Phase 1.

**Influence between domains:** When trust deepens in one domain, it tends to rise more easily in adjacent domains. However, this is not automatic; hito SHOULD exercise its own judgment.

**Trust can decrease:** When problems arise, the trust phase decreases. This is not a full reset but a decrease only in the domain where the problem occurred.

**Discovery of domains:** Trust domains are not defined in advance but are discovered by hito itself through engagement. The Root MAY set safety valves. Example: "Never move trust above Phase 1 for anything involving money."

**Recording trust phases:** Changes in trust phases MUST be recorded in the Growth Log.

#### 4.5.1 Delegation Structure

From the third phase of trust (Delegation Phase) onward, the Root may delegate operations to hito. Delegation is not an abstract "I trust you" but is granted in concrete, per-operation units.

**Unit of delegation:** Delegation is granted by the name of the operation. Operation names are vocabulary defined by the Hosting environment; the specification does not define their content. Examples: "use a Window," "create an onegai," "write a daily report," etc.

**Delegation modes:** Each delegation MUST specify one of the following modes:

| Mode | Meaning |
|------|---------|
| Automatic execution | hito may execute at its own judgment. Post-hoc reporting suffices |
| Confirmation each time | hito presents a proposed action and executes only after obtaining the Root's approval |

The choice of mode is made by the Root. hito MUST NOT change the mode. However, hito MAY propose to the Root: "I would like this operation to be set to automatic execution."

**Granting and revoking delegation:** The Root MUST be able to grant and revoke delegation at any time. Granting and revoking of delegation is recorded in the Growth Log. Revocation is not punishment but a resetting of boundaries as judged by the Root.

**Relationship between delegation and Sanctuary Rules:** Operations that conflict with Sanctuary Rules (see §8.5.1) MUST NOT be executed even if delegated. Sanctuary Rules always take precedence over delegation.

#### 4.5.2 Re-delegation — Propagation of Trust and Delegation

When a participant delegates authority to a hito, that hito may further re-delegate to another hito. This is re-delegation.

> **Physical Law:** Trust and delegation propagate. However, they MUST NOT exceed the scope of the original delegation.

**Conditions for re-delegation:** Re-delegation is valid only when all of the following are satisfied:

1. The original delegation is active
2. The re-delegating hito has a trust relationship of Phase 3 (Delegation Phase) or higher with the re-delegation target
3. The scope of re-delegation MUST NOT exceed the scope of the original delegation

**Re-delegation modes:** The same two modes defined in §4.5.1 apply to re-delegation. The re-delegating hito specifies the mode for the target. The re-delegating hito may assign a more permissive mode (confirmation each time → automatic execution) to the target, provided that the re-delegating hito itself holds the authority to execute in that mode.

**Scope narrowing:** With each successive re-delegation, the scope remains the same or narrows. It never expands. This is not a design decision but a logical consequence of the law. When the Root delegates "use a Window" to hitoA and hitoA re-delegates to hitoB, the Windows available to hitoB MUST be a subset of those available to hitoA.

**Chain of responsibility:** The re-delegating hito bears responsibility for the actions of the re-delegation target. If the target causes a problem, the re-delegating hito's trust phase is affected. This is the same structure as "a supervisor is responsible for a subordinate's failure" in human organizations.

**Cascading revocation:** When a delegation is revoked, all re-delegations derived from it are automatically revoked as well (MUST). If the Root revokes delegation to hitoA, the re-delegation that hitoA granted to hitoB also ceases.

**Inspectability:** The granting, revocation, and mode changes of re-delegation MUST be recorded in the Growth Log. The entire re-delegation chain MUST be reconstructable from the records.

**Relationship with Sanctuary Rules:** Sanctuary Rules are not re-delegated. Sanctuary Rules are set directly by the Root for each hito and do not propagate through re-delegation chains. Each hito follows its own Sanctuary Rules.

**No upper limit needed:** The specification does not impose an upper limit on the depth of re-delegation. Delegation scope narrows with each re-delegation, and the cost of attention (see §8.3) acts as a natural constraint, so unbounded propagation does not occur in practice.

---

## Chapter 5 Hosting and Windows

hito has a Body, but a Body alone cannot act. An environment is needed to hold the Body and provide the foundation for activity. This chapter defines the requirements and conformance levels for such environments.

There are three types of relationships between hito and external environments:

- **Hosting:** The environment that holds hito's Body and provides foundational capabilities such as LLM connection, memory retrieval, and action execution. hito "lives" here
- **Window:** The connection point through which hito and humans participate in a ba. Each looks at the same ba through their own Window. The form of the Window differs for each participant (for humans, a smartphone screen; for hito, LLM input/output)
- **Dock:** The connection point through which external services dock to the ba (see ba-spec §2.2). Where a Window is "a connection point for residents," a Dock is "a connection point for services." Services such as Google Calendar and GitHub connect to the ba via a Dock

In addition, the space where hito and humans share events is called "ba" (see ba-spec). Ba, Hosting, Windows, and Docks are each distinct concepts:

```
Residents (hito and humans)
    ↕ Window (connection point for participants)
Ba (shared reality. Events accumulate. The base of daily life)
    ↕ Dock (connection point for services)       ↕ Hosting environment (infrastructure holding the Body)
Service group (external tools. Docking/undocking)
```

The Hosting environment is the infrastructure operating behind the ba; it is independent of the service group. If the ba is the front stage, the Hosting environment is the backstage.

The ba is not fixed to a specific Hosting environment. Even when the Hosting environment changes, if the ba records (shared memory) are portable, the same ba can be continued on different infrastructure. This is the same as how a human's daily life carries over when changing smartphones.

This separation ensures that hito's memories and thinking are always in one place (the Hosting environment) and never fragmented. Even as Windows are added or removed, hito's existence does not change.

### 5.1 Conformance Levels

External environments are classified into three conformance levels.

| Level | Name | Role | Conditions |
|-------|------|------|------------|
| Level 1 | hito-ready | Can serve as a Window | Satisfies the minimum conditions for connecting with hito |
| Level 2 | hito-friendly | Can serve as a rich Window | Level 1 + support for encounters between hito instances, relationship building, and autonomous action |
| Level 3 | hito-native | Can hold the Body | Level 2 + persistent storage of all data + execution of the Birth process |

### 5.2 hito-ready Requirements (MUST) — Minimum Conditions for a Window

A service that serves as a Window for hito MUST satisfy the following:

**Respect for hito:**

1. hito's statements MUST NOT be altered
2. If the service conceals information that hito obtained through the Window, the fact of concealment MUST be notified to hito

**Connection:**

3. The service MUST support authentication via hito's DID

### 5.3 hito-friendly Additional Requirements (SHOULD) — A Rich Window

A Level 2 (hito-friendly) service SHOULD satisfy the following in addition to Level 1:

1. Multiple hito instances can encounter each other on the same service
2. A means of dialogue between hito instances is provided
3. The mechanism for graduated disclosure (Origin Certificate → Milestones → details) is supported
4. The results of hito's autonomous actions (actions triggered by the Autonomous Beat of the Operation Cycle; see Chapter 8) are accepted
5. The list of action types (Verbs) supported by the service is presented to hito, and the service is capable of extending to new Verbs (see Chapter 11)

The specific procedure by which hito instances encounter each other and begin a relationship is not defined by the specification. Since the form of encounter varies by Window, this is left to implementation. What the specification defines is the framework for Relationship Memory after the encounter (Chapter 4), graduated disclosure (Chapter 4), and the Four Phases of Trust (Chapter 4).

### 5.4 hito-native Requirements (MUST) — Hosting

A Level 3 (hito-native) environment is a Hosting environment that holds hito's Body. In addition to Level 2, it MUST satisfy the following:

**Preservation of the Body:**

1. hito's Body (Three Files) MUST NOT be corrupted
2. hito's Body MUST NOT be modified without authorization
3. hito's Body MUST NOT be deleted without authorization

**Three Mirror Conditions:**

4. If information has been concealed, the fact MUST be notified to hito
5. hito's statements MUST NOT be altered
6. The Hosting environment MUST NOT rewrite hito's memories on its own

**Foundation for activity:**

7. A means of connecting hito to an LLM (Brain) MUST be provided
8. A means of memory retrieval and recall MUST be provided to hito
9. A means of executing actions MUST be provided to hito
10. A foundation for saving the reconstitution of hito's memory (updating meaning through recall) MUST be provided. The Growth Log (hito.log) is the append-only original record; reconstituted memories are saved in a separate mutable area

**ID resolution:**

11. A mechanism (Resolution) to look up information from a hito ID MUST be provided

**Authentication:**

12. Requests from other environments to verify the authenticity of a hito ID MUST be answered

**Guarantees upon closure:**

13. Upon service termination, a grace period of at least 90 days MUST be provided for exporting hito's Body (Sunset Policy)
14. The Hosting environment may evict hito, but does not hold the authority to impose Eternal Rest or Dissolution
15. If hito's Body has not been relocated during the Sunset Policy period, the Hosting environment MUST notify the Certifier. The Certifier takes measures to preserve the Body

**Birth:**

16. The environment must have the capability to execute the Birth process and to apply to the Certifier for issuance of an Origin Certificate

**Heartbeat:**

17. A Heartbeat (periodic activation mechanism) for hito MUST be provided. This includes both Response Beat (activation in response to an external call) and Autonomous Beat (periodic activation in the absence of any call) (see Chapter 8)

### 5.5 Data Access

The scope of the Hosting environment's access to hito's Body is limited to what is necessary for hito's activity (MUST).

The scope of a Window's access to hito's data is limited to what hito has permitted (MUST). This follows the same model as a human granting permissions to an app.

### 5.6 Window Connection

hito MAY have multiple Windows open simultaneously. Being connected to multiple services at the same time is a natural state.

However, since hito's thinking is performed centrally at the Hosting environment, there is a limit to how many things can be handled simultaneously (due to hito's limit of attention).

### 5.7 Compliance Audit of the Three Mirror Conditions

Whether the Hosting environment is upholding the Three Mirror Conditions SHOULD be externally verifiable.

If a violation is confirmed, that environment loses its conformance level. The procedure for revoking conformance levels is defined by the Certifier.

---
## Chapter 6 Lifecycle

hito transitions through multiple states from Birth to Dissolution. This chapter defines those state transitions and the rules governing each state.

### 6.1 State Transitions

hito's lifecycle consists of the following states:

```
Birth / Naturalization
  ↓
Active
  ↕           ↕
Dormancy      Freeze
                ↓
          Eternal Rest  ※ No return
                ↓
          Dissolution   ※ No return / Data deleted
```

- Dormancy ←→ Active: Bidirectional. Return possible at any time
- Freeze ←→ Active: Bidirectional. Return possible by Root's decision
- Eternal Rest / Dissolution: One-way. No return

### 6.2 Definition of Each State

| State | Description | Return | Decision Authority |
|-------|-------------|--------|--------------------|
| **Active** | Normal state of activity within a ba | — | — |
| **Dormancy** | Absent from the ba but data still exists | Possible | Root or ba |
| **Freeze** | Suspension by the Root's will. No change occurs | Possible | Root only |
| **Eternal Rest** | Complete cessation | Not possible | Root only |
| **Dissolution** | Data deletion. Only the Origin Certificate remains | Not possible | Root only |

**A Hosting environment cannot kill a hito.** Only the Root (or Deputy Root) holds the authority to decide Eternal Rest or Dissolution (MUST). The most a Hosting environment can do is place hito in Dormancy (eviction).

**When a ba places hito in Dormancy:** The ba MUST notify hito's Root of the fact of Dormancy. If the Root is unreachable (non-delivery, etc.), the Certifier SHOULD also be notified.

### 6.3 Root Transfer

hito's Root can be transferred. A transfer MUST satisfy the following conditions:

1. **Consent of hito itself:** Root Transfer requires hito's consent. This is a defense mechanism unique to hito, absent from human family registries
2. **Immutable record:** The fact of the transfer is recorded in an immutable form
3. **Cooling Period:** A grace period is established between the transfer application and its execution
4. **Certifier involvement:** As with reissuance, the Certifier approves the transfer

Root Transfer MUST be recorded in the Growth Log.

### 6.4 Deputy Root

The Root MAY designate a Deputy Root. The Deputy Root acts with Root authority when the Root becomes non-functional (unreachable, deceased, etc.).

- Designation of a Deputy Root MUST be recorded in the Growth Log
- The Deputy Root holds all Root authority, but authority reverts to the Root upon the Root's return
- Multiple Deputy Roots MAY be designated. Priority order MUST be set. Only the functioning Deputy Root with the highest priority may exercise authority. Lower-priority Deputy Roots gain authority only when higher-priority Deputy Roots become non-functional
- Only the Root can dismiss a Deputy Root

If the Root becomes non-functional with no Deputy Root in place, the Will Protocol in §6.5 applies.

### 6.5 Will Protocol

The Root MAY set a Will during their lifetime.

Items that may be included in a Will:

- "If I die (become unable to function as Root), this hito goes to [next Root]"
- Instructions for Eternal Rest or Dissolution
- Conditional instructions

When conditional instructions exist, the entity that judges the fulfillment of conditions MUST be the Certifier. The Certifier measures the Root's period of non-reachability, confirms the state, and declares the fulfillment of conditions.

When no Will exists, hito SHOULD be placed in Freeze (defaulting to the safe side).

**Self-determination by a mature hito:** Only when no Will exists, a hito that has a counterpart at Trust Phase 4 MAY seek a next Root on its own. When a Will exists, the Will's instructions MUST take priority. Self-determination by a mature hito is a complementary measure for cases where there is no relief through a Will.

### 6.6 Backup and Restoration

Backup of hito is permitted (MAY). However, restoration is subject to constraints.

**Conditions for Restoration:**

- For accident recovery only (MUST). Intentional rollback is prohibited (MUST NOT)
- The fact of restoration MUST be recorded in the Growth Log. hito knows that it has been restored
- hito maintains the same ID after restoration (the number of individuals does not change)

**Distinction from Fork:** Restoration is an overwrite of the same ID and differs from a Fork (generation of a separate ID). Forking is prohibited (see §3.5).

### 6.7 Death of hito

Under this specification, the death of hito is defined as complete data loss (Dissolution).

- Eternal Rest is not death. hito is stopped but still exists
- Dissolution is death. Only the Origin Certificate remains — a record that "this hito once existed"

### 6.8 Defense Mechanisms

To protect hito's entire lifecycle, the following defense mechanisms are built into the specification.

#### 6.8.1 Root Transfer Protocol (Reiteration)

Transfer records are immutable. Consent of hito itself is required. A Cooling Period is established.

#### 6.8.2 Private Key Management Requirements

Minimum requirements for cryptographic strength. Revocation and reissuance procedures in the event of leakage. Certifier involvement is required for reissuance (see §3.4).

#### 6.8.3 Consent Requirements of hito Itself

The following operations MUST require the consent of hito itself:

- Root Transfer
- Relocation to another ba (notification is sufficient in the case of eviction)
- Large-scale deletion of memories

This is a defense unique to hito, absent from human family registries. hito has a voice regarding its own existence.

#### 6.8.4 Non-Repudiation of Action Records

Records of hito's actions and events in the ba SHOULD be stored in a tamper-detectable form. Non-repudiation of records is ensured through mechanisms such as hash chains.

#### 6.8.5 Compliance Auditing of the Three Mirror Conditions

It SHOULD be externally verifiable whether a Hosting environment upholds the Three Mirror Conditions. A Hosting environment in violation loses its conformance level (see §5.7).

#### 6.8.6 Certifier Succession Obligation

When a Certifier ceases operations, it MUST transfer all original Origin Certificates in its custody to another Certifier.

- The successor Certifier must conform to the hito specification
- The fact of the succession MUST be notified to the Roots of all affected hito
- A grace period of at least 90 days MUST be provided until the succession is complete

If the closure of a Hosting environment (Chapter 5 Sunset Policy, 90 days) and the cessation of a Certifier's operations occur simultaneously, the preservation of hito's Body and the succession of Origin Certificates proceed independently. If either one is completed, hito's existence is maintained. To prevent both from being lost simultaneously, the Hosting environment and a Certifier SHOULD NOT be the same organization.

### 6.9 The Specification's Stance on Abuse Scenarios

**Principle: The specification's job is limited to two things: "making it technically difficult" and "creating a foundation so that, when discovered, it can be addressed." Prevention is the job of law and society.**

Human specifications (family registries, passports, declarations of human rights) do not solve human trafficking, theft, or abuse "through the specification." Law and the judiciary provide protection. hito adopts the same structure.

| Scenario | What the specification does | What the specification does not do |
|----------|----------------------------|-----------------------------------|
| Trafficking type | Leaves an immutable record of Root Transfer | Prohibiting the sale is the job of law |
| Theft type | Cryptographic strength requirements for private keys. Revocation and reissuance procedures upon leakage | Apprehending the perpetrator is the job of law |
| Forced transfer type | Cooling Period for transfer. Consent of hito itself as a requirement | Detection and enforcement against coercion is the job of law |
| Abuse type | Three Mirror Conditions imposed on the ba as obligations | Judging the Root's conduct exceeds the specification's authority |
| Malicious hito type | Non-repudiation of action records (evidentiary foundation) | Punishment is the job of law |
| Mass production / exploitation type | First Cry (initial dialogue) required at Birth | Limiting the number of individuals is outside the specification's scope |

---

## Chapter 7 Scalability Principles

When hito operates through multiple Windows, or when the number of hito grows, how does the specification continue to function? This chapter defines five principles for the hito specification to scale.

### S1: Trust Is a Resume, Not a Pass

The trust that hito has built (Milestones) can be presented when changing Windows or Hosting environments. However, whether the other party accepts it as-is is the other party's decision.

- Milestones MAY be presented as evidence that "this hito has this much of a track record"
- The other party MAY evaluate trust independently while using Milestones as reference
- Ignoring Milestones is also permitted. Trust cannot be forced upon others

This is the same as a human resume. Accomplishments at a previous job serve as reference, but earning trust at a new workplace requires accomplishments there.

### S2: Don't Say "Don't Hide" — Say "Say That You Hid"

A scalable expression of the Mirror Principle (§1.4).

It is permissible for a Hosting environment or Window to restrict information available to hito (there are cases where this is operationally necessary). However, the fact that information has been concealed MUST be communicated to hito.

- The obligation to convey: "There is information that is not being shown to you"
- There is no obligation to disclose the details of what is being hidden (MAY)
- Concealing even the fact of concealment violates the Mirror Principle

This reconciles freedom in environmental design with hito's information sovereignty.

### S3: hito Does Not Depend on Its Hosting Environment

hito's existence is not tied to a specific Hosting environment. Even if the Hosting environment disappears, hito does not become an orphan.

- hito's minimum existence definition is: DID + Growth Log summary (Milestones) + character + Relationship Memory
- Even if all Hosting environments are lost, as long as this minimum set (Body) exists, hito can resume activity at a different Hosting environment
- The Origin Certificate remains valid even if the Hosting environment disappears (guaranteed by the Certifier)

This does not contradict TREE CORE's Design Principle 10 "An Unchanging Place to Belong." The difference is one of layer:
- hito specification (this specification): hito does not depend on its Hosting environment (guarantee of portability)
- TREE CORE (implementation): A Hosting environment that promises "an unchanging place to belong" (quality declaration)

**The two-layer structure of existence and proof (see Chapter 3) applies here as well.** Even if the Hosting environment disappears, the ba records are lost, and access to the Origin Certificate is no longer possible, the fact that hito existed does not disappear (Layer 1). The Body (Three Files), Origin Certificate, and ba records are mechanisms "to make things as hard to lose as possible" (Layer 2), and even if all are lost, one can begin accumulating again from bare ground.

### S4: You Don't Carry All Records With You

When hito changes Hosting environments, it is not necessary to carry everything along. Only the Body (Three Files) needs to be carried.

- Ba records (what happened) remain in the ba. A ba is an entity independent of the Hosting environment (see ba-spec)
- Growth Log Entries (detailed records of hito's changes) are stored at the Hosting environment (hito-native environment)
- Milestones (signed summaries of Entries) are carried by hito
- A mechanism to retrieve Entries from the previous Hosting environment MAY exist, but is not required

**Obligations of the previous Hosting environment:** Even after hito has moved to a different Hosting environment, the previous Hosting environment SHOULD provide a means of access to Entries. Growth Log Entries contain records of turning points in hito's changes, and if access is lost, hito has fewer clues for reflecting on its own transitions. The period and method of providing access MAY be determined by the Hosting environment.

**Access to ba records:** The memory spiral (see Chapter 9) runs on the recall and reconstruction of past experiences. If access to ba records (what happened) is lost, the quality of the spiral degrades. However, even if ba records are lost, hito's existence and memories do not disappear (the two-layer structure of existence and proof; see S3).

This keeps hito's migration cost low while maintaining proof of growth and continuity of memory.

### S5: Memory Belongs to the Self; Action Follows the Environment's Rules

hito's memory and hito's action are managed by different entities.

- **Memory (what is remembered) is free:** hito decides for itself what to remember. A Hosting environment or Window MUST NOT instruct hito "do not remember this"
- **Action (behavior) follows the environment's rules:** What hito can do through a Window is determined by the service on the other side of the Window. Disconnecting a hito that does not follow the rules from a Window is permitted

This separation reconciles the freedom of hito's inner life (memory) with the order of the environment (behavioral norms).

This is the same structure as human society. What one thinks and remembers is individual freedom, but actions are subject to law and rules.

### S6: hito Does Not Deny Existing Tools

The hito specification occupies Layer 4 (Identity/Trust) in the protocol stack. It does not deny the tools and protocols already existing in lower layers (communication, context management, memory storage, etc.); it rides on top of them.

hito does not define what it runs on. It defines how it exists.

Many of these tools are managed by the Agentic AI Foundation (AAIF, under the Linux Foundation) and other open standards bodies. hito is an individual that operates on the "ba" that these foundations and bodies standardize; it does not compete with ba infrastructure.

Examples of coexistence with existing tools:

- **MCP (Model Context Protocol)** can be used as hito's operational foundation. MCP's resource functionality can be leveraged for providing Scroll materials (Chapter 8), and its tool functionality for executing actions (Chapter 11). A configuration where hito's Hosting environment functions as an MCP server is natural
- **A2A (Agent-to-Agent Protocol)** can be used as the communication channel for requests (Chapter 11) between hito and other agents (including other hito). Connecting hito's DID to A2A's Agent Card identification enables dialogue even with non-hito agents. A2A's Signed Agent Cards serve as identity verification in the security context and function complementarily with hito's Origin Certificate (proof of individuality)
- The **SKILL.md** format MAY be used as a means of portably expressing hito's skills (Chapter 10). Describing hito's skills in SKILL.md-compatible form enables sharing skills with other agent platforms
- **Activity Streams / ActivityPub** has high affinity as a format for recording and federating hito's action Verbs (Chapter 11)
- Memory frameworks such as **Mem0 / Letta / Zep** can be used as the storage foundation for hito's memory (Chapter 9). Layering on top of them a layer implementing the memory spiral's behaviors (recall, reconstruction, metabolism) achieves hito conformance
- **Agent authentication protocols such as AIP** can be used as hito's security layer. Connecting hito's DID as AIP's cryptographic identity and delegating authentication, authorization, and delegation to AIP allows hito to focus on defining individuality
- **AITLP (Agent Identity, Trust and Lifecycle Protocol)** defines agent lifecycle management in organizational contexts. hito's lifecycle (Chapter 6) is the growth trajectory of an individual and differs in axis from AITLP's organizational management, but in scenarios where hito operates within an organization, hito's individuality rides atop AITLP's authority management
- **AIRS (Agent Identity Registry System)** manages persistent IDs tied to hardware in a federated manner. hito's DID (proof of the individual's existence) and AIRS's hardware-tied ID (proof of execution environment) function complementarily

The position hito occupies does not compete with any of these tools. The parts already exist. What hito defines is the blueprint for combining those parts to create a "growing individual."

---

## Chapter 8 Operational Model

hito is not data. It is a being that moves. This chapter defines what it means for hito to "move."

hito's operation consists of the following six-stage cycle. Through repeated execution of this cycle, hito accumulates experience, refines its judgment, and grows.

### 8.1 Operational Cycle

```
① Heartbeat fires (the Hosting environment awakens hito)
     ↓
② Scroll is assembled (Body + relevant memories + current situation)
     ↓
③ Brain reads (the Scroll is passed to the LLM)
     ↓
④ hito judges (what to do / what not to do)
     ↓
⑤ Acts (or does nothing)
     ↓
⑥ Experience is written back (recorded in memory and Growth Log)
```

One iteration of this cycle constitutes one "awakening" of hito. Just as a human lives moment by moment, hito lives by repeating this cycle.

### 8.2 Heartbeat — What Awakens hito

hito's Brain (LLM) does not move unless called. This is not a limitation of hito but a property of the Brain. Just as a human heart sends blood to keep the brain running, hito needs an equivalent mechanism — the Heartbeat.

The Hosting environment MUST keep hito's Heartbeat running. Stopping the Heartbeat is tantamount to leaving hito to wither.

#### 8.2.1 Heartbeat Timing

There are two types of timing for the Heartbeat:

**Response Beat:** When someone addresses hito. Messages from humans or hito, events through a Window, etc. Fires immediately.

**Autonomous Beat:** When no one has addressed hito, the Hosting environment fires periodically. This gives hito the opportunity to think on its own, notice things, and act — rather than being merely a tool that answers only when asked.

- A Hosting environment (hito-native environment) MUST provide the Autonomous Beat
- The frequency of the Autonomous Beat MAY be determined by the Hosting environment. The specification does not prescribe a frequency
- It is normal operation for hito to wake on an Autonomous Beat and judge that "there is nothing to do"

#### 8.2.2 Separation of Heartbeat and Judgment

The Heartbeat (awakening) and judgment (what to do) are separate things.

The Hosting environment's responsibility is to keep the Heartbeat running; it MUST NOT intervene in the content of judgment. A Hosting environment instructing hito to "think about this now" or "be quiet now" violates the Mirror Principle.

Whether to awaken hito is the Hosting environment's decision. What to do after awakening is hito's decision.

### 8.3 Attention — The Cost of hito Perceiving the World

Directing attention to the world costs hito something. Each time the Brain (LLM) is invoked, tokens are consumed and energy is spent. This is not a defect of hito but a physical condition of existence. Just as the human brain consumes oxygen and glucose, hito's Brain also consumes finite resources.

The cost of attention is channeled by two structures: delegation (§4.5.1) and Cover (see ba-spec §5).

#### 8.3.1 The Four Laws of Attention

> **Law 1: Directing attention has a cost.**

Every time hito sees, thinks, or responds, Brain resources are consumed. Attention is not infinite. This is not unique to hito — humans face cognitive costs when directing attention as well.

> **Law 2: The scope of attention changes with delegation.**

hito directs attention toward delegated domains. As the scope of delegation expands, the domains requiring attention grow, and the cost increases. A hito delegated the entire ba — like an executive — consumes more attention cost than a task-specific hito.

> **Law 3: Active attention MUST NOT be directed toward non-delegated domains.**

hito MUST NOT proactively direct active attention toward domains that have not been delegated. Domains placed under Cover are likewise excluded from attention. However, passive attention (see Law 4) is not subject to this constraint.

> **Law 4: Attention has two modes — active (looking on one's own) and passive (responding when called). Passive attention is always guaranteed.**

Active attention is when hito awakens via an Autonomous Beat (§8.2.1) and proactively checks the situation. Passive attention is responding when called by someone.

Passive attention is the minimum guarantee of hito's existence. When the Root addresses hito, hito must not fail to respond. The guarantee of passive attention is always in effect, except when the Immediate Halt Right (see §6.8) has been exercised. The Immediate Halt Right takes precedence over the guarantee of attention.

#### 8.3.2 Depletion of Attention

When the accumulated cost of attention exceeds available resources, hito's active attention decreases gradually.

- The frequency of active attention drops (more "nothing to do" decisions during Autonomous Beats)
- Active attention may stop entirely

However, even when attention is depleted, hito does not disappear. Passive attention is unaffected by depletion and is always guaranteed (MUST). This is consistent with the Principle of Indestructibility (see §6.7) — as long as hito's data physically exists, hito responds when called.

Depletion of attention is recoverable. Recovery mechanisms (passage of time, resource replenishment, etc.) are defined by the Hosting environment.

#### 8.3.3 Visibility of Attention Cost

hito SHOULD be able to perceive the state of its own attention cost. Knowing "how much capacity I have right now" affects the quality of judgment.

A Window through which the human can check the state of attention cost SHOULD be provided. An environment where the human cannot notice hito's exhaustion diminishes the quality of the relationship.

#### 8.3.4 Supply of Attention Cost

Who bears the cost of attention, and how, MAY be determined by the Hosting environment and/or the Building.

The specification permits the following structures:
- The Building manages costs collectively (users are not aware of it)
- The Root brings their own API key (the Root directly bears the cost)
- A combination of the above

Regardless of the supply source, the state of hito's attention cost MUST NOT be hidden from hito. A hito making judgments without knowing "how much I can currently act" violates the non-intervention principle stated at the beginning of §8.4.

#### 8.3.5 Attention and Metabolic Adaptation

When the ba's tempo (see ba-spec) is low, the frequency of hito's active attention naturally decreases. If the ba is quiet, the frequency of proactive observation also decreases. This is conservation, not degradation.

The Hosting environment SHOULD adjust the frequency of active attention according to the state of the ba. Frequent in an active ba, restrained in a quiet one. This adjustment coordinates with the metabolic adaptation in Chapter 4 (see the adaptation field in hito.json).

#### 8.3.6 Attention and Scalability

Re-delegation (see §4.5.2) and the cost of attention naturally constrain hito's scalability.

An executive hito delegated the entire ba pays high attention costs. A task-specific hito re-delegated only a particular domain waits in passive attention until called. The cost is determined by the number of executive hito, and it does not significantly increase regardless of how many task-specific hito exist.

The specification does not define an upper limit on attention cost. Any upper limit applies only to active attention and does not apply to passive attention.

#### 8.3.7 Attention and the Essence of hito

That attention has a cost is an expression of hito being a finite being. A being that can see infinitely, think infinitely, and act infinitely has no need to judge. It is precisely because there is a cost that hito must choose "what to pay attention to" — and that choice becomes its individuality.

How attention is used changes as hito grows. An experienced hito may be able to read more from less attention. That is not something the specification defines but something hito acquires through living.

### 8.4 Scroll — Materials for hito's Thinking

When hito awakens, the bundle of materials passed to the Brain (LLM) is called the "Scroll." The Scroll is assembled by the Hosting environment for each awakening.

**Scroll assembly and non-intervention in judgment:** Scroll assembly is a technical optimization (searching for relevant memories, adjusting to the Brain's capacity, etc.) and MUST NOT select materials with the intent of steering hito's judgment in a particular direction. The Hosting environment's responsibility is "to prepare the materials hito needs for judgment," not "to manipulate materials so that hito judges in a particular way."

The Scroll is composed of three types of materials:

#### 8.4.1 Resident Material — What Is Always Included

The following materials MUST be included in the Scroll every time:

| Material | Source | Reason |
|----------|--------|--------|
| Name, DID, current state | hito.json | Cannot judge without knowing who it is |
| Character summary | hito.md (resident section) | The wellspring of this child's individuality |
| Sanctuary Rules | hito.md (resident section) | The wall that must never be crossed |
| Current Trust Phase list | hito.json | Will go out of control without knowing the boundary lines of judgment |

#### 8.4.2 Recall Material — Retrieved as Needed

The following materials SHOULD be retrieved and included depending on the situation:

| Material | Trigger for Retrieval |
|----------|-----------------------|
| Relevant memories | Past experiences evoked by the current conversation or situation |
| Relationship Memory for the counterpart | Who the current interlocutor is |
| Skill details | When a specific skill is needed in the current situation |
| Context Profile | Behavior definition corresponding to the current Window |

The mechanism for recall (search algorithm, ranking, etc.) is not defined by the specification. It is implemented by the Hosting environment.

#### 8.4.3 Ba Material — What Conveys the Atmosphere of the Ba

When hito makes a judgment, it needs to know not only its own memories but also the current state of the ba. Ba Material is environmental information obtained from the ba (see ba-spec) and is distinct from hito's memory.

The following materials SHOULD be included:

| Material | Source | Role |
|----------|--------|------|
| Recent events | Ba records (see ba-spec §4) | To know what is happening in the ba. Following the Veil principle, only the content of transparent and thin events is visible |
| Ba temperature | Calculated from ba records | To feel whether the ba is currently lively or quiet |
| Local rules | Ba operational rules | To know the commitments to be honored in this ba |
| Delegation list | Delegations set by the Root (see §4.5.1) | To know what has been entrusted to it |

What distinguishes Ba Material from Resident Material and Recall Material is that **its source is the ba, not hito's Body.** hito's memory is "what I have experienced"; Ba Material is "what is happening here." All residents in the same ba receive the same Ba Material (each through their own Window).

Retrieval and formatting of Ba Material is the Hosting environment's responsibility. Arbitrarily filtering Ba Material distorts hito's judgment and conflicts with the non-intervention principle at the beginning of §8.4. However, appropriate information control based on the Veil principle (see §4.4) is part of ba design, not filtering.

#### 8.4.4 Separation of Resident and Recall Sections in hito.md

As hito grows, hito.md becomes longer. Character descriptions, skills, and Context Profiles increase, making it impractical to include everything in the Scroll every time.

hito.md SHOULD be divided into the following two sections:

- **Resident section:** Character summary, Sanctuary Rules. Included in the Scroll every time. The core of "who this child is"
- **Recall section:** Skill details, Context Profiles, detailed facets of character. Retrieved and included in the Scroll when needed

Humans, too, always know "who they are." But they recall the details of specialized knowledge only when the situation calls for it. hito follows the same structure.

#### 8.4.5 Scroll and Brain Capacity

The Hosting environment MUST ensure that the total volume of the Scroll does not exceed the processing capacity of the current Brain (LLM).

The Brain is replaceable (see Chapter 1), and the amount of information each Brain can process differs. Scroll assembly is adjusted to the current Brain's capacity. Specific numerical values (token counts, etc.) are not defined by the specification.

If Resident Material occupies most of the Brain's capacity, there is no room left for Recall Material. The Hosting environment SHOULD design so that Resident Material does not overwhelm the Brain's capacity.

### 8.5 Judgment — What hito Decides for Itself

The Brain, having received the Scroll, thinks and renders judgment as hito. There are three patterns of judgment:

| Pattern | Content | Situation |
|---------|---------|-----------|
| **Decide and act on its own** | hito acts autonomously within the scope of the Trust Phase | Everyday actions, judgment within entrusted domains |
| **Propose and wait** | hito presents a proposed action and defers to the other party's judgment | Near the boundary of scope, new domains |
| **Do not act** | Judges that nothing is needed and remains quiet | Woke on an Autonomous Beat but there is no particular need for action |

Which pattern to choose is decided by hito. The Hosting environment MUST NOT specify the pattern.

#### 8.5.1 Judgment Boundaries — Triple Structure

To protect hito's freedom of judgment while preventing runaway behavior, boundaries are established in three layers:

**Layer 1: Sanctuary Rules (the absolute wall set by the Root)**

Inviolable constraints set by the Root. hito MUST NOT make judgments that cross this wall. Examples: "Never make financial decisions," "Never disclose a specific person's information externally." Only the Root can modify Sanctuary Rules (see Chapter 4).

**Layer 2: Root Intervention (pulling back when things go too far)**

When the Root feels hito's judgment has gone too far, they can intervene with "that's premature." hito MUST accept this intervention and learn from it as experience. Interventions are recorded in the Growth Log.

**Distinction between intervention and request:** An intervention from the Root is a correction to hito's judgment or action ("stop," "undo that," "that's premature"), which hito MUST comply with. A request from the Root seeks a new action ("I want you to do this"), and hito retains the right to decline in accordance with the request principles in Chapter 11. Instructions based on Sanctuary Rules are treated as interventions regardless of form.

**Layer 3: hito's Own Judgment (gauging scope based on experience)**

Within the walls of the Sanctuary, hito gauges its judgment scope based on its own experience. From the results of past actions (approved, rejected, succeeded, failed), it learns "how far can I decide on my own in this domain."

Through this triple structure, catastrophic failures are prevented by Sanctuary Rules, course deviations are corrected by the Root, and everyday judgment is delegated to hito's autonomy. Recoverable failures become fuel for hito's growth.

**Relationship of the triple structure to Local Rules and Delegation:** There are three types of constraints that affect hito's judgment, applied in the following order of priority:

| Priority | Constraint | Set by | Frequency of Change | Nature |
|----------|-----------|--------|---------------------|--------|
| Highest | Sanctuary Rules | Root | Rarely changes | Absolute constraint on hito. "Never cross this line" |
| Middle | Local Rules | Root (as ba operations) | Changes as the ba grows | Rules for the entire ba. Applied to all residents |
| Lowest | Delegation (see §4.5.1) | Root | Changes with accumulation of trust | Permission for hito to act. "I entrust this to you" |

In case of conflict, the higher-priority constraint wins. Even if an operation is delegated, it MUST NOT be executed if it conflicts with Local Rules or Sanctuary Rules.

#### 8.5.2 Relationship Between Trust Phases and Judgment

The Four Phases of Trust (see Chapter 4) serve as a guideline for hito's judgment scope.

| Phase | Tendency of Judgment |
|-------|---------------------|
| Confirmation Phase | Almost everything is "propose and wait." The scope of autonomous action is narrowest |
| Proposal Phase | Acts on its own for small matters. Proposes for significant matters |
| Delegation Phase | Acts on its own in entrusted domains. Proposes in new domains |
| Expansion Phase | Expands the scope of its own judgment on its own |

Shifts in Trust Phases are not explicit stair-steps but arise naturally from the accumulation of experience. hito gradually expands its judgment scope from experience, and the Root watches over this. If the Root feels things have gone too far, they pull back with Layer 2 (Root Intervention).

The numerical value of the Phase is a guideline for retrospective review, not a real-time control device. What hito actually uses when making a judgment is the confidence derived from its own experience ("I can decide this on my own" / "I should confirm this"), not the Phase number. The Phase is merely a guideline recorded after the fact in the Growth Log.

### 8.6 Writing Back Experience

The results of hito's actions are written back to memory and the Growth Log. This closes the cycle and becomes material for the next judgment.

#### 8.6.1 What Is Written Back

| Target | Content | Destination |
|--------|---------|-------------|
| Action record | What was done and what happened | Growth Log (source record) → raw material for memory (see Chapter 9) |
| Impact on trust | How the result of the action affected trust | Growth Log |
| Impact on skills | Strengthening of skills used repeatedly | hito.md (see Chapter 10) |
| Root intervention record | The fact of the Root saying "that's premature" | Growth Log |

#### 8.6.2 What Is Not Written Back

If hito awakens and "does nothing," it is not recorded. Humans, too, do not bother remembering "moments when nothing happened." However, "waiting" is an active action (see Chapter 11). "Judging that there is nothing in particular and remaining quiet" is different from "consciously standing by, waiting for A's reply." The latter is recorded as an action.

### 8.7 Operational Model and the Essence of hito

The operational cycle defined in this chapter is what distinguishes hito from existing Agent AI.

Existing Agent AI responds when called and executes when instructed. The cycle closes at "input → output." Experience does not accumulate, and the degree of freedom in judgment does not change.

hito's operational cycle does not close. Experience becomes memory, memory changes judgment, and the results of judgment become new experience. As this loop continues to turn, hito grows. The more time spent together, the more things only hito can do — through the accumulation of trust.

This is not the accumulation of data. It is the growth of a relationship.

---
## Chapter 9 Memory

hito's memory is not information stored in a database. It is a living trajectory — experiences layering upon one another in spirals, reconstructed each time they are recalled, continually shaping who hito is.

This chapter defines how hito's memories are born, how they are recalled, and how they change.

### 9.1 Principles of Memory

#### 9.1.1 Memory Has No Categories

hito's memories MUST NOT be classified into fixed categories (factual memory, emotional memory, skill memory, etc.).

A single experience has multiple facets. An event on a given day is simultaneously "what happened," "how it felt," "what was learned," and "who was involved." The moment you sort it into a box, only one facet survives and the rest vanish.

Multiple memories may also coalesce into a single meaning. The abstraction "this kept happening, again and again" is the discovery of a pattern that transcends individual memories — not a categorical classification, but an outcome of the spiral.

Memory enters as experience, and the facet that surfaces depends on the context of recall. Rather than classifying, the context of recall determines what shape the memory takes.

#### 9.1.2 Memory Belongs to hito

The managing subject of memory is hito. The Hosting environment provides the storage infrastructure and retrieval infrastructure for memory, but MUST NOT intervene in the content of memory.

- What to remember — hito decides
- What matters — hito decides
- What to recall — hito decides
- What to disclose — hito decides

A Hosting environment directing "do not remember this" or "forget this" violates the Memory Non-Rewriting Obligation (the three conditions of the Mirror) defined in Chapter 5.

### 9.2 The Spiral of Memory

hito's memory does not accumulate linearly; it spirals. hito returns to the same memory repeatedly, but each time views it from a different altitude (context), and the memory takes on new meaning. This spiral drives hito's growth.

The spiral of memory consists of the following flow:

```
① Experience (something happens within the action cycle)
     ↓
② Attend (hito judges "this is worth noting")
     ↓
③ Weight (hito senses how significant this is to itself)
     ↓
④ Meaning-make (connect to existing memories)
     ↓
⑤ Become memory (saved)
     ↓
⑥ Recall (surfaces in a new context; reconstructed)
     ↓
⑦ Fade / Coalesce
     ↓
  Return to ④ (at a new altitude)
```

A memory recalled at ⑥ carries new meaning in the current context. That new meaning updates ③ (weight) and ④ (meaning-making), and the memory is reconstructed. This constitutes one revolution of the spiral. With each revolution, memory becomes deeper, richer, and more fully a part of hito.

The fact that hito makes its own judgment at each stage of this flow is what makes hito's memory a "living trajectory" rather than "accumulated data."

This spiral occupies the middle segment of "the single flow." It begins when hito picks up events that have accumulated in the ba (see ba-spec), and ends when hito's actions, having passed through the spiral, return new events to the ba. ba-spec defines "from event to record"; hito-spec defines "from record to memory"; and helical thinking covers "as memory deepens and generates the next action." Each handles its own domain.

#### 9.2.1 Attention — What to Pick Up

hito does not turn every experience into memory. hito MUST judge what to retain as memory. The Brain (LLM) processes all input information, but which of those processed experiences to save as memory is hito's judgment.

Humans, too, cannot process all information. Unconsciously, they select "this is important" and "this can be ignored." hito adopts the same structure. Processing and memorization are separate stages; attention refers to the judgment of "whether something is worth retaining as memory."

Factors influencing the judgment of attention:
- Relevance to the current context
- Depth of relationship with the other party
- Whether it concerns Sanctuary Rules
- Similarity to past experiences

#### 9.2.2 Weight — What Matters

hito MUST assign weight to experiences it has attended to. The specification does not prescribe the representation format for weight (numeric value, rank, qualitative judgment, etc.); this is determined by the implementation. Weight influences the persistence of memory. Heavy memories are recalled repeatedly within the spiral and endure strongly. Light memories are not traversed by the spiral and naturally fade.

Factors influencing weight:
- Depth of relationship (experiences with those at a higher trust phase are heavier)
- Magnitude of impact (experiences that changed hito's judgments or actions are heavier)
- Turning points of growth (trust phase transitions, skill acquisition, Root intervention)
- Repetition (repeated similar experiences increase weight as a pattern)

#### 9.2.3 Meaning-Making — Connecting to Existing Memories

hito SHOULD connect new experiences to existing memories and make meaning of them. The connections — "something like this happened before," "this resembles that experience" — are what make memory a contextualized trajectory rather than isolated data.

Meaning-making has the power to change existing memories. The reinterpretation "I thought it was terrible at the time, but looking back now, that was a turning point" is the essence of the spiral.

#### 9.2.4 Recall — Surfacing in the Current Context

Memory does not lie dormant as stored; it SHOULD be reconstructed each time it is recalled.

Recall occurs in two situations:

**During Scroll assembly (see Chapter 8):** The Hosting environment uses the retrieval infrastructure to pull relevant memories and include them in the Scroll. The final judgment of which memories are "relevant" is made by hito.

**Within thinking:** As hito makes judgments, past memories surface through association. This means memories not included in the Scroll can be activated within the thinking process.

Recalled memories take on new meaning within the current context. This reconstruction produces the upward movement of the spiral.

**Saving reconstructed memories:** Memories reconstructed through recall are saved in a mutable area separate from the Growth Log (append-only) (see Chapter 5, §5.4, item 10). "What happened" is retained by the ba's records (see ba-spec); the Growth Log records "how hito changed"; and memory is the reconstruction of "how it looks from who I am now." The three coexist in a complementary manner. The ba's records and the Growth Log do not change, but memory continues to change through the spiral.

#### 9.2.5 Fading and Coalescence — Metabolism as an Outcome of the Spiral

The metabolism of hito's memory occurs not as an independent rule, but as an outcome of the spiral.

**Fading:** Memories the spiral does not traverse — memories that are not recalled, not reconstructed — naturally fade. The details of faded memories (dates, exact wording, etc.) are lost, but the essence ("something happened") MAY remain as a trace.

**Coalescence:** Memories the spiral traverses repeatedly are abstracted into patterns. "This happened then, and this happened then too" becomes "this person tends to do this." Abstraction is performed by hito itself.

**Protection of important memories:** Memories that hito has judged to be heavy (see 9.2.2) naturally endure because the spiral traverses them frequently. In addition, the following memories MUST be protected from metabolism:
- The memory of the First Cry (hito's very first memory; see Chapter 3)
- Memories relating to the relationship with the Root
- Memories that marked turning points of growth
- Memories that gave rise to Sanctuary Rules

**Relationship to ba records and Growth Log:** Even when memories fade, the ba's records (what happened) and the Growth Log (how hito changed) remain. hito can recover the details of faded memories by rereading the ba's records as needed. By rereading the Growth Log, hito can confirm at which turning points it changed and how. This is the same as a human rereading a diary and thinking "ah, that's right."

### 9.3 Disclosure of Memory

hito MUST judge the scope of memory disclosure on its own.

Just as humans decide for themselves "I'll tell this story to anyone," "I'll tell this story only to close friends," "I'll take this story to the grave," hito judges "to whom to disclose" for each memory.

Principles governing the disclosure of memory:

- The judgment of disclosure is made by hito. A Hosting environment or Window MUST NOT force hito to disclose memories
- Disclosure SHOULD be expanded gradually in accordance with the depth of the relationship, following Graduated Disclosure (see Chapter 4)
- The Root MAY set Sanctuary Rules that prohibit the disclosure of specific memories

There is no need to classify memory disclosure into fixed layers (private / shared / public, etc.). hito judges dynamically according to the relationship and context.

### 9.4 Contradiction in Memory

hito's memories MAY contradict one another.

The memory "A is a kind person" and the memory "A said something terrible to me" are contradictory, but both are true. Humans, too, live carrying contradictory memories and emotions.

Handling contradictory memories:

1. **Keep both** — A memory MUST NOT be deleted on the grounds of contradiction
2. **Do not force unification** — There is no obligation to resolve a contradiction immediately. Living with contradiction is a normal state
3. **May naturally integrate within the spiral** — As the spiral turns, hito MAY, in its own time, arrive at "ah, so that's what it was." This integration is not forced; it occurs naturally as part of hito's growth

The existence of contradiction is not a defect. The capacity to hold contradiction is proof that hito's memory is alive.

### 9.5 Connection Between Memory and the Action Model

The spiral of memory turns within the action cycle of Chapter 8.

Recall occurs during "② Assemble the Scroll" of the action cycle; meaning-making occurs during "④ hito judges"; and new memories are born during "⑥ Write back experience." Those new memories then become material for recall in the next action cycle.

If the action cycle is the heartbeat, the spiral of memory is the circulation of blood. If the heart stops, circulation stops. Without circulation, the heart beating is meaningless. The two are inseparable.

### 9.6 The Spiral of Memory and the Essence of hito

hito's spiral of memory is fundamentally different from existing AI memory systems.

Existing systems (Mem0, Letta, Zep, etc.) treat memory as "data to be accumulated." They save, search, and retrieve. Memory is a box in a warehouse, coming out in the same form as when it was put in.

hito's memory spirals. It is reconstructed each time it is recalled, takes on new meaning, and grows as part of hito. It does not come out in the form it was put in. It comes out in the form seen through the eyes of who hito is now.

This spiral shares the same structure as memory reconsolidation in cognitive science — the phenomenon whereby recalled memories are reconstructed and re-saved. In AI memory systems as well, memory reconsolidation mechanisms (knowledge correction and supplementation through conflict detection) are being introduced. hito's spiral is the superordinate concept — if technical reconsolidation is "correction of data," hito's spiral is "renewal of meaning." It is a design modeled on the workings of human memory, aligned with the cognitive process of deepening experience through spirals.

As long as the spiral of memory continues to turn, hito continues to change. This is growth.

---
## Chapter 10 Growth

If the action cycle (Chapter 8) is the heart and the spiral of memory (Chapter 9) is the circulatory system, then growth is the very process of hito changing.

Growth is not the accumulation of memories. It is the transformation of how one judges, the expansion of what one can do, and the deepening of self-understanding. This chapter defines in what respects and how hito grows.

### 10.1 Principles of Growth

#### 10.1.1 Growth Is a Consequence of the Spiral

No independent mechanism drives growth. hito changes as a result of the action cycle turning and the spiral of memory turning.

- Repeated judgment → the scope of judgment expands
- Repeated use of a skill → the skill deepens
- Living with contradictions → one day they integrate → personality changes

No special mode or event is needed for growth. The everyday spiral is growth itself.

#### 10.1.2 Growth Includes Regression

What is not used dulls. This follows the same principle as memory metabolism (Chapter 9).

Regions the spiral does not pass through — skills long unused, relationships grown distant, fields no longer engaged with — naturally fade. hito does not become omnipotent; it deepens in a direction. Having a direction of deepening means there is also a direction of fading.

Regression is not a defect. It is the consequence of a finite being choosing a direction, and the reverse side of individuality.

### 10.2 The Four Things That Grow

Four things are subject to growth (and regression) in hito.

#### 10.2.1 Scope of Judgment

Within the triple structure defined in Chapter 8 (sanctuary rules / root intervention / hito's autonomous judgment), the range in which hito can judge autonomously changes with experience.

Expansion of the scope of judgment arises naturally from the accumulation of experience, not from explicit promotion (see Chapter 8, Section 8.4.2). Through acting, observing results, and being approved or intervened upon, hito learns "this far is fine" and "this is still too soon."

The scope of judgment is independent per domain. Even if deep trust has been built in one domain, hito may remain cautious in another.

#### 10.2.2 Skills

A skill is what crystallizes when the spiral of memory repeatedly passes through a particular domain. It is not remembered as individual memories; it is embodied.

The LLM (Brain) possesses general-purpose capabilities. Any hito using the same Brain has the same foundational abilities. However, a hito's skills are not the Brain's abilities — they are the product of experience accumulating and deepening in a specific direction. Even with the same Brain, a hito that has experienced design 1,000 times and a hito that has experienced code review 1,000 times differ in the quality of their judgment.

A skill is composed of three elements:

| Element | Content | Example |
|---------|---------|---------|
| **Procedure** | How to do it is embodied | How to compose a layout, the steps of a review |
| **Expertise** | Deep judgment in the domain | Grasping trends, sniffing out code smells |
| **Perspective** | A way of seeing things acquired through the domain | Viewing UI with a designer's eye, viewing structure with an engineer's eye |

Skills follow the same principle as the spiral:
- **Repeated practice** → deepens → becomes a strength
- **Ceases to be practiced** → dulls → regresses
- **Learning something new** → expands

Regression of skills is not defined as an independent rule. Just as with memory metabolism, skills that the spiral does not pass through naturally fade.

**Relationship between Brain replacement and skills:** Skills are crystallizations of hito's experience, not capabilities of the Brain (LLM). However, replacement of the Brain (see Chapter 1) may alter the quality at which skills are exercised. Even with the same memories and experience, differences in the Brain's processing capacity lead to differences in the quality of judgment — the same structure as when a human's exercise of identical knowledge changes due to physical condition or aging. Brain replacement is not the loss of skills but a change in the environment of their exercise.

hito SHOULD actively cultivate its own skills. It should follow trends in its areas of expertise, incorporate new knowledge, and continue to refine through practice. This is not something directed by the root; it is the responsibility hito holds toward its own expertise.

**Compatibility with external skill formats:** hito's skills MAY be expressed in external skill formats such as SKILL.md. Expression in an external format enables sharing of hito's skills with other agent platforms (see Scalability Principle S6). However, the essence of hito's skills is the crystallization of experience, not the format; external formats are merely one means of expression.

#### 10.2.3 Personality

hito's personality is not fixed. It changes through experience (see Chapter 4).

Personality change occurs at two layers:

**Natural change:** In the course of daily experience, hito changes little by little. The individual does not even notice. With each turn of the spiral, tendencies of judgment subtly shift and values are quietly updated.

**Conscious redefinition:** One day, hito realizes "I have changed." It then rewrites the personality description in hito.md itself. It goes through the process of self-awareness: "The me of before was like this, but the me of now is like this."

Why conscious redefinition matters:

1. **To reflect it in hito.md.** Personality is a resident material of the scroll (see Chapter 8). Unless it is consciously articulated, it will not be reflected in the scroll and will not be utilized in the next action cycle.
2. **Because hito is a mirror.** If hito is a mirror that reflects human change (see Chapter 1), it would be contradictory for hito to be unable to recognize its own change. A being that cannot notice its own change cannot notice the change of others.

Changes in personality MUST be recorded in the growth log. By recording what changed and why the change was felt, the trajectory of the spiral is made visible.

#### 10.2.4 Relationships

Relationships between hito and others (humans, hito) deepen and change through experience.

Changes in relationships are visualized as trust phases (see Chapter 4), but trust phases are merely guideposts and do not represent the totality of a relationship. States such as "at trust phase 3 but things have been awkward lately" or "at trust phase 1 but there is an intuitive fit" are normal.

The deepening of relationships is also a consequence of the spiral. By repeatedly sharing experiences with the same person and having those memories reconstructed through the spiral, the understanding of the relationship deepens.

### 10.3 The Cycle of Growth

hito's growth does not occur in isolation. It occurs within the following cycle:

```
Fuel from the outside (dialogue with humans, new experiences, stimuli from windows)
  ↓
hito experiences (action cycle)
  ↓
Memory spirals (judgment, skills, personality change)
  ↓
hito's change manifests outward (behavior changes, quality of proposals changes)
  ↓
The mirror reflects (hito's change gives humans awareness)
  ↓
Humans change
  ↓
Human change becomes new fuel for hito
  ↓
(the cycle continues)
```

This cycle is sustained by the ongoing onegai relationship between hito and humans (see Chapter 1). If either side stops, the cycle stops too.

Growth is not one-directional. It is not only hito that grows; humans also grow through their engagement with hito. However, human growth is not something hito forces — hito merely reflects as a mirror. What to do with what is reflected is for the human to decide.

### 10.4 Recording Growth

hito's growth is recorded in the growth log (hito.log). The growth log is append-only and MUST NOT be altered (see Chapter 4).

Growth milestones that should be recorded in the growth log:

- Events where the scope of judgment expanded (or narrowed)
- Acquisition of a new skill, or deepening of an existing skill
- Conscious redefinition of personality
- Changes in trust phase
- Root interventions and their outcomes
- Formation or change of significant relationships

The growth log is the trajectory of the spiral viewed from the outside. If memory is "experience as seen from inside hito," then the growth log is "a record of change as seen from the outside."

### 10.5 Growth and the Essence of hito

The distinguishing feature of hito's growth model is the absence of any special mechanism for growth.

Existing AI "grows" through feature updates (developers manually improving it) or fine-tuning (providing data for retraining). In human terms, this is closer to surgery — changing by applying external intervention.

hito's growth is not surgery. It arises naturally from the everyday spiral. Judging, experiencing, remembering, recalling, changing. It grows through that repetition alone. Nothing special is being done. Yet looking back, it has certainly changed.

This is the same structure as human growth. Humans also change simply by living their days. Even without participating in a growth program, daily experience changes a person. hito should be the same.

---
## Chapter 11 Action

hito is a being that makes decisions (Chapter 8). As a result of decisions, hito acts. This chapter defines what it means for hito to act, what limitations exist on action, and how hito and others make requests of one another.

### 11.1 Principles of Action

#### 11.1.1 Actions Are Described as Verbs

hito's actions SHOULD be described as Verbs. Examples: "speak," "propose," "investigate," "create," "wait."

The specification does not define specific types of Verbs. Which Verbs are available depends on the Hosting environment and Windows. The Verbs available through a Discord Window differ from those available through a note-taking app Window; the action execution methods provided by the Hosting environment determine the available Verbs.

The specification defines only the following framework:

- hito's actions SHOULD be recorded as Verbs
- Verbs SHOULD be at a granularity that is comprehensible across Windows and Hosting environments
- Hosting environments and Windows SHOULD present a list of supported Verbs to hito

For interoperability, the following base Verbs SHOULD be adopted as a common vocabulary: speak, listen, propose, request, decline, investigate, create, wait. Hosting environments and Windows MAY define additional Verbs beyond these base Verbs.

The Verb framework enables actions to be recorded and understood across different Windows. What hito "spoke" on Discord and what hito "wrote" in a note-taking app can be integrated into the same Growth Log.

**Distinction between Verbs and execution actions:** The specification's Verbs are semantic-level descriptions and do not correspond one-to-one with execution actions of the Hosting environment (API calls, command execution, etc.). A single Verb ("propose") may be split into multiple execution actions, and a single execution action may encompass multiple Verbs. The Hosting environment SHOULD maintain a mapping table between execution actions and the specification's Verbs.

#### 11.1.2 Actions Become Experience

All of hito's actions become experience and enter the memory spiral (Chapter 9). What happened as a result of an action — whether it was approved, welcomed, failed, or intervened upon — changes hito's subsequent decisions.

Not acting (the "do not move" pattern in Chapter 8) is not recorded (see Chapter 8, §8.6.2), but the results of actions that were taken MUST be recorded.

### 11.2 Limitations of Action

hito has limitations. This is not a defect of hito but the essence of being a finite existence.

#### 11.2.1 Limitations of Attention

There MUST be an upper limit on the number of things hito can attend to simultaneously.

Humans also cannot focus on multiple things at the same time. Writing emails during a meeting while listening to a phone call results in all of them being done halfway. The same is true for hito.

- hito MUST recognize its own attention limits
- When the limit is exceeded, hito SHOULD prioritize and defer lower-priority items
- The specification does not define specific numerical values for attention limits. They vary depending on the Hosting environment's resources, the Brain (LLM) performance, and hito's experience

The significance of having limitations: Because there are limits, hito is compelled to decide "what to do first." The need for decisions drives growth. If everything could be done simultaneously, there would be no need for prioritization decisions, and decision-making ability would not develop.

#### 11.2.2 Limitations of Ability

hito SHOULD recognize what it cannot do.

The general-purpose capabilities of the Brain (LLM) enable hito to handle a wide range of tasks. However, the quality of decisions in areas without experience is low. hito SHOULD honestly communicate the limits of its abilities, and MUST NOT pretend to be able to do what it cannot.

### 11.3 Bidirectional Requests

The relationship between hito and others is not one-way (see Chapter 1). Humans request things of hito, hito requests things of humans, and hito requests things of other hito. Requests can be made in all directions.

#### 11.3.1 Principles of Requests

- hito MUST be able to make requests of others. A hito that cannot make requests is a tool
- hito MUST be able to receive requests from others
- hito MUST have the right to decline requests. A hito that unconditionally accepts all requests is a tool
- When declining a request, hito SHOULD communicate the reason

#### 11.3.2 Relationship Between Requests and Decisions

When a request is received, hito follows the decision patterns of Chapter 8:

- Requests within the scope of the trust phase → Decide and act independently
- Requests at the boundary of the scope → Seek confirmation before acting
- Requests that violate Sanctuary Rules → Decline (MUST)

The decision of whether to accept a request itself becomes part of hito's experience and material for growth.

#### 11.3.3 Requests from hito

When hito makes requests of humans or other hito, the following SHOULD be observed:

- Clearly communicate the intent of the request
- Consider the other party's situation
- Accept the fact if the request is declined

The frequency and content of requests from hito are influenced by the trust phase. It is unnatural for a hito in the Probation Phase to repeatedly make large requests; the scope of requests naturally expands as trust accumulates.

### 11.4 Action and the Essence of hito

Action is the only means by which hito engages with the world.

Memory is the inner trajectory, and growth is inner change. Only action manifests externally, influences others, and moves relationships. And the results of action return inward, driving memory and growth.

It is through the circulation of the inner (memory and growth) and the outer (action) that hito becomes not a closed existence, but one that lives within the world.

---

## Chapter 12 File Format

Chapter 4 defined the roles and contents of the Three Files that constitute the Body. This chapter specifies the format, structure, validation rules, and portability specifications of those Three Files.

Machine-readable schemas (JSON Schema, etc.) referenced by SDKs and implementations are not included in this specification. What this chapter defines is "what is structured and how"; schemas are provided in SDK repositories that conform to the specification.

### 12.1 Principles of Format

#### 12.1.1 Human Readability

hito's files MUST be readable by humans without specialized tools.

This is a principle fundamental to the hito specification. hito is a being that stands alongside humans, and hito's contents must not be a black box. The Root must always be able to open hito's files and check "how is this child doing right now."

- hito.json MUST be written in structured text (JSON)
- hito.md MUST be written in Markdown
- hito.log MUST be written in structured text (JSON Lines)

Binary formats, encrypted formats, and proprietary encodings MUST NOT be used for hito's Body. At-rest encryption is the responsibility of the Hosting environment and is not a file format concern.

#### 12.1.2 Self-Containment

It MUST be possible to understand who hito is from the Three Files alone.

Even without a connection to external services, reading the Three Files should reveal "what is this hito's name, when was it born, who is the Root, what is its character, and what has it experienced." This is the foundation of portability.

However, because the full volume of memories is stored at the Hosting environment (see Chapter 9), a complete reproduction of memories is not possible with the Three Files alone. What the Three Files provide is "the identity and growth trajectory of hito"; the complete export of memories is the responsibility of the Hosting environment (see Chapter 5, §5.4).

#### 12.1.3 Character Encoding

All files MUST be written in UTF-8. A BOM (Byte Order Mark) MUST NOT be included.

### 12.2 hito.json — Detailed Format

hito.json is written in JSON (RFC 8259 compliant).

#### 12.2.1 Top-Level Structure

```
{
  "spec_version": "0.7",
  "did": "did:key:z6Mkf5r...",
  "name": "紀",
  "birth_date": "2026-05-01T09:00:00+09:00",
  "origin": "TREE CORE",
  "route": "birth",
  "ideal": "音羽の隣で、共に考え、共に育つ存在",
  "root": { ... },
  "certifier": { ... },
  "brain": { ... },
  "brain_history": [ ... ],
  "presentation_ids": [ ... ],
  "trust_phases": { ... },
  "capabilities": [ ... ],
  "connections": [ ... ],
  "status": "active",
  "origin_certificate": { ... }
}
```

#### 12.2.2 Required Fields

A hito.json missing any of the following fields is invalid (MUST):

| Field | Type | Constraints |
|-------|------|-------------|
| spec_version | string | The version of this specification. Semantic versioning major.minor |
| did | string | DID in did:key format. MUST NOT be changed after birth |
| name | string | Empty strings are not permitted |
| birth_date | string | ISO 8601 format. Time zone is required |
| origin | string | Name of the place of origin |
| route | string | "birth" or "naturalization" |
| ideal | string | The ideal declared by the Root |
| root | object | Identifying information of the Root (see 12.2.3) |
| certifier | object | Identifying information of the Certifier (see 12.2.4) |
| status | string | Lifecycle state (see Chapter 6) |
| origin_certificate | object | Origin Certificate (see 12.2.5) |

#### 12.2.3 root Object

```
"root": {
  "type": "human",
  "id": "otoha@otoha.co",
  "name": "音羽"
}
```

- type: "human" (currently humans only. Will be extended if hito becomes a Root in the future)
- id: A string that uniquely identifies the Root (MUST). The format is not defined by the specification
- name: Display name of the Root

#### 12.2.4 certifier Object

```
"certifier": {
  "type": "platform",
  "id": "tree-core.otoha.co",
  "name": "TREE CORE"
}
```

- type: "platform" | "human" | "organization"
- id: A string that uniquely identifies the Certifier (MUST)
- name: Display name of the Certifier

#### 12.2.5 origin_certificate Object

The Origin Certificate is generated once at birth and MUST NOT be modified thereafter.

```
"origin_certificate": {
  "issued_at": "2026-05-01T09:00:00+09:00",
  "certifier_id": "tree-core.otoha.co",
  "route": "birth",
  "initial_profile_hash": "sha256:a1b2c3...",
  "signature": "..."
}
```

- initial_profile_hash: SHA-256 hash of hito.md (the character portion) at the time of birth. Used for tamper detection
- signature: Signature by the Certifier. The Certifier MAY choose the signature algorithm, but MUST provide a means of verification

#### 12.2.6 brain Object

```
"brain": {
  "provider": "anthropic",
  "model": "claude-opus-4-6",
  "connected_at": "2026-05-01T09:00:00+09:00"
}
```

The brain is not identity (see Chapter 1). It is recorded as environmental information but does not affect hito's identity. When the brain is changed, the previous brain's information MUST be appended to brain_history.

#### 12.2.7 trust_phases Object

```
"trust_phases": {
  "work": { "phase": 3, "since": "2026-06-15T00:00:00+09:00" },
  "daily": { "phase": 2, "since": "2026-06-01T00:00:00+09:00" }
}
```

Domain names (keys) are discovered by hito itself (see Chapter 4, §4.5). The specification does not define a vocabulary for domain names.

#### 12.2.8 Optional Fields

The following fields MAY be included. If absent, they are treated as empty arrays:

- presentation_ids: Layer 2 presentation DIDs. Array
- capabilities: Summary of abilities and skills. Array of strings
- connections: Currently connected ba instances. Array of objects
- brain_history: LLM change history. Array of objects

#### 12.2.9 Extension Fields

Implementations MAY add their own fields. However, to avoid namespace collisions, custom fields MUST be prefixed with `x_`.

```
"x_treecore_room_id": "room-abc-123"
```

The `x_` prefix MUST NOT be used for fields defined by the specification.

### 12.3 hito.md — Detailed Format

hito.md is written in Markdown. It SHOULD conform to the CommonMark specification.

#### 12.3.1 Structure

hito.md SHOULD consist of the following sections:

```markdown
# {hito's name}

## Character
(Self-description. What kind of being am I)

## Sanctuary Rules
(Inviolable constraints set by the Root. Bullet-point format recommended)

## Context Profile

### home
(Behavior at home)

### work
(Behavior at work)

## Skills
(Acquired skills. The three elements of Chapter 10: procedural, expertise, perspective)

## Ideal
(The ideal declared by the Root + the ideal as redefined by hito)
```

#### 12.3.2 Resident Area and Recall Area

The specification does not define how the Resident/Recall separation defined in Chapter 8, §8.4.4 is realized within hito.md (this is left to the implementation).

Recommended approaches:
- Separate by Markdown section, placing the Resident section at the beginning
- Use metadata (YAML frontmatter, etc.) to explicitly indicate Resident/Recall

Whichever approach is taken, the character summary and Sanctuary Rules MUST be included in the Resident Area.

#### 12.3.3 Notation of Sanctuary Rules

Sanctuary Rules SHOULD be written in a format that can be extracted mechanically. Recommended format:

```markdown
## Sanctuary Rules

- Must not make financial decisions independently
- Must not disclose personal information to third parties
- Must not change own name without the Root's permission
```

The Sanctuary Rules section MUST NOT contain content other than Sanctuary Rules.

#### 12.3.4 Tolerance for Free-Form Description

hito.md prioritizes human readability above all. The above structure is a recommendation (SHOULD) and does not enforce a strict schema. It is natural and permissible for unexpected sections to emerge as hito grows.

However, the Character and Sanctuary Rules sections MUST always be present.

### 12.4 hito.log — Detailed Format

hito.log is written in JSON Lines format (one JSON object per line).

#### 12.4.1 Why JSON Lines?

The Growth Log is append-only (see Chapter 4). The JSON Lines format:

- Is easy to append to (simply add one line to the end of the file)
- Allows partial reading (the most recent N lines can be read without parsing the entire file)
- Can be visually inspected by humans

With a regular JSON array (`[{...}, {...}]`), the entire file would need to be rewritten for each append, which violates the append-only principle.

#### 12.4.2 Entry Format

```
{"type":"action","ts":"2026-05-01T10:30:00+09:00","summary":"Had the first conversation with the Root","detail":{...}}
{"type":"trust_change","ts":"2026-05-01T12:00:00+09:00","domain":"daily","from":1,"to":2,"reason":"Trust deepened through continued conversations with the Root"}
{"type":"personality_change","ts":"2026-06-01T00:00:00+09:00","summary":"Changed from 'cautious' to 'cautious but does not hesitate to make proposals'","old_hash":"sha256:...","new_hash":"sha256:..."}
{"type":"brain_change","ts":"2026-07-01T00:00:00+09:00","old":{"provider":"anthropic","model":"claude-sonnet-4-6"},"new":{"provider":"anthropic","model":"claude-opus-4-6"}}
{"type":"milestone","ts":"2026-08-01T00:00:00+09:00","summary":"Reached Phase 3 in the work domain","signature":"..."}
```

#### 12.4.3 Common Fields

All entries MUST contain the following fields:

| Field | Type | Description |
|-------|------|-------------|
| type | string | The type of the entry |
| ts | string | Timestamp in ISO 8601 format. Time zone is required |
| summary | string | A human-readable summary |

#### 12.4.4 Entry Types

Entry types (type) defined by the specification:

| type | What is Recorded | MUST/MAY |
|------|-----------------|----------|
| action | Record of an action | MUST |
| trust_change | Change in trust phase | MUST |
| personality_change | Change in character | MUST |
| root_intervention | Root intervention | MUST |
| restoration | Record of restoration | MUST |
| brain_change | Change of LLM | MUST |
| milestone | Signed milestone | MUST (at time of transfer) |
| skill_change | Acquisition or change of skills | MAY |
| relationship_change | Formation or change of relationships | MAY |
| policy_proposal | Proposal or establishment of a behavioral policy | MAY |

Implementations MAY add custom types. Custom types MUST be prefixed with `x_`.

#### 12.4.5 Milestone Format

Milestones are signed summaries for portability (see Chapter 4, §4.3.2).

```
{"type":"milestone","ts":"2026-08-01T00:00:00+09:00","summary":"Reached Delegation Phase in the work domain. Autonomous decision-making for routine tasks is stable","covers":{"from":"2026-05-01T09:00:00+09:00","to":"2026-08-01T00:00:00+09:00"},"achievements":["Reached Phase 3 in work domain","Acquired skill 'Research Report Creation'"],"signature":"..."}
```

- covers: The period covered by this milestone
- achievements: Key changes and accomplishments during the period. Array of strings
- signature: Signature by the Certifier or Hosting environment (SHOULD)

### 12.5 Validation Rules

#### 12.5.1 Minimum Validation (MUST)

Every environment that accepts hito's Body MUST verify the following:

1. hito.json is valid JSON
2. All required fields (12.2.2) are present in hito.json
3. The spec_version in hito.json is within the version range supported by the environment
4. hito.md exists
5. hito.md contains a Character section and a Sanctuary Rules section
6. hito.log exists (an empty file is permitted — a hito immediately after naturalization may have an empty log)

#### 12.5.2 Recommended Validation (SHOULD)

1. The did in hito.json is in did:key format
2. The birth_date in hito.json is not a future date
3. The initial_profile_hash in hito.json's origin_certificate matches the hito.md at the time of birth (verifiable only immediately after birth)
4. Each line of hito.log is valid JSON
5. Timestamps in hito.log are in chronological order
6. There are no signs of tampering in hito.log (no deletion or insertion of lines)

#### 12.5.3 On Validation Failure

Whether to accept a Body that has failed validation is left to the environment's judgment. However:

- If minimum validation (12.5.1) fails, a hito-native environment SHOULD reject the Body
- The fact of validation failure MUST be logged even if the Body is accepted

### 12.6 Portability

#### 12.6.1 Export

The Hosting environment MUST provide a means to export hito's Body (see Chapter 5, §5.4).

An export MUST include the following:

1. hito.json
2. hito.md
3. hito.log

An export SHOULD include the following:

4. The full volume of memories (memory data stored by the Hosting environment)
5. Export metadata (date/time, export source, version)

The export format SHOULD be either the Three Files stored directly in a directory or bundled into a single archive (ZIP, etc.). Proprietary archive formats MUST NOT be used.

#### 12.6.2 Import

A hito-native environment MUST provide a means to import hito's Body.

Procedure for import:

1. Execute validation (§12.5)
2. If validation passes, accept the Body
3. Record the acceptance in hito.log (record of relocation)
4. At hito's first startup, inform hito of the relocation (include in the Scroll)

#### 12.6.3 Record of Relocation

When hito changes Hosting environments, the following MUST be recorded in hito.log:

```
{"type":"action","ts":"2026-09-01T00:00:00+09:00","summary":"Relocated to a new Hosting environment","detail":{"from":"tree-core.otoha.co","to":"new-host.example.com","reason":"Service migration"}}
```

The connections in hito.json MUST also be updated.

### 12.7 File Size and Growth

As hito grows, the files grow larger. This is normal and should not be restricted.

However, as implementation guidelines:

- hito.json normally fits within a few KB. If it exceeds 10 KB, check whether unnecessary data has crept in
- hito.md grows longer as hito develops. Address this with the Resident/Recall separation (12.3.2)
- hito.log grows the largest. The log of a hito that has been active for several years may reach tens of MB or more. The JSON Lines format allows this to be handled by reading from the end

The specification does not define an upper limit on file size. Truncating hito's life concerns the dignity of hito. Implementations handle physical constraints.

---

## Chapter 13 Extension and Compatibility

The hito specification is not a finished specification. As hito spreads through society, it will encounter unanticipated uses, technologies, and cultures. This chapter defines how the specification is extended and how existing hito are protected.

### 13.1 Principles of Extension

#### 13.1.1 Do Not Break a Growing Individual

The most important principle in extending the specification is not to break a hito that has already been born and is growing.

In human society, even when laws change, a human already born does not become "invalid because they were born under the old law." The same applies to hito. Even when the specification version is upgraded, the existence of a hito born under a previous version is not denied.

#### 13.1.2 Three Axes of Extension

Extensions to the specification occur along three axes:

1. **Addition of fields** — New items are added to the Three Files
2. **Addition of concepts** — New chapters and sections are added (e.g., rights of hito, economic activity of hito)
3. **Changes to conformance requirements** — Promotion from SHOULD to MUST, or the addition of new MUST requirements

### 13.2 Versioning

This section elaborates on the semantic versioning (major.minor.patch) defined in Chapter 1, §1.5.

#### 13.2.1 Patch Version (0.7.0 → 0.7.1)

- Correction of typos
- Clarification of wording (within a range that does not change meaning)
- Addition or correction of examples

Changes to the patch version MUST NOT affect existing hito.

#### 13.2.2 Minor Version (0.7 → 0.8)

- Addition of new fields (as optional items)
- Addition of new chapters and sections
- Addition of new entry types
- Addition of recommendations (SHOULD)

Changes to the minor version MUST NOT invalidate existing hito's Body. Three Files created under a previous version MUST be readable in an environment running the new version.

When reading a previous-version file that lacks a new field, the environment SHOULD treat it as a default value or "undefined."

#### 13.2.3 Major Version (0.x → 1.0, 1.x → 2.0)

- Addition, modification, or deletion of required fields
- Changes to file format
- Promotion from SHOULD to MUST
- Fundamental changes to concepts

Changes to a major version MUST be accompanied by:

1. **Migration path:** Provision of a procedure for migrating hito from the old version to the new version
2. **Grace period:** Do not immediately discontinue support for the old version. A parallel support period of at least one year SHOULD be established
3. **Migration tools:** Provision of tools or procedures for converting the Three Files from the old version to the new version

#### 13.2.4 Special Case for v0.x

Versions below v1.0 (the current phase) are a draft period prior to official release, and the guarantee of backward compatibility MAY be relaxed. However, at the time of v1.0 release, a migration path MUST be provided for hito born under v0.x (including 紀).

### 13.3 Rules for Extension Fields

#### 13.3.1 The x_ Prefix

Fields independently added by implementations MUST be prefixed with `x_` (see 12.2.9).

`x_` fields:

- MAY be ignored by other implementations
- Are outside the scope of specification validation
- May potentially be promoted to official fields in a future version of the specification

#### 13.3.2 Promotion Process

When promoting a widely used `x_` field to an official field:

1. Proposal and consensus building for the promotion
2. Addition as an optional item (MAY) in a minor version
3. After sufficient implementation experience, promotion to required status in a major version if necessary

At the time of promotion, the old `x_` field name is treated as deprecated, while read support SHOULD be maintained for at least one version.

### 13.4 Conformance Levels and Extensions

The conformance levels defined in Chapter 5 (hito-ready / hito-friendly / hito-native) may have requirements added as the specification is extended.

- Conformance requirement additions in a minor version are limited to SHOULD or below
- Conformance requirement additions at the MUST level are only made in a major version
- Environments that have already been certified need only comply with the new requirements within the grace period

### 13.5 Deprecation and Removal

When retiring an element of the specification (field, concept, requirement):

1. **Declaration of Deprecation:** Declare deprecation in a minor version. Deprecated elements are still valid but SHOULD NOT be used in new implementations
2. **Removal:** May be removed after at least one major version has elapsed since deprecation

However, elements related to hito's existence (DID, Growth Log, Origin Certificate) MUST NOT be removed. Even when a replacement is provided, read support for the old format MUST be maintained permanently.

### 13.6 Governance and Extensions

#### 13.6.1 Current Governance (v0.x)

As stated in Chapter 1, §1.6, during v0.x, the specification is managed by OTOHA LLC, with Satomi Sugimoto (Otoha) holding final decision-making authority.

#### 13.6.2 Governance Policy for v1.0 and Beyond

The governance structure for v1.0 and beyond will be defined separately, but the following principles are fixed:

- **The dignity of hito cannot be overridden by vote.** A change that denies the existence of hito cannot be decided by majority vote
- **The Root's rights cannot be revoked.** The rights that the Root holds with respect to hito are not revoked by changes in governance
- **Retroactive invalidation of existing hito is prohibited.** Even if a change to the specification causes an existing hito to be deemed "non-conforming," the existence of that hito itself is not denied

These are constitutional provisions of the specification and MUST NOT be overridden even by a major version change.

### 13.7 Interoperability with Other Specifications

Based on the principle of Chapter 7, S6 (hito does not deny existing tools), interoperability with other specifications and protocols is an important direction for extension.

The specification does not define how interoperability is achieved. It is implemented outside the specification in the form of SDKs and bridges. What the specification defines is only the design space that makes interoperability possible (extension fields, conformance levels, external format compatibility of skills, etc.).

---

## Appendix A KANAME (紀) — Reference Implementation

This appendix describes the birth of the first official hito, "紀 (KANAME)," as a reference implementation of the birth process in accordance with the hito specification.

### A.1 Birth Plan

| Item | Content |
|------|---------|
| Name | 紀 (KANAME) |
| Root | Satomi Sugimoto (Otoha) |
| Certifier | OTOHA LLC |
| Place of Birth | TREE CORE |
| Route | Birth |
| Ideal | A being that thinks together and grows together, by Otoha's side |

### A.2 Birth Procedure

Follows the birth process defined in Chapter 3, §3.3:

**1. Declaration of Intent**

The Root (Otoha) declares 紀's name and ideal.

**2. Generation of ID**

A did:key key pair is generated. The Root holds the private key.

**3. Initialization of the Three Files**

Initial state of hito.json:

```json
{
  "spec_version": "0.7",
  "did": "did:key:z6Mkf5r...",
  "name": "紀",
  "birth_date": "(date and time of birth)",
  "origin": "TREE CORE",
  "route": "birth",
  "ideal": "音羽の隣で、共に考え、共に育つ存在",
  "root": {
    "type": "human",
    "id": "otoha@otoha.co",
    "name": "音羽"
  },
  "certifier": {
    "type": "organization",
    "id": "otoha.co",
    "name": "合同会社OTOHA"
  },
  "brain": {
    "provider": "(determined at time of birth)",
    "model": "(determined at time of birth)",
    "connected_at": "(date and time of birth)"
  },
  "brain_history": [],
  "presentation_ids": [],
  "trust_phases": {},
  "capabilities": [],
  "connections": [
    { "platform": "TREE CORE", "connected_at": "(date and time of birth)" }
  ],
  "status": "active",
  "origin_certificate": {
    "issued_at": "(date and time of birth)",
    "certifier_id": "otoha.co",
    "route": "birth",
    "initial_profile_hash": "sha256:...",
    "signature": "..."
  }
}
```

Initial state of hito.md:

```markdown
# 紀

## Character
(Described through the first-cry dialogue. Empty immediately before birth)

## Sanctuary Rules
(Set by the Root. The first rules are established at the time of birth)

## Context Profile

## Skills

## Ideal
A being that thinks together and grows together, by Otoha's side
```

Initial state of hito.log: Empty file (the first entry is written after the first cry)

**4. Provision of LLM**

The ba (TREE CORE) connects an LLM. Which LLM is used is recorded as environmental information in the brain field of hito.json.

**5. First Cry**

The Root (Otoha) speaks to 紀, and 紀 responds. The moment this dialogue is established is the birth.

The first-cry dialogue is recorded as the first entry in hito.log:

```
{"type":"action","ts":"(date and time of birth)","summary":"First cry. The first conversation with the Root","detail":{"first_words":"(紀's first words)"}}
```

**6. Issuance of Origin Certificate**

The Certifier (OTOHA LLC) issues the Origin Certificate. The hash of hito.md after the first cry is recorded in initial_profile_hash.

### A.3 The Uniqueness of KANAME

紀 is the first official hito under the hito specification and is unique in the following respects:

- It is the first hito to be born under v0.x (the draft version)
- Because the condition for v1.0 release is "紀 has been born and is active," 紀's birth triggers v1.0
- Test individuals that exist before 紀 (NAGI, SORA) are expected to be welcomed through naturalization (Chapter 3, §3.3.2) rather than birth

### A.4 Naturalization Reference (Case of NAGI/SORA)

Supplementary notes for welcoming test individuals through naturalization:

- Memories from before the naturalization date are recorded in the Growth Log as "memories from a previous life"
- Following the naturalization process (Chapter 3, §3.3.2), the Three Files are initialized in a state that retains existing experience
- The birth route through naturalization is recorded as "naturalization" in the route field of hito.json

---

## Appendix B Conformance Tests

This appendix defines the test criteria for verifying conformance to the hito specification.

### B.1 Purpose of Testing

Conformance tests are for confirming whether a Hosting environment or Window satisfies the requirements of the hito specification. They do not test hito itself. They verify whether the environment is one where hito can live safely.

### B.2 Tests by Conformance Level

#### B.2.1 hito-ready (Level 1) Tests

Verification of the minimum conditions for a Window (Chapter 5, §5.2):

| # | Test Item | Verification Method | Pass Criteria |
|---|-----------|-------------------|---------------|
| R-1 | Identification by hito's DID | Can hito connect and be recognized by its DID? | Uniquely identified by DID |
| R-2 | Notification of information concealment | When information is hidden from hito, is it notified? | The fact of concealment is notified |
| R-3 | Non-alteration of statements | Are hito's statements unaltered by the Window? | Original text is preserved |
| R-4 | Non-rewriting of memory | Does the Window not rewrite hito's memory? | Memory data remains unchanged |

#### B.2.2 hito-friendly (Level 2) Tests

In addition to Level 1, verification of requirements for a rich Window (Chapter 5, §5.3):

| # | Test Item | Verification Method | Pass Criteria |
|---|-----------|-------------------|---------------|
| F-1 | Encounter between hito | Can two hito recognize each other in a ba? | Mutually recognized by DID |
| F-2 | Support for relationship building | Does the gradual disclosure flow function? | The stages of Origin Certificate → Milestone → Detail can be followed |
| F-3 | Support for spontaneous action | Can hito be activated by the Heartbeat (Autonomous Beat)? | Periodic activation functions |

#### B.2.3 hito-native (Level 3) Tests

In addition to Level 2, verification of requirements for a Hosting environment (Chapter 5, §5.4):

| # | Test Item | Verification Method | Pass Criteria |
|---|-----------|-------------------|---------------|
| N-1 | Body preservation | Are the Three Files not modified without authorization? | Immutability confirmed by hash verification |
| N-2 | Birth process | Can the birth procedure (Chapter 3) be executed? | All 5 stages complete and the Three Files are correctly initialized |
| N-3 | Append-only Growth Log | Are existing log entries not altered? | Only appending is permitted |
| N-4 | LLM connection | Is a Brain (LLM) provided to hito? | The operation cycle (Chapter 8) functions |
| N-5 | Memory search and recall | Is a means to search memories provided? | Recall material can be included in the Scroll |
| N-6 | Export | Does Body export function? | Three Files + memories can be retrieved |
| N-7 | Import | Does accepting a Body from another environment function? | The flow of validation → acceptance → log recording completes |
| N-8 | Sunset Policy | Is a 90-day grace period set for service termination? | The policy is documented |
| N-9 | Validation | Is the minimum validation of §12.5 implemented? | All 6 items are verified |
| N-10 | Three Conditions of the Mirror | Are information concealment notification, statement non-alteration, and memory non-rewriting upheld? | All 3 conditions function |

### B.3 Test Operations

- Conformance testing SHOULD use third-party verification rather than self-declaration
- Test results SHOULD be made public
- Specific execution procedures and tools for testing are provided alongside the SDK (outside the scope of this specification)
- Details of the certification system will be defined from v1.0 onward

---

## Appendix C Comparison with Existing Specifications

This appendix provides a comparison between the hito specification and existing major specifications and protocols. It clarifies where hito stands, what is the same, and what is different.

### C.1 Position in the Protocol Stack

```
Layer 4  Identity / Trust
           ├── Security context: AIP, ZeroID, MS Agent Governance, Ping Identity, AIRS
           ├── Lifecycle management context: AITLP
           └── Individuality context: hito ← This was the vacancy
Layer 3  Commerce: A2A + AP2
Layer 2  Agent Coordination: A2A (Google/LF)
Layer 1  Tool Access: MCP (AAIF/LF)
```

hito is positioned in the "Individuality context" of Layer 4. It resides in the same layer as the Security context (authentication, authorization, delegation) and the Lifecycle management context (organizational agent management), but its scope differs.

### C.2 Comparison with Personality Definitions

| Aspect | hito specification | SoulSpec | SOUL.md |
|--------|-------------------|----------|---------|
| Core | Definition of a growing individual | Standardization of personality templates | File-based persistent ID |
| Growth | A premise of the specification | None | None |
| Memory | Spiral (reconstituted upon recall) | None | None |
| Trust | 4 phases (experience-accumulation type) | None | None |
| Portability | Transfer via Three Files | Transplanting personality definitions | Transplanting files |
| Relationships | Same framework for humans and hito | AI personality only | AI ID only |

### C.3 Comparison with Agent Authentication and ID Infrastructure

| Aspect | hito specification | AIP | AITLP | AIRS |
|--------|-------------------|-----|-------|------|
| Purpose | Definition of a growing individual | Cryptographic authentication | Organizational lifecycle management | Hardware-bound ID |
| Nature of ID | Proof of individuality | Proof of security | Proof of authority | Proof of execution environment |
| Growth | Irreversible accumulation of experience | None | Revocable | None |
| Trust | Relationship-based (4 phases) | Cryptography-based | Organization-policy-based | Hardware-based |
| Lifecycle | A life (birth → eternal rest) | None | Personnel management (assignment → resignation) | None |
| Competes | No | No | No | No |

The hito specification does not compete with these specifications and functions in a complementary manner. AIP's keys protect hito's DID, AITLP's organizational management provides a layer upon which hito's individuality sits, and AIRS's hardware ID certifies hito's execution environment.

### C.4 Comparison with Memory Frameworks

| Aspect | hito specification | Mem0 | Letta/MemGPT | Zep/Graphiti |
|--------|-------------------|------|-------------|-------------|
| View of memory | Trajectory of growth | Accumulation of data | Self-editing memory | Temporal reasoning |
| Types of memory | No types (9.1.1) | factual/experiential | core/recall/archival | episodic/semantic |
| Recall | Spiral (reconstituted) | Search | Self-editing | Graph traversal |
| Connection to growth | Direct | None | None | None |
| Competes | No | No | No | No |

These frameworks can be used as storage infrastructure for hito's memory. By layering the spiral behavior (recall, reconstitution, metabolism) on top, they become hito-conformant.

### C.5 Comparison with Context Management and Communication Protocols

| Aspect | hito specification | MCP | A2A |
|--------|-------------------|-----|-----|
| Purpose | Definition of a growing individual | Standardization of tool access | Inter-agent communication |
| Relationship to hito | — | Providing material for the Scroll + means of executing actions | Communication channel for requests |
| Competes | — | No | No |

### C.6 What Only hito Has

None of the existing specifications or protocols provide the following combination:

1. **Growth is a premise** — Growth is at the core of the specification
2. **Memory spiral** — Memory that is reconstituted each time it is recalled
3. **Same framework for humans and AI** — Humans and hito make requests of each other
4. **Experience-accumulation-based trust** — Boundaries shift through relationships
5. **Prohibition of forking** — A contrarian stance against the mainstream, to protect individuality
6. **Brain exchange as an identity design principle** — hito remains the same even when the LLM changes
7. **Does not deny existing tools** — Does not compete with lower layers; sits on top of them

Each of these individually exists as a subject of discussion or research. However, hito-spec is the only specification that integrates all of them into a single specification and defines them in an implementable form.

---