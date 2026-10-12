# Claude Code Instructions

## Reading order

Read README.md and docs/README.md, then the relevant product requirements, architecture decisions, module specification and delivery task. Load only the documents needed for the task.

## Working rules

- Maintain documentation in English.
- Distinguish approved requirements, proposals, open questions and verified implementation facts.
- Do not infer approval from a folder name or an unreviewed proposal.
- Do not create or update documentation until its complete content has been reviewed and approved by the Product Owner.
- Follow the specification sequence and statuses in docs/README.md. Read linked prerequisites before acting on a specification.
- Keep one authoritative definition per concept and use internal links. Do not link to nonexistent documents.
- Do not record legacy repository attribution, commit references or old document paths.
- The product supports Persian, English and German; respect RTL Persian and LTR English/German layouts.
- Implement against approved requirements and explicit acceptance criteria. Identify unresolved decisions before dependent implementation.
- Link requirement IDs to decisions, tasks and acceptance tests.
- Update affected specifications when behavior changes; keep one authoritative location for each fact.
- Record material architecture decisions in docs/decisions/.
- Verify implementation claims using code, tests or runtime evidence; include the verification date.
- Never commit credentials, tokens, personal customer records or private operational evidence. This repository is public.
- Follow the user's explicit task scope. Do not deploy, apply production migrations or change external systems without authorization.

## Mandatory Permission Review for Every Module

For every new or amended module analysis, explicitly propose and document each relevant role's access: visible panels/menus/tabs, permitted operations, record/field scope, sensitive-action authority and export/history permissions. Include a concrete default-role matrix and distinguish enabled defaults, absent defaults, explicitly delegated permissions and capabilities awaiting domain analysis. Do not finalize a module with only a generic reference to roles.

Reconcile the proposal with the authoritative actors/access, identity, customer, collaborator and privacy specifications. Identify contradictions to the Product Owner before finalizing; update approved source definitions and dependent documents coherently after approval. Assess changes to role templates and affected existing/custom roles. Software updates must not silently overwrite administrator settings or expand ordinary role permissions.

The approved Role Management specification establishes full operational access for Platform Owner and Business Manager throughout the platform, with Business Manager categorically unable to restrict, suspend, disable, remove or take over Platform Owner directly or indirectly. Keep role and dependent specifications aligned with this direction; do not infer permission to bypass law, security verification or protected owner-recovery procedures. Full administrative policy covers newly approved sections; ordinary roles do not gain new permissions automatically.

Catalog and Pricing Coordinator must be considered for the planned service, education and product definition section as well as catalog/pricing. Detailed permissions for that section require its own analysis; this note is not an implemented capability.

## Privacy review

Apply [Data Protection and Privacy — Germany](docs/security/DATA_PROTECTION_AND_PRIVACY.md) to every new or amended specification. Complete PRIV-020 applicability, source, decision and evidence review. Recheck current official EU/German law and regulator guidance where relevant. Do not present approved design as legally certified or technically implemented. Do not override legal retention, lawful communication eligibility or purpose-based access through administrator confirmation. Keep unresolved legal blockers explicit before affected real-data launch.

## Current state

The product vision and Version 1 scope are approved in docs/product/PRODUCT_VISION.md. The approved actors, roles and access model is in docs/security/ACTORS_ROLES_AND_ACCESS.md. The approved identity, accounts and authentication specification is in [docs/security/IDENTITY_ACCOUNTS_AND_AUTHENTICATION.md](docs/security/IDENTITY_ACCOUNTS_AND_AUTHENTICATION.md). The approved [Customer Management specification](docs/modules/CUSTOMER_MANAGEMENT.md) defines the first detailed management module. The approved [Collaborator and Partner Company Management specification](docs/modules/COLLABORATOR_MANAGEMENT.md) defines individual/company records, invitations and profiles. Continue separate theoretical management/staff-module analysis, including Role Management and Access Management, before customer-facing modules. Detailed architecture, technology choices, module specifications and implementation are not approved by this file.

The approved [Role Management specification](docs/modules/ROLE_MANAGEMENT.md) defines reusable role templates, application controls and lifecycle. Continue the separate Access Management analysis next. Mandatory cross-document, privacy, per-module role-matrix and acceptance/evidence reviews are the working process; do not repeat that process as standalone sections in a module unless it defines necessary application behavior.
