# Investigation Timeline

## Case Information

**Case ID:** BEC-001  
**Incident Type:** Simulated Phishing / Business Email Compromise  
**Affected Account:** d.miller@northstar.example  
**Date:** 19 September 2026  
**Status:** Under Investigation

---

## Timeline

| Time (UTC) | Event | Source | Analyst Observation |
|---|---|---|---|
| 09:51 | Successful authentication | Authentication logs | Login from 198.51.100.44 |
| 10:02 | New mailbox session | Authentication logs | Session established from the same IP |
| 10:18 | Suspicious email sent | Email / mailbox logs | Payment request sent to Finance |
| 10:21 | Mailbox rule created | Mailbox logs | Messages containing "bank" or "payment" moved to Archive |
| 10:24 | Forwarding configuration detected | Mailbox logs | New mailbox forwarding configuration |
| 10:30 | Suspicious activity reported | Finance user | Payment request reported as suspicious |
| 10:35 | SOC investigation started | SOC record | Authentication and mailbox activity reviewed |

---

## Timeline Analysis

The investigation identified a sequence of related events involving the
executive mailbox.

A successful authentication from `198.51.100.44` occurred before the
suspicious payment-related email was sent.

Shortly afterward, a mailbox rule targeting financial keywords was
created, followed by a new forwarding configuration.

The close timing between these events requires investigation into
potential unauthorized access to the mailbox.

The evidence does not independently establish who controlled the
account or whether financial loss occurred.

---

## Key Correlations

### Authentication → Email Activity

The suspicious email was sent from the same account associated with
the earlier authentication from `198.51.100.44`.

### Email Activity → Mailbox Rule

A mailbox rule was created approximately three minutes after the
payment-related email was sent.

### Mailbox Rule → Forwarding

A forwarding configuration was detected approximately three minutes
after the mailbox rule was created.

### User Report → SOC Investigation

The finance employee reported the suspicious payment request at
10:30 UTC, triggering the SOC investigation.

---

## Initial Assessment

The timeline is consistent with a **potential Business Email Compromise
scenario** involving suspicious authentication and mailbox activity.

Further investigation should determine whether the account was
compromised and whether additional messages or mailbox activity were
affected.

> **Note:** All data in this timeline is simulated for cybersecurity
> education and portfolio purposes.
