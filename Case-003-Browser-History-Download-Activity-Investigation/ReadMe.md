![Repository Banner](./images/project-banner.png)

# Case 003 – Browser History & Download Activity Investigation

## Executive Summary

This investigation was conducted to determine whether files were downloaded from the internet using Google Chrome and to identify evidence of user browsing activity.

Using Chrome browser artifacts, Windows file system metadata, and PowerShell analysis, evidence was collected and examined to identify downloaded files, verify their existence on the system, establish a timeline of activity, and validate file integrity through cryptographic hashing.

The investigation confirmed that multiple files were downloaded using Google Chrome and remained present within the Downloads directory at the time of analysis. Metadata analysis and hash verification provided additional evidence supporting the findings.

---

## Investigation Objectives

The objectives of this investigation were to:

* Identify the browser used during the activity
* Locate browser history and download artifacts
* Determine which files were downloaded
* Verify the existence of downloaded files
* Analyze file metadata and timestamps
* Verify file integrity using cryptographic hashes
* Reconstruct a timeline of user activity

---

## Scenario

An organization suspected that a user downloaded files from the internet using a web browser.

The investigator was tasked with determining:

* Which browser was used
* What files were downloaded
* When the downloads occurred
* Whether the files still existed on the system
* Whether the files could be verified through hash analysis

---

## Evidence Collected

### Downloaded Files

* G162691946_78d2eb5c69934a7ca6e8d9ba28f8724c.pdf
* cmeofalltrades power-bi-portfolio main Project-02-Device-Compliance.zip
* InvestigationNotes.txt

### Browser Artifacts

* Chrome Download History
* Chrome History Database
* Chrome User Profile Artifacts

### System Artifacts

* Downloads Folder Contents
* PowerShell Metadata Output
* SHA256 Hash Results

### Forensic Tools

* Google Chrome
* Windows File Explorer
* Windows PowerShell

---

## Analysis

### Browser Identification

Analysis confirmed that Google Chrome was used during the investigation.

The primary browser artifact was located at:

```text
%LOCALAPPDATA%\Google\Chrome\User Data\Default\History
```

This artifact contains browsing history and download activity records.

---

### Download History Analysis

Chrome download history identified multiple downloaded files associated with user activity.

Observed downloads included:

* PDF Document
* ZIP Archive

The browser download history correlated with files present in the Downloads directory.

---

### Downloads Folder Examination

The Downloads folder was examined to determine whether downloaded files remained present on the system.

Identified files:

| File Name                                                               | Type      |
| ----------------------------------------------------------------------- | --------- |
| G162691946_78d2eb5c69934a7ca6e8d9ba28f8724c.pdf                         | PDF       |
| cmeofalltrades power-bi-portfolio main Project-02-Device-Compliance.zip | ZIP       |
| InvestigationNotes.txt                                                  | Text File |

The files remained accessible within the Downloads directory during analysis.

---

### Metadata Analysis

PowerShell was used to examine file creation and modification timestamps.

#### ZIP Archive

| Attribute | Timestamp   |
| --------- | ----------- |
| Created   | 09:44:26 AM |
| Modified  | 09:44:27 AM |

#### PDF Document

| Attribute | Timestamp   |
| --------- | ----------- |
| Created   | 09:49:34 AM |
| Modified  | 09:49:35 AM |

#### InvestigationNotes.txt

| Attribute | Timestamp   |
| --------- | ----------- |
| Created   | 09:50:53 AM |
| Modified  | 09:50:53 AM |

The metadata established a clear sequence of events and confirmed that the files were created and downloaded during the investigation period.

---

### Hash Verification

SHA256 hashes were generated to verify file integrity.

#### PDF Document

```text
1987DC08C54CB43302A7D4DB792D2DEDED36B4303CA36AE71947D1E27C5C739C
```

#### ZIP Archive

```text
E69396D734934D2963181251661DC4FF37668247C4C3ADD90C5BCE9F2CF4D78E
```

Hash analysis established a unique fingerprint for each file and provides a method for future integrity verification.

---

## Timeline Reconstruction

| Time               | Event                           |
| ------------------ | ------------------------------- |
| 09:44:26           | ZIP archive downloaded          |
| 09:44:27           | ZIP archive modified            |
| 09:49:34           | PDF document downloaded         |
| 09:49:35           | PDF document modified           |
| 09:50:53           | InvestigationNotes.txt created  |
| Investigation Time | Evidence collected and analyzed |

The timeline demonstrates a clear sequence of browser download activity followed by evidence collection and analysis.

---

## Findings

### Finding 1

Google Chrome was used to download files from the internet.

**Evidence:**

* Chrome Download History
* Chrome History Database

---

### Finding 2

Multiple files were successfully downloaded through the browser.

**Evidence:**

* Chrome Download Records
* Downloads Folder Contents

---

### Finding 3

Downloaded files remained present within the Downloads directory during analysis.

**Evidence:**

* File Explorer Examination
* Downloads Folder Review

---

### Finding 4

Metadata timestamps established the order in which files were downloaded and created.

**Evidence:**

* PowerShell Metadata Analysis

---

### Finding 5

SHA256 hashes were successfully generated for downloaded files.

**Evidence:**

* PowerShell Hash Output

---

## Conclusion

The investigation confirmed that Google Chrome was used to download multiple files from the internet.

Analysis of browser artifacts, download history, file metadata, and PowerShell output demonstrated that the downloaded files remained present within the Downloads directory at the time of analysis. Metadata timestamps established a clear sequence of events, while SHA256 hash verification provided integrity validation for the downloaded files.

Based on the available evidence, the findings support the conclusion that browser download activity occurred and that the downloaded files were successfully preserved and verified during the investigation.

---

## Lessons Learned

* Browser artifacts provide valuable evidence of user activity.
* Download history can be correlated with file system artifacts.
* Metadata analysis assists with timeline reconstruction.
* Hash verification supports evidence integrity validation.
* Multiple evidence sources should be correlated to strengthen investigative conclusions.
* Proper documentation is essential for forensic reporting.

---

## Skills Demonstrated

* Digital Forensics
* Browser Artifact Analysis
* Download Activity Investigation
* Metadata Analysis
* Timeline Reconstruction
* SHA256 Hash Verification
* Evidence Documentation
* Windows Forensics
* PowerShell Analysis
* Incident Investigation
