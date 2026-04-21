## Agentic Commerce

### 1. Working Group Name

* **Working Group Name:** Agentic Commerc
* **Short Name / Acronym:** AC WG
* **Date Approved:** YYYY-MM-DD
* **Last Updated:** YYYY-MM-DD
* **Homepage / Repo (if applicable): github.com/aaif/wg-agentic-commerc
* **Primary Contact (Chair/Lead):** Ilya Grigorik, Rahul Bansal

---

### 2. Purpose and Mission

**Mission Statement**  
The Agentic Commerce Working Group advances the Agentic AI Foundation’s mission by defining open specifications, frameworks, terminology, interfaces, and interoperability guidance for commerce workflows carried out by AI agents on behalf of users, businesses, and software systems. The Working Group focuses on enabling verifiable, portable, secure, and standards-aligned agentic commerce across discovery, negotiation, checkout, payment orchestration, and post-purchase lifecycle interactions while embracing principles of neutrality. 

#### Why this Working Group exists
This Working Group was formed to address:

* **Lack of shared vocabulary and reference models** for agentic commerce, including roles, transaction states, delegated authority, and autonomy boundaries.  
* **Fragmented interfaces across merchants, wallets, payment providers, and identity systems**, which limit interoperability between agents and commerce systems.  
* **Insufficient guidance for trust, safety, and accountability** in agent-initiated commerce, especially for consent, human oversight, fraud signaling, and post-purchase recourse.

#### Alignment to Foundation Goals
The work of this WG supports:

* **Open interoperability for agentic systems** through common models, interfaces, and implementation guidance.  
* **Safe, trustworthy, and governable agentic AI** through standards-oriented patterns for delegated authority, traceability, and human oversight.  
* **Cross-ecosystem collaboration** across identity, trust, security, payments, wallets, and commerce infrastructure.

---

### 3. Scope

#### In Scope (what the WG will explore)

* Merchant interaction  
  * Discovery & negotiation  
  * Cart, Checkout	  
  * Fraud (signal, interface)   
  * Human in the loop / autonomy  
  * Post-purchase (claims, dispute resolution, chargebacks)  
* Identity & delegated authority (collaboration with Identity and trust)   
* Agentic Payments (settlement)  
  * Wallets (interface)  
  * Interface to payment rails (card networks, real-time, blockchain)  
* Governance (operating within, agent-centric)

#### Out of Scope (what the WG will not do)

* Responsible AI and societal impacts  
* Payment Rails (operations, internals)  
* Fraud (detection, mitigation, resolution) – Security/Observability WGs  
* UIs / marketplaces / hardware (PoS)  
* Governance (existing non-agentic related)   
* Protocol design

#### Assumptions and Dependencies

* **Assumptions:** Identity and trust WG and Security and Privacy WG handling core responsibility with Agentic Commerce collaborating  
* **Dependencies:** Identity and trust WG, Security and Privacy WG, Observability and Traceability

---

### 4. Goals, Deliverables, and Success Criteria

#### 3-6-Month Goals

1. Agentic Commerce Taxonomy
2. Agentic Commerce Gap Analysis Document
3. Agentic Commerce Best Practices Guide
4. Agentic Commerce End-to-End Reference Architecture

#### **Planned Deliverables**
For each deliverable, define owner, format, and target date.

* Agentic Commerce Taxonomy  
  * **Owner:** [Role/Name], **Format:** report, **Target:** 2026-06-01  
* Agentic Commerce Gap Analysis Document  
  * **Owner:** [Role/Name], **Format:** report, **Target:** 2026-07-01  
* Agentic Commerce Best Practices Guide  
  * **Owner:** [Role/Name], **Format:** report, **Target:** 2026-08-01  
* Agentic Commerce End-to-End Reference Architecture  
  * **Owner:** [Role/Name], **Format:** report, **Target:** 2026-10-01

**Definition of Done (DoD)**  
A deliverable is considered complete when:

* It has been reviewed and approved through the Working Group process.  
* It has been published in the Working Group repository or site.  
* Any required supporting examples, reference materials, or validation artifacts have been made available.

**Success Metrics (KPIs)** (pick a small set)

* **Adoption:** number of downstream projects, implementations, or external references adopting WG outputs  
* **Quality:** completion of review process and any applicable security or architecture review  
* **Community:** active contributors, meeting attendance, issue throughput  
* **Timeliness:** percentage of milestones met on schedule

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

**Internal Coordination**

* Security and Privacy WG  
* Identity and Trust WG  
* Observability and Traceability WG

**External Coordination**

* FIDO (Agentic Payments WG)  
* OpenID Foundation  
* Projects:  
  * Google UCP  
  * OpenAI/Stripe ACP  
  * Mastercard VI  
  * Visa TAP  
* PCI SSC  
* EMVCo  
* OpenWallet Foundation

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
