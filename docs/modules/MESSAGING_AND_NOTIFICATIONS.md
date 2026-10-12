# Messaging, Notifications and Support Inbox

**Status:** Approved requirements; stated operating/legal decisions remain open.
**Owner:** Product Owner
**Implementation status:** Not verified.
**Scope:** Internal messaging for customers and collaborators, public notices, support conversations, editor/attachments and email alerts.
**Prerequisites:** [My Account](MY_ACCOUNT_AND_SETTINGS.md), [Actors and Access](../security/ACTORS_ROLES_AND_ACCESS.md), [Role Management](ROLE_MANAGEMENT.md), [Identity](../security/IDENTITY_ACCOUNTS_AND_AUTHENTICATION.md), [Privacy](../security/DATA_PROTECTION_AND_PRIVACY.md).
**Requirement groups:** MSG-001 through MSG-009.

## 1. Navigation and Mailbox [MSG-001]

A persistent header mailbox icon shows unread messages/notices and opens the same Messages and Notifications page reachable below My Account. This is independent of profile-settings tabs.

Folders/views: Private, Public, Sent, Drafts, Archived. Sent filters existing conversations, not duplicated records. Search own authorized subject/body; unread, date and support-state filters; Clear Filters.

Desktop list/details side-by-side; mobile list then conversation, preserving filter/scroll on return. Rows show subject, counterpart, latest message time, support-state where applicable, unread and attachment indicators. Selected conversation header shows subject/counterpart/state; messages in chronology with sender/date/time/files and a clear new-message divider.

Only actually displayed received messages are marked read; merely opening the mailbox or delivering email marks none read. Manual Mark Read/Unread and archive/unarchive are available; ensure display re-reading does not generate a fresh email-reminder cycle. Archive affects the person's view, not other recipients or retention.

Customers/collaborators use one account but work/customer contexts and authorization remain distinct. Ending work access must not reveal work history via customer context. No ordinary cross-mailbox access is implied.

## 2. Customer Sending and Reply [MSG-002]

Customers can send only to fixed **System Support**. No recipient selector/address book, no direct sending to employees or other customers.

New Message form: fixed recipient; required subject; full editor; files; Send, Save Draft and Cancel. Each new submission creates a support conversation, replies remain within it. Customers may reply to support only.

Other employees' permitted private messages to customers are one-way. Display Not Replyable with Contact Support creating a new support conversation referring to the authorized original. Public notices similarly do not accept direct replies. Reference linkage must not leak internal/private content.

Support is a queue, not a shared login. Replies display **System Support — responder first name**; do not disclose employee email/mobile/surname. Internal records retain the actual individual actor.

## 3. Collaborator Sending and Contacts [MSG-003]

New Message adds a searchable authorized address book, with employee/customer filters only if permitted. Show enough identification, not unnecessary personal contact details. Contact discovery and sending are separate permissions, rechecked server-side at dispatch.

Private messages to one authorized colleague are two-way. Private messages to an authorized customer are nonreplyable; use Support if a customer response is needed. Public/group notices need separate publication permission. Private multi-person chat is outside this initial scope.

Receipt of one's authorized messages exists for all accounts; employee status alone does not grant all-recipient discovery or support-queue access.

## 4. Editor, Drafts and Sending [MSG-004]

Editor for both groups: bold, italic, underline, lists, quote, link, table, RTL/LTR text, emoji, internal sticker collection, inline images and attachments. Primary controls: Send, Save Draft/automatic draft state and Cancel. Keep frequent tools visible, others in a clear supplementary toolbar.

Autosave drafts with feedback; preserve body/healthy files after errors; prevent duplicate submissions/retries. Sent-message edit/delete is not included; legal rights/retention disposal remain separate.

No raw active HTML/scripts. Sanitize content and links server-side, prevent executable markup/external image tracking and use internally hosted stickers/images. Provide keyboard/screen-reader operation and understandable statuses. Live unread updates require no manual refresh, with reconnect/fallback handling determined technically.

## 5. Attachments [MSG-005]

Approved initial limits, subject to capacity verification:
- PDF, JPG/PNG/WebP, DOCX/XLSX/PPTX.
- Up to 5 files/message; up to 20 MB/file and 50 MB total.
- No executables/scripts, macro documents, ZIP/RAR or encrypted files that cannot be inspected.
- Audio/video attachments are not included.

Attach button/drag-drop; name/size/progress; Uploading, Checking, Ready or Rejected; remove before send. Do not dispatch until all selected files are ready; allow removing a rejected file. Preserve other valid inputs.

Verify actual type and size/count server-side, inspect for malicious content, quarantine suspicious files and block access while checking/unavailable. Safe PDF/image previews; Office download only unless a separately approved safe preview tool is implemented. Inline images follow the same applicable controls/count/size policy; capacity details require technical consistency.

Download/preview authorization checks conversation membership/legitimate scope at each request; no permanent public URLs. Attachment URLs cannot bypass revoked access. No private file/body/name/image is included in alert emails. Files do not automatically become official domain-case documents; that transfer requires an explicit domain process.

## 6. Support Queue [MSG-006]

Separate authorized workspace from personal mailbox. Views: Needs Attention; Assigned to Me; All Authorized. Table: subject, permitted customer identity, state, assignee/unassigned, last message time and customer/support side. Search, filters and pagination; row selection opens conversation beside list.

Controls: Accept Responsibility; Assign to Authorized Support Worker (separate authority); Reply; Close with short reason; Reopen.

States: Awaiting Support Reply, Awaiting Customer Reply, Closed. Support reply sets Awaiting Customer; customer reply sets Awaiting Support and reopens closed conversations. Read/unread remains distinct.

Editor has clearly differentiated **Reply to Customer** and **Internal Note — Not Visible to Customer** modes. Internal notes/files are never exposed to customers or copied by ordinary conversation references.

Warn when another worker is composing; recheck new messages/assignment before send, preserving drafts. Responsibility does not itself widen authorization. Record personal actor/time for replies, notes, assignment and state changes.

## 7. Public Notices and Email Alerts [MSG-007]

Public Notice form for permitted staff: required title; all customers/all collaborators or permitted group audience; full editor/files; preview and authorized recipient count; Publish, Save Draft, Cancel. No recipient list visible to recipients; individual read state. Public does not mean Internet-public or permission to disclose private information. Contact Support may reference a notice. Direct replies are off.

Private-message email contains only a generic unread-private-message notice and sign-in link; exclude conversation title/body, files/names and sensitive counterpart details. Valid authentication/authorization is required at the destination; email access is not a bypass.

Schedule per unread conversation:
1. Initial alert after 5 minutes if still unread.
2. Reminder 3 days after initial alert if still unread.
3. Final reminder 7 days after initial alert if still unread.
4. No further reminder for the same unread episode.

Additional messages in the same already-unread conversation do not restart/duplicate the episode. After genuine reading, later newly received messages may establish a new episode; manual Mark Unread alone does not. Near-simultaneous alerts can be aggregated without revealing private information. Recheck eligibility/read state/preferences immediately before dispatch, cancel pending alerts after reading and make retries idempotent. “Unread” means platform read state, not email opening; no email tracking pixels.

Public email follows optional preferences and actual purpose: essential lawful service/security communications remain distinct; advertising requires applicable eligibility/consent. General SMS alerts are not included. Token emails/security notices are outside private-message reminder timing.

## 8. Default Role Permissions [MSG-008]

Separate permissions: scoped colleague/customer contact discovery; private sending to colleagues/customers; public/group publishing; support view/reply; support assignment/state control; internal notes; supervisory access; attachment use within allowed policies.

| Role | Initial proposal approved in analysis |
|---|---|
| Platform Owner / Business Manager | Full messaging/support administration, publishing and supervisory route subject to privacy/legal requirements and owner safeguards |
| User and Collaboration Coordinator | Scoped user messaging; support view/reply, assignment/state and internal notes needed for support |
| Sales Coordinator | Related customer/colleague messaging; no default global support administration |
| Academy / Consultation / Loan Coordinators | Customer/colleague messaging within their domain relationships |
| Instructor / Consultant / Specialist | Related internal colleague messaging; customer sending only if expressly delegated |
| Finance Officer | Relevant financial customer/colleague messaging |
| Catalog and Pricing Coordinator | Relevant internal messaging; no default customer sending |
| Customer | Send/reply to Support only; no address book |

Ordinary roles have no automatic public/group publication or support-queue access outside the explicit defaults above. Assignment to support tasks requires a valid support permission, not merely inbox ownership. Implement concrete scoped rules from related cases/teams/companies rather than all-user directory discovery. Role definitions can incorporate these existing permissions through approved administration; updates cannot silently grant ordinary/custom roles access.

My Account settings/own purchases/own mailbox are self-service, not central user-administration grants. Company has no shared mailbox/login account; individual representatives follow personal account rules.

## 9. Supervisory Access and Data Lifecycle [MSG-009]

Owner/Business Manager supervisory access uses a dedicated **Supervisory Review** route, not impersonation or merging another person's inbox. Require lawful purpose/necessity, recorded reason, fresh authentication and audit of access. Read-only; never send as the mailbox owner. Determine employee notices and applicable employment/legal conditions before enablement; full admin authority alone is not permission to read correspondence indiscriminately.

Retain separately classified support conversations, private work communications, public notices, drafts, temporary uploads, attachments, security/supervision records and backups according to a justified schedule. No final durations are set here; decide basis, trigger, duration, restricted archive, legal holds and deletion/restore behavior before affected real-data launch. Archive does not imply indefinite retention.

Rights requests may arrive through Support; route them into the same privacy workflow without forcing duplicate submission. Restricted internal notes may still require assessment in a statutory access request; “internal” is not automatic legal exemption.

Actual supplier roles/AVV, transfers, security controls, communication law, employee monitoring limitations and rights apply under the privacy baseline. Essential/send classification must be justified. No real messages/files or confidential assessments go into the public repository.

**Open launch decisions:** concrete retention schedule; supervisory legal procedure; supplier/security implementation; scoped recipient rules and support assignment concurrency; backup deletion and scan availability behavior. No group private chat, delivery/read guarantees for email, production implementation or legal certification is asserted.
