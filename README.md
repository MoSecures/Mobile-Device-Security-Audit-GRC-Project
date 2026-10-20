# Mobile Device Security Audit

A GRC configuration audit of a Jamf Pro–managed iPad fleet, mapped to **CIS Controls v8** and **NIST SP 800-53 Rev. 5**.
Full project: https://docs.google.com/spreadsheets/d/17na1uH5IwxJz3vnNuST1ibnXnxB7mmF9/edit?usp=sharing&ouid=114244723909827319807&rtpof=true&sd=true

## Summary

A fleet of 500+ shared iPads had almost no security baseline. Users could sign in with personal Apple IDs and install any app, which gave sensitive data a direct path out of the managed environment.

I audited 132 MDM settings, mapped each one to CIS and NIST controls, rated the risks, and remediated them with a new Jamf Pro configuration profile.

### Results

| Metric | Before | After |
| --- | --- | --- |
| High-risk findings | 5 | **0** |
| Controls compliant | 72% | **91%** |
| Non-compliant settings | 35 | **2** |
| Findings fully remediated | n/a | **7 of 13** |

Of the remaining findings, 4 are formally accepted with compensating controls and 2 are tracked in a plan of action with an owner and target date.

---

## The Problem

Apart from Apple's default settings, only two controls had been deliberately configured: an app blocklist and an offline-lock policy.

- **Personal Apple IDs were allowed.** iMessage, Photos, iCloud and Keychain could sync to accounts the organization didn't control.
- **The App Store was unrestricted.** The blocklist only stopped known-bad apps.
- **There was no documented baseline** to audit against.

---

## What I Did

1. **Baseline capture:** documented all 132 pre-change settings.
2. **Framework mapping:** mapped each setting to a CIS safeguard and a NIST control.
3. **Gap analysis:** rated each setting Compliant, Conditional or Non-Compliant.
4. **Risk rating:** grouped the gaps into 13 findings and scored them Likelihood × Impact (5×5).
5. **Treatment:** remediated each finding, or documented the risk acceptance with a compensating control.
6. **Validation:** re-assessed the new profile and calculated residual risk.

### The two changes that mattered most

- **Blocked Apple ID sign-in.** This closed the iCloud and iMessage data paths (NIST AC-20, CIS 4.12).
- **Replaced the blocklist with an allowlist.** Apps now deploy only through Jamf (NIST CM-7(5), CIS 2.5).

---

## Key Findings

| ID | Finding | Risk (before → after) | Status |
| --- | --- | --- | --- |
| F-02 | Personal Apple ID and iCloud sync allowed | High → Low | Remediated |
| F-01 | App Store unrestricted | High → Low | Remediated |
| F-03 | Managed/unmanaged data not separated | High → Low | Remediated |
| F-04 | Unsupervised host pairing allowed | High → Low | Remediated |
| F-08 | Document flow not restricted | High → Medium | Risk accepted |
| F-11 | Untrusted TLS certificates accepted | Medium | Open |
| F-12 | Network drive access in Files app | Medium | Open |

All 13 findings are in the report and the workbook.

> **Analyst note:** Disabling the App Store removed third-party unmanaged apps, but Apple's built-in apps (Files, Notes, Mail) are still unmanaged destinations. That's why F-08 stays Medium instead of dropping to Low.

---

## Files

| File | What it is |
| --- | --- |
| `Mobile_Device_Security_Audit_Report.pdf` | 8-page audit report |
| `Mobile_Device_Security_Audit_v2.xlsx` | Working papers (5 tabs, listed below) |
| `assets/` | Images used in this README |

**Workbook tabs:**

- **Executive Summary:** key results and a before/after chart
- **Control Assessment:** all 132 settings, before vs. after, with CIS and NIST mapping
- **Risk Register:** 13 findings with risk scores, treatment and owner
- **POA&M:** plan of action for open and accepted items
- **Methodology:** scope, scoring matrix and definitions

---

## Skills Demonstrated

- Control assessment against a security baseline
- Framework mapping (CIS Controls v8, NIST SP 800-53 Rev. 5)
- Risk scoring, risk treatment and risk acceptance
- Audit findings (condition, criteria, cause, effect)
- POA&M and executive reporting
- Apple MDM and Jamf Pro configuration profiles

---

## Confidentiality

This project is based on a real audit I performed. The client name, device counts, configuration details, risk scores and identifiers have been changed or anonymized to protect the client.

---

## Contact

**Mohammad Aboosaiedi** (CompTIA Security+, Network+)

- Email: [mo@mosecures.com](mailto:mo@mosecures.com)
- LinkedIn: [linkedin.com/in/mohammadaboosaiedi](https://www.linkedin.com/in/mohammadaboosaiedi/)
- Instagram: [@mosecures](https://www.instagram.com/mosecures/)
- TikTok: [@mosecures](https://www.tiktok.com/@mosecures)
