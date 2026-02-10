# SOC One-Page Runbook: NOVA Ransomware

**Purpose:** Rapidly contain, eradicate, and recover from suspected/confirmed NOVA ransomware while preserving evidence and meeting notification obligations.  
**Scope:** Endpoints, servers, M365/Google Workspace identities, email, collaboration apps, cloud storage, and third parties.  
**Severity:** Treat as **SEV-1** on suspicion of encryption + extortion indicators or confirmed IOC matches.

## 0) Trigger Criteria (any = activate incident)
- Ransom note, mass file encryption/renames, unusual file extensions, shadow copy deletion attempts
- Unusual privileged sign-ins, MFA fatigue, impossible travel, token replay, OAuth app abuse
- EDR alerting for ransomware behaviors, suspicious scheduled tasks, PSExec/WMI lateral movement
- Spike in file modifications/deletions in SharePoint/OneDrive/Drive; abnormal outbound traffic to known C2

## 1) Immediate Actions (first 15 minutes)
1. **Declare SEV-1** and start incident bridge + ticket; assign Incident Commander (IC).
2. **Preserve evidence:** do *not* power off unless encryption is actively spreading and isolation fails.
3. **Contain spread (priority order):**
   - Isolate affected hosts in EDR (network containment) or quarantine via NAC/VLAN.
   - Disable suspected compromised accounts; revoke sessions/tokens.
   - Block IOCs (domains/IPs/hashes) on email/web proxy/DNS/EDR.
4. **Protect backups:** verify backup immutability; restrict backup admin access; pause risky replication jobs if needed.
5. **Executive + Legal notification:** alert CISO/Legal/Privacy; initiate comms hold (“single source of truth”).

## 2) Containment Playbook (choose M365 or Google Workspace paths)

### A) Microsoft 365 / Entra ID / Defender
- **Identity**
  - Disable user(s), reset passwords; require MFA re-registration for impacted accounts.
  - Revoke refresh tokens / sign-out everywhere; block risky sign-ins (Conditional Access).
  - Review and remove suspicious **OAuth consented apps**, enterprise apps, app registrations, and mail forwarding rules.
- **Email / Collaboration**
  - Purge malicious emails (Defender for Office); block sender/domain; check transport rules.
  - Inspect SharePoint/OneDrive for mass changes; restrict sharing; enable “file restore” readiness.
- **Endpoint / Server**
  - In Microsoft Defender for Endpoint: isolate device; collect investigation package; run AV scan; hunt for persistence.
  - Hunt: unusual scheduled tasks, services, registry run keys, PS scripts, encoded commands, lateral movement tools.
- **Logging**
  - Ensure Unified Audit Log, Entra sign-in logs, MDE telemetry, and mailbox audits are retained/locked.

### B) Google Workspace / BeyondCorp / Endpoint Mgmt
- **Identity**
  - Suspend user(s); reset passwords; **invalidate sessions**; enforce 2SV re-enrollment if compromise suspected.
  - Review **OAuth app access**, domain-wide delegation, and API clients; remove suspicious grants.
- **Email / Collaboration**
  - Use Gmail Security Investigation Tool (or equivalent): identify/purge malicious messages; block senders/domains.
  - Review Drive for mass encryption/modification; restrict sharing; prepare Drive restore if available.
- **Endpoints**
  - Quarantine via endpoint management/EDR; collect forensics package; hunt persistence/lateral movement.
- **Logging**
  - Preserve Admin audit, login audit, Drive audit, Gmail audit; export to SIEM with retention controls.

## 3) Investigation Checklist (first 1–4 hours)
- Establish **patient zero**: phishing? exposed RDP/VPN? stolen creds? vulnerability exploitation?
- Determine **blast radius**: endpoints, servers, cloud apps, storage locations, privileged accounts.
- Confirm **data exfiltration** indicators: large outbound transfers, unusual cloud downloads, new API tokens, rclone usage.
- Capture artifacts: ransom note, file extensions, processes, command lines, scheduled tasks, registry keys, network connections.
- Identify **encryption timeline** and **initial access vector** to prevent reinfection.

## 4) Eradication
- Remove persistence (tasks/services/startup items), malicious tooling, unauthorized admin accounts, rogue OAuth apps.
- Patch exploited vulnerabilities; rotate secrets (VPN keys, API keys, service accounts).
- Reimage/rebuild impacted systems where integrity is uncertain.
- Validate clean state with EDR + threat hunting before reconnecting.

## 5) Recovery
- Restore from **known-good, immutable backups**; prioritize domain controllers/identity, core apps, file services.
- For M365: consider **OneDrive/SharePoint file restore**; validate permissions/sharing post-restore.
- For Google: use available restore mechanisms (Drive/Workspace backups, Vault exports as needed).
- Increase monitoring: heightened alerting for 14–30 days; watch for re-compromise.

## 6) Communications + Notifications (coordinate with Legal/Privacy)
- Follow your incident comms plan; avoid speculation; preserve privilege where applicable.
- Assess regulatory/customer notification triggers (jurisdiction + contracts).
- If third parties involved, trigger vendor IR requirements (see vendor addendum clause in repo).

## 7) Evidence Handling
- Maintain chain of custody for disk/memory images, logs, exports, and tickets.
- Store artifacts in restricted IR repository; document every action with timestamps.

## 8) Exit Criteria
- No active encryption, no persistence, IOCs blocked, root cause mitigated, restores validated.
- Executive sign-off; post-incident review scheduled within 5 business days.

**Key Roles:** Incident Commander (IC), SOC Lead, IR Lead, IT Ops Lead, Identity Admin, Legal/Privacy, Comms/PR, Vendor Manager.  
**Escalation:** If widespread encryption or confirmed exfiltration → engage external DFIR + cyber insurer immediately (per policy).
