# MDE · NIST CSF 2.0 Deployment Tracker

**A browser-based Microsoft Defender for Endpoint deployment tracking dashboard for MSSP security engineers, mapping 57 actionable tasks across all 6 NIST CSF 2.0 functions with per-task status tracking, notes, live progress metrics, dark/light mode, and full export support.**

---

## Overview

The MDE · NIST CSF 2.0 Deployment Tracker is a self-contained, single-file HTML dashboard designed for security engineers at Managed Security Service Providers (MSSPs) operating within the Microsoft Security stack. It provides a structured, auditable framework for deploying Microsoft Defender for Endpoint (MDE) across client environments while maintaining alignment with the NIST Cybersecurity Framework 2.0.

All data is stored locally in the browser via `localStorage` — no backend, no login, no external dependencies beyond Google Fonts. The entire tool is portable as a single `.html` file.

---

## NIST CSF 2.0 Function Coverage

The dashboard maps 57 deployment tasks across all six NIST CSF 2.0 functions:

| Function | ID | Tasks | Focus Area |
|---|---|---|---|
| Govern | GV | 8 | Licensing, RBAC, device groups, tenant settings, governance policy |
| Identify | ID | 10 | Device onboarding (Windows/Linux/macOS), TVM, asset inventory |
| Protect | PR | 12 | NGAV, ASR rules, Network Protection, Tamper Protection, BitLocker |
| Detect | DE | 10 | EDR, Advanced Hunting (KQL), Sentinel integration, deception |
| Respond | RS | 8 | AIR, Live Response, isolation workflows, playbooks, ticketing |
| Recover | RC | 7 | Remediation review, Secure Score, post-incident analysis |

Each task includes:
- A unique task ID (e.g., `PR-03`, `DE-05`)
- Mapped NIST CSF 2.0 subcategory reference (e.g., `PR.PS-01`, `DE.CM-09`)
- Priority level: High / Medium / Low
- A concise, actionable description of the MDE configuration step

---

## Features

### Tracking & Status Management
- **Per-task status** with four states: Not Started, In Progress, Complete, Blocked
- **Checkbox completion** with visual strikethrough on completed tasks
- **Per-task notes field** for engineer observations, ticket references, or blockers
- All state auto-saves to browser `localStorage` — persists across sessions and browser restarts

### Dashboard Metrics
- Live overview cards showing total tasks, completed, in-progress, blocked, and overall completion percentage
- High-priority pending task count surfaced at the top level
- Per-function completion percentages updated in real time as tasks are updated

### Navigation
- Tab-based navigation to view all functions together or drill into a single NIST CSF function
- Per-tab completion counters (e.g., `4/12`) showing progress at a glance

### Appearance
- Full dark mode and light mode support
- Theme preference persists across sessions
- Responsive layout — usable on tablet and mobile (limited columns on smaller screens)

### Export Options
| Format | Description |
|---|---|
| **CSV** | All 57 tasks with function, task ID, NIST subcategory, priority, status, and notes — ready for Excel or Google Sheets |
| **HTML Report** | A clean, standalone printable deployment report with summary metrics and full task table |
| **JSON Config** | Structured JSON export of the full configuration including metadata, summary, and all task states — suitable for version control, API ingestion, or audit logging |

The JSON Config also has an in-dashboard preview with one-click copy to clipboard.

---

## Use Cases

### 1. New MDE Client Onboarding (MSSP)
When onboarding a new client onto MDE, use the tracker as a deployment checklist. Work through the Govern and Identify functions first to establish licensing, RBAC, and device onboarding. Export the JSON config at project start and end to document the delta for the client's audit file.

### 2. Compliance Evidence & Audit Support
Map deployment activities directly to NIST CSF 2.0 subcategories for compliance reporting. Export the HTML report as a point-in-time snapshot for auditors, virtual CISOs, or client QBRs. The NIST subcategory column (e.g., `PR.PS-01`, `DE.CM-09`) provides direct traceability to control requirements.

### 3. SOC Team Coordination
Assign status and notes per task to track ownership across analyst tiers. Use the "Blocked" status to surface dependencies or escalations. Notes fields can hold ticket numbers (e.g., `INC-4821`), approval gates, or peer-review sign-offs.

### 4. Client Deployment Status Reporting
Export the HTML report before client check-in calls to show a structured, professional view of deployment progress. The per-function completion percentages provide an at-a-glance executive summary without exposing raw configuration details.

### 5. Deployment Baseline Documentation
Export JSON at the end of each deployment phase to create versioned configuration snapshots. Store these in a client folder or git repository to maintain a change history. The JSON schema is clean and human-readable, suitable for diffing between versions.

### 6. Onboarding New Security Engineers
Use the dashboard as a structured training guide for analysts new to Microsoft Defender for Endpoint. Each task description provides the what and where (portal location or policy type), and the NIST mapping provides the security rationale.

### 7. Security Posture Gap Assessment
Use the dashboard to assess an existing MDE deployment against a complete baseline. Mark tasks as Complete where controls are already in place and Blocked or Not Started where gaps exist. Export the CSV for a gap analysis report.

---

## Getting Started

1. Download `mde-nist-dashboard.html`
2. Open it in any modern browser (Chrome, Edge, Firefox, Safari)
3. No installation, login, or internet connection required after the initial load (fonts load from Google Fonts on first open)
4. Begin updating task statuses and notes — all changes save automatically

---

## Data & Privacy

All data is stored exclusively in your browser's `localStorage`. Nothing is transmitted to any server. The dashboard is fully offline-capable after the initial load. To transfer your progress to another machine, use the **JSON Config export** and manually load the state (or share the JSON for manual reference).

---

## Technical Notes

- **Single-file HTML** — no build tools, frameworks, or dependencies to install
- **Fonts**: JetBrains Mono (monospace/code elements) + DM Sans (UI text) via Google Fonts
- **Browser support**: All modern browsers (Chrome 90+, Edge 90+, Firefox 88+, Safari 14+)
- **Storage**: `localStorage` key `mde-tracker-state` for task state, `mde-theme` for theme preference
- **Export**: Uses `Blob` + object URLs for client-side file generation — no server required

---

## Microsoft Security Stack Context

This tool is scoped exclusively to **Microsoft Defender for Endpoint (MDE)** and its integrations within the Microsoft Security ecosystem, including:

- Microsoft Defender XDR portal
- Microsoft Intune (Endpoint Security policies)
- Microsoft Entra ID (Conditional Access, RBAC)
- Microsoft Sentinel (SIEM/SOAR integration)
- Microsoft Defender Vulnerability Management (TVM)
- Microsoft Defender for Identity (deception/lateral movement)
- Power Automate (response automation)

---

*MDE · NIST CSF 2.0 Deployment Tracker | Built for MSSP Security Engineers | Microsoft Security Stack*
