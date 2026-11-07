# Phishing to Business Email Compromise (BEC) Investigation

> **Note:** This is a simulated case (BEC-001) built for portfolio purposes.
> All names, IPs, domains, and logs are fictional (`.example` domains and
> documentation IP ranges). It shows my investigation methodology, not a
> real client incident.

A simulated investigation of a suspicious payment request sent from an
executive mailbox, covering email analysis, authentication log review,
IOC analysis, timeline reconstruction, MITRE ATT&CK mapping, and
incident response.

## Summary
- **Scenario:** On 19 Sep 2026, a finance employee (p.shah) received an
  urgent "updated bank details" vendor payment request that appeared to come
  from the CFO (d.miller@northstar.example).
- **Assessment:** Potential Business Email Compromise through unauthorized
  access to the CFO mailbox. Status: investigated, findings preliminary.
- **Key point:** SPF, DKIM, and DMARC all passed, so email authentication
  alone could not clear the message. Correlating the originating IP
  (198.51.100.44) with sign-in and mailbox logs is what raises the concern.
- **Impact:** No financial loss established in this simulation.

## Repository Contents
| File / Folder | What it contains |
|---|---|
| `phishing-email.txt` | The suspicious payment request |
| `evidence/email-headers.txt` | Email headers and analyst notes |
| `Authentication-events` | Simulated sign-in and session events |
| `Mailbox_eventlogs` | Simulated mailbox audit events |
| `IOC_list` | Indicators of compromise (CSV format) |
| `investigation/` | Timeline and ATT&CK mapping |
| `report/` | Final incident investigation report |

## Timeline (19 Sep 2026, UTC)
| Time | Event |
|---|---|
| 09:51 | Successful sign-in to the CFO account from 198.51.100.44 (unusual IP) |
| 10:02 | New mailbox session from the same IP |
| 10:18 | Payment request with updated bank details sent to Finance |
| 10:21 | Inbox rule created: "bank" / "payment" messages moved to Archive |
| 10:24 | New mailbox forwarding configuration detected |
| 10:30 | Finance employee reports the request as suspicious |
| 10:35 | SOC investigation started |

Full detail: [investigation/incident_timeline.md](investigation/incident_timeline.md)

## Key Findings
1. SPF, DKIM, and DMARC passed, which fits misuse of a legitimate account
   rather than simple domain spoofing.
2. The same IP appears in the sign-in, mailbox session, sent email, rule
   creation, and forwarding change.
3. The inbox rule hides replies containing financial keywords, which could
   delay detection.
4. A forwarding configuration was added minutes after the rule.
5. The evidence does not show how the credentials were obtained.

## MITRE ATT&CK Mapping (Investigative Hypotheses)
| Technique | ID | Basis |
|---|---|---|
| Valid Accounts | T1078 | Successful sign-in followed by mailbox activity |
| Email Collection | T1114 | Forwarding configuration and keyword rule |

No phishing sub-technique is assigned because the evidence shows no
malicious link or attachment. Mappings are hypotheses, not confirmed
attacker behavior.

## Recommendations
1. Reset the CFO password and revoke all active sessions.
2. Remove the inbox rule and forwarding configuration.
3. Enforce MFA and block legacy authentication.
4. Add conditional access for unfamiliar IPs and locations.
5. Require call-back verification for any bank-detail change.
6. Search for other mail sent from 198.51.100.44.

## Full Report
See [`report/`](report/).

## Skills Demonstrated
Email header analysis, authentication log review, IOC analysis,
timeline reconstruction, ATT&CK mapping, incident documentation.
