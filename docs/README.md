# Documentation Index

## Structure

| Directory | Purpose |
|---|---|
| product/ | Vision, scope, actors, requirements and measurable nonfunctional requirements |
| architecture/ | System context, components, boundaries and deployment design |
| modules/ | Module behavior, business rules and acceptance criteria |
| data/ | Data model, ownership, lifecycle and migration rules |
| contracts/ | API, event and external integration contracts |
| security/ | Authentication, authorization, privacy and security requirements |
| ux/ | User journeys, screen specifications, accessibility and design system |
| testing/ | Test strategy, acceptance coverage and validation evidence |
| decisions/ | Architecture decision records |
| delivery/ | Roadmap, scoped tasks and current handoff |
| operations/ | Deployment, monitoring, backup, recovery and runbooks |
| templates/ | Reusable specification templates |

Directories are created when their first reviewed document is added.

## Document conventions

Every substantive document must identify its status (Draft, Approved or Superseded), owner, scope and open questions. These unreleased specifications do not require update dates or version-history entries. Record implementation status separately, with evidence and verification date. Approval of a design does not imply deployment.

Requirements have stable IDs, such as CONS-001. Link requirements to relevant decisions, delivery tasks and acceptance tests. Do not renumber IDs when removing a requirement.

## Specification Sequence and Status

| Order | Specification | Status |
|---|---|---|
| 1 | [Platform vision and Version 1 scope](product/PRODUCT_VISION.md) | Approved |
| 2 | [Actors, roles and access model](security/ACTORS_ROLES_AND_ACCESS.md) | Approved; domain permission details follow module analysis |
| 2A | [Identity, accounts and authentication](security/IDENTITY_ACCOUNTS_AND_AUTHENTICATION.md) | Approved; operational parameters and recovery procedures require implementation analysis |
| 2B | [Data protection and privacy — Germany](security/DATA_PROTECTION_AND_PRIVACY.md) | Approved baseline; applicability, operating decisions and evidence remain open |
| 3 | [Customer Management](modules/CUSTOMER_MANAGEMENT.md) | Approved; source-domain definitions and legal/operating parameters remain open |
| 4 | Remaining management and staff modules, then customer-facing sections | Separate theoretical analysis and approval required |
| 5 | Overall architecture, module boundaries and relevant user journeys | Planned; detailed decisions not yet approved |
| 6 | Data, API, event and integration contracts | Planned; not yet created |
| 7 | Delivery plan and acceptance testing | Planned; not yet created |

Existing supporting documents:
- [Ownership terminology](architecture/OWNERSHIP_TERMINOLOGY.md): approved terminology only; not a complete role model.
- [Module specification template](templates/MODULE_SPECIFICATION.md): reusable structure, not a completed module specification.

## Dependencies and Internal References

- Each concept has one authoritative definition; other documents link to it rather than redefining it.
- Each specification identifies its reading prerequisites and links to completed prerequisite documents.
- Complete and approve necessary prerequisites before dependent specifications are finalized.
- Do not link to nonexistent documents or treat planned specifications as approved.
- Update prerequisite definitions coherently when domain analysis reveals a required change.
- Internal links are required. Do not record legacy repository attribution, commit references or old document paths.
- Engineering documentation is in English. The product supports Persian, English and German, with RTL Persian and LTR English/German interfaces.
- Do not create or update documents until their complete content has been reviewed and approved by the Product Owner.

## Reading Order

Start with the product vision, actors/access, identity and privacy baseline; then the applicable approved module and any completed prerequisites. Analyze each management/staff section separately before customer-facing sections. Read approved architecture/contracts and delivery criteria when they exist. Every new or changed specification must complete the privacy review in PRIV-020; unresolved legal launch blockers must remain explicit.
