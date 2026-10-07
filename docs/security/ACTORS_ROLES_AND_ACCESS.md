# Actors, Roles and Access Model

Status: Approved — actor and access model; domain permission catalogs require dedicated module analysis.
Owner: Product Owner
Last reviewed: 2026-10-07
Prerequisite: [Platform vision and Version 1 scope](../product/PRODUCT_VISION.md)

## 1. Purpose and Scope

This document defines the platform's people, organizations, roles and access model and provides the basis for analyzing permissions in each domain.

Registration, login identifiers, authentication, account recovery and invitation mechanics will be specified in a separate Identity, Accounts and Authentication document. That document has not yet been created.

## 2. Core Concepts

| Concept | Definition |
|---|---|
| Person | A real individual who may be a customer, owner, manager, employee, instructor, consultant, specialist in a particular field, or several of these simultaneously. |
| Organization | A collaborating company or organization represented by identified individuals. |
| User account | A person's means of logging into the platform. A person may be recorded in the system before an account is created. |
| Relationship type | The person's or organization's relationship with the business, such as customer, employee or external partner. |
| Permission | Authorization to perform a specific operation, such as viewing a case or approving a settlement. |
| Role | A set of permissions associated with a responsibility. |
| Access scope | The information and cases to which a permission applies. |

A relationship type or job title alone does not grant permissions. Access is determined by assigned roles and their scopes.

## 3. One Account and Multiple Roles

Each person has one login account and may hold multiple roles, for example instructor, consultant and customer simultaneously.

A collaborating company does not use a shared account. Its representatives log in with personal accounts so that responsibility for each action is identifiable. Each representative's access scope is assigned separately.

Recording a person in CRM does not necessarily mean that the person has a login account.

## 4. Environment Selection and Switching

The platform has two main environments: the Customer Portal and the Staff and Partner Portal.

| Person's access | Behavior after login |
|---|---|
| Customer Portal only | Enter the Customer Portal directly. |
| Staff and Partner Portal only | Enter the working environment directly. |
| Both portals | Display a choice of environment. |

A person with access to both environments can switch through a Switch Environment menu without logging out and back in.

In the Customer Portal, the person sees their own information and services. In the working environment, their work-related permissions apply.

Selecting an environment grants no additional permission. The system must check authorization for every operation and information access. Switching environments, changing a page URL or sending a request directly must not allow access restrictions to be bypassed.

## 5. Platform Owner and Business Manager

### 5.1. Platform Owner

Platform Owner has the highest administrative and business authority across the platform. Their access is not less than that of Business Manager and includes Business Manager's authority.

Platform Owner can manage roles, delegate access and manage platform domains.

The following safeguards are mandatory and must be implemented and tested:
- Business Manager and ordinary administrators cannot remove, restrict or replace Platform Owner.
- Ownership assignment or transfer is a separate operation under the owner's authority.
- Removing or deactivating the last active Platform Owner is prohibited.
- Full authority does not permit bypassing data integrity rules or making changes without audit records.

### 5.2. Business Manager

Business Manager administers business activities within the authority delegated by Platform Owner.

Platform Owner and Business Manager are distinct responsibilities but may be held by the same person.

### 5.3. Technical Administrator

If needed, a separate Technical Administrator role will be defined. Technical responsibility alone does not confer Platform Owner authority or full business access.

## 6. Initial Roles

The system starts with the following roles. Detailed permissions for each role will be completed during analysis of the relevant domains.

| Role | General responsibility |
|---|---|
| Platform Owner | Ultimate platform administration and authority. |
| Business Manager | Administration of business activities. |
| User and Collaboration Coordinator | User, invitation and collaboration management. |
| Catalog and Pricing Coordinator | Management of products, services and prices. |
| Sales and Customer Relations Coordinator | Sales, opportunities and customer follow-up. |
| Academy Coordinator | Education, courses and enrollment management. |
| Instructor | Work on assigned education and courses. |
| Consultation Coordinator | Consultation management and coordination. |
| Consultant | Delivery and follow-up of assigned consultations. |
| Loan Case Coordinator | Loan case follow-up. |
| Specialist Service Provider | Service delivery and recording progress and outcomes. |
| Finance Officer / Accountant | Authorized accounting and financial activities. |
| Customer | Use of services and management of their own information. |

Initial working roles are configurable defaults, not hard-coded role definitions. An authorized administrator may edit, copy or deactivate them and create new roles.

Platform Owner is subject to the safeguards in section 5.

## 7. Operational Permissions

Permissions are defined alongside each domain or process during its analysis, including:
- View.
- Create.
- Edit.
- Assign a responsible person.
- Approve.
- Pay.
- Settle.
- Export.
- Manage roles and access.

Sensitive operations have separate permissions. Editing financial information does not automatically authorize settlement approval.

Default roles are initialized with a defined set of relevant permissions. Accountant receives permissions defined for accounting responsibilities, not authority to administer the whole platform.

Custom roles are assembled from existing permissions. A new capability or permission type requires analysis and implementation of that capability.

Application logic checks permissions rather than role names. Renaming or recombining roles must not depend on changing application code.

## 8. Role Inheritance

A role may inherit permissions from one or more other roles.

For example, Business Manager may inherit permissions from designated domain management roles and hold additional authority.

Inheritance rules:
- Relationships must be explicit and visible.
- Circular relationships are prohibited.
- Job titles alone do not create inheritance.
- Changing a role's permissions also affects roles that inherit from it.
- A copied role is independent: changes to the original do not change the copy's directly assigned permissions. Any inheritance relationships retained in the copy must be explicit and visible.

A person's effective authority is obtained by combining permissions from active roles, including inherited permissions, and then applying data scope and process rules.

## 9. Data Access Scopes

| Scope | Example |
|---|---|
| Own information | The customer's own purchases and cases. |
| Assigned records | Sessions and cases assigned to a consultant. |
| A specified team or unit | Cases managed by a team. |
| A specified partner organization | Authorized records associated with a collaborating company. |
| Entire business | Business information within managerial authority. |
| Entire platform | Platform Owner authority. |

Permission inheritance and data scope are controlled separately. A manager may perform the same operations as a consultant with a broader scope.

A permission does not override process rules. For example, changing a finalized settlement must follow the financial correction process.

## 10. Role and Access Administration

### 10.1. Who May Administer Roles

- Platform Owner may create, copy, edit and deactivate roles; change permissions and scopes; and assign or revoke roles.
- Business Manager has the same capabilities for working roles within the business they manage, subject to delegated authority.
- Other people do not have this authority by default. Limited delegation requires an explicit decision and assignment by Platform Owner.
- Business Manager cannot create or edit a role to obtain Platform Owner authority for themselves or another person.

### 10.2. Administration Operations and Constraints

Within their authorized scope, an administrator may:
- Create a role.
- Copy an existing role.
- Change a working role's name, description and permissions.
- Configure inheritance relationships and authorized scopes.
- Assign or revoke roles.
- Deactivate a role.
- Set an expiry date on a role assignment.

Administrators may delegate only permissions and scopes that they are authorized to delegate.

Before saving a role change, the system must display affected people and roles. Role, inheritance, permission and assignment changes must be audited.

## 11. Restricting Access

### 11.1. Changes for All Holders of a Role

Editing the original role affects its holders and inheriting roles.

### 11.2. Changes for One Person

The administrator copies an existing role, restricts the copy and assigns it to the person. The previous broader role must be revoked if the person's access is intended to decrease.

The system must show where each permission originates. Removing a permission from one role does not remove access if another role still grants it.

Version 1 uses roles, inheritance and scopes for restrictions. Independent person-specific Deny exceptions are outside this initial model.

## 12. User Creation and Invitations

- Customers may request registration for themselves.
- Authorized employees may record a contact without creating a login account.
- Employees and partners receive working access through invitation by an authorized person.
- Public registration cannot grant working or administrative roles.
- Stopping working access does not necessarily delete the person's customer account or information.

Execution details will be defined in the Identity and Accounts specification.

## 13. Access Enforcement and Auditing

Access controls apply to operations, data, files, reports, search, notifications and exports.

Hiding a menu is insufficient. The system must check authorization when processing an operation or information request, including requests submitted directly without using the displayed interface. Access that has not been explicitly granted is not permitted.

Role changes and access revocations must be reflected in system authorization. The timing and technical mechanism will be defined during analysis of authentication and sessions.

## 14. Document Relationships and Further Analysis

- This model depends on the two-portal scope in the [Product Vision](../product/PRODUCT_VISION.md).
- The future Identity, Accounts and Authentication specification will define account creation and login based on this model.
- Each module specification will define its operational permissions and data scopes and link to this document.
- Initial role permission details will evolve as module analysis is completed; this document's principles remain their baseline.
- [Ownership terminology](../architecture/OWNERSHIP_TERMINOLOGY.md) defines ownership titles; this document defines their access responsibilities.
- The [documentation index](../README.md) provides the reading sequence and specification status.

## Implementation Status

This is an approved design specification. It does not claim that the model has been implemented or deployed.
