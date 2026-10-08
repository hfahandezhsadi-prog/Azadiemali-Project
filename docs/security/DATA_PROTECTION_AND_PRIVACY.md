# Data Protection and Privacy Requirements — Germany

**Status:** Approved design baseline; legal applicability, operating decisions and implementation evidence remain to be completed.
**Owner:** Product Owner; the operating legal entity remains responsible as controller.
**Scope:** All platform domains, websites, portals, CRM, communications, staff/partner processing, integrations and operational copies.
**Implementation status:** Not verified. This document is neither a certification nor a guarantee against complaints.
**Prerequisites:** [Product vision](../product/PRODUCT_VISION.md), [actors and access](ACTORS_ROLES_AND_ACCESS.md), and [identity and authentication](IDENTITY_ACCOUNTS_AND_AUTHENTICATION.md).
**Requirement identifiers:** PRIV-001 through PRIV-021 are stable groups. Module specifications must reference applicable groups and supply concrete decisions and acceptance evidence.
**Classification:** Statutory duties apply when their legal conditions are met; safeguards explicitly described as platform requirements are approved design choices. Guidance supports interpretation and is not itself legislation.

## 1. Authority and Review Baseline [PRIV-001]

The platform is intended for use in Germany. Applicable EU and German law takes priority over a product preference or administrative confirmation. Assess processing in its actual context, including the legal entity, people affected, recipients, service and deployed technology. Do not infer lawfulness from the existence of an account, contract, checkbox or administrative permission.

Use GDPR/DSGVO, relevant BDSG provisions, TDDDG for terminal access/storage, UWG for marketing communications and applicable accounting retention law. Sector-specific rules for employment, credit, property services and consumer transactions require assessment in the relevant module; this privacy baseline does not decide licensing or all consumer-law obligations.

Recheck authoritative law and applicable regulator guidance during each module analysis, material change and launch review. Record the applicable provision and rationale privately where business details are confidential. Published proposals for legal reform are not enacted requirements. The German competent supervisory authority must be identified from the actual establishment and processing; do not assume that BfDI supervises every private business.

## 2. Accountability and Operating Responsibilities [PRIV-002]

Identify the controller's legal name, address, contact channel, decision makers and privacy-request owner before processing real data. Platform Owner is an application role, not necessarily the legal controller.

Maintain a processing inventory / Verzeichnis von Verarbeitungstätigkeiten (VVT) as a platform requirement. Determine the statutory Article 30 duty and any applicable exemption; do not assume a small business is exempt, particularly where processing is regular.

For each activity record: purpose, data subjects and categories, source, legal basis and necessity, controller/processor roles, recipients, transfer locations, retention and deletion triggers, access, security measures, rights handling and accountable owner. These records and contracts belong in controlled operational storage; only blank templates and nonconfidential requirements belong in this public repository.

Legal accountability cannot be delegated away by buying software. Assign review and evidence responsibilities across product, operations, security and privacy/legal functions.

## 3. Lawfulness and Purpose [PRIV-003]

Document a legal basis for each purpose before activating that processing. Separate service delivery, account security, accounting, marketing and employee administration. Contract necessity is assessed against the actual service rather than a broad clause. Legal obligation requires an identified applicable provision. Legitimate interests requires a documented interest, necessity assessment and balancing against individuals' rights.

Use consent only where appropriate and valid: specific, informed, freely given and demonstrable. Do not bundle optional marketing into required registration or treat acceptance of a privacy notice as blanket consent. Record the relevant text and affirmative action; permit withdrawal as easily as giving consent. Withdrawal does not retrospectively invalidate lawful processing and does not erase a separately applicable statutory retention duty.

New use of existing information needs a compatibility/legal-basis assessment and appropriate notice. CRM data, customer histories and work records are not interchangeable simply because the same person ID links them.

Source: [EDPB — lawful processing](https://www.edpb.europa.eu/sme/be-compliant/process-personal-data-lawfully_en).

## 4. Minimization and Accuracy [PRIV-004]

Collect information at the point where it is necessary for a defined activity. The approved registration fields remain first name, last name and email; customer mobile remains optional. Their necessity must be documented for the actual service before launch. Additional bank details, address, objectives or identity evidence are deferred to relevant module analysis, not universally required at registration.

Use stable internal person/account identifiers to reference separate domain records. Linking must not copy every domain's information into an unrestricted universal profile. Avoid automatic identity merging based only on name, email similarity or CRM matches; ambiguous linkage requires secure review.

Support corrections at the authoritative source and propagate them appropriately. Historical accounting records may need an auditable correction rather than overwriting issued documents. Financial data is confidential but not automatically Article 9 special-category data. Free text and uploaded documents can reveal such data; assess necessity, Article 9 conditions and safeguards before permitting that processing. Article 10 criminal-conviction data requires its own legal assessment.

## 5. Transparency and Language [PRIV-005]

Provide understandable notices at collection, including registration, invitations, uploads, forms and relevant integrations. For indirect collection assess Article 14 notice duties, timing and exceptions.

Notices must address the responsible entity/contact, purposes and bases, legitimate interests where used, recipients, transfers and safeguards, retention criteria, relevant rights, withdrawal where applicable, supervisory complaints, mandatory/optional fields and consequences, and automated decision-making where relevant.

The login/registration language selector controls interface language and the subsequent platform session, subject to the user's later choice. Privacy notices and security messages must remain understandable in the supported Persian, English and German experiences. Notices do not substitute for technical safeguards.

## 6. Privacy by Design and Default [PRIV-006]

Default views expose only necessary information. Enforce purpose, permissions and record scope in server requests, search, totals, previews, reports, notifications, files and exports. Platform Owner and Business Manager authority does not justify viewing or using all personal information for any purpose.

Keep customer and collaborator operational/financial records logically separate while sharing verified identity and authentication. Suspension or erasure of one relationship must not silently remove the other. Physical database design remains open.

As a recommended assessment framework, use the German supervisory authorities' Standard Data Protection Model (SDM): minimization, availability, integrity, confidentiality, unlinkability, transparency and intervenability. It is a method, not a certification or automatic proof of compliance. Translate applicable objectives into module controls and evidence.

Source: [DSK — SDM and implementation guidance](https://www.datenschutzkonferenz-online.de/anwendungshinweise.html).

## 7. Authentication and Employment [PRIV-007]

Apply the approved identity specification while minimizing contact and security telemetry. SMS activation/recovery uses a verified suitable number; it must not impose use of an employee's private phone without a necessity and employment-law assessment. Provide an appropriate employer-provided channel/device or approved operational arrangement where needed. Employee consent must not be assumed freely given merely because a form is signed.

Passkey biometric/PIN verification occurs locally at the authenticator. The platform must not collect fingerprint or facial templates for this feature. Protect credential identifiers and public keys as account data. TOTP enrollment secrets, recovery codes, setup links and SMS codes require restricted protection and must never appear in ordinary logs, analytics or manager screens.

Record work and customer activity separately. Security records must not silently become employee performance monitoring. Any such additional purpose requires separate legal assessment, transparency and, where applicable, employee-representation participation.

Sources: [BDSG §26](https://www.gesetze-im-internet.de/bdsg_2018/__26.html), [identity specification](IDENTITY_ACCOUNTS_AND_AUTHENTICATION.md).

## 8. Registration, Purchases and Reminders [PRIV-008]

The approved product intent requires registration and authentication before website purchases and portal access to purchased products. Before implementation launch, assess necessity per service and applicable German guidance/case law on mandatory accounts and guest access. Do not assume that every purchase may require a permanent account; equally, do not treat every account-based ongoing digital service as prohibited. Any necessary product change returns for approval before release.

Registration reminders require a documented lawful basis and a UWG assessment of the actual message and context. Calling a message “operational” does not make it lawful. Do not infer advertising consent from an abandoned registration or purchase. If marketing rules apply, obtain valid prior consent or establish every condition of the applicable statutory exception.

Automatic and manual reminders share eligibility checks, send limits and history. Cancel queued reminders after completion, deletion, relevant objection or other loss of eligibility. Define expiry for abandoned attempts. The proposed 24/48-hour schedule is not approved timing. Schedule, maximum sends and legal eligibility must be resolved before enablement. Do not include promotional offers in security/continuation messages. Email-opening trackers are not part of the approved design.

Sources: [UWG §7](https://www.gesetze-im-internet.de/uwg_2004/__7.html), [DSK guest-access guidance](https://www.datenschutzkonferenz-online.de/media/dskb/20222604_beschluss_datenminimierung_onlinehandel.pdf). [HmbBfDI account/guest-access assessment, including OLG Hamburg 5 U 30/24](https://datenschutz-hamburg.de/news/gastzugang-im-onlinehandel). These are context-specific exceptions, not a general exemption for this platform. Guidance and relevant later case law must be considered together; the launch assessment remains open.

## 9. Retention and Erasure [PRIV-009]

Create a category-specific retention schedule before real-data launch. Include accounts, incomplete registration, invitations, verification/recovery material, customer cases/documents, financial records, employee/partner records, reminders, consent evidence, security/audit logs, exports, support and backups.

For each category specify purpose/basis, retention start trigger, period or objective criterion, archive access, legal holds, disposal action and owner. No single duration applies to all customer data. Account inactivity or suspension is not a justification for indefinite storage.

Accounting records require classification against current HGB/AO and any applicable special/transitional rules. Do not erase legally required invoices or records because a manager confirms deletion. Retain only the necessary records for the required purpose with limited access; dispose of unrelated data when no basis remains. Pseudonymized data remains personal data when reidentification is possible.

Deletion must cover linked stores, caches, search indexes, analytics copies, files and processor instructions where applicable. Backups require defined expiry, controlled access and a restore procedure that reapplies valid deletions/restrictions before ordinary use. Maintain minimal deletion-control evidence where lawfully needed; do not reimport erased profiles from CRM or backups.

Sources: [HGB §257](https://www.gesetze-im-internet.de/hgb/__257.html), [AO §147](https://www.gesetze-im-internet.de/ao_1977/__147.html).

## 10. Administrative Deletion and Dependencies [PRIV-010]

Customer full deletion is reserved to Platform Owner or Business Manager, within scope and owner safeguards. Display relevant dependencies, shared work effects, open cases, payments, refunds, debts, records subject to retention and consequences. Require explicit reviewed confirmation, reason and secure reauthentication.

Confirmation permits deletion of legally deletable data; it cannot override statutory preservation, a valid legal hold, another person's rights, protected ownership or system integrity. Explain retained categories and reasons and restrict retained data to its justified purpose. Record the actual result rather than falsely reporting that all data was erased.

Administrative deletion is distinct from processing a data-subject erasure request. A user's request must not be denied simply because they cannot exercise the administrative delete permission.

## 11. Individual Rights Workflow [PRIV-011]

Provide a usable contact/request pathway covering access, correction, erasure, restriction, objection, portability where applicable, consent withdrawal and applicable rights relating to automated decisions. It need not be an eighth customer-profile tab.

Track receipt, proportionate identity verification, responsible reviewer, deadline, systems searched, recipients/processors contacted, lawful exceptions, decision and secure response. Do not routinely demand an identity-document copy if less intrusive verification is sufficient. Rights requests must remain possible without an active login.

Ordinarily respond within one month; a justified extension of up to two further months requires notice and reasons within the first month. Apply the statutory conditions for refusal, fees or exceptions rather than inventing policy exclusions. Access responses must protect other people's rights and not disclose account secrets. Communicate correction/erasure/restriction to recipients where legally required. Portability is conditional and is not a universal right to every internal record.

Source: [EDPB — individual rights](https://www.edpb.europa.eu/sme/be-compliant/respect-individuals-rights_en).

## 12. Suppliers and Recipient Roles [PRIV-012]

Inventory hosting, storage, email, SMS, social login, payments, analytics, customer support, CRM, conferencing and partner services before use. Determine their factual role for each activity: processor, independent controller or joint controller. A “partner” title is not an automatic role classification.

Where a supplier is a processor, execute an Article 28 AVV/DPA and assess guarantees, instructions, confidentiality, security, subprocessors, assistance, incident handling, audit and return/deletion. Joint controllership requires the applicable Article 26 arrangement and transparency. Independent-controller disclosure still needs a lawful basis and safeguards.

Vendor selection must consider actual data flows and contract terms, not a generic claim of “GDPR compliant.”

Source: [EDPB — controller or processor](https://www.edpb.europa.eu/sme/learn-the-basics/data-controller-or-data-processor_en).

## 13. International Transfers [PRIV-013]

Map storage, subprocessors and remote support/access. EU hosting alone does not establish that no international transfer occurs. Before a relevant EEA-to-third-country transfer, identify an applicable Chapter V mechanism, its scope and current validity.

Where relying on adequacy, verify actual coverage; where relying on SCCs or another safeguard, carry out the necessary assessment and additional measures. Do not make routine transfers depend on exceptional derogations without legal review. Keep supplier/transfer evidence and reassess when providers, laws or access arrangements change.

Source: [EDPB — transfers](https://www.edpb.europa.eu/sme/be-compliant/international-data-transfers_en).

## 14. Cookies and Device Access [PRIV-014]

Inventory cookies, local storage, SDKs, embedded media, tracking pixels and similar device access. Assess TDDDG §25 separately from the GDPR basis for subsequent personal-data processing.

Strictly necessary terminal operations may qualify for the statutory exception. Optional analytics/advertising must not be enabled before valid consent where required; support rejection and withdrawal without deceptive design. Do not load social-provider trackers merely by displaying a login button. Define the actual integration and review its data flow.

Source: [TDDDG §25](https://www.gesetze-im-internet.de/ttdsg/__25.html).

## 15. Security and Operational Measures [PRIV-015]

Risk-appropriate technical and organizational measures must cover confidentiality, integrity, availability and recovery. The platform requires encrypted transport, appropriate protection at rest, key/secret management, least privilege, scoped MFA, secure sessions, vulnerability/dependency management, backup restoration tests, incident response and access reviews. Exact technology and measurable parameters follow architecture analysis.

Minimize log contents and access. Audit accountability does not justify unlimited logging or retention. No production personal data, credentials or confidential legal evidence may be committed to this public repository or copied into unapproved test environments. Use synthetic test data by default.

Verify unauthorized access, scope boundaries, deletion, export, recovery and restore behavior through meaningful acceptance tests. Security alone cannot make unnecessary or unlawful processing lawful.

## 16. Breach Response [PRIV-016]

Define detection, containment, evidence preservation, escalation and controller/processor contacts. Document personal-data breaches, consequences, assessment and measures, including reasons when notification is not required.

The controller must notify the competent authority without undue delay and, where feasible, within 72 hours of awareness unless the breach is unlikely to result in a risk to individuals' rights and freedoms. Explain delay where required and provide information in phases when necessary. Communicate to affected individuals without undue delay where high risk requires it, subject to applicable exceptions. Processors notify the controller without undue delay. Do not wait for an exhaustive technical investigation to assess time-sensitive duties.

Source: [EDPB breach notification guidelines](https://www.edpb.europa.eu/documents/guideline/guidelines-92022-on-personal-data-breach-notification-under-gdpr_en).

## 17. Risk, DPIA and Prior Consultation [PRIV-017]

Screen each processing activity for likely high risk before implementation, considering nature, scope, context, purposes, vulnerable people, sensitive documents, profiling, monitoring and dataset combination. Consider the competent German authority's mandatory DPIA lists.

Where Article 35 applies, complete a Datenschutz-Folgenabschätzung before processing: describe operations/purposes, necessity/proportionality, risks and measures; involve the DPO where designated and review material changes. If unmitigated high risk remains, evaluate required Article 36 prior consultation before processing. A platform containing loan workflows does not automatically mean every feature needs a DPIA; document the assessment.

Source: [EDPB DPIA guidance](https://www.edpb.europa.eu/documents/guideline/data-protection-impact-assessments-high-risk-processing_en).

## 18. DPO and Oversight [PRIV-018]

Assess Article 37 and BDSG §38 against actual operations. The German provision includes the threshold of generally at least 20 people regularly engaged in automated personal-data processing and additional cases independent of that number, including processing subject to a DPIA. Article 37 has its own criteria. Do not assume “small company” means no DPO.

If required, designate a qualified Datenschutzbeauftragter, ensure independence/resources and absence of conflicting duties, and publish/communicate required contacts. The controller retains responsibility. Keep the applicability decision and reassess organizational changes.

Source: [BDSG §38](https://www.gesetze-im-internet.de/bdsg_2018/__38.html).

## 19. Conditional Processing Boundaries [PRIV-019]

Children's access and age/parental-consent rules need analysis if introduced; Article 8 is not a universal age rule for every legal basis. Solely automated decisions producing legal or similarly significant effects, including credit outcomes, require Article 22 assessment and safeguards. Current Version 1 loan cases record human-managed reports, not automated lending decisions or live bank integration.

Do not introduce new biometric identity checks, special-category collection, employee monitoring, large-scale profiling or cross-domain marketing by treating the privacy baseline as prior approval. Analyze and approve the actual capability first.

## 20. Mandatory Module Review and Evidence [PRIV-020]

Every new or amended specification must include:
1. Purposes, people, categories, sources and minimum fields.
2. Basis and necessity, including mandatory/optional distinction.
3. Access purposes, permissions and record/field scope.
4. Notices, consent/objection controls where applicable.
5. Retention, holds, deletion, backup/restore and relationship effects.
6. Individual rights and authoritative correction/export paths.
7. Suppliers, AVV/roles, recipients and international transfers.
8. Device access, communications and UWG/TDDDG applicability.
9. Security measures, incident dependencies and evidence.
10. DPO/DPIA/sector-rule screening and open launch blockers.

Mark each item Applicable, Not applicable with reason, or Open with owner and resolution requirement. Blank checklist completion is not proof. Trace requirements to design, implementation tests and operational evidence. Unresolved legal blockers prevent affected real-data launch; they do not require inventing premature database fields.

## 21. Launch Decisions and Source Register [PRIV-021]

Outstanding operating decisions: controller details and authority; actual field/account necessity by service; lawful reminder content, eligibility, schedule and limits; retention schedule; supplier contracts and transfer assessments; privacy notices; request handling and deadlines; DPO/DPIA screening; incident runbook; cookie/device inventory; and technical verification. The document establishes requirements, not completed operational evidence.

### Legal Traceability and Evidence Register

| Legal area | Baseline groups | Required operating evidence |
|---|---|---|
| GDPR Articles 5, 6, 24, 25 | PRIV-002–006, 020 | Purpose/necessity inventory, legal-basis decisions, privacy-design review |
| GDPR Articles 7, 9, 10 | PRIV-003–004, 019 | Applicable consent evidence and special-category/criminal-data assessment |
| GDPR Articles 12–22 | PRIV-005, 010–011, 019 | Notices, rights procedure, deadlines and secure response evidence |
| GDPR Articles 26, 28–30 | PRIV-002, 012 | Role assessment, VVT, applicable AVV/joint-controller arrangements |
| GDPR Article 32 | PRIV-007, 015 | Technical/organizational measures, access reviews and verification |
| GDPR Articles 33–34 | PRIV-016 | Incident register, risk decisions, authority/user notification evidence |
| GDPR Articles 35–36 | PRIV-017 | DPIA screening, required assessment and consultation decision |
| GDPR Articles 37–39; BDSG §38 | PRIV-018 | DPO applicability, designation/resources and contacts where required |
| GDPR Articles 44–49 | PRIV-013 | Transfer map, mechanism, coverage and assessment |
| BDSG §26 | PRIV-007 | Employment necessity, device/channel and monitoring-purpose assessment |
| TDDDG §25 | PRIV-014 | Terminal-access inventory and exemption/consent decisions |
| UWG §7 | PRIV-008 | Actual-message classification, permission/exception and send eligibility |
| HGB §257; AO §147 | PRIV-009–010 | Category-specific retention schedule and lawful disposal/hold decisions |

Each operating entry must have an accountable owner, current decision status, legal/source reference, affected requirement IDs, evidence location and unresolved action. Statuses distinguish Open, Assessed, Implemented and Verified; these are not interchangeable. Private assessments and real evidence must remain outside the public repository.

Authoritative reference set:
- [GDPR official text, including Articles 5–7, 9–10, 12–22, 24–25, 26–30, 32–39 and 44–49](https://eur-lex.europa.eu/eli/reg/2016/679/oj/eng).
- [German BDSG](https://www.gesetze-im-internet.de/bdsg_2018/).
- [German TDDDG](https://www.gesetze-im-internet.de/ttdsg/).
- [German UWG](https://www.gesetze-im-internet.de/uwg_2004/).
- [EDPB small-business practical guide](https://www.edpb.europa.eu/sme_en).
- [DSK official guidance and decisions](https://www.datenschutzkonferenz-online.de/).

Primary law is authoritative; regulator guidance assists interpretation; framework recommendations guide design. Revalidate sources at the relevant decision. Keep legal assessments and implementation status separate from approved product requirements.
