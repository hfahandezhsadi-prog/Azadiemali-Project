# Role Management

**Status:** Approved application requirements.
**Owner:** Product Owner
**Scope:** Work-role definitions, initial templates, permissions, inheritance and role lifecycle in User and Collaboration Management.
**Implementation status:** Not verified.
**Prerequisites:** [Actors and Access](../security/ACTORS_ROLES_AND_ACCESS.md), [Identity and Authentication](../security/IDENTITY_ACCOUNTS_AND_AUTHENTICATION.md), [Customer Management](CUSTOMER_MANAGEMENT.md), [Collaborator Management](COLLABORATOR_MANAGEMENT.md), [German Privacy Baseline](../security/DATA_PROTECTION_AND_PRIVACY.md).
**Requirement identifiers:** ROLE-001 through ROLE-012 are stable groups.

## 1. Purpose and Concepts [ROLE-001]

Role Management defines reusable work-role permissions. Version 1 has no separate Access Management menu. Individual assignments, record scope, company/relationship source and start/end timing use the approved Collaborator Management registration/profile paths; do not duplicate conflicting assignment forms here.

| Concept | Meaning |
|---|---|
| System default template | Approved initial configuration for a responsibility |
| Role definition | Saved direct permissions and inheritance, reusable for multiple people |
| Role assignment | Person, role, scope, relationship source and validity |

A role is configured once. For another employee, select the saved role and configure only their assignment particulars.

Customer is a fixed baseline, outside editable work-role management. Platform Owner is protected, with exactly one active holder, outside ordinary creation/copy/assignment/deactivation. All ordinary work roles can have multiple holders.

## 2. Initial Roles and Permissions [ROLE-002]

### Administrative roles

Platform Owner and Business Manager have full operational access to all platform sections, menus, authorized information and application operations. Business Manager cannot directly or indirectly restrict, block, deactivate, delete, replace or take over Platform Owner or their authority. Enforce this in role edits, inheritance, assignments, account actions, recovery, contact/security changes, deletion and collaboration termination.

Full administrative access is a protected policy, including new platform sections; deleting an ordinary grant must not accidentally remove that protected policy. Neither role is exempt from law, secure verification, legal retention, data integrity or protected owner processes. Neither may view passwords or authentication secrets. Ownership transfer remains separate.

### Ordinary initial roles

| Role | Approved initial access |
|---|---|
| User and Collaboration Coordinator | Customer/collaborator operations detailed below |
| Catalog and Pricing Coordinator | Catalog/pricing and the planned service, education and product definition area; exact new-area actions await that area's approved analysis |
| Sales and Customer Relations Coordinator | Necessary customer identity and Academy/consultation/service summaries within scope; permitted registration reminders |
| Academy Coordinator | Necessary customer identity/Academy records and relevant collaborator education summaries within scope |
| Instructor | No central customer/collaborator/role administration by default; instructor-workspace permissions await Academy analysis |
| Consultation Coordinator | Necessary customer identity/consultation records and related collaborator summaries within scope |
| Consultant | No central administration by default; consultant-workspace permissions await consultation analysis |
| Loan Case Coordinator | Necessary customer identity/loan records and related collaborator summaries within scope |
| Specialist Service Provider | No central administration by default; service-workspace permissions await service analysis |
| Finance Officer / Accountant | Necessary customer identity and financial tab within scope; financial-module operations await its analysis |

No hypothetical operational permissions are enabled for unanalyzed areas. Technical Administrator remains subject to separate analysis.

### Defaults for approved modules

Owner/Business Manager have all permitted operations in Customer and Collaborator Management, subject to owner protection and legal/process constraints.

| Role | Customer Management defaults |
|---|---|
| User and Collaboration Coordinator | Customer/incomplete/inactive lists; identity, account-state and relevant administrative history; basic edits/secure contact change; reminders; reset initiation; customer-access disable/restore |
| Sales Coordinator | Necessary identity and Academy/consultation/service summaries within assigned scope; permitted reminders |
| Academy Coordinator | Necessary identity and Academy tab within scope |
| Consultation Coordinator | Necessary identity and consultation tab within scope |
| Loan Coordinator | Necessary identity and loan tab within scope |
| Finance Officer | Necessary identity and finance tab within scope |
| Other ordinary roles | No default central access unless separately approved |

Coordinator whole-account suspend/restore and session revocation require explicit owner delegation. Full customer deletion remains reserved to Owner/Business Manager.

| Role | Collaborator Management defaults |
|---|---|
| User and Collaboration Coordinator | Individual/company lists; record creation/edits; invitations/resend/cancellation; collaboration-status management; necessary profile/account-state and administrative history; reset initiation |
| Relevant domain coordinators | Necessary collaborator information and work summaries for their own domain/scope |
| Instructor/Consultant/Specialist | No central collaborator administration by default |
| Other ordinary roles | No default unless expressly approved |

Coordinator role assignment requires explicit owner delegation. Whole-account suspend/restore and session revocation are not default powers; deletion remains reserved to Owner/Business Manager. History-sensitive details, export and original source records have independent permissions; summary viewing does not grant them.

## 3. Main Page [ROLE-003]

Controls: name/description search; Type filter (All/Default/Custom); Status filter (All/Active/Inactive); Clear Filters; Create Role; and Column Settings.

Table: name, short description, type, status, active-assignment count and source roles. Search/counts and holder details respect viewer scope. Support sort and pagination 20/30/50, default 20.

Select a row to reveal **Role Details** and open a side drawer, preserving filters, page/sort and scroll. Provide keyboard operation and optional full-page display. Customer is absent. A separate **Protected Role** area shows Platform Owner for information only, without ordinary actions.

## 4. Role Details and Settings [ROLE-004]

Header: role name, type/status badges, Close and full-page display. Tabs:
1. Information and Settings.
2. Permissions and Inheritance.
3. People and Dependencies.
4. Change History.

Information starts read-only. Name/responsibility description are editable; internal ID, type and creation/last-change times are system-controlled.

Actions:
- Edit Information: name/description with Save/Cancel.
- Copy Role.
- Compare with Default Template, where a template reference exists.
- Deactivate or Activate according to state.
- Delete only if eligible.

Hide actions outside operator authority. Explain state-based unavailability, e.g. a used role must be deactivated rather than deleted. Server enforcement remains mandatory.

## 5. Create and Copy Forms [ROLE-005]

Three steps:

**Information and basis:** required unique new name, required responsibility description and searchable basis selector: original approved system template or current configuration of a permitted existing role. A new role starts with the chosen basis's settings, not an empty checklist. Owner and Customer cannot be work-role bases. Naming cannot create or impersonate protected owner authority.

**Permissions and inheritance:** load basis settings for adjustment within authority. Permission copying is independent of the original; retained inheritance is a live link and must be explicitly shown. Do not copy people, assignment scopes, company associations or validity dates.

**Review:** show name, description, effective permissions, inheritance and differences from basis; **Create and Save Role**, Back and Cancel. Earlier steps provide Next/Back/Cancel as appropriate.

Saving a definition assigns nobody. A manager may deliberately remove all permissions and save with a clear “This role currently grants no access” message. Editing an existing role loads its last saved settings.

Field-level errors preserve input. Exit with unsaved changes offers Continue Editing or Leave Without Saving.

## 6. Permission Selection [ROLE-006]

Initially read-only, with **Edit Permissions and Inheritance**. Controls: permission title/description search; module filter; Direct/Inherited origin filter; Selected filter; Sensitive filter.

Display approved modules as expandable sections. Permission rows show title, explanation, direct checkbox, sensitivity and inherited source where applicable. Separate list/tab viewing, edits, exports, history and security actions. Use the module-defined permission catalogs, not invented generic grants.

Show inherited access separately so clearing a direct checkbox cannot imply inherited access was removed. Explain dependencies before save; do not silently add permissions.

**Select Current Permissions in This Section** selects only existing permitted operations, never future permissions or reserved authorities. Full deletion restrictions are visibly reserved to Owner/Business Manager and cannot be enabled through custom-role copying.

Footer: Preview Menus and Operations; Review and Save; Cancel. Preview does not imply access to every record; individual scope remains applicable. UI visibility never replaces request-level authorization.

## 7. Inheritance [ROLE-007]

Searchable multi-select for permitted source roles; selected links can be removed in edit mode. Multiple sources are supported; self-inheritance and cycles are rejected.

Show direct, inherited and final permissions with traceable sources. Inheritance transfers permissions, not holders, assignment scopes or dates. Owner and Customer are excluded as sources. Operators must have authority over resulting permissions, including transitive inheritance.

Changing a source affects descendants; include this effect in confirmation. A directly removed permission remains if another direct/inherited path grants it. Reserved deletion/ownership/process constraints remain enforced. Inheritance is optional; independent direct-permission roles are supported. Person-specific standalone Deny overrides remain outside Version 1.

## 8. Review, Save and Concurrent Changes [ROLE-008]

Review dialog shows added/removed permissions, inheritance changes, affected people/roles within authorized visibility, remaining grants from other sources and a required reason for security changes.

Controls: Confirm and Save; Return to Editing. Sensitive changes require fresh secure reauthentication. Validate delegating authority and protected rules server-side at save time.

Prevent silent overwrite when another administrator changed the role. Offer Load Latest State and Review Again, preserving/reviewing intended changes where appropriate.

Successful changes affect current sessions and subsequent/direct requests; stale menus/tokens must not preserve revoked authorization. Exact technical propagation mechanisms remain implementation decisions.

## 9. People and Dependencies [ROLE-009]

Two searchable/filterable/paginated tables:
- Holders: name, collaboration type, assignment scope/state and start/end.
- Dependent roles: name and direct/indirect dependency.

Authorized links open collaborator profiles or role details. Assignment changes use the existing approved assignment path.

To change everyone, edit the shared role. To change one person's scope/time, edit their assignment. To change only one person's permission set, create an adjusted independent role and replace the broader assignment. The adjusted role remains reusable. Explain other active grants that may preserve access.

Keep scope tied to each relevant permission assignment; combining roles must not transfer broad scope from one domain to unrelated permissions.

## 10. Deactivation, Reactivation and Deletion [ROLE-010]

Deactivate prevents new assignment and stops permissions sourced from that role, including inheritance paths. It does not close accounts or end collaborations. Other grants remain.

Before action show holders, descendants and lost/remaining access; require reason and sensitive-action verification.

Reactivate shows restored access and obtains one explicit confirmation. Revoked/expired assignments and assignments restricted by suspended/ended relationships do not revive. Review inherited effects as part of the confirmation.

Delete only custom roles with no usage history or dependencies. Default roles are deactivated rather than fully deleted. A role with usage/history/dependencies is not deletable. Recheck eligibility at execution to prevent concurrent use races. No ordinary lifecycle action can remove or weaken protected ownership or the full administrative policy.

Retain necessary history under defined retention, not indefinitely by default.

## 11. Application Updates and Template Comparison [ROLE-011]

Store approved system templates separately from editable operational definitions. New permissions appear in the catalog after implementation and approval. Ordinary/custom roles do not gain them automatically, administrator settings are not overwritten and custom roles do not reset to their basis.

Compare with Default Template displays current differences. Let the manager select changes to apply; review effects before saving. A full reset cannot conceal added/removed authority. Copying an updated template does not alter earlier independent copies; live inheritance changes still follow ROLE-007.

Full administrative access for Owner/Business Manager is a protected exception, covering approved new sections while preserving owner and legal/process safeguards. Do not spread this exception through custom-role copying/inheritance.

Permissions use stable internal IDs; renaming or moving menus does not alter authority. Retain enough template references to explain comparisons; exact storage/version mechanics remain technical design.

## 12. Administration Authority and Change History [ROLE-012]

Owner and Business Manager may perform all permitted work-role management operations. Others require limited explicit owner delegation. Separate permissions for View, Create, Copy, Edit Information, Change Permissions, Change Inheritance, Deactivate, Reactivate, Eligible Delete and View History/Export. Definition editing does not automatically authorize assignment.

A delegated operator cannot escalate their own or another person's authority beyond delegation through role editing, copying or inheritance. Business Manager cannot affect protected owner authority indirectly through shared definitions or dependencies.

History records creation/copy, metadata/permission/inheritance changes, lifecycle and eligible deletion with actor, time, necessary reason, outcome and before/after difference. Provide search, event/date filters, pagination and View Before/After. No manual history editing/deletion; lawful retention disposal remains applicable.

Holder names, assignments and audit details are personal data: limit access to necessary purposes, protect exports, set retention and preserve data-subject rights independently of administrative role actions. Do not log authentication secrets or store real personal/operational evidence in the public repository. The German privacy baseline governs these behaviors; role permission alone is not a legal basis.

This document defines application behavior. It does not claim implemented controls or legal certification. Unspecified source-domain permissions, audit retention and technical enforcement mechanisms require resolution before their affected operation is launched.
