# NOVA Ransomware Runbook – Control Mapping (ISO 27001 / NIST / SOC 2)

## ISO/IEC 27001:2022 (Annex A) – relevant mappings (high-level)
- **A.5.24 / A.5.25 / A.5.26** Incident management planning, assessment/decision, response
- **A.5.28** Collection of evidence (chain of custody, integrity)
- **A.5.30** ICT readiness for business continuity (restore testing, resilience)
- **A.8.7 / A.8.8 / A.8.9** Malware protection, technical vulnerability mgmt, configuration mgmt
- **A.8.15 / A.8.16** Logging, monitoring
- **A.8.23** Web filtering / network controls for IOC blocking
- **A.5.19 / A.5.20 / A.5.21 / A.5.22** Supplier relationships + security in agreements + monitoring

## NIST (CSF 2.0 high-level + 800-53 rev5 examples)
**Identify**
- Asset inventory / critical services mapping (CM, PM)

**Protect**
- Access control / MFA / least privilege (AC-2, AC-6, IA-2)
- Backup protections / immutability (CP-9, CP-10)
- Email/web protections (SC-7, SI-3)

**Detect**
- Centralized logging & monitoring (AU-2, AU-6, SI-4)
- Threat hunting (SI-4, IR-5)

**Respond**
- Incident response plan/execution (IR-1, IR-4, IR-6)
- Evidence handling (IR-4, AU, chain of custody procedures)

**Recover**
- Recovery planning + restore validation (CP-2, CP-4, CP-10)

## SOC 2 (Trust Services Criteria) – typical alignments
- **Security (Common Criteria):**
  - CC6 (Logical access), CC7 (System operations/monitoring), CC8 (Change mgmt), CC9 (Risk mitigation)
- **Availability (if in scope):**
  - A1 (availability commitments, resilience, backup/restore, DR testing)
- **Confidentiality/Privacy (if in scope):**
  - Data exfil assessment, breach evaluation, notification governance

## Runbook Step → Control linkage (quick crosswalk)
- **Declare SEV-1 / start bridge / assign IC** → ISO A.5.24–A.5.26; NIST IR-4; SOC2 CC7
- **Isolate hosts / disable accounts / revoke tokens** → ISO A.8.7, A.8.16; NIST AC/IA/SI; SOC2 CC6/CC7
- **IOC blocking** → ISO A.8.23, A.8.16; NIST SC-7/SI-4; SOC2 CC7
- **Evidence & chain of custody** → ISO A.5.28; NIST IR/AU; SOC2 CC7 (auditability)
- **Eradication + patching + secret rotation** → ISO A.8.8/A.8.9; NIST SI/CM/AC; SOC2 CC8/CC9
- **Restore from immutable backups + validate** → ISO A.5.30; NIST CP; SOC2 Availability + CC7
- **Notification decisions** → ISO A.5.24–A.5.26; NIST IR-6; SOC2 governance criteria
