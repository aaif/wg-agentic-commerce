## Agentic Commerce

### 1. Working Group Name

* **Working Group Name:** Agentic Commerce
* **Short Name / Acronym:** AC WG
* **Date Approved:** YYYY-MM-DD
* **Last Updated:** YYYY-MM-DD
* **Homepage / Repo (if applicable):** github.com/aaif/wg-agentic-commerce
* **Primary Contact (Chair/Lead):** Ilya Grigorik, Rahul Bansal

---

### 2. Purpose and Mission

**Mission Statement**
The Agentic Commerce Working Group advances the Agentic AI Foundation’s mission by cataloging, aligning, and harmonizing open specifications, frameworks, and terminology for commerce workflows carried out by AI agents on behalf of users, businesses, and software systems. The Working Group provides interoperability guidance and reference architectures across discovery, negotiation, checkout, payment orchestration, and post-purchase lifecycle interactions, supporting convergence of emerging protocols while maintaining protocol neutrality. The Working Group does not author competing commerce protocols; it identifies common ground across existing and emerging work and recommends paths forward to the Technical Committee.

#### Why this Working Group exists
Multiple agentic commerce protocols are emerging in parallel — across merchants, wallets, payment networks, identity providers, and AI platforms — without a neutral forum in which they can be compared, mapped, or aligned. This Working Group exists to be that forum, addressing:

* **Lack of shared vocabulary and reference models** across emerging protocols, including roles, transaction states, delegated authority, and autonomy boundaries.
* **Fragmented interfaces across merchants, wallets, payment providers, and identity systems**, which force each protocol to re-solve the same integration problems and limit composition across ecosystems.
* **Insufficient shared guidance for trust, safety, and accountability** in agent-initiated commerce, leading each protocol to reinvent these primitives independently.

#### Alignment to Foundation Goals
The work of this WG supports:

* **Open interoperability for agentic systems** through common models, interfaces, and implementation guidance.  
* **Safe, trustworthy, and governable agentic AI** through standards-oriented patterns for delegated authority, traceability, and human oversight.
* **Cross-ecosystem collaboration** across identity, trust, security, payments, wallets, and commerce infrastructure.

---

### 3. Scope

#### Scoping Principle

The WG focuses on **interfaces, signals, and interoperability patterns** between agentic systems and the broader commerce stack. The WG does **not** address the **operations, internals, or implementation details** of the underlying systems — those remain with their respective domain owners (payment networks, fraud platforms, identity providers, etc.) or with sibling WGs.

#### In Scope (what the WG will explore)

Across the agentic commerce lifecycle:

* **Discovery & negotiation** — agent–merchant interfaces for offers, availability, terms, and fulfillment options.
* **Cart & checkout** — cart composition, validation, and checkout handoff between agent and merchant systems.
* **Identity & delegated authority** — buyer identity, agent authority scoping, and consent conveyance *(in collaboration with the Identity & Trust WG)*.
* **Agentic payments** — interfaces between agents, wallets, and payment networks (cards, real-time, on-chain); intent, authorization, and settlement signals. **Excludes** the operational mechanics of any specific rail.
* **Fraud signaling** — risk-posture signals exchanged between agents, merchants, and risk systems. **Excludes** detection, mitigation, and resolution.
* **Human-in-the-loop & autonomy boundaries** — confirmation, escalation, and autonomy-level representation.
* **Post-purchase interfaces** — claims, dispute initiation, chargeback signaling, and order-status conveyance.

#### Out of Scope (what the WG will not do)

* **Operations, internals, and implementation details** of any specific commerce system — payment rail operations, fraud detection/mitigation/resolution, identity-provider internals, marketplace operations.
* **Responsible AI and societal-impact policy** — handled at the Foundation level.
* **End-user UI, marketplace product design, and hardware** (PoS, terminals).
* **Non-agentic commerce governance** — legacy topics not specific to agentic flows.
* **Authoring new commerce protocols** — the WG catalogs, aligns, and recommends; it does not produce competing protocol specifications *(see §2)*.

#### Assumptions and Dependencies

**Assumption.** Core agent identity, security, and observability primitives are addressed by sibling WGs. The Agentic Commerce WG focuses on the **commerce-specific application** of those primitives, not their definition.

**Separation of concerns with sibling WGs:**

* **Identity & Trust WG** owns agent and buyer identity primitives, delegation models, and credential formats. **AC WG** applies these to commerce flows (buyer-to-agent delegation in checkout, agent identity in merchant interactions).
* **Security & Privacy WG** owns threat models, encryption, and privacy frameworks. **AC WG** applies these to commerce-specific data (payment data, cart/checkout PII, dispute evidence).
* **Observability & Traceability WG** owns telemetry, audit, and logging frameworks. **AC WG** applies these to commerce signals (transaction audit trails, post-purchase event records).

Coordination is continuous; this WG does not duplicate work in progress in sibling WGs.

---

### 4. Goals, Deliverables, and Success Criteria

#### Initial Goals

1. **Agentic Commerce Capability Map**
2. Agentic Commerce Gap Analysis Document
3. Agentic Commerce Best Practices Guide
4. Agentic Commerce End-to-End Reference Architecture
5. **Recommendations to the Technical Committee on Foundation-Hosted Projects**

#### **Planned Deliverables**
For each deliverable, define owner, format, and target date.

* **Agentic Commerce Capability Map**
  * **Description:** A reference matrix of capabilities the agentic commerce ecosystem must support — across discovery, delegated authority, checkout, payment signaling, fraud signaling, and post-purchase flows — together with a minimal shared frame for roles and lifecycle phases. Existing protocols (UCP, ACP, Mastercard VI, Visa TAP, and others) map their native features to this capability set on their own terms; the WG does not introduce alternative terminology for protocol-defined concepts.
  * **Owner:** [Role/Name], **Format:** report, **Target:** 2026-09-01
* **Recommendations to the Technical Committee on Foundation-Hosted Projects**
  * **Description:** Based on the Capability Map and Gap Analysis, a set of recommendations to the AAIF Technical Committee identifying which existing or emerging agentic commerce projects (or portions thereof) are candidates for hosting under the Foundation. Recommendations include rationale, scope, suggested governance model, and dependencies. The WG does not make hosting decisions; it produces structured input for the TC.
  * **Owner:** [Role/Name], **Format:** report, **Target:** 2026-10-01

**Definition of Done (DoD)**
A deliverable is considered complete when:

* It has been reviewed and approved through the Working Group process.
* It has been published in the Working Group repository or site.
* Any required supporting examples, reference materials, or validation artifacts have been made available.

**Success Metrics (KPIs)** (pick a small set)

* **Alignment:** number of existing or emerging agentic commerce protocols (e.g., UCP, ACP) that incorporate or reference the WG’s capability map and interoperability guidance.
* **Quality:** completion of review process and any applicable security or architecture review.
* **Community:** active contributors, meeting attendance, issue throughput.
* **Timeliness:** percentage of milestones met on schedule.

---

### 5. Working Methods

#### Operating Model
* Consensus-driven / chair-led consensus / voting as fallback  
* Work tracked in: Google docs & GitHub repo  
* Primary artifacts: guidance docs

#### Meetings
* **Cadence:** bi-weekly  
* **Duration:** 60 minutes  
* **Time Zone Considerations:** Pacific Time (PT); meetings are every other Wednesday at 9:00 AM PT starting Wednesday, February 18  
* **Open Meetings:** No — meetings are open to members only  
* **Minutes/Notes:** github.com/aaif/wg-agentic-commerce/meeting-minutes  
* **Recordings:** stored in openprofile.dev calendar

#### Communication Channels
* **Async:**`#wg-agentic-commerce`  
* **Sync:** \[Zoom/Meet\]  
* **Announcements:** wg-agentic-commerce@lists.aaif.io

---

### 6. Membership and Participation

**Who can participate**

* Participation is open to all individuals and organizations consistent with foundation policies.

**Member Roles** (customize as needed)

* **Participants:** anyone attending meetings or contributing asynchronously.  
* **Contributors:** individuals making substantive contributions (issues, PRs, docs, reviews).  
* **Maintainers/Approvers (optional):** individuals with approval rights in repositories.  
* **Chairs/Co-Chairs:** individuals responsible for operations and facilitation.

**Joining**

* To join, a participant should: join the mailing list, join the Discord channel, attend meetings, and sign CLA/DCO if required.

**Expectations**

* Follow the Code of Conduct and collaboration norms.  
* Make contributions in the open (issues/PRs) whenever possible.  
* Declare conflicts of interest when relevant.

---

### 7. Governance and Decision-Making

**Leadership Structure**

* **Chair(s):** Ilya Grigorik  
* **Co-Chair(s):** Rahul Bansal

**Selection and Term**

* Chairs are selected by: election  
* **Term Length:** 12 months  
* **Renewal:** allowed, max 2 consecutive terms  
* **Removal/Resignation:** removal: voted out by 2/3 majority vote, resignation by written email to CTO.

**Decision Process**

* Default method: **rough consensus** documented in issues/meeting notes.  
* When consensus cannot be reached:  
  * Escalation path: \[e.g., TC / Foundation Governing Board\]  
  * Fallback vote rules (if used): quorum \[%\], threshold \[simple majority/supermajority\], voting eligibility \[contributors/maintainers\].

**Quorum (if voting is used)**
* Quorum is met when 50% eligible voters are present or 50% have responded asynchronously.

---

### 8. Relationship to Other Groups

**Sibling Working Groups (intra-Foundation)**

* Security and Privacy WG
* Identity and Trust WG
* Observability and Traceability WG

*See §3 Assumptions and Dependencies for separation of concerns.*

**External Standards Bodies**

* FIDO (Agentic Payments WG)
* OpenID Foundation
* PCI SSC
* EMVCo
* OpenWallet Foundation

**Source Projects (primary inputs to the Capability Map)**

* UCP
* ACP
* Mastercard VI
* Visa TAP
* (and other emerging agentic commerce proposals)

The WG engages with these projects as primary inputs to the Capability Map (§4, Deliverable 1) and may invite their authors to participate directly in the WG’s work.

---

### 9. Intellectual Property, Licensing, and Compliance

(Use language consistent with foundation policies; customize only if you have explicit approval.)

**Licensing**

* Code contributions: per repository license (Apache 2.0)  
* Documentation/specs: per repository license (CC-BY-4.0)

**Contribution Requirements**

* Contributions must comply with DCO/CLA policy, repository contribution guidelines, and review requirements.

**Antitrust and Competition Law**

* Meetings and communications must follow the foundation’s antitrust guidelines.  
* Avoid discussions of pricing, market allocation, or other restricted topics.

**Code of Conduct**

* This WG adheres to the [Linux Foundation Project’s Code of Conduct](https://lfprojects.org/policies/code-of-conduct/).

---

### 10. Security, Safety, and Responsible AI (Agentic AI-Specific)

**Security Practices**

* **Threat modeling expectations:** optional  
* **Vulnerability disclosure process:** per foundation and repository policy  
* **Security review gates for releases:** dependency scanning, SAST, SBOM where applicable

**Agentic Safety and Risk Management**

* **Safety considerations relevant to this WG:** tool access control, delegated authority boundaries, transaction consent, human oversight, fraud signaling interfaces  
* **Required practices (if any):** abuse case documentation and review where applicable  
* **Data handling expectations:** avoid sensitive data in issues, logs, and examples

**Privacy**

* **Guidance for handling personal data:** follow foundation policy and applicable repository guidance  
* **Logging/telemetry guidelines:** collect only what is necessary for observability, traceability, and debugging, and avoid unnecessary sensitive personal or financial data

---

### 11. Deliverable Lifecycle and Publication

**Release Cadence**

* **Expected cadence:** as needed  
* **Versioning scheme:** date-based/spec versioning

**Review and Approval**

* **Required reviewers:** chairs, contributors, and maintainers/approvers as applicable  
* **Approval mechanism:** maintainer approval and chair sign-off

**Archival / Deprecation**

* **Deprecation policy:** documents or artifacts may be deprecated when superseded, with status documented in the repo  
* **Sunset criteria:** no activity for a sustained period or goals achieved

---

### 12. Resources and Budget (Optional)

* **Expected infrastructure needs:** GitHub repository, issue tracking, meeting notes repository, conferencing platform  
* **Funding requests (if any):** \[events, audits, tooling\]  
* **Sponsor engagement model (if applicable):** \[brief description\]

---

### 13. Amendments

This charter may be amended by consensus or vote of the Working Group, with documented notice and updates in the GitHub repository, and subject to TOC/board approval if required.

---

### 14. Ratification

By approving this charter, the Working Group commits to operating transparently, in the open, and in alignment with foundation policies.

* **Approved By:** \[TOC / Governing Board / Steering Committee\]  
* **Date:** \[YYYY-MM-DD\]  
* **Signatories (optional):** \[Names/Titles\]
