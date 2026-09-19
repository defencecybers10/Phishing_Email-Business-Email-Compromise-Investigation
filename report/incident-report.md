# Incident Investigation Report

## Case Information

| Field | Details |
|---|---|
| Case ID | BEC-001 |
| Incident Type | Phishing / Business Email Compromise |
| Severity | Medium |
| Status | Investigated |
| Date | 19 September 2026 |
| Affected Account | d.miller@northstar.example |
| Organization | Northstar Technologies |
| Environment | Simulated Microsoft 365 environment |

---

## 1. Executive Summary

A simulated phishing email was reported by a finance employee after receiving an urgent request to process a vendor payment using updated banking information.

The message appeared to originate from the company's CFO, d.miller@northstar.example.

During the investigation, suspicious authentication and mailbox activity was identified.

A successful authentication from `198.51.100.44` was followed by:

- A new mailbox session
- A payment-related email
- Creation of a suspicious mailbox rule
- Detection of a new mailbox forwarding configuration

The available evidence is consistent with a potential Business Email Compromise scenario.

No actual financial loss is established in this simulation.

---

## 2. Initial Alert

The investigation began when the finance employee reported a suspicious payment request.

The request contained several characteristics requiring validation:

- Urgent payment request
- Updated vendor banking information
- Request for immediate action
- Message appearing to originate from an executive account

---

## 3. Evidence Reviewed

The following simulated evidence was reviewed:

### Email Evidence

- Simulated phishing email
- Email headers
- Sender and recipient information
- Authentication results
- Originating IP address

### Authentication Evidence

- Successful authentication
- Source IP address
- Mailbox session activity

### Mailbox Evidence

- Email-sending activity
- Mailbox rule creation
- Forwarding configuration change

---

## 4. Key Indicators of Compromise

| IOC | Type | Relevance |
|---|---|---|
| d.miller@northstar.example | Email account | Account associated with suspicious activity |
| 198.51.100.44 | IP address | Source of authentication and mailbox activity |
| BEC-001-20260919@northstar.example | Message ID | Identifier for suspicious email |
| "bank" / "payment" archive rule | Mailbox rule | Suspicious mailbox configuration |
| New forwarding configuration | Mailbox activity | Potential unauthorized configuration |

---

## 5. Investigation Findings

### Finding 1 — Suspicious Authentication

A successful authentication to the executive account occurred from `198.51.100.44`.

The same IP address was associated with subsequent mailbox activity.

### Finding 2 — Suspicious Payment Request

A payment-related email was sent shortly after the authentication event.

The email requested that Finance process a vendor payment using updated banking information.

### Finding 3 — Suspicious Mailbox Rule

Approximately three minutes after the email was sent, a mailbox rule was created to move messages containing financial keywords such as "bank" or "payment" to the Archive folder.

This activity requires investigation because mailbox rules can affect the visibility and handling of messages.

### Finding 4 — Forwarding Configuration

A new mailbox forwarding configuration was detected approximately three minutes after the mailbox rule was created.

The available evidence does not establish the destination or confirm that data was actually forwarded.

---

## 6. Timeline Summary

| Time (UTC) | Event |
|---|---|
| 09:51 | Successful authentication |
| 10:02 | New mailbox session |
| 10:18 | Suspicious payment email sent |
| 10:21 | Suspicious mailbox rule created |
| 10:24 | Forwarding configuration detected |
| 10:30 | Finance reports suspicious request |
| 10:35 | SOC investigation begins |

---

## 7. MITRE ATT&CK Mapping

The investigation identified activity potentially relevant to:

- T1078 — Valid Accounts
- T1114 — Email Collection

These mappings represent investigative hypotheses based on the simulated evidence.

The evidence does not establish how credentials were obtained or confirm that email data was actually collected or exfiltrated.

---

## 8. Recommended Incident Response Actions

### Containment

- Restrict or temporarily disable the affected account
- Revoke active sessions
- Remove unauthorized mailbox rules
- Remove unauthorized forwarding configurations

### Credential Security

- Reset the affected user's credentials
- Verify MFA configuration
- Review recent authentication activity
- Investigate suspicious sign-ins and devices

### Email Investigation

- Search for related messages
- Identify other recipients of similar payment requests
- Review mailbox activity for additional suspicious changes
- Investigate related accounts and messages

### Business Verification

- Independently verify vendor banking changes
- Contact the vendor using a trusted communication channel
- Do not rely solely on payment instructions received through email

### Post-Incident

- Preserve relevant logs and evidence
- Document investigation findings
- Review email security controls
- Continue monitoring the affected account

---

## 9. Root Cause Assessment

Based on the simulated evidence, potential unauthorized access to the executive mailbox may have preceded the suspicious payment request.

However, the available evidence does not establish the exact method of compromise.

Additional evidence such as detailed identity-provider logs, device information, MFA events, mailbox audit records, and related email activity would be required for a definitive root cause.

---

## 10. Final Assessment

**Potential Business Email Compromise (BEC)**

The simulated investigation identified a suspicious sequence involving authentication activity, a financial payment request, mailbox rule creation, and forwarding configuration changes.

The evidence supports further investigation and incident response actions but does not establish actual financial loss or definitively identify the person responsible.

---
