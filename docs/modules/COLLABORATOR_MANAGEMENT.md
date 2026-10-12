# Collaborator and Partner Company Management

**Status:** Approved requirements; operating parameters, source-domain definitions and legal launch decisions remain open.
**Owner:** Product Owner
**Scope:** Individual collaborators, partner companies, invitations, work relationships, assigned roles/scopes, profile summaries and account administration.
**Implementation status:** Not verified. This specification does not certify legal compliance or deployed security.
**Prerequisites:** [Product vision](../product/PRODUCT_VISION.md), [actors and access](../security/ACTORS_ROLES_AND_ACCESS.md), [identity and authentication](../security/IDENTITY_ACCOUNTS_AND_AUTHENTICATION.md), [German privacy baseline](../security/DATA_PROTECTION_AND_PRIVACY.md), and [Customer Management](CUSTOMER_MANAGEMENT.md) for the common table/profile pattern.
**Requirement identifiers:** COLLAB-001 through COLLAB-016 are stable groups. Use them in decisions, tasks and acceptance evidence.

## 1. Purpose and Boundaries [COLLAB-001]

Collaborator Management belongs to User and Collaboration Management. It covers employees, independent consultants/instructors/specialists and partner companies, including their identified representatives.

Manage records, invitations, activation, work relationships, role assignments, scoped access, basic information, account security and administrative history. Display necessary work-responsibility summaries; perform Academy, consultation, service and loan operations in their authoritative modules.

There is no financial tab, bank-information form, remuneration summary, payment or settlement operation here. All collaborator/company finances belong in the platform financial system. This is not a full HR, payroll, attendance or performance-evaluation module. CRM prospects are not added merely because they exist in CRM.

## 2. Workspace and Profile Pattern [COLLAB-002]

Two main tabs:
- **Individual Collaborators:** internal employees, independent collaborators and company representatives.
- **Partner Companies:** company definitions and their work relationships.

Individual lists provide active collaborators, drafts/invitations/incomplete activation or scheduled access, and suspended/ended relationships. Company lists support collaboration-status filtering. Preserve distinctions between work-relationship status, invitation progress and account sign-in status.

Use the approved customer pattern: table, row selection, visible **Collaborator Profile** or **Company Profile** action, then a side drawer with management tabs. Keep the list available and preserve filters, sort, page and scroll. Offer full-page display where needed, including small screens. Selecting another record must clearly update the drawer without mixing information; provide keyboard-accessible selection/focus.

## 3. Shared Identity and Multiple Responsibilities [COLLAB-003]

One person has one stable identity and login account, with multiple customer/work roles if appropriate. Basic identity is shared; customer and work records remain separate.

Adding Consultant to an existing Instructor modifies that account's roles/scopes: no new account, invitation or password. Adding a first work relationship to an existing customer uses the same account after secure matching and completion of work activation/security; do not reset their existing password merely because work access is added. Ambiguous matching requires authorized review, not automatic merging.

Work authentication/recovery takes precedence while an active work relationship remains. Suspending one role does not automatically lower account recovery strength. A company has no shared login; its representatives use individual accounts.

Every access assignment associated with a company must identify that company/work relationship as its source. Independent assignments remain distinguishable, enabling company suspension without cutting unrelated access.

## 4. Individual Table [COLLAB-004]

One row per person, regardless of role count.

Default columns: internal person ID, first/last name, email and verification state, collaboration type, current roles/access areas, linked company where applicable, collaboration status and work-access state.

Display collaboration status as a label such as Active, Suspended or Ended, without numerical summaries. A person with an active collaboration remains Active; display underlying relationship details in the profile. Remaining mixed-status precedence requires implementation analysis; do not confuse active relationships with a suspended whole account.

Optional columns: mobile, record-creation date, work-activation completion, applicable access start/end dates, last account sign-in and last Work Portal use. Work activity is separate from customer activity; show **Not used yet** where absent. Multiple relationship dates must be presented with a clear relationship context, not an arbitrary merged date.

Search permitted IDs/names/emails/mobile across all authorized results. Filter type, company, role, relationship/activation/access state and relevant dates. Support sorting, column preferences, saved settings, clear filters, scoped totals and pagination **20/30/50**, default **20**. Export needs an independent permission. No bulk password reset, suspension or deletion. No internal follow-up-owner field.

## 5. Add Individual Collaborator [COLLAB-005]

| Field | Requirement |
|---|---|
| First and last name | Required |
| Email | Required for invitation and sign-in |
| Mobile | Required for every individual collaborator |
| Collaboration type | Internal, independent or company representative |
| Related company | Required and visible only for a company representative |
| Roles and access areas | Multiple checkboxes from permitted configured roles |
| Scope per role | Explicit within delegating authority |
| Access start | Now or a specified date |
| Access end | Disabled by default; enable only if needed |

No field classifies the supplied mobile as private or company-owned. The number must support the approved SMS process. Applicable employment necessity and suitable employer arrangements still require assessment under PRIV-007; the product policy is not a statutory mandate or permission to compel private-device use.

Related company is a searchable combobox of finalized companies within the administrator's scope. Store its stable ID, show its name, and do not accept free-text company creation here. Draft, suspended and ended companies cannot be selected for a new association. Create the company in Partner Companies first. Existing historical links remain visible under permitted access.

Use one roles/access selection area, not duplicate “activity” and “role” selections. Available initial work roles:
- Business Manager.
- User and Collaboration Coordinator.
- Catalog and Pricing Coordinator.
- Sales and Customer Relations Coordinator.
- Academy Coordinator.
- Instructor.
- Consultation Coordinator.
- Consultant.
- Loan Case Coordinator.
- Specialist Service Provider.
- Finance Officer / Accountant.
- Approved configurable/custom work roles within delegation authority.

All ordinary work roles may have multiple holders. Platform Owner is a single protected active assignment, absent from this form; Customer is not assigned through work-role checkboxes. A Technical Administrator role remains subject to separate analysis.

Selected roles enable their permitted menus/functions only after activation and the access start, using actual effective permissions and scope. Selection does not grant all records in a domain.

Actions: **Save Draft**, without invitation or working access; and **Save and Send Invitation**, after showing roles/scopes and confirmation. Existing collaborator matches direct the administrator to the existing profile to amend roles. Existing customer-only matches use secure work onboarding on the same account. Do not reveal records beyond the operator's scope through matching.

## 6. Invitation, Activation and Token Security [COLLAB-006]

The authoritative activation sequence is AUTH-005: authorized invitation, email link, explicit activation start, automatic SMS, SMS verification, user-chosen permanent password for new accounts, verified authenticator enrollment and recovery codes, then work access when the start date allows. Existing customer passwords/factors follow AUTH-005.4.

Approved timing: invitation link **48 hours from sending**; activation SMS **5 minutes**. SMS expiry alone does not require another email invitation. Resending codes follows operational limits. Invitation timing does not define password-reset-link, owner-recovery or customer-reminder timing.

Security requirements:
- Generate an unpredictable token with a cryptographically secure random generator, bound to its invitation/person and restricted purpose.
- Store a secure validation representation, not a readable reusable token; protect all secret material and keys.
- Enforce expiry, revocation and atomic single consumption, including concurrent use.
- A replacement invitation invalidates the preceding one.
- Use HTTPS and trusted link construction. Prevent token leakage in logs, analytics, third-party requests and manager screens.
- The link grants activation-only access, never working access.
- An email scanner or simple link opening cannot consume activation or trigger SMS; require the person's explicit action.
- Limit guessing, sends/resends and abuse without enabling easy permanent lockout of another person.
- Choose maintained cryptographic libraries and current appropriate parameters during technical architecture; do not invent cryptography or claim “maximum security” without verification.

A successfully exchanged invitation may create a restricted activation session. Its lifetime and continuation rules must be defined so a legitimately unfinished user can resume without reusing a consumed token; it never grants work access. Replacement links retain genuinely valid completed steps without bypassing required current verification. Operational session/resend parameters remain launch blockers.

Reference: [OWASP sensitive-link/token guidance](https://cheatsheetseries.owasp.org/cheatsheets/Forgot_Password_Cheat_Sheet.html), applied to the invitation threat model; it is engineering guidance, not legislation.

## 7. Invitation and Incomplete Activation Management [COLLAB-007]

Columns: person name, email, collaboration type, proposed roles, activation stage, last invitation send, link expiry and inviting administrator.

States: Draft, Awaiting activation start, Activation incomplete, Link expired, Invitation cancelled, or Activation complete / awaiting access start. Delivery failure is a separate outcome, not proof of user inaction.

Actions: view steps/history; edit draft; cancel invitation; replace an expired invitation; correct a sent invitation by cancelling it and issuing a reviewed replacement. On completed working access, remove the person from unfinished lists while retaining justified history.

**Resend Activation Link** is allowed only if activation is incomplete and the link expired. Disable it while valid and after activation. A cancelled invitation requires a separately authorized new issuance. The replacement email is sent to the registered person's email; explicit activation then sends SMS to that person's registered mobile.

Record issuance, cancellation, replacement and completion. Preserve valid completed steps, prevent duplicates and reject superseded links. Cancellation of a customer's work invitation does not close their customer account. Administrators cannot see secrets or manually mark verification/MFA complete.

## 8. Individual Profile — Identity [COLLAB-008]

Six profile tabs: Identity; Collaborations; Roles and Access; Work Activity Summary; Account and Security; Change History.

Identity is read-only: stable ID, first/last name, email/mobile and verification, creation date, completed work activation or unfinished state, last account sign-in, last work use and preferred interface language. Changes use the unified form in Account and Security. Login language selection and subsequent preference changes follow the identity/privacy baseline. Do not expand this tab to home address, birth date, ID documents or banking information.

## 9. Individual Profile — Collaborations [COLLAB-009]

Show actual relationship type, company if relevant, state, start/end where defined, permitted suspension/end reason and last change. Multiple roles within one collaboration do not create multiple collaboration records. Independent collaboration and company representation can be distinct relationships.

Operations: edit; suspend; resume; end; establish renewed collaboration with the same identity/account and preserved justified history. A collaboration end date differs from a role-access end date.

Before stopping a relationship, show affected grants and open courses, sessions, cases or responsibilities requiring review/reassignment. Stop only related work grants, enforce the restriction in existing sessions and preserve independent/customer access. Resume after review without automatically reviving separately revoked/expired grants. Record actor, reason, time and outcome.

## 10. Individual Profile — Roles and Access [COLLAB-010]

Table: role, scope, state (scheduled/active/suspended/expired), start and optional end; show **No end date** when absent.

One **Edit Roles and Access** form shows multiple checkboxes, per-role scope/start and optional end toggle, with Save/Cancel. Show existing assignments and expiry settings accurately; a new optional end is off by default.

Before save display added/removed/narrowed access and end timing. Explain if another role still grants a permission removed from this assignment. Menus derive from effective permissions, not labels alone.

Operators can delegate only permitted roles/scopes. Role-definition creation, copying, inheritance and edits belong in Role Management; this profile assigns existing definitions. Platform Owner is excluded. Sensitive changes require reauthentication and audit. Revoked/narrowed permissions apply to current sessions and direct requests.

## 11. Individual Profile — Work Activity Summary [COLLAB-011]

Show relevant recorded responsibilities:
- Academy: course/class, responsibility, schedule and state.
- Consultations: case/session ID and subject, appointment and state.
- Specialist services: ID/title, responsibility, stage and state.
- Loan cases: ID, responsibility, stage/state and last update.

Summarize current work, items awaiting the collaborator and completed work only where the source module defines these states. Separate current responsibilities from history; role removal does not erase recorded work. Additional managerial activity reports require their own domain analysis.

Provide search, type/state/date filters, pagination and separately authorized source links. Do not reschedule, reassign, edit outcomes or administer education here. Summary visibility does not expose all source documents/confidential notes. No attendance, employee ranking or performance-monitoring capability is approved.

## 12. Individual Profile — Account, Security and Deletion [COLLAB-012]

Display activation/account/work-access state, verified contacts, enabled password/social/passkey methods, MFA status without secrets, and latest invitation/expiry if unfinished.

Independent operations:
- **Edit Information:** one form for first/last name, email and mobile; Save/Cancel. Changed contacts require secure verification before replacement of valid destinations. Lost-factor changes use controlled recovery. Show shared customer-profile effects before saving.
- Resend expired unfinished activation under COLLAB-007.
- Initiate staff password reset under AUTH-018: email plus SMS, user-chosen password, retained MFA and session termination.
- Stop sign-in: blocks all account methods and ends current sessions; warn explicitly about customer access on shared accounts.
- Restore sign-in: review reasons/restrictions; do not restore revoked roles.
- Revoke sessions without deleting roles or ending collaboration.
- Initiate controlled MFA recovery; no direct administrative disable/bypass.
- Delete collaborator under the constraints below.

Work-only restriction belongs in relationship/role management and does not inherently suspend the whole shared account. Administrators never choose/view passwords, register factors on behalf of users or freely overwrite recovery destinations. Sensitive actions need fresh secure authentication, authorization, auditing and appropriate security notifications. Owner-specific protection takes precedence.

### Delete collaborator

Reserved to Platform Owner or Business Manager within legitimate scope. Show course/session/case duties, company associations, financial/contract retention, linked customer relationship and other dependencies. Require reviewed confirmation, reason and reauthentication.

Delete legally deletable collaborator data and revoke work access; preserve necessary restricted records under retention/holds. If also a customer, preserve the customer account/records and necessary shared identity. If only a collaborator, assess closing/deleting login credentials with dependencies and lawful preservation. Never delete the protected owner through this action. State actual deletions, ended links and retained categories/reasons; do not falsely claim complete erasure.

Deletion confirmation cannot override law, legal holds or integrity. Data-subject erasure requests remain a separate rights process.

## 13. Individual Profile — Change History [COLLAB-013]

Record creation/invitation, activation, basic edits, relationship changes, role/scope changes, account/security actions, recovery and deletion. Show time, actor, event, short description, necessary reason and outcome.

Support search, event/date filters, pagination and authorized detail; previous/new field values require appropriate visibility and minimization. No manual edit/delete from this screen. Retention-based disposal remains required. Viewing and exporting history are separate permissions.

Never log passwords, SMS/recovery codes, secret links or authenticator secrets. Recovery evidence remains restricted, not a general history attachment. Logs are administrative/security accountability, not a covert work-performance system.

## 14. Partner Company Records and Profiles [COLLAB-014]

Create the company before creating a related individual representative. Company registration is a record definition, not authentication; no invitation, password, MFA or activation SMS. A required company contact mobile is independent of every representative mobile and must not be labelled verified without verification.

Company table: name, cooperation areas, contact email/mobile, collaboration state and start. Optional internal ID, creation date and end. Use the same scoped search, filters, preferences, sort, export permission and 20/30/50 pagination. Select a row to open Company Profile.

### Company fields and creation

| Field | Requirement |
|---|---|
| Internal ID / platform record creation date | Automatically generated; not requested from the company |
| Full legal name | Required |
| Trading name | Optional if different |
| Legal form | Required, e.g. GmbH, UG, AG, GbR or sole trader |
| Contact email / mobile | Required platform fields |
| Cooperation areas | Multiple selection of approved platform domains |
| Collaboration start | Default today; editable |
| Collaboration end | Off by default; enable when needed |
| Short collaboration description | Optional |
| Business address | Country, city, postcode, street/number; collect before an applicable contracting process needs it |
| Directors / legally authorized representatives | Names and positions, potentially multiple; appropriate to legal form and actual relationship need |
| Commercial register number and court | Where registered and relevant to the process |
| VAT ID (USt-IdNr.) | Where available and needed |
| Website | Optional |

Do not require all conditional legal/business information for an initial definition. Register identity fields belong here when necessary; bank account/IBAN, account-holder details and financial-process-specific tax data are handled solely in Finance when needed. Foundation date, private director contacts and ID copies are not default fields. Naming a legal representative does not create a user or grant authority in the application.

Save Draft or Register Company. Final registration creates active or scheduled cooperation according to start date; no access is granted to anyone. Warn about potential duplicates but never automatically merge by similar name/number. Company fields must remain applicable to foreign legal forms and sole traders without forcing fictitious German register data.

German statutory business-letter, invoice and provider-disclosure requirements apply to their respective operations/entities; they do not universally mandate collecting every partner field at first definition:
- [GmbHG §35a](https://www.gesetze-im-internet.de/gmbhg/__35a.html).
- [UStG §14](https://www.gesetze-im-internet.de/ustg_1980/__14.html).
- [DDG §5](https://www.gesetze-im-internet.de/ddg/__5.html).
Assess applicable form/service and actual legal role before making conditional fields mandatory.

### Three company profile tabs

**Company Information:** read-only company data and a small **Collaborators Linked to This Company** list with name, relationship state and authorized individual-profile link. No separate Representatives tab and no representative creation/invitation/role editing here.

**Collaboration and Settings:** one Edit Information and Collaboration form with Save/Cancel; company contact changes never alter individual contacts. Cooperation-area edits do not silently change individual roles; show inconsistencies for authorized review. Suspend, resume, end and delete operations follow the effects below.

**Change History:** creation/edits/status changes and establishment/end of representative links, with actor/time/reason/outcome and the same restricted history rules.

### Company suspension, end, restoration and deletion

Show affected representatives, company-derived grants and open responsibilities first. Suspend/end only grants sourced from this company; do not suspend representative login accounts, independent work or customer access. Restoration requires review and cannot revive revoked/expired grants.

Company deletion is reserved to Owner/Business Manager, with dependency review, confirmation, reason and reauthentication. Preserve restricted records where legally required, avoid orphaning finance/source records, and report actual erased/retained data and ended links. Do not delete associated individuals simply because a company record is removed.

## 15. Permissions, Defaults and Scope [COLLAB-015]

| Role | Default module authority |
|---|---|
| Platform Owner | Required platform administration subject to legal purpose, minimization and owner safeguards |
| Business Manager | Full operational platform access, including individual/company administration and reserved deletion, equivalent to Owner; no direct/indirect restriction, suspension, deletion or takeover of protected Owner |
| User and Collaboration Coordinator | Records, invitations/resends, edits, relationship-status management and password-reset initiation; no deletion |
| Relevant domain coordinators | Related collaborator information and work summaries within their own domain/scope; no default account-security administration |
| Instructor / Consultant / Specialist Service Provider | No central administration access by default |
| Customer | No access |

Coordinator role assignment requires explicit owner delegation. Whole-account suspend/restore and session revocation are not default coordinator powers. Domain viewing defaults do not grant unrestricted contact, audit, company or other-domain access.

Separate permissions must cover:
- Individual/company lists and each profile tab.
- Create, edit, invite, resend and cancel.
- Suspend/resume/end a relationship.
- Assign roles/change scope.
- Initiate reset; account suspend/restore; session revocation; controlled recovery initiation.
- View history and export.
- Delete individual/company, reserved to Owner/Business Manager.

Apply assigned/team/company/business/platform scopes independently from role inheritance. Counts, match searches, combobox results, source summaries, histories/files and exports follow the same restriction. Source records require source-module permission. No explicit grant means no access. Hide controls and enforce all requests server-side. Role cloning/inheritance cannot bypass reserved deletion or owner constraints. Legal purpose remains required even for broad owner access.

## 16. Privacy Review, Acceptance and Open Decisions [COLLAB-016]

The German privacy baseline is mandatory and takes precedence over administrative confirmation. This module's design review does not establish completed legal assessments or implementation.

| PRIV-020 review item | Applicability and required resolution |
|---|---|
| Purposes, people and minimum fields | Applicable: staff/partner administration, security and responsibility coordination; collect optional/conditional data only for defined needs |
| Legal basis and necessity | Open operating assessment for each activity and mandatory contact field, including BDSG §26 employment context |
| Access and scopes | Applicable: COLLAB-015 and source-scoped work summaries; test field/record isolation |
| Notices and consent | Applicable: Article 13/14 transparency for invitees, directors, representatives and indirectly supplied contacts; no blanket marketing consent |
| Retention/deletion/backups | Open category schedule; COLLAB-012/014 enforce lawful preservation and shared-relationship isolation |
| Rights | Applicable: baseline request pathway works without login and independently of manager deletion powers |
| Suppliers/roles/transfers | Open actual email/SMS/hosting contracts, factual processor/controller roles and transfer assessment |
| Device access/communications | Applicable to portal integrations and messages; no trackers/promotion; assess applicable TDDDG/UWG requirements |
| Security/incidents/evidence | Applicable: restricted activation, token protections, fresh MFA, audit minimization and baseline incident process |
| DPIA/DPO/sector screening | Open assessment against actual deployment; no new profiling or performance monitoring approved |

Entity data alone is not necessarily personal data, but sole-trader data, directors, representatives, named contacts and person-related mobiles/emails may be. Do not exempt the whole company profile from GDPR. Supply Article 14 notices within applicable timing where information comes from administrators, companies or registers, unless a documented exception applies.

Open before affected real-data launch: processing bases/field necessity; employee channel arrangements without private/company classification fields; category retention; supplier/transfers and notices; recovery reviewers/evidence; SMS retry/send limits and restricted-session lifetimes; mixed relationship-status precedence; source-domain definitions/scopes; cryptographic implementation and tests. Exact database topology remains deferred.

Acceptance criteria:
1. Each person is one row/account; adding roles does not issue another invitation/password.
2. Customer-to-work onboarding preserves identity and existing password while requiring work security.
3. Company representative selection reveals a required searchable finalized-company combobox; other types hide it.
4. Required individual/company mobiles remain independent; company records do not trigger authentication.
5. Role checkboxes derive from permitted definitions; Owner is absent and ordinary roles permit multiple holders.
6. Access-end is off by default; scheduled/expired grants enforce their dates.
7. Table/profile state persists with correct scope, pagination and no stale-record mixing.
8. Invitation and SMS expire at 48 hours/5 minutes respectively; token consumption/replacement/scanner handling satisfy COLLAB-006.
9. Resend works only for expired unfinished activation; cancellation leaves customer access intact.
10. Six individual and three company tabs are present; financial functions and a separate Representatives tab are absent.
11. Unified identity edits require valid contact verification and display shared customer effects.
12. Company/relationship suspension revokes only dependent grants in existing sessions and preserves independent/customer access.
13. Deletion is reserved, dependencies visible, owner protected and legal preservation cannot be confirmed away.
14. Audit/history/external source links/export and direct requests enforce independent permissions.
15. Notices, rights, retention and restored backups meet the baseline; operational evidence remains outside the public repository.

Future implementation must link tests/evidence to these groups. No implementation, deployment, licensing or legal certification claim is made here.
