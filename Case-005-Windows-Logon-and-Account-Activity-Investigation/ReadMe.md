Case 005 – Windows Logon & Account Activity Investigation
Executive Summary

This investigation was conducted to analyze Windows authentication artifacts and determine whether user accounts successfully authenticated to a Windows workstation, whether failed logon attempts occurred, and whether any user account management activity was present.

Using Windows Security Event Logs and PowerShell, authentication events were examined to identify successful and failed logons, determine logon types, enumerate local user accounts, and investigate account management activity. A timeline was reconstructed using the collected evidence to establish the sequence of authentication events.

The investigation confirmed a successful interactive logon by the local user account Cierra Emerson, identified a failed authentication attempt immediately preceding the successful login, and found no evidence of account creation, modification, or deletion during the investigation period.

Investigation Objectives

The objectives of this investigation were to:

Analyze Windows Security Event Logs
Identify successful and failed authentication attempts
Determine Windows logon types
Enumerate local user accounts
Investigate account management events
Reconstruct an authentication timeline
Determine whether evidence supported suspicious account activity
Scenario

An organization suspected that an unauthorized user attempted to access a Windows workstation outside of normal operating procedures.

The investigator was tasked with determining:

Which user successfully logged into the workstation
Whether failed authentication attempts occurred
Whether user accounts had been created, modified, or deleted
Whether authentication artifacts indicated suspicious activity
Tools Used
Windows Event Viewer
Windows Security Event Logs
Windows PowerShell
Get-LocalUser
Windows 11
Evidence Collected
Security Event ID 4624 – Successful Logon

Analysis of Security Event ID 4624 identified a successful interactive logon using the local account:

Account Name

Cierra Emerson

Account Domain

CIERRA-EMERSON

Logon Type

2 (Interactive)

Process

C:\Windows\System32\svchost.exe

The event confirmed that the user successfully authenticated locally at the workstation.

Security Event ID 4625 – Failed Logon

Security Event ID 4625 documented a failed authentication attempt immediately before the successful logon.

The event confirmed that an incorrect password was entered before successful authentication.

Logon Type Analysis

The successful authentication event recorded Logon Type 2.

Logon Type 2 represents an Interactive Logon, indicating that a user authenticated directly at the keyboard of the workstation rather than through a network or service account.

Local User Enumeration

PowerShell enumeration identified the following local user accounts:

Account	Status
Administrator	Enabled
Cierra	Enabled
Cierra Emerson	Enabled
DefaultAccount	Disabled
Guest	Disabled
WDAGUtilityAccount	Disabled

The successful authentication event corresponded to the Cierra Emerson account.

Account Management Investigation

Windows Security Event Logs were examined for the following account management events:

Event ID	Description
4720	User Account Created
4722	User Account Enabled
4723	Password Changed
4724	Password Reset
4725	User Account Disabled
4726	User Account Deleted
4738	User Account Modified

No matching events were identified.

Based on the available evidence, no user account creation, modification, deletion, or administrative account changes occurred during the investigation period.

Authentication Timeline
Time	Artifact	Finding
6:42:05 PM	Event ID 4625	Failed logon attempt recorded
6:42:08 PM	Event ID 4624	Successful interactive logon (Type 2) by Cierra Emerson
Investigation	PowerShell	Local user accounts verified
Investigation	Event IDs 4720–4738	No account management activity identified
Investigation Findings

The investigation determined:

A successful interactive Windows logon occurred using the local account Cierra Emerson.
A failed authentication attempt immediately preceded the successful login.
Authentication originated locally from the workstation.
Multiple local user accounts were present, with three enabled accounts identified.
No evidence of account creation, modification, password reset, account deletion, or account enable/disable activity was identified.
Authentication artifacts indicate normal user activity rather than evidence of unauthorized account manipulation.
Conclusion

Analysis of Windows authentication artifacts successfully reconstructed user logon activity on the workstation.

Security Event ID 4624 confirmed successful interactive authentication by the Cierra Emerson account, while Event ID 4625 documented a failed login attempt immediately beforehand. Enumeration of local user accounts verified the account involved in the authentication events, and review of account management event IDs found no evidence of administrative account changes during the investigation period.

Based on the available evidence, the workstation exhibited expected authentication behavior with no indication of unauthorized account creation or modification.

Evidence Screenshots
Screenshots/

├── Successful-Logon-4624.png
├── Failed-Logon-4625.png
├── Interactive-Logon-Type-2.png
├── Local-User-Accounts.png
├── Account-Management-Events.png
└── Timeline.png
Skills Demonstrated
Windows Security Event Log Analysis
Authentication Forensics
Windows Logon Type Identification
Local Account Enumeration
Windows PowerShell
Timeline Reconstruction
Digital Evidence Documentation
Incident Investigation Methodology
Lessons Learned

This investigation demonstrated how Windows Security Event Logs can be used to reconstruct authentication activity and distinguish between successful and failed logon attempts. It reinforced the importance of interpreting Windows logon types to differentiate interactive user sessions from background service activity.

The investigation also highlighted that the absence of account management events is itself a meaningful forensic finding, indicating that no user account creation, modification, or deletion occurred during the investigation period. Correlating authentication events with local account enumeration provided a comprehensive view of user access to the workstation and strengthened the overall evidentiary findings.
