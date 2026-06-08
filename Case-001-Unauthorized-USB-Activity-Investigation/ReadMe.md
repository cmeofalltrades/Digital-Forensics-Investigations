# Case 001 – Document Activity Investigation

**Project Type:** Digital Forensics Investigation

**Investigator:** Cierra Emerson

**Date:** June 2026

**Tools Used:**

* Autopsy 4.23.1

---

# Executive Summary

A forensic examination was conducted to investigate document activity associated with a simulated unauthorized USB usage scenario. The objective was to identify file creation and modification activity and determine whether evidence existed to support user interaction with sensitive documents.

A logical file set containing three business-related documents was analyzed using Autopsy. Metadata analysis identified modification activity on two of the three documents. Timeline reconstruction established a sequence of file creation and modification events.

This investigation served as an introductory digital forensics exercise focused on evidence identification, metadata analysis, timeline creation, findings development, and report writing.

---

# Investigation Scope

The purpose of this investigation was to:

* Identify files contained within the evidence source
* Examine file metadata
* Determine whether files were modified after creation
* Construct a timeline of observed activity
* Document findings and conclusions

---

# Evidence Examined

The following files were analyzed:

| File Name                  | File Type                |
| -------------------------- | ------------------------ |
| Payroll.xlsx               | Microsoft Excel Workbook |
| Budget.xlsx                | Microsoft Excel Workbook |
| Employee-Terminations.docx | Microsoft Word Document  |

Evidence Source Type:

* Logical File Set

Analysis Platform:

* Autopsy 4.23.1

---

# Methodology

The following process was used:

1. Created a forensic case in Autopsy.
2. Added the evidence folder as a Logical File Set.
3. Processed the evidence using Autopsy ingest modules.
4. Examined file metadata.
5. Recorded file creation and modification timestamps.
6. Constructed an activity timeline.
7. Developed findings and conclusions based on observed evidence.

---

# Timeline of Events

| Timestamp        | Event                               |
| ---------------- | ----------------------------------- |
| 2026-06-08 22:37 | Budget.xlsx Created                 |
| 2026-06-08 22:37 | Budget.xlsx Modified                |
| 2026-06-08 22:37 | Payroll.xlsx Created                |
| 2026-06-08 22:38 | Employee-Terminations.docx Created  |
| 2026-06-08 22:39 | Employee-Terminations.docx Modified |
| 2026-06-08 22:41 | Payroll.xlsx Modified               |

---

# Findings

## Finding 1 – Payroll.xlsx Modification Activity

Metadata analysis revealed that Payroll.xlsx was created on June 8, 2026 at 22:37 and modified on June 8, 2026 at 22:41.

The modification occurred approximately four minutes after file creation, indicating activity occurred after the file was initially created.

---

## Finding 2 – Employee-Terminations.docx Modification Activity

Metadata analysis revealed that Employee-Terminations.docx was created on June 8, 2026 at 22:38 and modified on June 8, 2026 at 22:39.

The modification occurred approximately one minute after file creation, indicating activity occurred after the file was initially created.

---

## Finding 3 – Budget.xlsx Activity

Metadata analysis revealed that Budget.xlsx contained identical creation and modification timestamps.

No evidence was identified indicating modification activity after the initial file creation event.

---

# Analysis

The metadata associated with the evidence files indicates that two documents experienced post-creation modification activity.

Payroll.xlsx demonstrated the latest modification timestamp among the examined files. Employee-Terminations.docx also exhibited modification activity after creation.

Budget.xlsx did not display evidence of subsequent modification activity based on the available metadata.

The collected evidence supports the conclusion that user interaction occurred after the initial creation of multiple files within the examined evidence set.

---

# Conclusion

Analysis of the provided evidence identified post-creation modification activity within Payroll.xlsx and Employee-Terminations.docx.

Payroll.xlsx exhibited the latest modification timestamp observed during the examination. Budget.xlsx did not show evidence of modification after creation.

The available metadata establishes that activity occurred on multiple files after their initial creation. No evidence was identified indicating file deletion, file transfer, or data exfiltration during this examination.

---

# Lessons Learned

* Digital investigations should focus on evidence rather than assumptions.
* Metadata can provide valuable insight into user activity.
* Findings and conclusions must remain separate.
* Timelines help reconstruct activity in a clear and repeatable manner.
* Autopsy provides an effective platform for organizing and analyzing digital evidence.

---

# Skills Demonstrated

* Digital Forensics Fundamentals
* Evidence Identification
* Metadata Analysis
* Timeline Reconstruction
* Findings Development
* Evidence-Based Reporting
* Autopsy Case Management
* Investigative Documentation

---

**Case Status:** Closed

**Case Number:** Case-001
