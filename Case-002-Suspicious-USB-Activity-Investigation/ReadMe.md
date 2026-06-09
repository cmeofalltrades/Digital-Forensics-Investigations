![Repository Banner](./images/project-banner.png)
# Case 002 - Suspicious USB Activity Investigation

## Overview

This investigation examines potential unauthorized use of removable media on a Windows workstation.

The objective was to determine whether a USB storage device was connected to the system, identify the device involved, and analyze evidence indicating whether sensitive files were copied to external media.

This investigation utilized native Windows forensic artifacts and Autopsy to perform timeline analysis, metadata examination, and file correlation.

---

## Investigation Objectives

- Identify connected USB devices
- Review Windows event logs for USB activity
- Analyze file metadata
- Compare original files and copied files
- Verify file integrity using cryptographic hashes
- Reconstruct a timeline of events
- Determine whether file copying likely occurred

---

## Tools Used

| Tool | Purpose |
|--------|--------|
| Windows Event Viewer | USB activity analysis |
| Device Manager | Device identification |
| PowerShell | File timeline collection |
| Autopsy 4.23.1 | Forensic analysis |
| Windows File Properties | Metadata review |

---

## Scenario

A company suspected that an employee connected an unauthorized USB storage device and copied potentially sensitive documents.

The investigator was tasked with determining:

- Whether a USB device was connected
- What device was used
- Whether files were copied
- Whether document modifications occurred before transfer

---

# Evidence Collected

## Documents

- Employee-Salaries.xlsx
- Quarterly-Budget.xlsx
- Executive-Notes.docx

## USB Device

- Kingston DataTraveler 3.0 USB Device

---

# Evidence Analysis

## USB Device Identification

Device Manager identified:

Kingston DataTraveler 3.0 USB Device

Event Viewer logs confirmed Plug-and-Play activity associated with the device.

---

## Event Log Analysis

### Relevant Event IDs

| Event ID | Description |
|-----------|-----------|
| 2003 | Driver loading for newly discovered device |
| 2100 | PnP device activity |
| 2102 | Device management operation |

### Observed Times

09:26:06 AM

09:26:17 AM

09:26:18 AM

These events confirm USB device initialization and successful connection.

---

## Metadata Analysis

### Employee-Salaries.xlsx

Created:
09:01:46 AM

Modified:
09:01:47 AM

### Quarterly-Budget.xlsx

Created:
09:02:15 AM

Modified:
09:02:15 AM

### Executive-Notes.docx

Created:
09:02:51 AM

Modified:
09:28:20 AM

---

# Autopsy Analysis

Autopsy was used to compare original files against copied versions located within the USB evidence set.

## Hash Verification

Original and copied files produced identical cryptographic hashes.

Example:

MD5:
d939bb8cf9c682865b5adaafead68167

SHA256:
e4b9616be8023ced27418db14dda730c9aa58d6baa5ce54f51d6a32b6d969b7b

This indicates the copied file contents were identical to the source file.

---

# Timeline Reconstruction

| Time | Event |
|--------|--------|
| 09:01:46 | Employee-Salaries.xlsx created |
| 09:02:15 | Quarterly-Budget.xlsx created |
| 09:02:51 | Executive-Notes.docx created |
| 09:26:06 | USB activity begins |
| 09:26:17 | Driver load event recorded |
| 09:26:18 | Additional USB events recorded |
| 09:28:20 | Executive-Notes.docx modified |
| 09:45:17 | USB copies created |
| 09:45:18 | Additional USB file activity |

---

# Findings

## Finding 1

A Kingston DataTraveler 3.0 USB storage device was connected to the system.

Evidence:
- Device Manager
- Event Viewer

---

## Finding 2

Windows successfully initialized and mounted the device.

Evidence:
- Event IDs 2003
- Event IDs 2100
- Event IDs 2102

---

## Finding 3

The investigated files existed before USB activity occurred.

Evidence:
- File metadata
- PowerShell timeline output

---

## Finding 4

Files were duplicated to removable media.

Evidence:
- Matching file hashes
- Separate storage locations
- Different creation timestamps

---

## Finding 5

Executive-Notes.docx was modified before being copied.

Evidence:
- Metadata timestamps
- Autopsy timeline

---

# Conclusion

The investigation confirmed the connection of a Kingston DataTraveler 3.0 USB device to the workstation.

Forensic analysis showed that multiple documents existed prior to USB activity and were later duplicated to removable media. Hash verification confirmed the copied files were identical to their original counterparts.

The available evidence supports the conclusion that files were copied to external storage after document creation and modification activity occurred.

---

# Lessons Learned

- USB activity can be reconstructed using Windows event logs.
- Metadata timestamps provide valuable context when building timelines.
- Hash analysis is critical when validating copied files.
- Autopsy provides an efficient method for correlating timestamps and metadata.
- Logical file acquisitions may alter certain timestamps and should be documented during analysis.

---

# Skills Demonstrated

- Digital Forensics
- USB Artifact Analysis
- Event Log Analysis
- Metadata Analysis
- Timeline Reconstruction
- Hash Verification
- Evidence Documentation
- Autopsy
- Windows Forensics
