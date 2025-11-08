# 🌴 Vacation Tracking System (VTS)

A centralized internal system for managing employee vacation requests, approvals, balances, and HR workflows.

---

## 🧭 Vision (Consolidated)

* Improve internal business processes by reducing the time needed to manage vacation time requests.
* Empower employees to manage their own vacation, sick, and personal leave without deep policy knowledge.
* Primary design goal: the system must be **easy to use**, **intuitive**, and **intelligent**.

---

## 🧠 Problem Domain

Centered around the management of employee vacation time, sick leave, and personal time off within an organization.

---

## ⚙️ Functional Requirements (Merged)

1. **Rules-based validation engine** for leave requests (policy limits, balances, blackout periods, tenure rules, etc.).
2. **Optional manager approval** depending on role/level; some senior roles may bypass approval.
3. **Notifications** via email (and portal inbox if available) to employees and managers on submit/approve/reject/cancel.
4. **Single Sign-On** (SSO) via the organization’s portal; use the portal’s user context for all authentication.
5. **Activity logs** for all transactions (auditable: who, what, when, before/after values, IP/device).
6. **HR & System Administration overrides** with full audit tracking (amend, grant, revoke, correct balances).
7. **Managers can directly grant personal/comp time** within configured limits.
8. **Integration services** with legacy HR/Payroll/Directory to sync employees, calendars, and balances.
9. **Vacation timeline access window:** view prior year records and plan up to **1.5 years ahead**.
10. **Self-service dashboard** for employees (submit, track, cancel) and managers (review queues, filters, bulk actions).
11. **Internal API** for querying summaries (e.g., per-employee/year, team calendar, remaining balances).
12. **Balance lookup** on request creation and after status changes to ensure consistency.

---

## 🧩 Non-Functional Requirements (Merged)

* **Usability:** UI must be simple, clear, and employee-friendly (primary design goal).
* **Performance:** Core operations (submit, approve, fetch balances) should complete within acceptable SLAs (e.g., P95 < 1s for reads, < 2s for writes where feasible).
* **Scalability:** Support organization-wide usage (concurrent users, seasonal peaks) without degradation.
* **Reliability & Consistency:** Accurate balances and idempotent operations; safe retries.
* **Security:** SSO + RBAC; least privilege; sensitive fields masked; audit immutability.
* **Maintainability:** Clean, modular architecture; testable services; configuration-driven rules.
* **Auditability:** End-to-end trace of every state change.
* **Observability:** Metrics, logs, and alerts (errors, latency, queue depth).

---

## ⛔ Constraints (Merged)

1. **Web application** within the existing **Intranet Portal**.
2. Must **reuse existing hardware and middleware**.
3. Must use **existing SSO** for authentication.
4. Respect **legacy integrations** (HR/Payroll) and their data contracts.
5. **HR** remains the source of truth for policy and employee master data.

---

## 🎭 System Actors

* **Employee** — submit/track/cancel leave; view balances.
* **Manager** — review/approve/reject; grant comp/personal leave within limits.
* **HR Clerk** — manage policies/records; override decisions.
* **System Administrator** — configure, maintain uptime, logs, backups.
* **Email Service** — delivers notifications.

---

## 📊 System Diagrams

### 1) Employee Flowchart
![Employee Flow](docs/employee_flowchart.png)

### 2) Manager Flowchart
![Manager Flow](docs/manager_flowchart.png)

---

## 🔁 Sequence Diagrams (Split)

### A) Employee — Manage Time (Submit Leave Request)

![VTS Sequence Diagram](docs/employee_sequence_diagram_mange_time.svg)

### B) Manager — Review & Decision

![VTS Sequence Diagram](docs/manger_sequence_diagram_mange_time.svg)



