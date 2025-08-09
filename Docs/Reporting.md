## 📝 Recon Reporting — From Scan Data to Strategic Insight

Every module in the Recon Suite produces structured output. But raw data isn’t enough. That’s why **Recon generates two distinct report types** designed to communicate clearly across roles.

---

## 📣 1. Non-Technical Risk Brief — For Stakeholders & Compliance Teams

A clear, jargon-free overview of what was found, why it matters, and what obligations may be triggered.

### Includes:
- 📌 **Issue summaries**: Each finding explained in simple terms (e.g., "An outdated login page may allow unauthorized access.")
- 🛡️ **Risk levels**: Severity ranked in accessible language (Low / Moderate / High)
- 📜 **Regulatory notes**: GDPR implications or NIS2 considerations (e.g., unencrypted PII transit)
- 🔁 **Business impact**: How this could affect operations, reputation, or legal standing

This isn’t about fear—it’s about clarity and actionable awareness.

---

## 🧪 2. Technical Recon Report — For Engineers & Remediation Teams

A structured, actionable document detailing vulnerabilities and the precise steps required to mitigate.

### Includes:
- 🔍 **Finding metadata**: Port, protocol, host, timestamp, hash reference
- 🧭 **Technical description**: CVE IDs, fingerprint data, payload results
- 🛠 **Mitigation guidance**: Patch instructions, config recommendations, firewall rules
- 📊 **Exploitability index**: Likelihood + potential impact
- 🧾 **Audit logs**: All actions timestamped and hash-indexed

It’s not just a technical dump—it’s **a remediation plan in markdown**.

---

## 🧩 Supporting Files

- `report-nontech-[session].md`
- `report-tech-[session].md`
- `.hashmap` → links findings to log entries for traceability
- `/samples/` → sanitized demo reports for public education or onboarding
