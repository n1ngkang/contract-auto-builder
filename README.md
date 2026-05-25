# demoCompany Contract Automated Generation System

## Executive Summary

This project features a high-performance, enterprise-grade **Modular Contract Automation Engine** built on Google Apps Script (GAS). It is strategically architected to orchestrate single-store agreements, complex group/shared contract aggregations, fully automated renewal pipelines, and dynamic multi-version email dispatches.

By transitioning from a fragmented legacy script setup to a strict **Domain-Driven Design (DDD)**, the system completely decoupling core platform capabilities from shifting business rules. This modern architecture guarantees minimal code redundancy, slashes maintenance overhead, and establishes a highly scalable infrastructure ready for rapid regional and multi-product onboarding.

---

## System Architecture

The project features a high-performance, modularized Google Apps Script environment, where clear separation of concerns maps business logic, legal definitions, and UI event tracking.

### Core & Domain Modules (Root Engine)

These modules act as the processing engine, handling target pipelines spanning individual agreements, multi-store clusters, automated renewals, and messaging:

* [`TW_autorenew_core.js`](./TW_autorenew_core.js) — **The Master Orchestration Engine.** Regulates execution lifecycles, transactional safety, conditional parsing, and automated data synchronization loops across renewal windows.
* [`TW_group_core.js`](./TW_group_core.js) & [`TW_group_settings.js`](./TW_group_settings.js) — **The Group-Merchant Vertical.** Driving multi-store hierarchical computations, cross-branch data aggregation, and structural settings specific to shared store plans.
* [`TW_single_core.js`](./TW_single_core.js) & [`TW_single_settings.js`](./TW_single_settings.js) — **The Single-Merchant Vertical.** Governs single-store lifecycles, computing isolated contract terms, pricing parameters, and direct validation gates.
* [`TW_email_core.js`](./TW_email_core.js) — **The Core Communications Gateway.** Powers email schema assembly, asynchronous dispatch pipelines, and external asset mapping.

---

### UI & Control Layer

* [`ui.js`](./ui.js) — **The Native Workspace Controller.** Injects programmatic extensions directly into the Google Sheets runtime environment via `onOpen()`. It provides internal stakeholders with specialized action dashboards:

---

### Template Layer

* [`/autorenewal_email_template/`](./autorenewal_email_template/) — Dedicated repository subdirectory storing responsive HTML notification markup:
  * [`html email body1.html`](./autorenewal_email_template/html%20email%20body1.html) / [`body2.html`](./autorenewal_email_template/html%20email%20body2.html) — Standard individual contract templates.
  * [`share plan html email body1.html`](./autorenewal_email_template/share%20plan%20html%20email%20body1.html) / [`body2.html`](./autorenewal_email_template/share%20plan%20html%20email%20body2.html) — Hierarchical group/shared contract configurations.
---

## Technical Value Propositions

### 1. Domain-Driven Decoupled Architecture
By partitioning corporate logic into strict domain boundaries (`single`, `group`, `email`, `autorenew`), the engine mitigates cross-module side effects. Upgrading or refactoring one contract vertical results in **zero blast radius** across the rest of the ecosystem.

### 2. High-Reusability Abstraction Layer
Centralizing platform utilities into the `/core` boundary ensures single-source-of-truth reliability. This layout achieves a massive drop in code duplication, making future system-wide adjustments trivial.

### 3. Configuration-Driven Business Agility
Contract execution branches, limits, and product rates are abstracted out into structural `settings` modules. Operational stakeholders or developers can hot-swap critical legal constraints or pricing matrices instantly without rewriting core state machines.

### 4. Separated Presentation & Version-Controlled Email Templates
Email assets are kept entirely out of backend script strings and placed into an externalized HTML template directory. This setup empowers seamless visual changes, localized messaging matrices, and flawless content iterations.

### 5. Highly Elastic Contract Processing Multiplexer
The standard interface abstraction allows a single unified execution wrapper to dynamically process fundamentally different billing structures:
* **Time-Sliced Single Store Models**
* **Hierarchical Group Share Matrices**
* **Automated Renewal Subscriptions**

---

## Deployment & Development

### Infrastructure Requirements
* **Node.js** (v18+ recommended)
* **Google Apps Script CLI** ([`clasp`](https://github.com/google/clasp) configured globally)
* **Google Workspace Corporate Credentials**

### Workspace Setup

```bash
# 1. Authenticate with Google Cloud Platform & GAS
clasp login

# 2. Clone the script project locally using your unique Script ID
clasp clone <YOUR_APPS_SCRIPT_ID>

# 3. Deploy changes back up to the cloud environment
clasp push
