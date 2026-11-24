# Agentic Commerce Capability Map: Discovery and Negotiation, Product Facts, Price Disclosure and Quotes (Proposed Input)

**Status:** Working-group participant input for the Capability Map and the Gap Analysis. It is not part of either deliverable until the chairs integrate it. Cells are initial flags: our reading of what each protocol had merged on 2026-11-20, released or not (versions in §7). They are pending the WG's protocol mapping task and review by each protocol's maintainers. Notes say when a counted field is not yet in a release. Row IDs use "DN" for the discovery and negotiation phase.

**Author:** AirShelf, AAIF working group participant. We run UCP endpoints for B2B sellers that sell by quote. We filed or commented on several of the UCP threads cited here, and §7 lists each one.

## 1. Scope and placement

This input covers part of the discovery and negotiation phase in charter §3. It covers what an agent is told about a product, its price and its terms before it buys: product facts, price disclosure, quotes, and a record of what was shown. Charter §3 describes this phase as "agent–merchant interfaces for offers, availability, terms, and fulfillment options". We include product facts in it because an agent relies on them before it buys. The input does not cover product listing and search, which UCP's catalog and ACP's product feed both provide. It also does not cover availability or fulfillment options. Issue #5 covers cross-boundary evidence and audit, and PR #6 covers post-purchase flows. §4 links this input to both.

## 2. Proposed capability rows

**Method.** The rows come from gaps we met while running UCP endpoints for sellers that sell by quote. So several rows match UCP threads we filed or commented on. Other contributors have asked for the same capabilities: ucp#385 for fit claims, ucp#1110 for fact sources, checks and price on request, acp#321 for product claims with proof, and acp#36 for related products. Each cell describes the protocol's merged specification, including changes not yet released. Cells count structured fields and states. Open proposals are not counted in any cell, and §3 lists the ones we found for every protocol.

The six protocols are UCP (Universal Commerce Protocol), ACP (Agentic Commerce Protocol), AP2 (Agent Payments Protocol), x402, Visa's Trusted Agent Protocol (TAP) and Mastercard's Verifiable Intent (VI).

**Flags.** Each cell takes one of four flags. No cell is fully covered.
- **partial**: a merged field or state covers at least one element of the row's capability, for the row's object.
- **not found**: the protocol works at this point in the flow, and we found no merged field or state for the row.
- **not in layer**: the protocol defines nothing at this point in the flow. For DN1 to DN4, it has no way to describe a product before checkout, such as a catalog, a feed or a product schema. For DN5 and DN6, it has no checkout, order or payment request. A protocol that takes payment for one page or one resource does have a payment request, so its DN5 and DN6 cells are not found.
- **out of scope**: the protocol's specification says in its own words that this area is outside its scope, and the protocol defines nothing for the row. If it defines a field for part of the row, the cell is partial. This flag wins over not in layer.

**Rules for every cell.**
1. Object. DN1 to DN3 cover product facts other than price. DN4 covers how a price is disclosed. DN5 covers order lines, meaning one or more items with quantities. DN6 covers a record of the facts, prices or terms shown for products or order lines. A price for one web page or one paid resource is noted but not counted in DN4 to DN6.
2. A cell counts only an explicit field or state. An optional field left empty is not a state. For DN4, a plain price field does not count. DN4 needs a field or state that says which kind of disclosure applies, such as a price only some buyers may see. A link counts as a source only when the specification labels it as one.
3. DN6 counts a record made by either side. The note says whose record it is.
4. A signature shows who served a fact. It does not show who checked it, so it does not count for DN2.

| # | Capability | Description | Representative signals | UCP | ACP | AP2 | x402 | Visa TAP | Mastercard VI |
|---|---|---|---|---|---|---|---|---|---|
| DN1 | Fact source | A product fact can say where it came from: entered by the seller, read from the seller's own document, or inferred. | Source type, document link, page or section, quoted line | not found | not found | out of scope | not in layer | not in layer | not in layer |
| DN2 | Fact check attribution | Who checked a product fact against its source, and when. | Who checked (seller, platform or third party), check time, result | not found | not found | out of scope | not in layer | not in layer | not in layer |
| DN3 | Fit claims with source | A claim that one product fits or works with another, with its source. | Relation type, target product, source | not found | not found | out of scope | not in layer | not in layer | not in layer |
| DN4 | Price disclosure state | Whether an item has a public price, a price on request, a price only some buyers may see, or an indicative range, and for a range, whose price it reflects, such as the maker's list price or a dealer's. | Price state, range, who may see it, basis | not found | not found | out of scope | not in layer | not in layer | not in layer |
| DN5 | Quote and acceptance | A seller-issued price for specific lines, with an expiry, accepted by id and carried to the order. | Quote id, status, expiry, accepted lines | partial | partial | partial | not found | not found | partial |
| DN6 | Record of what was shown | A record of the product facts and terms as served, with the time, that stays checkable if the source changes later. It may be held by the seller, the agent, or both. | Served content or its hash, time, source | partial | partial | partial | not found | not found | partial |

**Notes on the flags:**
- UCP DN1, noted but not counted: an answer from UCP's ask capability, which answers questions in natural language, may carry `links` "related to the answer". They are not labelled as sources.
- ACP DN1, noted but not counted: at checkout, `suggested_price.source` names the feed and feed update a reported price came from (`feed_id`, `feed_update_id`, `updated_at`). It covers prices only, which rule 1 leaves to DN4 to DN6. We count it under DN6. It is merged but not yet released.
- UCP DN4: a variant must carry `price`, with an optional `list_price` for comparison display, so there is no price-on-request state. The sign-in scope `dev.ucp.shopping.catalog.search:read` is described as "personalized results, member pricing, gated inventory". The returned price carries no field saying it is a member price or who may see it, so rule 2 does not count it.
- UCP DN5: a checkout carries business-priced lines and `expires_at`, and the order keeps `checkout_id`. There is no quote object.
- UCP DN6: an order keeps a snapshot of the policies that applied at checkout. A business may sign catalog responses, which covers every fact in them, but signing is optional.
- ACP DN5: a checkout session carries `quote_id` and `quote_expires_at`, and the order links to the session. There is no quote object or step to issue one.
- ACP DN6: at checkout, the agent reports in `suggested_price` the price it showed the buyer, with `observed_at` and its source feed. It is what the agent reports, not a copy of what the seller served. It is merged but not yet released.
- AP2 DN1 to DN4: AP2's specification says "The exact details of the Commerce Protocol (e.g., catalog APIs, checkout updates, and specific APIs for communication between the different roles) are outside the scope of AP2."
- x402, Visa TAP and Mastercard VI DN1 to DN4: none defines a catalog, a feed or a product schema, so these cells read not in layer. x402's Bazaar extension lists paid endpoints for discovery. None states that product information is outside its scope.
- ACP DN4: the feed makes price optional. Rule 2 does not count an empty optional field as a state.
- AP2 DN5 and DN6: the user's signed authorization (mandate) carries the merchant-signed checkout and binds it by hash. AP2 leaves the checkout's format to the commerce protocol. With UCP it is UCP's Checkout object. AP2 defines no expiry for the checkout it binds. A UCP Checkout object carries `expires_at`.
- x402 DN5 and DN6, noted but not counted (rule 1): the offer-and-receipt extension signs an offer for one paid resource (`resourceUrl`), with an optional `validUntil`, and a receipt with `issuedAt`. It prices one resource, not order lines.
- Visa TAP DN5 and DN6, noted but not counted (rule 1): when a merchant asks for payment with HTTP 402 (Payment Required), the agent's Browsing IOU (`browsingIOU`, specification section "Payment") repeats the `invoiceId` and `amount` from that response for one page. It prices a page, not product lines, and has no expiry or time.
- Mastercard VI DN5 and DN6: a checkout token (`checkout_jwt`) that lists items and prices is bound to the mandate by hash. §6.3 says it "SHOULD be signed as a JWS ... using the merchant's private key" (a JWS is a signed JSON token). It also says that in Immediate mode, where the user approves final values, "the agent creates the `checkout_jwt`". Its schema is implementation-defined in v0.1.

## 3. Open proposals and questions found (2026-11-20)

We searched issues, pull requests and discussions in each protocol's public repo. All threads below were open on 2026-11-20. Listing a thread does not mean the WG or its maintainers support it.

| Row | Protocol | Thread | What it adds |
|---|---|---|---|
| DN1 | UCP | ucp#1110 item 8 | A source object on attributes: supplier authored, supplier document or inferred |
| DN2 | UCP | ucp#1110 item 5 | `verified_by` and `verified_at` on certifications |
| DN2 | ACP | acp#321 (spec enhancement proposal, seeking a sponsor) | Product claims linked to an independent proof record, with digest and time |
| DN3 | UCP | ucp#385 | Compatibility claims with relation type, target and source |
| DN3 | ACP | acp#36 | Related products with a relationship type, without a source |
| DN4 | UCP | ucp#969, draft ucp#1042 | Caller-dependent pricing states for price on request, building on ucp#877 |
| DN4 | UCP | ucp#1110 item 1 | Price on request with an indicative range, its visibility and basis |
| DN4 | ACP | acp#45 | For hotels, a non-binding lead price confirmed by quote |
| DN4 | x402 | x402#3181 | Optional typical-price metadata for listed paid endpoints |
| DN5 | UCP | ucp#929, draft ucp#930 | A quote extension accepted by id and carried to the order |
| DN5 | ACP | acp#45, acp#165 | A quote token revalidated at checkout, and line-level `valid_until` |
| DN5 | ACP | acp discussions #209, #318, #320 | A question about quoting before checkout, quote schemas for print from another project, and another project's quote-to-commit model for subscription changes |
| DN5 | AP2 | ap2#69 | A feature request for negotiation, with no fields defined |
| DN5 | x402 | x402#1960, x402#683 | Another project's quote-and-commit protocol, and basket line items |
| DN6 | ACP | acp#329, acp#330 | Signed approval receipts for exact items, amounts and expiry |
| DN6 | ACP | acp#325 (spec enhancement proposal, awaiting a sponsor) | Checkout completion bound to the state the buyer approved: amount, currency and a hash of the line items, which the seller recomputes and refuses on a mismatch |
| DN6 | AP2 | ap2#338 | A dispute evidence file that can be checked offline later |
| DN6 | x402 | x402#2833, x402#2906, x402#3234, x402#3304, x402#3371, x402#3377, x402#3758, x402#3783 | Receipts and delivery evidence, some with a hash of the response served and its time |
| DN6 | Visa TAP | tap#16 | Merchant-signed receipts with a hash of the transaction payload and its time |
| DN6 | Mastercard VI | vi#47 | A format from another project for receipts and dispute evidence |

## 4. Link to evidence for disputes

When a buyer disputes a purchase because a fact or price was wrong, both the buyer's agent and the seller need to show what was served before the purchase. DN6 is the case before purchase of the evidence work in issue #5 and PR #6 row P5, evidence binding. If the chairs prefer, DN6 can be merged into P5 as its phase before purchase. Accepting a quote (DN5) may be evidence of agreed terms. Whether the person who accepted could bind the buyer is a question for P3, buyer authorization and consent evidence. How long these records are kept is one of the retention questions in issue #8. On the WG list (message 37), participants agreed that a principal-verification record should last at least as long as the order can still be disputed. Issue #8 could ask whether a similar floor fits DN6.

## 5. Gap Analysis input (as of 2026-11-20)

- DN1 to DN3. We found no merged specification that gives a single product fact a source type, a quoted line, the party that checked it, or a fit claim with its source. UCP ask answers may carry related links. ACP's unreleased checkout names the feed a reported price came from, which covers prices only. Open UCP proposals cover DN1 and DN3, and DN2 for certifications. ACP has one for DN2, and one for product relations without a source.
- DN4. We found no merged specification with a price-on-request state or an indicative range. UCP's sign-in scope mentions member pricing, but the price itself carries no disclosure state. ACP's feed makes price optional in the released and the unreleased schema, where a variant requires only `id` and `title`. It does not say what a missing price means. Open proposals exist in UCP, ACP and x402.
- DN5. UCP, ACP, AP2 and Mastercard VI cover part of this row. ACP sessions carry a quote id and quote expiry, and UCP checkouts expire. AP2's mandate carries a merchant-signed checkout and binds it by hash. Mastercard VI binds a mandate by hash to a checkout token that lists items and prices, which the agent may create. x402 and Visa TAP price one paid resource or page, which rule 1 does not count. We found none that defines a quote that a seller issues for specific lines before checkout. Open proposals exist in UCP, ACP and x402, and AP2 has a feature request.
- DN6. UCP, AP2 and Mastercard VI record some checkout terms. x402 signs the terms for one paid resource, and Visa TAP's Browsing IOU repeats the amount for one page. Rule 1 does not count either. At checkout, ACP lets an agent report the price it showed the buyer. A signed UCP catalog response covers every fact in it, but signing is optional and we found no protocol that says who keeps it. We found no protocol that requires a record of the product facts shown before checkout. Open proposals in ACP, AP2, x402, Visa TAP and Mastercard VI add receipts and dispute records. Some x402 proposals hash the response served. tap#16 hashes the transaction payload.
- Open proposals change quickly. This input should be rechecked when it is integrated.

## 6. Next steps

- Review of each column by the people who maintain that protocol.
- Alignment of DN6 with issue #5, PR #6 row P5 and issue #8, and of quote acceptance (DN5) with row P3.
- The chairs may prefer to fold DN1, DN2 and DN3 into one row on where a fact came from and who checked it. That works for us.
- Alignment of DN6 with ActionState's evidence layer, presented on the 18 November call, and the IETF drafts it shared on the WG list afterwards, such as draft-mih-agent-evidence-request (datatracker.ietf.org/doc/draft-mih-agent-evidence-request).
- Placement of buyer approval before price. Whether a seller has approved a signed-in buyer to see its prices may belong under identity and delegated authority, next to the buyer-capacity attribute in issue #8 and the principal-verification work MintID presented on 28 October. We left it out of this input's rows for that reason. ACP's checkout lists a `pending_approval` status without a definition. Open issue acp#96 asks for one, and guesses it means approval inside the buyer's own organization. One open proposal covers a seller approving a buyer before showing prices. It is ucp#1047 with draft ucp#1059, which we filed.
- Integration into the map assembly per chair direction.

## 7. Sources

**UCP:** github.com/Universal-Commerce-Protocol/ucp, main at 1be6f77 (2026-11-18, the latest commit on 2026-11-20), release 2026-08-25. Every UCP field we count is in release 2026-08-25. The ask capability joined that release on 2026-11-02 (ucp#1024). `source/schemas/common/ask.json`, `source/schemas/shopping/checkout.json`, `source/schemas/shopping/order.json`, `docs/specification/shopping/catalog/index.md` (scopes), `docs/specification/signatures.md`.

**ACP:** github.com/agentic-commerce-protocol/agentic-commerce-protocol at 7fdd78d (2026-07-18, the latest commit on 2026-11-20), releases to 2026-04-17 plus `spec/unreleased`. `spec/2026-04-17/json-schema/schema.agentic_checkout.json` (`quote_id`, `pending_approval`), `spec/unreleased/json-schema/schema.agentic_checkout.json` (`suggested_price`), `spec/unreleased/json-schema/schema.feed.json`.

**AP2:** github.com/google-agentic-commerce/AP2, v0.2. `docs/ap2/checkout_mandate.md`, `docs/ap2/specification.md`.

**x402:** github.com/x402-foundation/x402 at 971e64f (2026-11-19), spec v2. `specs/x402-specification-v2.md`, `specs/extensions/extension-offer-and-receipt.md`, `specs/extensions/bazaar.md`.

**Visa TAP:** developer.visa.com/docs/trusted-agent-protocol/trusted-agent-protocol-specifications (no version shown, read 2026-11-20), and github.com/visa/trusted-agent-protocol.

**Mastercard:** github.com/agent-intent/verifiable-intent, v0.1 draft. `spec/credential-format.md` §6.2 and §6.3, `spec/constraints.md` §4.2. Mastercard Agent Pay has public identity guides on developer.mastercard.com but no public protocol specification we could find, so the column covers Verifiable Intent only.

**Our UCP involvement:** we filed ucp#877, ucp#1047 and ucp#1059. We commented on ucp#385, ucp#401, ucp#929, ucp#969, ucp#1110 and draft ucp#1123.
