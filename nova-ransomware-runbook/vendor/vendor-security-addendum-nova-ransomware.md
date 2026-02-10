# Vendor Security Addendum Clause – Ransomware & Security Incident Response (NOVA)

**1) Definitions.**  
“Security Incident” means any actual or reasonably suspected unauthorized access to, acquisition of, disclosure of, alteration of, loss of control of, or unavailability of Systems or Customer Data, including ransomware/extortion events. “Customer Data” includes any data processed or stored on behalf of Customer.

**2) Minimum Security Controls.**  
Vendor shall maintain an information security program aligned to ISO 27001 and/or NIST-based controls and consistent with SOC 2 Security principles, including at minimum:
- MFA for privileged access; least privilege; strong authentication controls
- Centralized logging and monitoring for security-relevant events
- Malware/ransomware protections (EDR/AV) and secure configuration baselines
- Vulnerability management with risk-based patching
- Backups with logical separation and protection from modification/deletion (e.g., immutability or equivalent safeguards)
- Encryption in transit and at rest for Customer Data (where applicable)

**3) Incident Notification (Time-Critical).**  
Vendor shall notify Customer **without undue delay and in any event within 24 hours** of discovery of a Security Incident that affects (or is reasonably likely to affect) Customer Data or Customer’s environment. Notice must include:
- Incident summary, suspected root cause/initial access vector (if known)
- Systems/data impacted, timeframe, indicators of compromise (IOCs) and containment steps
- Whether ransomware encryption and/or extortion occurred and whether exfiltration is suspected
- Mitigation actions taken and planned next steps  
Vendor will provide updates at least every **24 hours** during active incident response (or more frequently if materially significant developments occur).

**4) Cooperation & Evidence Preservation.**  
Vendor shall promptly cooperate with Customer, Customer’s designated DFIR, legal counsel, regulators, and auditors as applicable, including:
- Preserving relevant logs and evidence and maintaining chain-of-custody
- Providing reasonable access to incident artifacts (IOCs, timelines, log extracts)
- Supporting containment actions (account/session revocation, access restriction, network blocks)

**5) No Ransom Payment Without Consent.**  
Vendor shall not pay (or commit to pay) any ransom/extortion demand relating to a Security Incident involving Customer Data or systems used to provide services to Customer **without Customer’s prior written consent**, unless prohibited by law or required for immediate safety; in such case Vendor must notify Customer as soon as legally permissible.

**6) Subprocessors / Downstream Flow-Down.**  
Vendor shall ensure all subprocessors who may access Customer Data are bound by written terms no less protective than this Addendum, including the same notification timelines and cooperation obligations.

**7) Remediation, Reporting, and Corrective Actions.**  
Within **10 business days** after containment, Vendor shall provide a written incident report including:
- Root cause analysis, scope, impact assessment (including exfiltration determination methodology)
- Remediation actions, security control improvements, and timelines
- Measures to prevent recurrence  
Vendor shall complete corrective actions within agreed timeframes and provide evidence upon request.

**8) Audit & Assurance.**  
Upon request, Vendor shall provide current SOC 2 report and/or ISO 27001 certificate (or equivalent independent assessment summary). Customer may request reasonable security questionnaires and, for material incidents, a targeted review of remediation evidence.

**9) Liability & Costs (optional commercial language).**  
For Security Incidents attributable to Vendor’s failure to meet the obligations herein, Vendor shall bear reasonable costs associated with incident response assistance, notifications required by law, and credit monitoring where mandated, subject to the parties’ master agreement and applicable law.

**10) Survival.**  
These obligations survive termination for as long as Vendor retains Customer Data or access to Customer Systems.
