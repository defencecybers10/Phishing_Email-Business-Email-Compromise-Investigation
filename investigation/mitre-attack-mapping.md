# MITRE ATT&CK Mapping

## Case Information

**Case ID:** BEC-001  
**Incident Type:** Simulated Phishing / Business Email Compromise

---

## Technique Mapping

| Technique | ID | Evidence | Assessment |
|---|---|---|---|
| Valid Accounts | T1078 | Successful authentication to d.miller@northstar.example followed by mailbox activity | Potentially applicable |
| Email Collection | T1114 | Suspicious mailbox rule and forwarding configuration were observed | Potentially applicable |

---

## 1. Valid Accounts — T1078

### Evidence

A successful authentication to:

`d.miller@northstar.example`

was recorded from:

`198.51.100.44`

The same source IP was subsequently associated with mailbox activity.

### Assessment

This activity is consistent with the use of a valid account.

However, the available simulated evidence does not establish how
the credentials were obtained or who performed the authentication.

---

## 2. Email Collection — T1114

### Evidence

A mailbox rule was created to move messages containing:

- "bank"
- "payment"

to the Archive folder.

A mailbox forwarding configuration was also detected shortly afterward.

### Assessment

These mailbox changes may support investigation of potential email
collection or monitoring activity.

The simulation does not provide sufficient evidence to confirm that
messages were actually collected or exfiltrated.

---

## Techniques Not Mapped

The phishing email itself is documented in this investigation, but
the available evidence does not establish a specific phishing
sub-technique such as a malicious attachment or phishing link.

Therefore, no more specific phishing technique is assigned at this
stage.

---

## Mapping Conclusion

The investigation provides evidence that is potentially consistent
with:

- **T1078 — Valid Accounts**
- **T1114 — Email Collection**

These mappings are investigative hypotheses based on the simulated
evidence and should not be treated as confirmed attacker techniques
without additional evidence.

