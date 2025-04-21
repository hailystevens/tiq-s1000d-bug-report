# 🔐 Safe Reproduction Guide

_This guide outlines best practices for safely reproducing, investigating, and documenting production-like issues—especially in environments containing sensitive data or regulated information._

---

## 🚧 General Principles

- **Do Not Test in Live Production** unless explicitly authorized
- **Avoid exposing** personal, protected, or organizational data (PHI, PII, internal tokens)
- **Simulate user behavior** with mocked credentials or test accounts
- **Redact before share**: always scrub logs, screenshots, and metadata

---

## 🧪 Safe Debugging Steps

### 1. Use a Non-Production Clone or Feature Environment
- If available, spin up a UAT or staging instance that mimics production
- Mask all user-facing data with generated dummy records

### 2. Configure Safe Monitoring
- Enable **console logging** with filters (`token`, `signalr`, `negotiate`, `walkme`)
- Use browser DevTools → **Preserve logs**
- Add manual `setInterval()` log timestamps during critical windows (see `step-by-step-debugging.md`)

### 3. Token and Session Handling
- Use test identities wherever possible
- **Do not copy/paste real tokens** into documentation or GitHub
- Scrub `accessToken`, `idToken`, and anything in Local/Session Storage before saving logs

### 4. Network & Stack Logs
- Save HAR files with sensitive content excluded (filter out `Set-Cookie`, `Authorization` headers)
- Use annotated text-based stack traces instead of raw dumps
- Replace real URLs with placeholders (`https://example-uat.com`)

### 5. Screenshot Guidelines
- Blur or crop any EHR/patient/provider-facing UIs
- Label mockups as: `Simulated Screenshot – No PHI`
- Export with filename conventions like: `error-placeholder-sim.png`

### 6. Data Redaction Checklist
Before uploading or publishing any log, ask:
- [ ] Does this contain any real email, MRN, token, or provider info?
- [ ] Is the filename or timestamp traceable to real-world records?
- [ ] Could this violate HIPAA, FERPA, or an NDA?

If yes → redact or exclude entirely.

---

## 📦 Sample Directory Conventions
```
/logs/                       # Redacted or simulated only
/screenshots/               # Mock UI or blurred
/data-modules/              # Generic structured documentation
/docs/                      # Markdown how-tos and safe workflows
```

---

## ✅ Summary
Safely reproducing incidents is about more than just replication—it's about **respecting boundaries**, **protecting privacy**, and building a **repeatable, secure process** for technical analysis. Treat every log like a flight recorder: valuable, sensitive, and critical to handle with care.

---

_Last reviewed: April 2025 — Maintained by Haily Stevens_
