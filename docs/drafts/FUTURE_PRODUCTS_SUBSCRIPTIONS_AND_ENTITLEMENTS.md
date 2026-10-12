# Future Idea: Products, Subscriptions and Customer Entitlements

**Status:** Draft — exploratory idea, explicitly outside the approved Version 1 implementation commitment.
**Owner:** Product Owner
**Purpose:** Preserve the future commercial direction separately from approved specifications.
**Implementation status:** Not implemented or verified by this document.
**Authority:** This draft does not override approved product, identity, access or module requirements.
**Privacy prerequisite:** [German data protection baseline](../security/DATA_PROTECTION_AND_PRIVACY.md).

## Idea

Support a combination of individual purchases and subscriptions:
- Live online courses/camps sold as enrollment in a specific event.
- Recorded education with video, visualizations, handouts, animation, learning exercises/tests and checklists. These features need separate Academy analysis; not all are Version 1 commitments.
- Individually purchased recorded courses with access intended to have no contractual expiry, subject to precisely defined customer terms.
- Monthly/yearly subscriptions to selected learning collections.
- Potential Bronze, Silver and Gold service levels. Billing period and benefit level are separate concepts.
- Recurring property-document review, for example a defined number of properties per week or month, rather than only one-off services.
- Consultation subscriptions with defined sessions/minutes.
- Property tools/reports sold individually or included within subscription allowances, potentially supplied through licensed external APIs.

## Architectural Direction to Assess

Keep the fixed customer identity/access baseline separate from commercial entitlements. Customer plans should not become employee-style security roles.

A purchased product or valid subscription can be a source of entitlement to content, service or tool usage. One customer can have multiple concurrent sources. Expiry of a subscription must not remove separately purchased rights. Ongoing accepted service cases require explicit contractual completion rules rather than automatic erasure.

Consider product references, entitlement source, applicable validity and usage allowances where needed. Do not finalize a database schema or implement an entitlement engine solely from this idea.

Paid recurring plans require analysis of renewal, cancellation, failed payments, refunds, upgrades/downgrades, allowance consumption and rollover. Human services require precise deliverable, scope, revision, scheduling and response-time definitions; unlimited service is not assumed.

Define what indefinite/lifetime access means, including content editions, updates and service discontinuation, before advertising it.

## Inspiration — Not Requirements

- [Udemy Personal Plan FAQ](https://support.udemy.com/hc/en-us/articles/1500002721401-Personal-Plan-Frequently-asked-questions): individual purchases can coexist with subscription access.
- [Udemy lifetime-access explanation](https://support.udemy.com/hc/en-us/articles/229603708-Lifetime-access): access conditions require careful definition.
- [Coursera Plus](https://www.coursera.org/courseraplus): subscription to a defined included catalog, not necessarily every product.

Provider offerings may change; verify them during actual commercial analysis.

## External Property Tools and Licensing

Potential inspiration includes ImmoScout24 and property price-atlas/valuation services. No provider, API availability or commercial reuse right is approved.

Before promising integration, verify exact endpoints/data, permission to display and monetize output, analysis/derived-report rights, storage/deletion limits, attribution, export rights, fees/quotas and loss-of-provider handling.

[ImmoScout24 API terms](https://api.immobilienscout24.de/terms-of-use/de/) contain use and storage restrictions. Ordinary API access is not blanket authorization to resell valuation or price-analysis products. A suitable product-specific agreement may be necessary. No scraping or unauthorized reuse is proposed.

## German Legal and Privacy Review

Apply PRIV-020 before future specification or implementation: processing purpose/basis, minimum property documents, third-party data, permissions, notices, retention, suppliers/AVV, international transfers, security and DPIA/DPO screening.

Consumer-subscription rules, cancellation and withdrawal, recurring payments, digital-content obligations and applicable professional-service licensing require separate review. [BGB §312k](https://www.gesetze-im-internet.de/bgb/__312k.html) must be assessed for applicable online consumer subscriptions.

No real customer/property data or confidential API contracts belong in this public draft.

## When to Revisit

Revisit during Catalog/Pricing, Academy, Sales/Payments, Consultation, Specialist Services and integration analysis. Any scope promotion requires explicit Product Owner approval and coherent updates to authoritative specifications.

Customer treatment as a fixed baseline outside editable work-role management is a current analysis decision to align in the authoritative role specification at final approval; this draft itself does not amend that file.

## Open Questions

Catalog inclusion; one-off versus subscription eligibility; benefit levels and prices; duration/allowances; coexistence and cancellation; learning feature scope; legal terms; provider licenses; data flows and operational economics remain undecided.
