# Azadiemali Platform Vision and Version 1 Scope

Status: Approved — product vision and scope; detailed specifications remain subject to review.
Owner: Product Owner
Last reviewed: 2026-10-07

## Platform Languages

The platform will support Persian, English and German. The Persian interface will use right-to-left layout; English and German interfaces will use left-to-right layout. The translation scope for content, notifications and generated documents will be determined in the relevant detailed analysis. Engineering documentation is maintained in English.

## 1. Business Overview

Azadiemali is a business currently focused on educating the Iranian and Persian-speaking community living in Germany about real estate. Its subject areas include buying, selling, renting, investing in, maintaining, optimizing and renovating property.

Its activities extend beyond publishing general educational content. The business identifies interested audiences and provides education, consultation and services related to real estate and financing, according to their personal-use or investment needs.

The two main audience groups are:
- Persian speakers who need property-related services in Germany for personal use.
- Persian speakers who intend to enter the German real estate investment market or develop their activities professionally.

## 2. Problem and Platform Purpose

Business information and activities are currently distributed mainly across Instagram, WhatsApp and manual follow-up. This fragmentation makes customer relationship management, sales, scheduling, service delivery and follow-up difficult.

The platform will provide an integrated environment for managing the audience journey from first contact through purchase, service delivery and subsequent follow-up.

It should connect customer information, education, consultation, specialist services, loan cases and related financial activities, and reduce reliance on manual recording and follow-up.

## 3. Overall Platform Structure

The platform has two main environments:
1. Customer Portal: access to the customer's own information, education, services and related processes.
2. Staff and Partner Portal: platform administration and service delivery by employees, consultants, instructors and collaborating individuals or companies.

Available functions and information in the Staff and Partner Portal will vary according to each person's role, responsibilities and relationship with the business. Roles and permissions will be defined through dedicated analysis.

Course, instructor and service introductions should be accessible before login. Purchases, enrollment and personal tracking will take place through the Customer Portal.

## 4. Customer Portal Scope for Version 1

### 4.1. Account and Profile

Manage customer information and user experience settings. Dedicated analysis must cover profile information, account security, notification preferences, privacy and personal information management.

References to application settings do not constitute a commitment to deliver a mobile application in Version 1.

### 4.2. Academy and Education

The Academy consists of two related areas.

**A. Self-paced multimedia education**
- Purchase paid educational packages or enroll in free education.
- Access the customer's educational content.
- Support a self-paced learning experience.

Content structure, learning paths, progress tracking and other capabilities will be defined in the dedicated specification. Inclusion in Version 1 does not require advanced features such as examinations or certificates.

**B. Courses and educational camps**
- Purchase or enroll in free or paid courses and camps lasting one or several days.
- View upcoming course schedules and calendars.
- View course introductions, instructors and their backgrounds.
- Access information about enrolled courses.

Online delivery is in scope. Inclusion of in-person courses in Version 1 will be determined during detailed analysis.

### 4.3. Consultation

Customers must be able to request and manage consultation, including:
- Selecting or describing the consultation topic.
- Requesting and coordinating appointments.
- Viewing and managing consultation appointments.
- Paying consultation fees.
- Tracking request and session status.

Time selection, confirmation, rescheduling, cancellation and other rules will be determined in the dedicated analysis.

### 4.4. Specialist Services

Request and track services with defined delivery stages and outputs, such as:
- Reviewing documents for property purchases and sales.
- Property valuation.
- Estimating renovation costs.
- Finding suitable property.
- Energy consultation and optimization.
- Specialist services requiring multiple in-person or online sessions.

Each service may have a case containing delivery stages, documents, responsible parties, sessions and a final outcome.

Consultation focuses on receiving guidance through a session. A specialist service focuses on performing work and delivering an outcome; it may include multiple consultation sessions.

### 4.5. Loan Cases and Follow-up

Support customers through loan consultation and follow-up, including:
- Viewing case status and stages.
- Receiving recommendations and requests for additional information.
- Submitting documents and tracking their status.
- Communicating with the person responsible for follow-up.
- Viewing proposals, assessments and action history through a timeline.

This is a case management and customer communication system. Direct integration with banking and financial systems is outside Version 1 scope. Responsible people record statuses and outcomes.

Processes, documents and responsibilities require dedicated analysis.

## 5. Staff and Partner Portal Scope for Version 1

### 5.1. User and Collaboration Management

Manage customers, employees, consultants, instructors and collaborating individuals or companies, together with their information and relationship to the business.

Account structure, roles, permissions and collaboration processes will be defined through dedicated analysis.

### 5.2. Product Catalog and Pricing

Define and manage educational products and services, including introductions, delivery conditions and pricing. Authority to create or change products and prices will follow the management permission model.

### 5.3. Sales and Order Management

Manage education and service sales, orders, payments, cancellations and refunds. This capability is shared across domains to avoid inconsistent, duplicated sales processes.

### 5.4. Academy Management and Instructor Workspace

Manage self-paced education, courses and camps, and provide an appropriate working environment for instructors.

Content, delivery schedules, participants and instructor responsibilities will be defined through dedicated analysis.

### 5.5. Consultation Management and Consultant Workspace

Manage consultation requests, scheduling, sessions and follow-up for management, responsible employees and consultants, according to their respective access permissions.

### 5.6. Specialist Service Management

Manage service cases, delivery stages, documents, responsible parties, sessions and outputs, including the capabilities required by internal and external providers.

### 5.7. Loan Case Management

Manage customer loan cases, request documents, record assessments and proposals, assign responsible parties and communicate case progress.

This area connects to the customer's loan workspace and does not depend on banking integration.

### 5.8. CRM

The CRM must be analyzed and designed according to business needs. It should track the customer journey from first contact through sales, service delivery and follow-up, and help improve relationships and revenue generation.

Sales, education, consultation and service cases manage their specialist information; the CRM provides an integrated view of customer history and communications.

Customer business history is separate from system audit events.

The choice between building a custom CRM and using and customizing an existing product will follow requirements analysis.

### 5.9. Basic Accounting and Financial Management

Provide the capabilities of a simple accounting system for basic management of business finances, including initial financial calculations, billing documents and settlements with individuals and companies.

The capability level, profit and loss calculation method and accounting details will be determined through dedicated analysis.

The system must support integration with larger accounting software. Selecting and implementing a particular integration requires a separate decision.

### 5.10. Reporting

Produce general and specialist reports according to the needs of managers, employees and other authorized users.

Each report must respect the user's responsibilities and access level. Metrics, calculations and report formats will be defined through dedicated analysis.

## 6. Shared Capabilities

The following capabilities are used across domains and must be designed consistently:
- Communications and messages.
- Notifications.
- Documents and files.
- Calendars and scheduling.
- Sales and payments.
- Access control.
- Audit event recording.

Detailed analysis will determine which capabilities also need a shared portal view in addition to their domain-specific presentation.

## 7. Version 1 Boundaries and Further Decisions

The domains described above are within Version 1 scope. The depth of each domain's capabilities will be determined through dedicated analysis. Inclusion of a domain does not imply delivery of every advanced capability.

This document does not finalize:
- Detailed domain permission catalogs and role-to-permission mappings; the foundational model is defined in [Actors, Roles and Access](../security/ACTORS_ROLES_AND_ACCESS.md).
- Advanced education and accounting capability levels.
- The choice of an existing or custom CRM.
- A specific accounting software integration.
- Inclusion of in-person educational courses in Version 1.
- Implementation and release sequence.
- Numerical success targets.

A mobile application and direct banking integration are not Version 1 commitments.

## 8. Expected Outcomes

Version 1 should enable:
- Customers to track their own requests, purchases, education and services within a coherent environment.
- Employees and partners to manage activities within their responsibilities.
- Consistent information and statuses between the Customer Portal and the Staff and Partner Portal.
- Reduced reliance on scattered messages and records for customer follow-up and service delivery.
- Manageable and reportable basic finances and settlements.

These outcomes express the direction of product success. Testable criteria and numerical targets will be determined during domain analysis and delivery planning.

## 9. Further Analysis and Documentation

Following approval of this document, each area will be analyzed separately to define requirements, users, flows, rules, data, access, integrations and acceptance criteria.

Dedicated documents will be prepared where needed. No document is created or updated in the repository until its content has been fully reviewed and approved.

Scope changes and additional capabilities remain possible, subject to review and approval.

The [actors, roles and access model](../security/ACTORS_ROLES_AND_ACCESS.md) is approved. The next analysis is identity, accounts and authentication. Subsequent analysis follows user journeys, overall architecture, module specifications, data and integration contracts, then delivery and acceptance testing.

## 10. Document Dependencies

This document is the product scope entry point and has no prerequisite specification.

Use the [documentation index](../README.md) to locate existing specifications and their status. The approved [ownership terminology](../architecture/OWNERSHIP_TERMINOLOGY.md) defines business and platform ownership titles; it does not define the complete role or permission model.

Dependent specifications must link back to this document and to their completed prerequisites. Do not create links to documents that do not yet exist.

## Implementation Status

This document specifies approved product intent and scope. It does not claim that the capabilities have been implemented or deployed.
