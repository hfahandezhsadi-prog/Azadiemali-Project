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

Every substantive document must identify its status (Draft, Approved or Superseded), owner, last review date, scope and open questions. Record implementation status separately, with evidence and verification date. Approval of a design does not imply deployment.

Requirements have stable IDs, such as CONS-001. Link requirements to relevant decisions, delivery tasks and acceptance tests. Do not renumber IDs when removing a requirement.

## Specification Sequence and Status

| Order | Specification | Status |
|---|---|---|
| 1 | [Platform vision and Version 1 scope](product/PRODUCT_VISION.md) | Approved |
| 2 | [Actors, roles and access model](security/ACTORS_ROLES_AND_ACCESS.md) | Approved; domain permission details follow module analysis |
| 2A | [Identity, accounts and authentication](security/IDENTITY_ACCOUNTS_AND_AUTHENTICATION.md) | Approved; operational parameters and recovery procedures require implementation analysis |
| 3 | Main user journeys | Planned; not yet created |
| 4 | Overall architecture and module boundaries | Planned; not yet created |
| 5 | Dedicated module specifications | Planned; not yet created |
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

Start with the product vision, then read completed actors/access definitions, relevant user journeys, architecture, the applicable module specification and contracts, and finally the delivery task and acceptance criteria.
