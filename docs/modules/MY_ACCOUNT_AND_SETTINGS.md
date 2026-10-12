# My Account, Profile Settings and My Purchases

**Status:** Approved requirements; explicit operating/legal decisions remain open.
**Owner:** Product Owner
**Implementation status:** Not verified.
**Scope:** Customer and collaborator self-service account interface.
**Prerequisites:** [Identity](../security/IDENTITY_ACCOUNTS_AND_AUTHENTICATION.md), [Actors and Access](../security/ACTORS_ROLES_AND_ACCESS.md), [Customer Management](CUSTOMER_MANAGEMENT.md), [Collaborator Management](COLLABORATOR_MANAGEMENT.md), [Privacy](../security/DATA_PROTECTION_AND_PRIVACY.md).
**Requirement groups:** ACCOUNT-001 through ACCOUNT-008.
**Messaging reference:** [Messaging and Notifications](MESSAGING_AND_NOTIFICATIONS.md).

## 1. Navigation [ACCOUNT-001]

My Account is a parent entry with independent pages: Profile and Settings; Messages and Notifications; My Purchases (customer environment only). Messaging is not embedded as a profile-settings tab. A persistent mailbox icon in the platform header opens the same mailbox and shows unread count. Profile and Settings is available in both environments.

A customer-collaborator has one identity/security configuration. Keep customer/work operational contexts separate. Environment switching and authentication follow AUTH-015. Existing help, language and sign-out entry points may remain in the user menu.

Profile tabs: My Information; Account Security; Language and Display; Notification Preferences; Privacy; and My Collaboration and Access (collaborators only).

## 2. My Information and Registration Completion [ACCOUNT-002]

| Field | Customer-only | Collaborator |
|---|---|---|
| First/last name | Required; editable | Read-only; correction request |
| Email | Required, verified; secure change | Same |
| Mobile | Optional | Required; secure change |

Initially display information with Edit Information. Editing reveals Save/Cancel. Staff names remain locked; the same restriction applies in either environment for a customer-collaborator.

Request Name Correction opens current read-only values, proposed first/last name, explanation, Submit/Cancel. Show Pending, Approved or Rejected with outcome/reason. An authorized manager applies approved corrections; do not demand ID documents by default. This procedure must support statutory rectification rather than arbitrary refusal. Shared identity changes appear in both profiles.

Email/mobile edits require secure reauthentication and new-destination verification. Show Pending Verification and allow cancellation; retain valid prior contacts until completion. Completed email change updates the sign-in identifier. Lost old factors use controlled recovery, not a contact-edit bypass.

Customer registration completion uses this same information form in restricted Complete Required Information mode with Save and Continue. First name, last name and platform-verified email are required; mobile remains optional. Show field errors while preserving input, then continue to required account-security enrollment. No normal portal access before required registration/security completion.

Do not add photo, birth date, residential address, bank details or identity documents without relevant domain analysis.

## 3. Account Security [ACCOUNT-003]

Keep controls within the security tab; buttons open the applicable dialog/process rather than unrelated navigation.

| Section | Controls |
|---|---|
| Password | Set/not set state; Change Password; Create Local Password for eligible passwordless customer accounts |
| Authenticator | Enrollment state; Set Up or Replace Authenticator |
| Passkeys | Name, creation/last-use where known; Add, Rename, Secure Delete |
| Recovery codes | Status; Generate New Set |
| Google/Facebook | Connected state; Connect/Disconnect |
| Sessions | Device/browser where reliable, last activity/current marker; End Selected or End Other Sessions |

Password form: current password, new/repeated password, Save/Cancel; securely reauthenticate according to the valid account method. AUTH-012 policy remains authoritative, including minimum 15 characters, support for at least 64, breached/common password blocking and permitted paste/password managers. Do not confuse authenticated password change with forgotten-password reset.

Customer-only recovery uses AUTH-017; staff/shared-account reset uses administrator-initiated AUTH-018 email/SMS; owner follows protected recovery. Reset never disables MFA.

Enroll/replace Authenticator through a restricted secret/QR step and proof of a valid code. Verify replacement before removing the old method. No simple MFA-Off toggle. Do not redisplay enrollment secrets after completion.

Passkey enrollment uses browser/authenticator user verification. Qualifying passkeys follow approved password/MFA sign-in rules; biometrics remain on the device. Deleting a credential/link cannot strand the user without a valid approved sign-in/recovery path. Owner backup requirements remain mandatory.

Generate recovery codes after secure reauthentication, warn that the old set is invalidated, display/download the new set securely once; do not redisplay old codes. Social links use validated provider identity, never email matching alone.

Show relevant security activity belonging to the person, not other users' audit trails. Location, if provided, is approximate. Sensitive changes require fresh verification, audit and appropriate security notifications. Sessions and shared-account work-policy protections follow the identity specification; security secrets are never visible to managers.

## 4. Language and Display [ACCOUNT-004]

Controls: Persian/German/English language selector; searchable timezone with device suggestion and user correction; 12/24-hour clock; date-format preview; Save/Cancel.

The language chosen at login determines the ensuing interface; later profile changes persist. Persian RTL, English/German LTR. Do not imply automatic translation of user messages/course content. Shared account preferences apply across environments.

Timezone affects display, not actual appointment time; label appointment timezone and handle daylight-saving changes. Date format follows selected language. Additional themes/visual preferences require separate UI analysis; do not present nonfunctional settings.

## 5. Notification Preferences [ACCOUNT-005]

Offer applicable implemented options: email for private messages; optional nonpromotional public notices; class/session reminders; optional request-status updates by domain; relevant collaborator work notifications. Save/Cancel.

Essential security/service communications are clearly distinguished from optional preferences, with lawful purpose determined rather than assumed. Marketing, if introduced, requires separate lawful consent/eligibility and defaults off. Private/public classification does not establish marketing or necessity.

Disabling email never deletes inbox messages or marks them read. No general SMS notification feature is included; approved SMS activation/recovery remains. Messaging emails follow MSG-007 timing and privacy rules.

## 6. Privacy and Requests [ACCOUNT-006]

Controls: View Privacy Notice in understandable supported language; applicable optional-consent controls; Submit Data Request; own request history; Request Closure of Customer Access where relevant.

Request form: type, explanation, Submit/Cancel. Support applicable access, rectification, erasure, restriction, objection and portability. History: ID, type, submitted time, state/latest reply; open secure details. Link existing name-correction requests rather than duplicate them. Support/no-login requests must enter the same accountable process.

Closure is a request, not immediate irreversible erasure. Show purchases, appointments and open cases before confirmation; review consequences before execution. Closing customer access preserves independent work, does not itself erase purchases/required records, and allows assessment of secure return to the same account. Exact purchased-entitlement effects/return rules remain open and must be settled before enabling closure. Data-erasure requests remain distinct.

PRIV-011 deadlines, proportional verification and legally justified exceptions apply; platform permission rules cannot prevent exercising rights.

## 7. My Collaboration and Access [ACCOUNT-007]

Collaborator-only read-only tab: own relationship/company/state/dates; assigned roles; per-assignment scope/start/end/state; permission sources. Select a role to inspect its allowed functions and scope without mixing unrelated grants.

No controls to edit roles, extend validity or increase access. Do not expose others' data or confidential managerial history. Customer purchases remain separate.

## 8. My Purchases [ACCOUNT-008]

Customer page controls: order number/title search; education/course/camp/consultation/service type; order-state and payment-state filters; date range; Clear Filters.

Table: order number, item summary/type, date, amount/currency, order and payment state. Pagination 20/30/50, default 20. Select row to reveal Purchase Details and open a drawer preserving list context.

Tabs:
- Order Information: all line items, quantities, recorded prices/discounts/tax and final amount.
- Payments and Invoices: recorded payments/refunds and related documents.

Controls: View/Download Invoice; Open Related Learning/Session/Service with valid entitlement/source authorization; Contact Support About This Order with a validated order reference. Avoid exposing unrelated order data via message links.

Read authoritative order/finance data; do not duplicate accounting or conflate paid with completed service. No currency aggregation without approved conversion. Genuine zero-price orders show Free; activities without an order remain in their source modules.

Repayment, cancellation, refund and order-change actions await approved sales/finance analysis. This page does not invent those rules.

**Open implementation decisions:** contact/security link limits and session parameters; legal retention; customer closure effects; detailed supplier/rights procedures; domain financial operations. This is approved application intent, not certification or deployment evidence.
