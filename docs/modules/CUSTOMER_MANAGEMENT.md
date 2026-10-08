# Customer Management

**Status:** Approved requirements; domain calculations, operational parameters and legal launch decisions remain open.
**Owner:** Product Owner
**Scope:** Customer lists, registration follow-up, inactive customers, customer profile summaries and account administration in the Staff and Partner Portal.
**Implementation status:** Not verified.
**Prerequisites:** [Product vision](../product/PRODUCT_VISION.md), [actors and access](../security/ACTORS_ROLES_AND_ACCESS.md), [identity and authentication](../security/IDENTITY_ACCOUNTS_AND_AUTHENTICATION.md), [data protection baseline](../security/DATA_PROTECTION_AND_PRIVACY.md).
**Requirement identifiers:** CUST-001 through CUST-017 are stable groups.

## 1. Menu and Boundaries [CUST-001]

The parent section is **User and Collaboration Management** (مدیریت کاربران و همکاری‌ها), with:
1. Customer Management.
2. Collaborator Management.
3. Role Management.
4. Access Management.

Collaborators include employees, consultants, instructors, outside individuals and companies. The external subgroup label is **Specialists and Partner Companies** (متخصصان و شرکت‌های همکار). Its detailed specification follows separate analysis.

Contacts and leads with neither an account nor a purchase belong exclusively in CRM. They must not appear in customer-management lists or search. Sales opportunities and prospective-customer communications are CRM responsibilities; this section is not a lead-management interface.

The module provides a coherent customer overview, not a second academy, consultation, service, loan or finance administration system. Domain-specific changes remain in their authoritative modules.

## 2. Customer and Shared Identity [CUST-002]

Completed registration qualifies a person as a customer even without a purchase. Incomplete registration has its own workflow and status.

The approved website purchase flow requires registration, verification and required authentication before purchase; access to acquired products requires portal sign-in. Service-specific account necessity remains subject to the privacy baseline's launch assessment. A legitimately recorded off-site/existing purchase without a login account may have a customer record, but the system must not silently create login credentials. Such records require a distinct account-not-created label and lawful onboarding.

A customer who is also a collaborator appears in each appropriate relationship list. Identity and login account are shared; customer and collaborator cases and finances are separate. Shared account authentication/recovery follows the active work relationship policy. Domain references use stable identifiers; physical database layout and additional profile fields are deferred.

Initial customer fields remain first name, last name and email, with optional mobile. Do not expand collection to addresses, bank accounts or biographies in this specification. Future domain data can be referenced and selectively displayed after its purpose, access and schema are approved.

## 3. Main Workspace Tabs [CUST-003]

| Tab | Purpose |
|---|---|
| Customers | Completed customer registrations with active customer access; separately labeled legitimate customer records without an account where applicable. |
| Incomplete Registrations | Actual initiated registration attempts whose required steps remain unfinished, not CRM leads. |
| Inactive Users | Previously active customers whose customer access or entire login account has been disabled. |

No recent activity is a filter, not automatically an inactive-account status. Never conflate incomplete, account-not-created, suspended and active states.

## 4. Customer Table [CUST-004]

The comprehensive table supports server-authorized search, filtering, sorting and pagination across all permitted results, not merely the displayed page.

Core columns: customer/person identifier, first and last name, email, mobile (or “Not provided”), registration-start date and last successful account sign-in. Status/account-not-created labels must disambiguate exceptional records. Registration-completion date and last use of the Customer Portal are selectable optional columns to avoid an overloaded default table.

Last account sign-in may be a work sign-in. Record last Customer Portal activity independently. If the customer has never used it, show “Not used yet.” Do not manufacture dates for absent events.

Search by permitted identifier, name, email and mobile. Provide appropriate date, completion and activity filters, including never used; sorting; clear filters; optional-column selection; saved filter/column preferences; permitted-result totals; and page-size choices **20, 30 or 50**, default **20**.

Preserve page, filters, sort and scroll when opening/closing a profile or returning from an authorized source module. Counts and search must not reveal records outside scope. Export is a separate permission and subject to minimization.

## 5. Selection and Profile Drawer [CUST-005]

Selecting a row by mouse or keyboard highlights it and displays the **Customer Profile** (نمایهٔ مشتری) button in a stable table action area. The button opens a large side drawer while the main table remains available. Do not require a permanent details button in every row.

The drawer header identifies the person by name, stable ID and relevant customer/account status. It contains the seven tabs below. Selecting another authorized customer updates the drawer clearly and prevents stale data from the previous selection. Close returns to the preserved table state.

Provide an optional full-page profile view. On smaller displays, the detail view may occupy the screen while preserving return navigation. Define accessible focus, keyboard operation and status announcements in UI implementation. Base the experience on the list/details drawer pattern, as used in record previews; this reference does not mandate a third-party product.

## 6. Incomplete Registration Table [CUST-006]

Display registration-request ID, linked person ID if known, available name/email, method (form/Google/Facebook), start time, current unfinished steps and last recorded action. Steps include email verification, required profile completion and required authenticator/passkey enrollment.

Support search, stage/date/no-progress filters, pagination and access-controlled detail. Clearly distinguish an unverified email from a verified contact. An administrator may view allowed details, resend a valid verification/continuation message or request a reminder. They cannot manually declare channel verification or MFA complete.

Expired or cancelled links must not bypass steps. A continuation link directs the user to the outstanding stage and follows approved authentication requirements. Retention/expiry for abandoned attempts must be decided before real-data launch.

## 7. Registration Reminders [CUST-007]

Provide both automatic and administrator-triggered reminders, with one shared eligibility and send-control system.

**24 and 48 hours are timing proposals, not finalized requirements.** Final timing, maximum counts, intervals and expiry remain open. Enable sending only after the lawful-basis and UWG assessment described in the privacy baseline.

Show total sends, automatic/manual breakdown, last send, sending actor where manual, status and subsequent progress/completion. Distinguish queued, sent and failed; show delivery only when reliable provider evidence exists. Completion after a reminder is an observed sequence, not proof of attribution.

Manual sending must show previous reminders and be subject to the same limits as automatic sending. Prevent duplicates from repeated clicks, concurrent jobs or retries. Recheck registration state and legal eligibility immediately before dispatch. Cancel pending messages when registration completes or eligibility ends. Use expiring single-use continuation/verification mechanisms without skipping required security.

Keep content directed to completing the current registration stage. Do not add marketing, email-opening trackers or imply consent from an incomplete attempt. Audit sends and outcomes without storing secret-bearing links. Reminder history itself needs justified retention.

## 8. Inactive User Table [CUST-008]

Show customer identifier, name/contact, registration date, suspension date/type, recorded reason and last relevant activity. Administrative actor and detailed reason are available only to authorized reviewers.

Distinguish **Customer access disabled** from **Stop sign-in** (توقف ورود به سیستم), which suspends the shared login account. For a customer–collaborator, show the consequence for work access before a whole-account action.

Provide search and status/reason/date filters, profile access and permitted restoration. Restoring customer access does not restore revoked work roles. Review the reason and remaining restrictions before reactivation.

## 9. Profile Tab 1 — Identity and General Information [CUST-009]

Show registered identity/contact information, verification states, registration start/completion, last account sign-in, independent last Customer Portal use and customer/account status. Display permitted status reason/time as appropriate.

This tab is primarily read-only. Basic/contact changes occur through account management. Internal IDs, historical event timestamps and verification facts are not freely editable. Show only necessary authorized information, not every underlying domain field. Do not display passwords, codes, TOTP secrets or secret-bearing links.

## 10. Profile Tab 2 — Academy and Education [CUST-010]

Provide a useful customer-status summary and available history:
- Educational-package count, course/camp enrollment count, active entitlements and latest recorded learning activity.
- Package title, acquisition date, free/paid designation, access state/expiry and progress or last activity only when implemented in the Academy.
- Course/camp title and instance, enrollment date, schedule, instructor, enrollment status, and attendance/completion only where recorded by the source module.

Provide search, relevant filters, pagination and authorized links to the source Academy record. Do not introduce mandatory progress tracking, examinations or certificates through this overview. Purchase/payment details refer to the financial tab. Enrollment, attendance corrections, scheduling and content administration remain in the Academy.

## 11. Profile Tab 3 — Consultations [CUST-011]

Summarize requests, sessions, open items and next appointment when recorded. Show subject, request/session date, assigned consultant or “Unassigned,” scheduling state, status and authorized outcome summary.

Provide relevant search/filters/pagination and links to the source request/session. Show reschedule/cancellation history if already recorded. Confidential consultant notes require their own permission and must not be disclosed automatically. Scheduling, cancellation, assignment and professional note entry remain in consultation management.

## 12. Profile Tab 4 — Services [CUST-012]

Show total/open/completed services and customer service history: ID, title, request date, responsible person/company, status/stage, last update and permitted outcome or deliverable summary.

Support search, filters, pagination and authorized source links. Do not duplicate service assignment, stage changes, document editing or delivery operations in this tab.

## 13. Profile Tab 5 — Loan and Banking-Related Cases [CUST-013]

Provide a reporting overview: total/open cases and cases awaiting documents; ID, subject, creation date, responsible person, state/stage, document-status summary, last follow-up and recorded outcome/proposal.

Search/filter/paginate permitted records and link to the source case. Do not expose document contents or confidential assessments solely because a summary is visible. No live banking integration, loan decision entry or specialist case administration is introduced here.

## 14. Profile Tab 6 — Finances and Payments [CUST-014]

Summarize successful payments, refunds and, where the finance specification defines them, outstanding debt or credit. Display recorded purchases/invoices/payments with reference, subject, transaction type, date, amount/currency, status, nonsensitive payment-method description and authorized related order/service link.

Keep currencies separate unless an approved conversion rule exists. Orders, invoices and payments are related records, not independent amounts to add indiscriminately. The finance module owns calculation/status definitions; the profile must not invent accounting logic or double count.

Provide authorized date/type/status/currency filters, search and pagination. This is read-only reporting: refunds, invoice correction, debt adjustment and payment entry remain in the responsible module. Collaborator remuneration and settlements stay separate from customer finances. Do not display full payment credentials or unnecessarily complete bank details.

## 15. Profile Tab 7 — Account Management [CUST-015]

Show customer access/account states, verified-contact states, enabled login methods, MFA enrollment status and, if authorized, the existence of an active collaborator relationship. Work details are not automatically disclosed.

Separately authorize:
- Basic-information editing.
- Secure email/mobile changes with required verification and reauthentication.
- Password-reset initiation using the applicable customer-only, work or owner process.
- Customer-access disable/restore.
- Stop sign-in / shared-account suspend/restore.
- Session revocation.
- Full customer deletion.

Before saving, explain whether the action affects customer access only, the shared account, work access or security notifications. Shared effects require appropriate authority and owner safeguards. Do not let customer-only administrative permissions weaken work recovery or manually bypass verification/MFA.

Audit actor, time, reason, action, target and outcome. Require secure reauthentication for sensitive actions and notify affected users where appropriate. Passwords remain chosen by users and invisible to administrators. Do not offer bulk reset, suspension or deletion; perform these through the individual profile.

### Full deletion

Only **Platform Owner or Business Manager** may perform it, within legitimate scope. Show dependencies and impacts before confirmation: financial retention, payments/refunds/debts, open cases, linked records, collaborator relationship and protected ownership. Require confirmation that dependencies were reviewed, recorded reason and secure reauthentication.

Confirmation authorizes deletion only where lawful. Preserve and restrict records under legal retention/holds; never orphan financial records or silently delete the work relationship. State which data was deleted, retained or restricted and why. Last-owner and protected-owner safeguards remain mandatory. A custom role copy cannot obtain this reserved authority.

Data-subject erasure requests are handled under the privacy workflow, independently of this administrative button.

## 16. Permissions, Defaults and Scope [CUST-016]

Permissions must remain separate for list access, incomplete registrations, inactive users, each profile tab, audit/history visibility and export. Mutation permissions must separately cover basic editing, contact change, reminders, reset initiation, customer disable/restore, whole-account suspend/restore, session revocation and deletion.

| Initial role | Default access in this module |
|---|---|
| Platform Owner | Required platform-scope administration, subject to purpose, legal and owner safeguards. |
| Business Manager | Customer business management in authorized business scope; no alteration of protected ownership. |
| User and Collaboration Coordinator | Three workspace lists, identity/account-state and relevant administrative history; basic/contact administration, reminders, reset initiation, customer disable/restore. No whole-account suspension/restoration or session revocation by default; explicit owner delegation required. |
| Sales and Customer Relations Coordinator | Necessary customer identity plus Academy, consultation and service summaries for assigned scope; authorized registration reminders. No account-security administration by default. |
| Academy Coordinator | Necessary customer identity and Academy information within scope. |
| Consultation Coordinator | Necessary customer identity and consultation information within scope. |
| Loan Case Coordinator | Necessary customer identity and loan-case information within scope. |
| Finance Officer / Accountant | Necessary customer identity and financial information within scope. |
| Instructor, Consultant, Specialist Service Provider | No central customer-management access by default; use assigned specialist workspaces. |
| Customer | No access to this staff administration module; own-portal permissions are specified separately. |

Export is not inferred from viewing a tab. A profile-tab summary permission does not automatically allow opening full source records/documents. Source modules enforce their own permissions.

Apply own/assigned/team/partner-organization/business/platform scopes as appropriate, at record level. A person visible through one assigned consultation does not make all their services or finances visible. Lists, filters, totals, histories and exports must follow the same restrictions.

Combine active assigned/inherited permissions as defined in the foundational access model; no explicit grant means no access. Removing one grant does not remove another active grant. Hide unavailable controls and enforce the decision server-side. Reserved deletion/ownership constraints are process rules, not grantable through role cloning.

## 17. Privacy Review, Acceptance and Reusable Pattern [CUST-017]

Apply the privacy baseline to every customer table, source summary, reminder, edit, export and lifecycle action. Permission and manager approval are necessary but do not replace legal basis, minimization or retention.

Open before affected launch: service-specific account necessity; reminder legal eligibility/content, schedule/limits; retention of incomplete and inactive accounts, audit and financial records; suppliers/transfers; privacy notices and rights workflow; source-module calculations and sensitive-field scope; exact secure operation/recovery parameters.

Acceptance must establish:
- CRM leads are absent from all customer lists/search.
- Active, incomplete, inactive and account-not-created states remain distinct.
- Pagination/search/filter/sort and counts cover only permitted data; preferences/table context persist.
- Row selection exposes Customer Profile; drawer switching never mixes customer records.
- Last account sign-in and last Customer Portal use are independent; never-used states display correctly.
- Seven summary tabs reflect source data without duplicate specialist operations.
- Partial registration cannot be completed by administrator bypass.
- Automatic/manual reminders share duplicate prevention and eligibility; completion cancels pending sends.
- Shared-account recovery remains at work/owner strength where applicable.
- Customer suspension and account suspension have distinct clearly explained effects.
- Bulk reset/suspension/deletion is unavailable.
- Only Owner/Business Manager can perform reserved deletion; legal preservation and owner safeguards cannot be confirmed away.
- Source links, confidential fields, exports and direct requests enforce separate permissions and scope.
- Rights, retention and backup restoration behavior meet the privacy baseline.

Use this module as the future analysis pattern: boundaries and actors; workspace states; list/search/pagination; selection/details; source summaries; individual operations and dependencies; permission matrix/scopes; privacy review; open decisions; and observable acceptance criteria. Analyze each later domain separately before preparing its approved English specification.
