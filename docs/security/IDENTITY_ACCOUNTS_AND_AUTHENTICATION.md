# Identity, User Accounts, and Authentication

**Platform:** Azadi Mali (Financial Freedom)
**Status:** Approved — requirements; operational parameters remain to be specified.
**Owner:** Product Owner
**Scope:** Registration, activation, authentication, environment switching, account recovery, and initial owner setup.
**Open questions:** Exact code/link lifetimes, attempt limits, session durations, registration reminder schedule and limits, manual recovery evidence and reviewing authority; see Sections 6.4 and 23. These must be resolved before the affected implementation is launched.
**Implementation status:** Not verified. Approval of these requirements does not establish implementation, testing, or deployment.
**Prerequisites:** [Actors, Roles, and Access](ACTORS_ROLES_AND_ACCESS.md) and [Platform vision and Version 1 scope](../product/PRODUCT_VISION.md).
**Privacy baseline:** [Data protection and privacy requirements — Germany](DATA_PROTECTION_AND_PRIVACY.md) applies to all collection, communications, telemetry, recovery and lifecycle operations.
**Requirement identifiers:** Each numbered section is a stable requirement group, `AUTH-001` through `AUTH-023`; its subordinate rules belong to that group. These IDs must be preserved and used when linking future decisions, tasks, and acceptance tests.

## 1. Purpose and Foundational Principles [AUTH-001]

This document defines account creation, activation, sign-in, recovery, and account security checks. It is organized into three categories: registration and account creation; sign-in methods and authentication; and sign-in flow and additional security checks. Visual layouts and individual interface objects are defined separately in the UI design specification.

Authority to create users, invite collaborators, and assign roles is governed by the Actors, Roles, and Access specification.

- Each person has one user account and may simultaneously be a customer and hold one or more work roles.
- Shared identity and authentication do not merge customer and collaborator records. Their relationships, operational records, and financial records remain logically separate. Physical database placement is a later architecture decision.
- For an account with an active staff or collaborator relationship, staff/collaborator authentication and recovery requirements take precedence for the shared account, including when the person chooses the customer environment. Platform Owner safeguards remain applicable and must not be weakened.
- Recording a person in the CRM, creating a sign-in account, and granting a role are three separate operations.
- A person recorded in the CRM or through a bot does not automatically receive an account or access.
- The verified email address is the identifier used for password-based sign-in. Each account also has a stable internal identifier that does not change when its email address changes.
- Partner organizations do not use shared accounts. Their representatives use individual accounts with explicitly assigned access.
- Email or mobile verification proves access to that communication channel. It does not, by itself, establish legal identity or prove the accuracy of other personal information.
- Administrators must not set or view a user's permanent password.
- No sign-in or recovery method may bypass role restrictions or security requirements.

---

# Category One: Registration and Account Creation

## 2. New Customer Registration [AUTH-002]

Customers may register through either of the following routes.

### 2.1. Registration Form

| Information | Requirement |
| --- | --- |
| First name | Required |
| Last name | Required |
| Email address | Required |
| Password and password confirmation | Required |
| Mobile phone number | Optional |

Process:

1. The person completes the registration form.
2. The system records the registration request and sends email verification instructions.
3. The person verifies email ownership using a single-use link or code.
4. The person completes or corrects missing or inaccurate required information.
5. The person enrolls and verifies an authenticator app or a qualifying passkey.
6. Normal access to the customer panel is enabled only after all required steps are complete.

Before completion, the person has only the limited access needed to continue registration, correct information, and configure account security.

### 2.2. Registration with Google or Facebook

Process:

1. The person selects registration with Google or Facebook.
2. The system validates the provider response and verifies that it belongs to the current authentication flow.
3. Available profile information is retrieved to prefill the profile.
4. If the provider does not return an email address, the person must supply one.
5. Email ownership is verified by the platform itself.
6. The person completes or corrects required profile information.
7. The person enrolls and verifies an authenticator app or a qualifying passkey.
8. Normal customer access is enabled only after all required steps are complete.

Rules:

- Platform email verification is required for both registration routes, including social registration.
- Names and other provider-supplied information can be corrected and must not be treated as definitive proof of legal identity.
- The social provider used during registration is linked as a sign-in method. It does not need to be enabled again afterward.
- Social registration does not require a local password. The person may add a local password later after secure reauthentication.
- The provider's stable account identifier is used for the connection; email alone is not the linking key.

### 2.3. Incomplete Registration and Completion Reminders

- A person who has started registration but has not completed the required steps remains in an incomplete-registration state and must not be treated as an active customer.
- The system supports automatic email reminders to complete registration, enabled only after the documented legal-basis and UWG assessment required by the privacy baseline. The exact schedule and maximum number of reminders are configurable operational parameters to be finalized; 24 and 48 hours after registration starts are proposed initial timings, not fixed approved values.
- An authorized administrator may manually trigger the same reminder process from incomplete-registration management.
- Automatic and manual reminders share delivery logic, resend limits, and duplicate-send protection. The administrator must see the last reminder time before sending another.
- Immediately before dispatch, the system must check that registration is still incomplete and eligible for a reminder. Scheduled reminders must be canceled when registration is completed or lawful eligibility otherwise ends; this includes relevant objection or deletion.
- Reminders direct the person to their remaining registration step without repeating completed steps unnecessarily. Continuation links must not bypass email verification, MFA enrollment, or other security requirements. Expired verification steps require fresh valid verification.
- Reminder messages are intended solely for the relevant registration process and must not contain promotional content. That label is not proof of legal eligibility: assess the actual message/context under GDPR and UWG; incomplete registration does not establish marketing consent. Email-opening trackers are outside the approved design.
- Authorized administrators can view reminder counts, last-send time, automatic/manual origin, sending administrator where applicable, pending/sent/failed outcomes, and confirmed delivery only when supported by reliable provider evidence.
- Reminder history records the remaining registration steps at sending time, subsequent registration progress, and final completion time where applicable. Completion after a reminder must not be represented as proof that the reminder caused completion.
- Retention and cleanup rules for abandoned registration attempts and reminder history must be specified under the privacy baseline before real-data launch; this requirement alone does not choose a retention duration or deletion schedule.
- Reminder visibility, manual sending, and access to registration information require explicit permissions and respect data scope.

## 3. Customer Profile Completion [AUTH-003]

First name, last name, and a verified email address must be present before normal access is granted.

| Additional information | Requirement |
| --- | --- |
| Mobile phone number | Optional |
| Information specific to a service | Deferred to that service's approved analysis; collect only when necessary |

Do not expand initial profile collection to biographies, objectives, addresses or bank details in this specification. Additional fields are deferred to domain analysis. The necessity of registration fields and compulsory accounts must be assessed per actual service before launch under the privacy baseline.

Financial, family, or employment information must not be mandatory solely to create a general account. Each service collects the information necessary for its own process.

## 4. Linking to an Existing CRM or Bot Contact [AUTH-004]

The system must prevent duplicate identities without making unsupported links or merges.

- Similar first or last names are insufficient for linking.
- Customer email verification is mandatory before linking.
- Verified information must be checked against the existing record.
- Ambiguous matches or multiple candidate records require review by an authorized person.
- The system must not automatically merge people based on an ambiguous match.
- Existing cases and information must not be exposed to the new account before the link is approved.
- Email verification alone may be insufficient to establish ownership of every existing case. Required evidence must reflect the information and sensitivity of the case.

## 5. Staff and Collaborator Account Creation and Activation [AUTH-005]

This process covers employees, consultants, instructors, specialist service providers, partner organization representatives, and other holders of work roles.

### 5.1. Authority to Create and Invite

Work access may be created only by:

- The Platform Owner.
- The Business Manager within their authorized scope.
- A person explicitly granted authority to create or invite users.

Inviters may grant only roles and scopes they are authorized to delegate. Public registration must never grant a work or administrative role.

### 5.2. Required Information

| Information | Requirement |
| --- | --- |
| First name | Required |
| Last name | Required |
| Individual registered email address | Required |
| Registered mobile number suitable for mandatory SMS activation/recovery | Required |
| Work role or roles | According to responsibilities |
| Access scope | According to roles and assignments |
| Partner organization relationship | Where applicable |
| Access end date | Where applicable |

The authorized administrator enters required information in advance. The person may add approved optional profile information later. A mandatory SMS channel does not automatically require an employee's private phone: assess necessity and employment-law conditions and provide an appropriate employer-provided number/device or approved operational arrangement where needed. Contact data must not be reused for marketing merely because it supports activation.

### 5.3. Initial Activation

1. An authorized administrator records the person's information, roles, and scopes.
2. The account or invitation is placed in a pending-activation state.
3. A single-use invitation link with an expiration time is sent to the registered email address.
4. The person opens the link and explicitly starts activation.
5. The system automatically sends a one-time SMS code immediately to the registered mobile number.
6. The person enters and verifies the code.
7. The person chooses a permanent password that satisfies the password policy.
8. The person enrolls an authenticator app and proves successful enrollment by entering a valid code.
9. The person receives recovery codes.
10. Work access is enabled only after all required steps have been completed.

Rules:

- The invitation link grants only restricted access to activation, not to the work panel or work information.
- The SMS code verifies activation; it is not an ordinary sign-in password.
- Merely opening the link, including by an email security scanner, must not consume the invitation or send an SMS.
- The person must not freely change the destination email or mobile number during activation. Changes require an authorized process.
- Links and codes must be single-use, expire, and have limits on attempts and resends.
- An authorized person may issue a replacement invitation after expiration. The replaced invitation must no longer be usable.
- Invitation issuance, cancellation, resending, and completion must be audited.

### 5.4. Existing Customer Accounts

When the invited person already has a customer account:

- The invitation is securely connected to that same account after verification.
- A second account must not be created.
- The existing password must not be reset solely because the person received an invitation.
- Invitation email and SMS verification are still required.
- Work-environment security requirements must be completed.
- An existing enrolled authenticator may satisfy the enrollment requirement after successful verification; enrollment does not have to be repeated unnecessarily.
- Adding work roles must not remove the customer relationship.

## 6. Initial Platform Owner Setup and Owner Recovery [AUTH-006]

### 6.1. Initial Setup

The owner's complete personal information does not have to be prepopulated in the database. The first owner account may be created during a dedicated setup process.

1. During installation or initial provisioning, a random, single-use setup code is generated and kept securely.
2. The code may start initial setup only while no Platform Owner exists.
3. The owner supplies their name, email address, and mobile phone number.
4. The owner verifies both email and mobile ownership.
5. The owner personally chooses a password and enrolls and verifies MFA before obtaining administrative access.
6. The owner account and ownership assignment are recorded in the database as part of completed setup.
7. The setup code is consumed and the initial-owner setup route is closed. Neither can be reused to create an additional owner.

There must be no public default username/password, shared owner credential, or permanently hidden full-privilege account. A setup code is not an ordinary administrator login.

### 6.2. Required Owner Safeguards

- A verified mobile number is mandatory in addition to the verified email address.
- The owner enrolls an authenticator app and securely retains single-use recovery codes outside the account.
- The owner registers at least one backup passkey, preferably on a physical security key.
- Secure backup access must not depend exclusively on the owner's email account or mobile number.
- Additional owners and ownership transfers follow the protective rules in the Actors, Roles, and Access specification.
- Business Managers and ordinary administrators must not delete, restrict, replace, or take over the owner through invitations or recovery.
- The last active owner must not be deleted or deactivated.
- Full authority does not permit bypassing data-integrity rules or making unaudited changes.

### 6.3. Loss of Access to the Owner's Email

| Available access | Recovery path |
| --- | --- |
| The owner can still sign in with a passkey or password plus authenticator | Securely reauthenticate, register a new email address, and verify it; access to the old email is not required |
| The primary sign-in method is unavailable, but a backup exists | Use the backup passkey or the controlled recovery-code process, then verify a new email address |
| All ordinary and backup methods are unavailable | Use the predefined emergency recovery process with ownership verification |

- SMS alone must not authorize changing the owner's email, removing MFA, or taking over ownership.
- An owner email change must be audited, notifications sent to the previous email and verified mobile number, and other sessions terminated.
- Recovery restores the same owner account and existing ownership; it must not create a replacement owner.
- Business Managers and ordinary administrators may not independently perform owner recovery or replace the owner.

### 6.4. Emergency Recovery Code

Initial setup and emergency recovery are separate mechanisms.

- After setup, a single-use emergency recovery code is prepared for the existing owner account and kept securely outside the platform, for example as a printed copy in a safe.
- The system stores only the information required to validate the code securely, not a readable copy of the secret.
- The code opens only a restricted recovery process, not the administrative panel directly.
- The emergency process must include predefined ownership-verification checks before account security details can be replaced.
- After successful recovery, the used code is invalidated and a replacement code is issued for secure storage.
- Emergency recovery must be audited, notified through available registered channels, and accompanied by appropriate session revocation.
- No emergency credential may serve as a permanently available hidden administrative account.
- Before launch, the required evidence, authorized reviewing person or authority, and emergency recovery procedure must be defined. An unspecified manual process is not a complete operational recovery solution.

---

# Category Two: Sign-In Methods and Authentication

## 7. Shared Sign-In Page [AUTH-007]

There is one shared sign-in page for customers, staff, and collaborators.

- Password-based sign-in uses the verified email address.
- After authentication, the system reads the account's active relationships, roles, and permissions.
- Customer or staff status must not be inferred from the appearance or domain of the email address.
- Accounts with both types of access receive an environment selection after satisfying the applicable shared-account authentication policy. The system must determine that policy from registered relationships before granting access; email appearance and the selected environment must not determine a weaker policy.
- A sign-in method does not itself create a role or permission.

## 8. Language Selection [AUTH-008]

- Language selection and switching must be available on the sign-in and registration pages.
- After sign-in, the platform is displayed in the language selected on that page.
- The selection is saved for subsequent visits.
- Language can also be changed inside the panel.
- Language is not a separate mandatory registration field.
- Language selection does not affect roles, permissions, or security requirements.

## 9. Customer Sign-In Methods [AUTH-009]

This section's customer policy applies to customer-only accounts. If the account also has an active staff or collaborator relationship, Section 10 governs authentication for the shared account, including customer-panel access.

| Method | Required verification |
| --- | --- |
| Email and permanent password | Authenticator code |
| Linked Google or Facebook account | Authenticator code |
| Qualifying passkey | User verification with fingerprint, facial recognition, or device PIN |

- Password or social sign-in must not provide normal access before authenticator verification is completed.
- Access to a social account alone is insufficient.
- A qualifying passkey may replace both the password and the additional authenticator code.
- Email codes are used for email verification and password recovery, not as a substitute for the authenticator in ordinary sign-in.

## 10. Staff and Collaborator Sign-In Methods [AUTH-010]

| Method | Required verification |
| --- | --- |
| Email and permanent password | Authenticator code |
| Google or Facebook securely linked to the account | Authenticator code |
| Qualifying passkey | User verification and satisfaction of work-environment security requirements |

- Staff may enable social sign-in, but doing so does not remove work-environment security requirements.
- Matching social and registered email addresses alone do not authorize account linking or sign-in to an existing account.
- An email code or activation SMS code does not replace work sign-in MFA.
- Owners and other administrators are subject to authentication security requirements as well.

## 11. Linking and Unlinking Social Sign-In [AUTH-011]

- Google or Facebook is added to an existing account from within that account after secure reauthentication.
- Ownership of the social account is established using a validated provider response.
- A social account linked to one person must not simultaneously be linked to another person's account.
- Accounts must not be automatically linked solely because their email addresses match.
- Linking and unlinking must be audited and notified to the user.
- Removing a sign-in method must not leave the person without a usable sign-in method.
- Changing the provider-side email must not create a new internal account or grant new roles.

## 12. Password Policy [AUTH-012]

The policy applies to customers, staff, and owners.

- Minimum password length: 15 characters.
- The system must support passwords of at least 64 characters in length.
- Common, readily guessable, and known compromised passwords must be rejected.
- Long passphrases, spaces, and password managers are permitted.
- Pasting and password autofill must not be blocked.
- Mandatory combinations of uppercase letters, lowercase letters, digits, and symbols are not the primary security requirement.
- Routine forced password changes without a security reason are not required.
- Evidence of compromise or account takeover requires a password change.
- Passwords must not be stored in readable form or written to logs.
- Administrators must not be able to view users' passwords.

## 13. Authenticator Apps [AUTH-013]

- Google Authenticator and other TOTP-compatible apps are supported.
- Enrollment is complete only after the person enters a valid code; displaying a QR code alone is insufficient.
- Codes have limited validity, and an accepted code must not be replayed.
- Failed verification attempts must be limited.
- Authenticator enrollment secrets must not appear in logs or notifications.
- Adding, replacing, or removing an authenticator requires secure reauthentication.
- Users receive single-use recovery codes and must keep them securely.

## 14. Passkeys [AUTH-014]

Customers and staff may enable passkeys from their account security panel.

- Adding a passkey requires secure reauthentication.
- Passkey authentication must require user verification with fingerprint, facial recognition, or device PIN.
- When these requirements are met, a password or additional authenticator code is not required for that sign-in.
- Sensitive operations may require a fresh passkey authentication.
- A person may register multiple passkeys, view them, name them, and remove them.
- Removing the last usable authentication method without establishing a replacement is prohibited.
- A passkey does not grant additional access or roles.
- Loss of a device or passkey is handled through secure recovery.

---

# Category Three: Sign-In Flow and Additional Security Checks

## 15. Environment Selection and Switching [AUTH-015]

| Account access | System behavior |
| --- | --- |
| Customer only | Open the customer panel after required authentication checks |
| Staff/collaborator only | Open the work panel after required work authentication checks |
| Both environments | Satisfy staff/collaborator authentication requirements for the shared account, then display environment selection; choosing the customer environment must not lower the security policy |

For a person who is both a customer and a staff member:

- One account and its existing sign-in methods are used; no separate account or password is required.
- While a staff or collaborator relationship is active, its authentication policy applies before either environment is opened. Customer registration or customer-panel selection must not bypass staff activation, authentication, or recovery safeguards.
- Customer and collaborator operational and financial records remain separate. A work role does not authorize access to other customers' information from the person's customer panel.
- At initial sign-in, successful authentication that already satisfies work requirements does not require an immediate duplicate MFA challenge merely because the person selects the work panel.
- The customer panel shows only that person's own customer information and services.
- The work panel shows information and functions authorized by the person's active work roles and scopes.
- The person may switch environments from within the platform without signing out or re-entering email and password.
- Switching from the customer panel to the work panel requires fresh authenticator or qualifying passkey verification.
- Switching from the work panel to the customer panel does not, by itself, require additional verification.
- Environment selection does not create a permission, and customer access must not bypass work security requirements.
- If work access is revoked, the same account may continue to provide customer access when the customer relationship remains active.

The system must check authorization for every operation and information access. Changing environments, manipulating a page address, or sending a request directly must not bypass access restrictions.

## 16. Reauthentication for Sensitive Operations [AUTH-016]

Secure reauthentication is required for:

- Changing the sign-in email address.
- Changing the mobile number used for activation or recovery.
- Changing a password.
- Linking or unlinking social sign-in.
- Adding or removing a passkey.
- Changing, removing, or recovering an authenticator.
- Changing sensitive roles or permissions.
- Transferring ownership.
- Sensitive financial operations defined in the relevant module specification.

An active session alone is insufficient. Authentication does not replace authorization; both must be satisfied.

## 17. Customer Password Recovery [AUTH-017]

This self-service process applies only to customer-only accounts. Accounts with an active staff or collaborator relationship must use Section 18 for password reset, even if the request originates from a customer-facing page. Ownership protections in Section 6 take precedence for Platform Owner accounts.

1. The person requests recovery using the registered email address.
2. The system sends a single-use, expiring link.
3. The person uses the link to choose a new password.
4. Existing sessions are terminated after the reset is completed.
5. Subsequent sign-in still requires an authenticator or qualifying passkey.

Rules:

- Password recovery must not remove or disable MFA.
- Customers without a local password may use their existing social sign-in or passkey. Adding a local password must follow a secure process.
- Simultaneous loss of password and MFA requires a separate recovery process.
- Public recovery responses must not reveal whether an account exists.

## 18. Administrator-Initiated Staff Password Reset [AUTH-018]

1. An authorized administrator initiates the reset.
2. A single-use, expiring link is sent to the person's registered email address.
3. The person opens the link and starts the process.
4. The system sends a one-time SMS code to the registered mobile number.
5. The person verifies the code and personally chooses a new password.
6. Existing sessions are terminated after completion.
7. Subsequent sign-in still requires MFA.

Rules:

- Administrators must not choose or view the new password.
- Resetting a password must not remove authenticators or passkeys.
- Destination email and mobile details must not be freely changed within this process.
- The administrator's action, reset completion, and associated notifications must be audited.
- Reset authority does not permit taking over an account or changing platform ownership.
- Owner recovery is subject to the special safeguards in Section 6 and must not be performed by ordinary administrators.

## 19. MFA Recovery and Loss of Access Methods [AUTH-019]

A separate process covers loss of a phone, authenticator, passkey, email access, or mobile access.

Recovery may use:

- A single-use recovery code.
- Another previously enrolled valid authenticator or passkey.
- A controlled identity-review process when those methods are unavailable.

Rules:

- Email access alone must not be sufficient to remove MFA.
- An administrator must not bypass all controls by simply changing a mobile number and resetting a password.
- Contact changes and MFA removal without the original factors are sensitive account recovery operations.
- Recovery must be audited, notified to the account holder, and accompanied by necessary session revocation.
- Replacement security methods must be verified after recovery.
- Required evidence, authorized reviewers, and manual review steps must be defined in the operational recovery design. Undefined or ambiguous recovery is not permitted.
- An account with an active staff or collaborator relationship must use the staff/collaborator recovery policy regardless of the entry page or selected environment. Customer recovery must not serve as a weaker alternative.
- Owner recovery follows the additional requirements in Section 6.

## 20. Session Management and Abuse Prevention [AUTH-020]

- Users can view active sessions and terminate them.
- Users can terminate all other sessions.
- Sessions have expiration and inactivity limits; exact values are defined in the technical design.
- Role revocation, access expiration, and work suspension must affect existing sessions as well as future sign-ins.
- Closing work access does not necessarily remove customer access.
- Security policy must be reevaluated when relationships or work access change, including for existing sessions. Revoking one work role or suspending work access must not by itself switch the shared account to customer-only recovery while an active staff/collaborator relationship remains. Owner safeguards continue to take precedence.
- Sign-in attempts, code guesses, recovery requests, and SMS/email sends must be limited.
- Limits must not enable easy, permanent denial of access to another person's account.
- Suspicious behavior may trigger additional security checks.
- Device and location information are risk signals, not substitutes for authentication.
- All sign-in and account communications use secure connections.

## 21. Security Notifications and Audit [AUTH-021]

Security telemetry and audit require defined purpose, minimization, restricted access and retention under the privacy baseline. Work activity must not be silently repurposed as employee performance monitoring. Passkeys use local authenticator verification; the platform must not collect biometric templates for this feature.

Important events must be recorded, with relevant events notified to the user, including:

- Account activation.
- Password changes or resets.
- Security email or mobile changes.
- Social sign-in linking or unlinking.
- Authenticator or passkey additions, removals, or changes.
- Account or MFA recovery.
- Work access changes.
- Suspicious sign-in activity.

Audit records identify the actor, action, time, and outcome. Passwords, one-time codes, secret-bearing links, emergency or setup codes, and authenticator enrollment secrets must not be included in readable audit records.

## 22. Account and Relationship Lifecycle [AUTH-022]

The following are distinct operations:

- Closing a customer relationship.
- Suspending or ending work access.
- Suspending the entire account for security reasons.
- Returning as a customer or being reinvited as a collaborator.
- Requesting personal data deletion.

Rules:

- Ending one relationship must not automatically delete another.
- Removing a work role must not automatically delete the person or historical records.
- Full account suspension blocks all sign-in methods.
- Data deletion follows the [privacy baseline](DATA_PROTECTION_AND_PRIVACY.md) and relevant domain retention/dependency rules. Administrative confirmation cannot override legal preservation. Customer-management deletion is reserved to Platform Owner or Business Manager, within scope and protected-owner safeguards; see [Customer Management](../modules/CUSTOMER_MANAGEMENT.md).
- Reregistration must not bypass suspension or create duplicate identities.

## 23. Related Documents and Operational Details [AUTH-023]

- Roles, administrator authority, and owner safeguards come from the Actors, Roles, and Access specification.
- Sign-in, registration, activation, and recovery page layouts are defined in the UI specification.
- Each module defines its own permissions and sensitive operations.
- Data retention, lawful collection/communications, individual rights and deletion are governed by the [privacy baseline](DATA_PROTECTION_AND_PRIVACY.md). Category-specific operating decisions must be completed before affected launch.
- Exact link/code lifetimes, attempt limits, session durations, recovery review procedures, and technical tools are defined in the implementation design.
- Owner emergency recovery evidence and reviewing authority must be defined before launch.
- Activation, recovery, and invitation links must remain usable across site releases until their intended expiration or revocation.
- Implementation details must not weaken the principles or approved decisions in this document.
