# 🖥️ Mock IETM Viewer Walkthrough

This document simulates how the TIQ incident data modules would appear inside an Interactive Electronic Technical Manual (IETM) viewer such as Boeing’s **S1000Dprism**. The goal is to show how modular XML entries can be navigated, rendered, and referenced by analysts and maintainers.

---

## 🔍 Viewer Structure

```
TIQ SYSTEM INCIDENT REPORTS
├── Token Renewal Failure (DM: tiq-token-refresh.xml)
│   ├── Description
│   ├── Fault & Cause
│   ├── Remedy Steps
│   ├── Logs + Timeline
│   └── Remarks
│
├── appendChild Null Error (DM: appendchild-null.xml)
│   ├── Description
│   ├── Stack Trace Figure
│   ├── DOM Handling Fixes
│   └── Remarks
│
└── Moment.js Deprecation (DM: moment-warning-deprecation.xml)
    ├── Description
    ├── Console Warning
    ├── Refactor Strategy
    └── Remarks
```

Each entry would be rendered via a left-hand TOC (Table of Contents), with tabbed or expandable panels for:
- Content (XML body rendered to styled HTML)
- Linked graphics (e.g. screenshots)
- Stack traces or HAR log segments
- Reference navigation (e.g. hyperlinks to other DMs)

---

## 📘 Example Output (Prism-like Render)

**Module:** `TIQ-99-01-MNT-0001`  
**Title:** Token Refresh and SignalR Reconnection Failure

> _Description:_ This data module documents a recurring midnight issue in the TIQ application where silent OAuth2 token refresh fails...

**Fault:**
```
Symptom: UI becomes unresponsive after token expires
Cause: Stale PKCE parameters reused in silent OAuth2 flow
```

**Remedy Steps:**
1. Reinitialize PKCE params for each token renewal
2. Guard HubConnection start/stop with locking
3. Log all token transitions and silent renews

📎 **Logs Available:** `console-token-loop.txt`  
🧭 **Navigation:** Click “Related Module” → `appendchild-null.xml`

---

## 📲 Tablet / Offline Rendering (Prism)
- All modules packaged into a single IETP dataset
- Can be loaded on iPad, Toughbook, or offline laptop
- Logs and images stored locally in `/resources`

---

## 💡 Takeaway
This simulation demonstrates how system behavior reports can be:
- Authored as structured XML
- Viewed interactively through modular manuals
- Linked, filtered, and reused within aerospace documentation systems like Prism

Ideal for maintenance engineers, QA analysts, and system support teams working across distributed platforms.

---

_Last updated: April 2025_

> ✈️ Created by Haily Stevens — Built for Boeing-aligned incident response documentation
