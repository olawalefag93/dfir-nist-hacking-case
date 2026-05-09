# 📸 Screenshot Capture Guide — NIST Hacking Case

> This guide tells you exactly what to capture in Autopsy to populate the `screenshots/` folder. Take these in order — they tell the story of the investigation visually.

---

## Naming Convention

Always save as: `##-descriptive-name.png`  
Example: `01-hash-verification.png`

Use **Windows Snipping Tool** or **Greenshot** for clean captures. Crop out your desktop/taskbar — keep it professional.

---

## Required Screenshots

### `01-hash-verification.png`
**Where:** Autopsy → Case → Data Source summary panel  
**What to show:**
- MD5 hash: `aee4fcd9301c03b3b054623ca261959a`
- SHA-1 hash: `da2fe30fe21711edf42310873af475859a68f300`
- Verification status (PASS / green checkmark)

---

### `02-autopsy-user-accounts.png`
**Where:** Autopsy → Results → OS Accounts  
**What to show:**
- The `MR` user account
- SID: `S-1-5-21-2000478354-688789844-1708537768-1003`
- Full Name field: **empty** (this is significant — highlight it)

---

### `03-installed-programs.png`
**Where:** Autopsy → Results → Installed Programs  
**What to show:**
- The full list of installed programs
- Highlight / scroll to show: Cain & Abel, NetStumbler, Anonymizer, 123 Write All Stored Passwords, Look@LAN, Ethereal, WinPcap

---

### `04-prefetch-execution.png`
**Where:** Autopsy → Results → Recent Activity → Run Programs (Prefetch)  
**What to show:**
- CAIN.EXE (2004-08-27 10:33:03, count: 2)
- NETSTUMBLER.EXE (2004-08-27 10:12:35, count: 1)
- ETHEREAL.EXE (2004-08-27 10:34:54, count: 1)
- LOOKATLAN.EXE (count: 2)

---

### `05-browser-history.png`
**Where:** Autopsy → Results → Web History  
**What to show:**
- 2600.org visit
- elitehackers.com visit
- wardriving.com visit
- whatismyip.com visit
- Sort by date to show Aug 20 and Aug 27 sessions

---

### `06-yahoo-identity.png`
**Where:** Autopsy → Results → Web History → filter for `yahoo.com`  
**What to show:**
- The URL containing `fn=Greg&ln=Schardt&id=mrevil2000`
- Full URL visible: `edit.yahoo.com/config/id_check?.fn=Greg&.ln=Schardt&.id=mrevil2000`
- Date: 2004-08-20 ~15:35 EST

---

### `07-hacking-searches.png`
**Where:** Autopsy → Results → Web Search  
**What to show:**
- Google: `"what is my ip"` — 2004-08-25 16:07:51
- Google: `"who am i"` — 2004-08-25 16:07:32
- MSN: `"hacking"` — 2004-08-20 15:33:11
- MSN: `"download rencode buddy"` — 2004-08-20 21:27:41

---

### `08-netstumbler-install.png`
**Where:** Autopsy → Results → Installed Programs  
**What to show:**
- Network Stumbler 0.4.0 entry
- Install timestamp: 2004-08-27 15:12:15

**BONUS:** Also capture the prefetch entry showing it was executed.

---

### `09-cain-abel-execution.png`
**Where:** Autopsy → Results → Run Programs (Prefetch)  
**What to show:**
- CAIN.EXE prefetch entry
- Path: `/PROGRAM FILES/CAIN`
- Last run: 2004-08-27 10:33:03
- Run count: **2**

---

### `10-footprinting-directory.png` *(bonus)*
**Where:** Autopsy → File browser → navigate to `My Documents/FOOTPRINTING/`  
**What to show:**
- The FOOTPRINTING directory and its contents (nmapNT files)
- This visually proves pre-planned reconnaissance activity

---

### `11-defrag-prefetch.png` *(bonus)*
**Where:** Autopsy → Results → Run Programs (Prefetch)  
**What to show:**
- DEFRAG.EXE entry
- Date: 2004-08-26 10:46:18
- This is the anti-forensic indicator

---

### `12-high-entropy-oembios.png` *(bonus)*
**Where:** Autopsy → Results → Interesting Items → High Entropy  
**What to show:**
- oembios.bin entry
- Entropy score: 7.999987
- File path in system32

---

## Tips for Good Screenshots

- **Use full Autopsy window** — don't crop important columns
- **Highlight the key row** — click/select the relevant item so it's highlighted blue
- **Show the timestamp column** — always keep date/time visible
- **Add a red box or arrow** in image editor if needed to draw attention (Paint, Greenshot, etc.)
- **Keep file names consistent** — no spaces, use hyphens

---

## After Capturing

Once you have your screenshots, update the `README.md` image links if you want them embedded:

```markdown
![Hash Verification](screenshots/01-hash-verification.png)
```

You can add an **Evidence Gallery** section to the README to make it more visual for hiring managers viewing your GitHub.

---

*Part of NIST-HC-2004-001 DFIR Lab | github.com/olawalefag93*
