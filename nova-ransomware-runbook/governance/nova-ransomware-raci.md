# NOVA Ransomware – RACI Matrix

| Activity | SOC Analyst | SOC Lead | Incident Commander (IC) | IR/DFIR Lead | IT Ops | Identity Admin | Legal/Privacy | Comms/PR | Vendor Manager | Exec (CISO/CIO) |
|---|---|---|---|---|---|---|---|---|---|---|
| Declare SEV-1 & open incident | R | A | A | C | C | C | C | C | C | I |
| Initial triage & validation | R | A | C | C | C | C | I | I | I | I |
| Endpoint isolation / quarantine | R | A | C | C | A/R | C | I | I | I | I |
| Account disable / token revoke | C | C | C | C | I | A/R | I | I | I | I |
| IOC blocking (email/web/DNS/EDR) | R | A | C | C | C | C | I | I | I | I |
| Evidence preservation / chain of custody | R | A | C | A/R | C | C | C | I | I | I |
| Scope assessment (blast radius) | R | A | C | A/R | C | C | C | I | I | I |
| Third-party / vendor engagement | I | C | C | C | I | I | C | C | A/R | I |
| Regulatory/contract notification decision | I | I | C | C | I | I | A/R | C | C | A |
| Eradication (persistence removal, patching) | C | C | C | A/R | A/R | A/R | I | I | I | I |
| Recovery (restore, validation) | I | C | C | C | A/R | C | I | I | I | A |
| Executive updates / comms approval | I | C | A/R | C | I | I | A | A/R | I | A |
| Lessons learned / corrective actions | C | A | A/R | R | R | R | C | C | C | A |

Legend: **R**=Responsible, **A**=Accountable, **C**=Consulted, **I**=Informed
