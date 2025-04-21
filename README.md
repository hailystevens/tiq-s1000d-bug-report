# 🛠️ S1000D Bug Report

This project demonstrates how real-world bug reports can be converted into modular, structured S1000D technical documentation using XML. Inspired by support issues encountered while working in a clinical systems support role, these simulated Data Modules (DMs) showcase how structured content can enhance clarity, traceability, and maintainability across technical teams.

---

## 📚 Project Goals

- Simulate the structure and flow of Boeing’s S1000D-based technical publications  
- Convert live production bug reports into reusable XML Data Modules  
- Practice CSDB-like organization using GitHub as a lightweight platform  
- Demonstrate a strong understanding of technical documentation lifecycles and support workflows

---

## 📦 Project Structure

```
boeing-s1000d-bug-report/
├── /data-modules/       # XML data modules in S1000D style
├── /screenshots/        # Annotated HAR logs, console errors, and bug evidence
├── /docs/               # Project explanation and simulated viewer logic
├── README.md            # You're here
└── LICENSE              # Optional
```

---

## 🔧 Tools Used

- GitHub for version control and modular storage (mimicking CSDB structure)  
- Custom XML Data Module templates (S1000D-like structure)  
- VS Code + XML Linter for authoring and validation  
- Local static server for simulating IETM viewer compatibility  
- [Issue 6 Errata Reference](https://www.s1000d.org/) for real browser/test environment behaviors

---

## 📁 Sample Data Modules

| File                        | Description                                                                 |
|----------------------------|-----------------------------------------------------------------------------|
| `tiq-token-refresh.xml`     | Describes a midnight OAuth2 token failure and SignalR race condition        |
| `tiq-moment-deprecation.xml`| Logs unrecognized date formats and breaks in date parsing                   |
| `tiq-ui-hang.xml`           | Details a broken interface flow post-refresh requiring manual reload        |

Each file contains:
- A structured XML layout  
- Fault isolation and symptom description  
- Root cause analysis and remedy steps  
- Optional reference to logs/screenshots in `/screenshots/`

---

## 🧠 Why S1000D?

The S1000D XML standard is widely used in aerospace and defense for technical publications. By reformatting support tickets and system incidents into Data Modules, we:
- Improve modularity and reusability  
- Enhance future integration with CSDB and IETP workflows  
- Build technical documentation that aligns with Boeing’s real-world tooling:  
  `S1000Dmanager`, `authorPro XE`, `publisher`, and `prism viewer`

---

## 🔗 Connect

Created by [Haily Stevens](https://github.com/hailystevens) — Clinical Systems Support + aspiring Systems Analyst at Boeing ✈️  
This repo is part of an ongoing technical documentation and tooling development portfolio.

---

> ⚠️ All files in this project have been scrubbed of any protected health information (PHI), sensitive identifiers, and proprietary code. Logs, screenshots, and content are simulated, redacted, or recreated for educational and demonstration purposes only.
