# 🧪 Investigation Notes — NIST Hacking Case

**Case ID:** NIST-HC-2004-001  
**Examiner:** Olawale John Fagade  
**Date:** May 8, 2026  

---

## 1. Investigation Approach

This investigation followed a structured digital forensics methodology aligned with NIST SP 800-86 (*Guide to Integrating Forensic Techniques into Incident Response*) and general DFIR best practices. The process proceeded in five phases:

```
1. Evidence Acquisition & Integrity Verification
2. System Identification
3. User & Account Analysis
4. Artifact Collection & Analysis
5. Timeline Reconstruction & Reporting
```

All analysis was performed on a forensic copy of the original evidence. The original disk image was never modified.

---

## 2. Tools Used

| Tool | Version | Purpose |
|---|---|---|
| **Autopsy** | 4.x | Primary forensic analysis platform |
| **Sleuth Kit** | Bundled with Autopsy | File system analysis |
| **IE Analyzer (Autopsy module)** | — | Browser history / index.dat parsing |
| **Keyword Search (Autopsy)** | — | String and pattern searching |
| **File Type Identification** | MIME-type analysis | Detecting disguised files |
| **Entropy Analysis** | Autopsy module | Identifying encrypted/compressed files |
| **Hash Verification** | MD5 + SHA-1 | Evidence integrity |

---

## 3. Phase 1 — Evidence Acquisition & Integrity Verification

### What I Did
- Loaded the 8-part DD image (`SCHARDT.001` through `SCHARDT.008`) into Autopsy
- Ran MD5 and SHA-1 hash verification against the provided hash values
- Confirmed zero bad blocks on the image

### Results
| Hash | Value | Status |
|---|---|---|
| MD5 | `aee4fcd9301c03b3b054623ca261959a` | ✅ VERIFIED |
| SHA-1 | `da2fe30fe21711edf42310873af475859a68f300` | ✅ VERIFIED |
| Bad Blocks | None | ✅ CLEAN |

### Why This Matters
Hash verification is a legal and forensic requirement. If the hash doesn't match, the evidence may have been tampered with and could be inadmissible. A matching hash proves the forensic copy is bit-for-bit identical to the original.

---

## 4. Phase 2 — System Identification

### What I Looked At
- **Windows Registry** (`SOFTWARE` hive) for OS details and installed programs
- **SAM hive** for user account information and SIDs
- **SYSTEM hive** for computer name and configuration

### Key Artifacts
| Artifact | Location | Finding |
|---|---|---|
| OS Version | Registry → SOFTWARE\Microsoft\Windows NT | Windows XP (x86) |
| Computer Name | Registry → SYSTEM\ControlSet | N-1A9ODN6ZXK4LQ |
| Product ID | Registry | 55274-640-0147306-23684 |
| Primary User SID | SAM hive | S-1-5-21-2000478354-688789844-1708537768-1003 |
| User Full Name | SAM hive | **BLANK — suspicious** |

### Notes
A blank full name on the primary non-admin account is unusual and suggests deliberate identity concealment. This was a key early indicator that warranted deeper identity attribution analysis.

---

## 5. Phase 3 — User & Account Analysis

### What I Looked At
- **SAM hive** — local user accounts
- **User profile directories** — `C:\Documents and Settings\`
- **Internet Explorer cache** — `index.dat` files
- **Browser history** for identity artifacts

### Identity Attribution Process

The account full name was blank, so I pivoted to browser artifacts to attribute identity:

1. Searched IE cache for Yahoo and email-related URLs
2. Found Yahoo ID check URL containing registration parameters
3. Extracted: `fn=Greg`, `ln=Schardt`, `id=mrevil2000`
4. Cross-referenced with user profile path: `C:\Documents and Settings\MR. Evil\`
5. **Conclusion:** Greg Schardt operated this machine under the alias "Mr. Evil / mrevil2000"

---

## 6. Phase 4 — Artifact Collection & Analysis

### 6.1 Registry Analysis — Installed Programs

**Artifact:** `HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall`

Parsed the Uninstall registry key to enumerate all installed software with timestamps. Flagged any tools associated with offensive security, network reconnaissance, or anonymization.

**Key finding method:** Sorted by install date, then cross-referenced program names against known hacking tool databases.

---

### 6.2 Prefetch Analysis — Program Execution

**Artifact:** `C:\Windows\Prefetch\*.pf`

Windows XP creates `.pf` (prefetch) files for every executable run. Each file contains:
- Full path of the executable
- Last execution timestamp
- Execution count

This is one of the most reliable sources of program execution evidence on Windows XP — even if the program has been uninstalled, the prefetch file may remain.

**Key finding:** CAIN.EXE had been run **twice**, MIRC.EXE **three times**, and NETSTUMBLER.EXE confirmed executed — proving these tools weren't just installed but actually used.

---

### 6.3 Browser Forensics — IE Index.dat

**Artifact:** Multiple `index.dat` files in:
- `C:\Documents and Settings\MR. Evil\Local Settings\Temporary Internet Files\Content.IE5\`
- `C:\Documents and Settings\MR. Evil\Cookies\`
- `C:\Documents and Settings\MR. Evil\Local Settings\History\`

Autopsy's IE Analyzer module parsed these binary cache files and extracted:
- Full URLs visited
- Domain names
- Access timestamps
- Cookie usernames

**Key finding:** The index.dat preserved every URL visited, including Yahoo registration URLs with the subject's real name embedded in the query string — even after browsing sessions ended.

---

### 6.4 File System Analysis — Suspicious Files

**What I looked for:**
- Files in unusual locations (e.g., hacking tools in user temp directories)
- MIME-type mismatches (extension doesn't match actual file type)
- High-entropy files (possible encryption)
- Files in directories with suspicious names (e.g., "FOOTPRINTING")

**MIME-type mismatch detection:** Autopsy identifies actual file content via magic bytes and flags cases where the extension is misleading. Found several `.lic`, `.opt`, and `.bin` files that were actually MS Office-format binaries — possible data hiding.

**Entropy analysis:** `oembios.bin` scored 7.999987/8.0 entropy. Truly random data (like encryption output) approaches maximum entropy. This file warrants further cryptanalysis.

---

### 6.5 File Carving — Deleted/Unallocated Space

Autopsy's file carving module scanned unallocated disk sectors and recovered:
- Hundreds of text, HTML, Java, and DLL files
- Two large Windows Registry exports (`.reg` files, 852 KB and 2.8 MB)
- WinPcap DLLs (`Packet.dll`, `wpcap.dll`)
- Prefetch files for tools no longer on the system
- Media files (`.wmv`, `.wma`) requiring further review

**Note on DEFRAG:** Because DEFRAG.EXE was run on Aug 26, some unallocated space may have been overwritten. File carving results from this image may be incomplete as a result.

---

### 6.6 Anti-Forensic Indicators

| Indicator | Evidence | Interpretation |
|---|---|---|
| Blank account name | SAM hive | Deliberate identity concealment |
| Anonymizer installed | Registry + IE cache | IP masking |
| DEFRAG executed | Prefetch: 2004-08-26 | Possible evidence destruction |
| Googled "who am i" / "what is my ip" | IE cache | Operational security awareness |
| Tools in TEMP directories | Prefetch paths | Avoiding permanent installation traces |

---

## 7. Phase 5 — Timeline Reconstruction

### Method
Timestamps were collected from multiple artifact sources and merged into a unified timeline:

1. **Registry timestamps** — software install times
2. **Prefetch timestamps** — last execution times + run counts
3. **IE cache timestamps** — URL access times (from index.dat)
4. **File system metadata** — created/modified/accessed times

All timestamps were normalized to EST (the system's local timezone, confirmed from the Windows timezone registry setting).

### Challenge: Timestamp Reliability

Windows file timestamps can be manipulated, but prefetch and index.dat timestamps are harder to forge and generally reliable. Registry timestamps reflect the last write to a key, which typically aligns with install events.

---

## 8. Key Investigative Decisions

### Why I prioritized IE cache over browser history UI
The `index.dat` binary format is a lower-level artifact than what the browser "history" UI shows. It persists longer, captures more URLs (including redirects and cached resources), and preserves cookie data with usernames. Autopsy's IE Analyzer module decodes it natively.

### Why prefetch was central to execution analysis
On Windows XP, prefetch files are the most reliable execution evidence available without a live memory capture. Registry run keys and recent documents can be manipulated more easily. Prefetch run counts and timestamps provided high-confidence execution evidence for Cain & Abel, NetStumbler, and Ethereal.

### Why the DEFRAG finding matters
DEFRAG.EXE execution one day before the final activity session creates a forensic gap. Defragmentation moves file clusters and overwrites previously-freed space. If the subject deleted evidence before running DEFRAG, recovery of those deleted artifacts may be impossible. This should be noted in any legal proceedings.

---

## 9. Limitations

| Limitation | Impact |
|---|---|
| DEFRAG executed on Aug 26 | Deleted files from Aug 26 or earlier may be unrecoverable |
| No live memory capture available | Running processes, network connections, and RAM artifacts unavailable |
| No network capture available | Cannot confirm actual data exfiltration or remote connections |
| Timestamps can be manipulated | All timestamps treated as corroborating, not sole evidence |
| USB device content unknown | External media contents were not available for analysis |

---

## 10. References

- NIST SP 800-86: *Guide to Integrating Forensic Techniques into Incident Response*
- Autopsy Documentation: https://www.autopsy.com/support/docs/
- Sleuth Kit Documentation: https://www.sleuthkit.org/
- Windows Prefetch Analysis: Brian Carrier, *File System Forensic Analysis*
- IE Index.dat Format: Joachim Metz, libmsiecf

---

*Examiner: Olawale John Fagade | CompTIA Security+ | AWS CCP | Fortinet NSE 1-3*
