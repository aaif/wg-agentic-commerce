# Agentic Commerce Capability Map: Post-Purchase Section (Proposed Input)

**Status:** Proposed input for Deliverable 1 (Agentic Commerce Capability Map), submitted via issue #5 and this PR. Prepared for the map assembly; protocol coverage cells are initial flags pending the protocol mapping task (UCP, ACP, AP2, x402).

## 1. Scope and placement

This section covers the post-purchase phase of the agentic commerce lifecycle, per charter §3 ("Post-purchase interfaces: claims, dispute initiation, chargeback signaling, and order-status conveyance") and §4 Deliverable 1. It treats post-purchase as a capability set rather than a protocol: each capability is a requirement any compliant flow must satisfy, independent of the protocol that carries it. Rail internals remain with their owners (charter §3).

Lifecycle placement: the post-purchase phase begins when an order is placed and payment authorization succeeds, and spans order-status conveyance, eligibility and remedy negotiation, state-changing actions (cancel, return, refund, exchange, adjustment), and claims, dispute, and chargeback signaling through resolution.

## 2. Proposed capability rows

| # | Capability | Description | Representative signals / artifacts | Protocol coverage (initial) |
|---|---|---|---|---|
| P1 | Eligibility inquiry | An agent asks what remedies apply to a given order and line item; the merchant responds with transaction-specific options (returns, refunds, exchanges, store credit, cancellations, price adjustments). Eligibility is a negotiation, not a static lookup: it depends on dynamic conditions. | Remedy options per order/line item, eligibility terms, constraints, expiration | UCP, ACP: partial; AP2: partial; x402: none (payment terms only) |
| P2 | Remedy offer and negotiation | Structured exchange of remedy options, constraints, and terms across merchant-specific rules, agent to merchant and back. | Remedy offer, counter-offer, terms, acceptance state | UCP, ACP: partial; AP2: partial; x402: none |
| P3 | Buyer authorization and consent evidence | A representation of what the human principal approved, kept distinct from presentation, including evidence of consent for any state-changing action (renewed approval). | Consent record, principal identity reference, approval scope, authorization timestamp | UCP, ACP: partial; AP2: partial; x402: none |
| P4 | State-change execution signals | Intent, authorization, and completion signals for cancel, return, refund, exchange, and adjustment operations, separate from observation of order state. | Intent signal, authorization signal, execution state, completion receipt | UCP, ACP: partial; AP2: partial; x402: none |
| P5 | Evidence binding | A portable representation connecting the agent, the shopper or organization on whose behalf it acts, the delegation, the transaction, and the consent or intent evidence for each state change, so a later dispute can be resolved without re-negotiating what happened. | Delegation ID, transaction ID, agent and shopper identity references, signed claim, timestamp | Cross-cutting; see §3 |
| P6 | Dispute and claims initiation | Signals for claims, dispute initiation, and chargeback signaling, including evidence submission and resolution state. | Claim signal, dispute initiation trail, evidence submission, resolution state | UCP, ACP: partial; AP2: partial; x402: none |
| P7 | Adjustment ledger | A shared representation of the order event history so agents can reconstruct and explain what happened over time, extending the observation layer discussed in the UCP walkthrough. | Order event history, state transitions, replayable log | UCP: partial; others: not defined |

Cross-boundary dimensions apply across P1-P7: signal provenance (self-reported vs observed marker per signal, source attribution, assurance level) and authorization strength for state changes (the gap between observing an order and initiating a state change, and the evidence supporting each step).

## 3. Evidence and auditability: machine-readable contract

The auditability and evidence-binding capabilities (issue #5 row) are supported by a bounded verification result: a machine-readable verdict envelope that a relying system can consume directly, or use to replay verification when stakes demand it. Minimum fields:

1. verdict (supported | contradicted | unresolvable, the three-state reconciliation)
2. verifier (identity that computed the classification, distinct from the producer)
3. verifier_signature (signed over the verdict and evidence fingerprints)
4. evidence_refs (delegation, transaction, claim/consent references, the binding set)
5. evidence_fingerprints (canonical hashes, RFC 8785, for deterministic replay)
6. verification_basis (which checks were evaluated, so independent verifiers compare like for like)
7. witness_scope (what the verdict does and does not cover)
8. timestamp (freshness)

Consumption rule: a relying system may treat the verdict as bounded when the envelope is complete (verdict bound to evidence, verifier identifiable and signed, scope explicit); otherwise the safe default is replay. The evidence layer standardizes the envelope; the relying party owns the state-to-action rule, fast path versus audit path.

Open questions carried from the row: What is the minimal set of bindings a dispute resolver can rely on? Which records must be retained, by whom, and for how long? How does the envelope interoperate with sibling WG primitives (Observability and Traceability audit trails; Identity and Trust delegation and consent)?

## 4. Gap Analysis input

The June session named the boundary this section addresses: preserving useful evidence across agent, platform, merchant, payment-provider, and risk-system boundaries, and the distinction between agent identity/risk and shopper identity/risk, with evidence binding both to a delegation and transaction. The July session added open questions on merchant receipt, validation, transaction binding, and renewed approval for state changes, and flagged that post-purchase expertise and representation remained limited, a completeness risk for the map.

This section closes that gap as a capability set. Adjacent capabilities (eligibility, remedy, consent, state-change signals, dispute initiation, adjustment ledger) are first-class dimensions here, distinct from discovery, negotiation, checkout, and payment orchestration.

## 5. Next steps

- Protocol coverage mapping (UCP, ACP, AP2, x402, and emerging proposals) against P1-P7, flagging where consent evidence and evidence binding are absent.
- Alignment of the verdict envelope with Observability and Traceability evidence record work and Identity and Trust consent primitives, per charter §3 separation of concerns.
- Integration into the map assembly per chair direction, including lifecycle placement and cross-references to the cross-boundary evidence row.
