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

## Current state

The product vision and Version 1 scope are approved in docs/product/PRODUCT_VISION.md. Actors, roles and access are the next analysis. Detailed architecture, technology choices, module specifications and implementation are not approved by this file.
