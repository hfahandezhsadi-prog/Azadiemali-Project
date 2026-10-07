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
| migration/ | Legacy source register and review/transfer history |
| templates/ | Reusable specification templates |

Directories are created when their first reviewed document is added.

## Document conventions

Every substantive document must identify its status (Draft, Approved or Superseded), owner, last review date, scope, sources and open questions. Record implementation status separately, with evidence and verification date. Approval of a design does not imply deployment.

Requirements have stable IDs, such as CONS-001. Link requirements to relevant decisions, delivery tasks and acceptance tests. Do not renumber IDs when removing a requirement.

## Reading order

Product vision and scope → relevant requirements → system architecture and decisions → module specification and contracts → delivery task and acceptance criteria.
