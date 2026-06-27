![Repository Banner](./images/project-banner.png)

# Case 005 – Windows Logon & Account Activity Investigation

## Executive Summary

This investigation was conducted to analyze Windows authentication artifacts and determine whether successful and failed user logons occurred on a Windows workstation, whether local user accounts were examined, and whether account management activity occurred during the investigation period.

Using native Windows Security Event Logs, PowerShell, and Windows authentication artifacts, evidence was collected and analyzed to reconstruct user logon activity. The investigation identified successful and failed authentication events, examined Windows logon types, enumerated local user accounts, and established a timeline of authentication activity.

The investigation confirmed that a failed authentication attempt was immediately followed by a successful interactive user logon and that no account creation, modification, or deletion events occurred during the investigation period.

---

## Investigation Objectives

The objectives of this investigation were to:

* Analyze Windows Security authentication events
* Identify successful and failed logon attempts
* Examine Windows logon types
* Enumerate local user accounts
* Investigate account management activity
* Reconstruct an authentication timeline
* Determine whether evidence supports normal or suspicious authentication activity

---

## Scenario

An organization suspected that an unauthorized user attempted to access a Windows workstation outside of normal operating procedures.

The investigator was tasked with determining:

* Which account successfully authenticated
* Whether failed authentication attempts occurred
* Whether local user accounts had been modified
* Whether Windows authentication artifacts documented user activity
* Whether a timeline of authentication activity could be reconstructed

---

## Evidence Collected

### Authentication Artifacts

* Windows Security Event ID 4624 (Successful Logon)
* Windows Security Event ID 4625 (Failed Logon)
* Windows Logon Type Information

### System Artifacts

* Windows Security Event Logs
* Local User Accounts
* Account Management Event IDs
* PowerShell Enumeration

### Forensic Tools

* Windows Event Viewer
* Windows PowerShell
* Get-LocalUser

---

## Analysis

### Successful Logon Analysis

Windows Security Event ID 4624 was examined to identify successful authentication events.

Observed artifacts included:

* Account Name: Jane Doe
* Account Domain: JANE-DOE
* Logon Type: 2 (Interactive)
* Source Address: 127.0.0.1
* Authentication Process: svchost.exe

The authentication event confirms that the user successfully logged into the workstation using an interactive Windows logon.

---

### Failed Logon Analysis

Windows Security Event ID 4625 recorded a failed authentication attempt immediately before the successful logon.

Evidence included:

* Failed password attempt
* Failed authentication event
* Successful authentication immediately afterward

The sequence of events demonstrates that an unsuccessful authentication attempt was followed by a successful interactive user logon.

---

### Local User Analysis

PowerShell was used to enumerate local user accounts.

| Account            | Status   |
| ------------------ | -------- |
| Administrator      | Enabled  |
| Jane               | Enabled  |
| Jane Doe           | Enabled  |
| DefaultAccount     | Disabled |
| Guest              | Disabled |
| WDAGUtilityAccount | Disabled |

The enumeration confirmed the presence of the local user account identified during authentication analysis.

---

### Account Management Analysis

Windows Security Event Logs were examined for account management activity.

The following Event IDs were reviewed:

| Event ID | Description           |
| -------- | --------------------- |
| 4720     | User Account Created  |
| 4722     | User Account Enabled  |
| 4723     | Password Changed      |
| 4724     | Password Reset        |
| 4725     | User Account Disabled |
| 4726     | User Account Deleted  |
| 4738     | User Account Modified |

No account management events were identified during the investigation.

The absence of these events indicates that no user account creation, modification, password changes, or account deletion occurred during the examination period.

---

## Timeline Reconstruction

| Time          | Event                                                 |
| ------------- | ----------------------------------------------------- |
| 06:42:05 PM   | Failed authentication recorded (Event ID 4625)        |
| 06:42:08 PM   | Successful interactive logon recorded (Event ID 4624) |
| Investigation | Local user accounts enumerated                        |
| Investigation | Account management events reviewed (none identified)  |

The timeline demonstrates a clear progression of authentication activity from a failed logon attempt to a successful interactive user authentication.

---

## Findings

### Finding 1

A failed authentication attempt occurred immediately before a successful user logon.

**Evidence:**

* Windows Security Event IDs 4625 and 4624

---

### Finding 2

Windows Security Event Logs successfully documented interactive user authentication.

**Evidence:**

* Event ID 4624
* Logon Type 2

---

### Finding 3

PowerShell enumeration confirmed the presence of the authenticated local user account.

**Evidence:**

* Get-LocalUser

---

### Finding 4

No account creation, password modification, account deletion, or other account management activity was identified.

**Evidence:**

* Windows Security Event IDs 4720–4738

---

### Finding 5

Windows authentication artifacts established the sequence of authentication events during the investigation.

**Evidence:**

* Windows Security Event Logs
* Timeline Reconstruction

---

## Conclusion

The investigation confirmed that Windows authentication artifacts successfully documented user logon activity during the examination period.

Analysis of Windows Security Event Logs, authentication metadata, and PowerShell account enumeration demonstrated that authentication activity can be reconstructed through multiple independent forensic artifacts. Additionally, no evidence of account management activity was identified, indicating that no local user accounts were created, modified, or deleted during the investigation.

Based on the available evidence, the findings support the conclusion that Windows authentication artifacts provide valuable insight into successful logons, failed authentication attempts, and overall account activity on a Windows workstation.

---

## Lessons Learned

* Windows Security Event Logs provide valuable evidence of user authentication activity.
* Event IDs 4624 and 4625 are essential for reconstructing successful and failed logons.
* Windows Logon Types distinguish interactive user activity from background system authentication.
* PowerShell provides an efficient method for enumerating local user accounts.
* The absence of account management events is itself a meaningful forensic finding.
* Correlating multiple Windows authentication artifacts strengthens forensic conclusions.
* Proper documentation improves the integrity and repeatability of investigations.

---

## Skills Demonstrated

* Digital Forensics
* Windows Authentication Analysis
* Windows Security Event Log Analysis
* Logon Investigation
* Local User Enumeration
* PowerShell Analysis
* Timeline Reconstruction
* Evidence Documentation
* Windows Forensics
* Incident Investigation
