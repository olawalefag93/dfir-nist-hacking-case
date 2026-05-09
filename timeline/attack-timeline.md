# 🕐 Attack Timeline — NIST Hacking Case (NIST-HC-2004-001)

**Subject:** Greg Schardt (alias: Mr. Evil / mrevil2000)  
**System:** Windows XP SP1 — Computer Name: N-1A9ODN6ZXK4LQ  
**Activity Period:** August 19–27, 2004  
**All times in EST**

---

## Timeline Overview

```
Aug 19 ──── System Setup / First Boot
Aug 20 ──── Mass Tool Installation + Hacking Research
Aug 25 ──── Network Scanning + IP Obfuscation Research
Aug 26 ──── Remote Access + Anti-Forensic Activity
Aug 27 ──── Wardriving + Packet Capture + Final Activity
```

---

## Detailed Chronology

### 📅 August 19, 2004 — System Initialization

| Time (EST) | Event | Source | Significance |
|---|---|---|---|
| 17:52:01 | SPOOLSV.EXE executed | Prefetch | Printer spooler — OS startup |
| 17:53:05 | LSASS.EXE executed | Prefetch | Security subsystem — OS startup |
| 17:53:19 | MSOOBE.EXE executed | Prefetch | Windows XP out-of-box setup wizard |
| 18:04:11 | EXPLORER.EXE executed | Prefetch | Desktop shell — first user login |
| 18:04:12 | USERINIT.EXE executed | Prefetch | User initialization |
| 18:05:04 | MSMSGS.EXE executed | Prefetch | MSN Messenger started |
| 23:04:24 | `about:Home` accessed | IE Cache | First IE browser launch |
| 23:04:50 | WebFldrs XP installed | Registry | Windows web folders component |

**Assessment:** System was freshly installed on August 19. Windows XP setup completed and user profile initialized for `MR. Evil`.

---

### 📅 August 20, 2004 — Tool Installation + Hacking Research

| Time (EST) | Event | Source | Significance |
|---|---|---|---|
| 10:05:00 | SETUP.EXE executed | Prefetch | Initial setup executable |
| 10:05:52 | CAIN25B45.EXE executed | Prefetch | **Cain & Abel installer launched** 🔴 |
| 10:06:18 | WINPCA~1.EXE executed | Prefetch | WinPcap driver installed via Cain |
| 10:06:45 | FABERTOYS_FULLSETUP.EXE executed | Prefetch | Faber Toys installed |
| 10:08:02 | A32-19.EXE executed | Prefetch | Unknown executable |
| 10:08:37 | CUTE3032.EXE executed | Prefetch | CuteFTP installer |
| 10:08:54 | 30.EXE executed from TEMP | Prefetch | Temp executable — suspicious |
| 10:09:03 | CuteHTML installed | Registry | Web editor |
| 10:09:16 | WORDPAD.EXE executed | Prefetch | Document opened |
| 10:09:46 | MIRC612.EXE executed | Prefetch | **mIRC installer launched** 🟠 |
| 10:10:47 | WHOIS.EXE executed (v1) | Prefetch | First Whois tool execution |
| 10:11:56 | POWERTOYSETUP.EXE executed from TEMP | Prefetch | PowerToys installer |
| 10:12:05 | MSIEXEC.EXE executed | Prefetch | Windows installer |
| 10:12:54 | 123WASP_SETUP.EXE executed | Prefetch | **Password harvesting tool installer** 🔴 |
| 10:13:06 | REGSVR32.EXE executed | Prefetch | DLL registration |
| 10:13:11 | GLJ15.TMP executed (×8) | Prefetch | Temp file executed multiple times |
| 10:50:40 | NOTEPAD.EXE executed | Prefetch | Text editor opened |
| 15:04:51 | `file/Drivers/Anonyymizer/keys.txt` | IE Cache | **Anonymizer license key file accessed** 🔴 |
| 15:05:09 | Anonymizer Bar 2.0 installed | Registry | **IP concealment tool installed** 🔴 |
| 15:05:16 | Anonymizer thanks page opened | IE Cache | Post-install confirmation |
| 15:05:58 | **Cain & Abel v2.5b45 installed** | Registry | **Password cracker confirmed installed** 🔴 |
| 15:07:25 | Faber Toys installed | Registry | — |
| 15:08:19 | Forté Agent installed | Registry | Usenet client |
| 15:09:02 | CuteFTP installed | Registry | FTP client |
| 15:09:03 | CuteHTML installed | Registry | — |
| 15:09:09 | `file/Drivers/GhostWare/Receipt.rtf` | IE Cache | GhostWare receipt accessed |
| 15:09:16 | WORDPAD opened Receipt.rtf | Prefetch | — |
| 15:10:04 | mIRC installed | Registry | IRC chat client |
| 15:12:15 | **123 Write All Stored Passwords installed** | Registry | **Credential harvesting** 🔴 |
| 15:12:43 | PowerToys for XP installed | Registry | — |
| 15:13:08 | **Network Stumbler 0.4.0 installed** | Registry | **Wardriving tool installed** 🔴 |
| 15:31:31 | Visited **2600.org** | IE Cache | **Hacker magazine site** 🔴 |
| 15:31:54 | Browsed 2600.org/hacked_pages | IE Cache | **Hacked pages archive browsed** 🔴 |
| 15:32:05 | Visited 2600.org/hacked_pages/2000/01/thomas.loc.gov | IE Cache | Specific hacked page |
| 15:32:12 | Visited 2600.com/hacked_pages | IE Cache | Mirror site browsed |
| 15:33:11 | **MSN Search: "hacking"** | IE Cache | **Explicit hacking search** 🔴 |
| 15:33:35 | Visited cleo-and-nacho.com/mainpages/hacking.htm | IE Cache | Hacking tutorial page |
| 15:34:16 | Visited Yahoo.com | IE Cache | — |
| 15:34:27 | Yahoo account registration initiated | IE Cache | — |
| 15:35:05 | **Yahoo ID `mrevil2000` checked — Greg Schardt** | IE Cache | **Identity attribution** 🔴 |
| 15:38:23 | Logged into Yahoo Mail (mrevil2000) | IE Cache | Email account access |
| 15:38:27 | Accessed Yahoo inbox | IE Cache | — |
| 15:38:45 | Logged out of Yahoo Mail | IE Cache | — |
| 15:45:57 | Visited **elitehackers.com** | IE Cache | **Hacking community site** 🔴 |
| 15:46:02 | Browsed elitehackers.com/ua/ | IE Cache | Underground area |
| 15:49:01 | Visited t50.com | IE Cache | — |
| 15:50:40 | `file/Program Files/mIRC/channels/channels.txt` opened | IE Cache | mIRC channel list accessed |
| 19:05:11 | Visited cnn.com | IE Cache | News browsing |
| 21:15:02 | `mkC:/cool_mail.htm` accessed | IE Cache | Local HTML file |
| 21:21:55 | Visited outpimp.com | IE Cache | — |
| 21:27:41 | **MSN Search: "download rencode buddy"** | IE Cache | **Tool download research** 🟠 |
| 21:27:53 | Visited magnescan.com/pricelist.asp | IE Cache | — |

**Assessment:** August 20 was the primary tool installation day. Within a single session the subject installed Cain & Abel, mIRC, CuteFTP, Anonymizer, password harvesters, and wardriving tools. The same session included explicit searches for hacking content and browsing of underground hacking sites.

---

### 📅 August 25, 2004 — Network Scanning + IP Research

| Time (EST) | Event | Source | Significance |
|---|---|---|---|
| 10:23:53 | **PING.EXE executed** | Prefetch | **Network host discovery** 🟠 |
| 10:25:47 | DUMPREP.EXE executed | Prefetch | Crash dump reporter |
| 10:25:50 | DWWIN.EXE executed | Prefetch | Error reporting |
| 10:26:55 | FTINIT.EXE executed | Prefetch | Faber Toys init |
| 10:27:27 | Faber Toys executed | Prefetch | — |
| 10:55:26 | LALSETUP250.EXE executed from Desktop | Prefetch | **Look@LAN installer launched** 🟠 |
| 10:55:32 | IRSETUP.EXE from TEMP | Prefetch | Setup routine |
| 10:55:36 | AGENT.EXE executed | Prefetch | Forté Agent newsreader |
| 10:56:33 | **LOOKATHOST.EXE executed** | Prefetch | **LAN host scanner executed** 🔴 |
| 11:20:34 | **MIRC.EXE executed** (3 times total) | Prefetch | **IRC client executed** 🟠 |
| 11:20:35 | AGENTSVR.EXE executed | Prefetch | Agent server component |
| 15:25:04 | Visited yahoo.com | IE Cache | — |
| 15:26:44 | Yahoo browsing | IE Cache | — |
| 15:27:45 | Visited **majorgeeks.com** | IE Cache | Tool download site |
| 15:29:30 | Browsed majorgeeks.com/downloads2.html | IE Cache | Download browsing |
| 15:49:28 | majorgeeks.com/download.php browsed | IE Cache | — |
| 15:49:42 | Look@LAN (lalsetup250.exe) FTP download confirmed | IE Cache | `ftp://mondadori.com/.../lalsetup250.exe` |
| 15:51:06 | Visited fastclick.net, tribalfusion.com | IE Cache | Ad networks (browsing artifacts) |
| 15:51:24 | FTP download from mondadori.com confirmed | IE Cache | Look@LAN source |
| 15:52:59 | Visited mosnews.com | IE Cache | Russian news site |
| 15:54:05 | Browsed mosnews.com/commentary | IE Cache | — |
| 16:07:26 | Visited **google.com** | IE Cache | — |
| 16:07:32 | **Google Search: "who am i"** | IE Cache | **Identity/IP obfuscation research** 🔴 |
| 16:07:51 | **Google Search: "what is my ip"** | IE Cache | **IP concealment behavior** 🔴 |
| 16:08:02 | Visited **whatismyip.com** | IE Cache | **External IP lookup** 🔴 |
| 16:13:00 | Visited fosi.ural.net | IE Cache | — |
| 16:13:01 | Visited microsoft.com/windows/ie/getosver | IE Cache | IE version check |
| 16:22:17 | MSN homepage browsed | IE Cache | — |

**Assessment:** August 25 shows a clear pattern of network reconnaissance and IP obfuscation. The subject scanned the LAN with Look@LAN, ran mIRC, and then researched their own IP address using multiple methods — a strong indicator of awareness of being tracked or preparation for unauthorized remote access.

---

### 📅 August 26, 2004 — Remote Access + Anti-Forensic Activity

| Time (EST) | Event | Source | Significance |
|---|---|---|---|
| 10:05:06 | RUNDLL32.EXE executed | Prefetch | System utility |
| 10:05:15 | **TELNET.EXE executed** | Prefetch | **Remote terminal access attempted** 🔴 |
| 10:06:14 | **LOOKATLAN.EXE executed** (2nd time) | Prefetch | **LAN scanner run again** 🔴 |
| 10:13:57 | **WHOIS.EXE executed** (2nd time) | Prefetch | **Domain reconnaissance** 🟠 |
| 10:25:03 | LOGON.SCR executed | Prefetch | Screensaver |
| 10:46:18 | **DEFRAG.EXE executed** | Prefetch | **⚠️ Disk defragment — possible anti-forensic activity** 🔴 |
| 10:46:18 | DFRGNTFS.EXE executed | Prefetch | NTFS defragmenter |
| 10:51:43 | HELPSVC.EXE executed | Prefetch | Help service |
| 15:08:12 | **Accessed file://4.12.220.254/Temp/yng13.bmp** | IE Cache | **File on remote host accessed** 🔴 |

**Assessment:** August 26 is the most operationally significant day. The subject used Telnet for remote access, ran LAN scanning again, performed Whois reconnaissance, and then executed DEFRAG — a possible deliberate attempt to overwrite deleted file evidence. The access of a file on an external IP (`4.12.220.254`) suggests active communication with or reconnaissance of a remote target system.

---

### 📅 August 27, 2004 — Wardriving + Packet Capture + Final Activity

| Time (EST) | Event | Source | Significance |
|---|---|---|---|
| 10:08:04 | **System boot #4** | Prefetch (NTOSBOOT) | 4th boot of the system |
| 10:08:10 | **USB device connected** | System Log | **Removable media — possible exfil** 🟠 |
| 10:12:11 | NETSTUMBLERINSTALLER executed | Prefetch | **NetStumbler re-installed** 🔴 |
| 10:12:18 | HH.EXE executed | Prefetch | Help file opened |
| 10:12:35 | **NETSTUMBLER.EXE executed** | Prefetch | **Wardriving tool executed** 🔴 |
| 10:14:44 | RUNDLL32.EXE executed | Prefetch | — |
| 10:14:52 | UNINSTALL.EXE from WinPcap dir | Prefetch | WinPcap uninstall attempt |
| 10:14:58 | **CMD.EXE executed** (2nd time) | Prefetch | **Command line used** 🟠 |
| 10:15:08 | WINPCAP_3_01_A.EXE from Desktop | Prefetch | **WinPcap re-installed from Desktop** 🔴 |
| 10:15:17 | NPF_MGM.EXE executed | Prefetch | WinPcap network filter manager |
| 10:15:18 | DAEMON_MGM.EXE executed | Prefetch | WinPcap daemon manager |
| 10:16:15 | TASKMGR.EXE executed | Prefetch | Task manager opened |
| 10:28:36 | ETHEREAL-SETUP-0.10.6.EXE from Desktop | Prefetch | **Ethereal installer re-run from Desktop** 🔴 |
| 10:31:17 | RUNDLL32.EXE executed | Prefetch | — |
| 10:33:03 | **CAIN.EXE executed** (2nd confirmed time) | Prefetch | **Cain & Abel launched again** 🔴 |
| 10:34:54 | **ETHEREAL.EXE executed** | Prefetch | **Packet capture tool launched** 🔴 |
| 10:42:41 | IEXPLORE.EXE executed (18th time) | Prefetch | Browser opened |
| 10:46:17 | LOGONUI.EXE executed (7th time) | Prefetch | Lock/logon screen |
| 15:09:23 | Visited **wardriving.com** | IE Cache | Wardriving resource browsed |
| 15:09:27 | Visited wardriving.com/setup.php | IE Cache | Wardriving setup guide |
| 15:09:54 | Visited **netstumbler.com** | IE Cache | — |
| 15:10:00 | Visited netstumbler.com/downloads | IE Cache | NetStumbler download page |
| 15:11:07 | Downloaded netstumblerinstaller_0_4_0.exe | IE Cache | **Wardriving tool download confirmed** 🔴 |
| 15:11:13 | Visited winpcap.mirror.ethereal.com | IE Cache | WinPcap mirror |
| 15:11:33 | Visited WinPcap download page | IE Cache | — |
| 15:14:20 | **Downloaded WinPcap_3_01_a.exe** | IE Cache | **Packet driver downloaded** 🔴 |
| 15:17:05 | Visited ethereal.com/download.html | IE Cache | Ethereal download page |
| 15:17:15 | **Accessed FTP: mirror.sg.depaul.edu/pub/security** | IE Cache | **Security tools FTP repository** 🔴 |
| 15:17:20 | Browsed depaul.edu/pub/security/ethereal | IE Cache | — |
| 15:17:44 | Browsed depaul.edu/pub/security/ethereal/win32 | IE Cache | — |
| 15:24:24 | **Downloaded ethereal-setup-0.10.6.exe from depaul.edu** | IE Cache | **Packet analyzer download** 🔴 |
| 15:29:19 | Ethereal 0.10.6 installed (confirmed) | Registry | — |
| 15:32:40 | DNS error page — browsing continued | IE Cache | — |
| 15:42:47 | MSN homepage visited | IE Cache | — |
| 15:43:19 | Visited **maktoob.com** | IE Cache | Arabic language web portal |
| 15:44:35 | Browsed maktoob.com/MAIN/ | IE Cache | — |

**Assessment:** August 27 was the most technically active day. The subject reinstalled WinPcap, relaunched Cain & Abel, ran Ethereal for packet capture, executed NetStumbler for wardriving, downloaded tools from a university security FTP server, and browsed wardriving resources. A USB device was connected at system boot. This is consistent with a final operational session.

---

## Summary Attack Progression

```
Phase 1 — Preparation (Aug 19–20)
├── Fresh OS install
├── Mass offensive tool installation
├── Identity concealment setup (Anonymizer, blank account name)
└── Initial hacking research (2600.org, hacking searches)

Phase 2 — Reconnaissance (Aug 20–25)
├── Identity registration as "mrevil2000"
├── mIRC for potential covert comms
├── LAN scanning with Look@LAN
├── Whois and domain research
└── IP address obfuscation research

Phase 3 — Operations (Aug 26)
├── Telnet remote access execution
├── Repeated LAN scanning
├── Access of file on remote host (4.12.220.254)
└── DEFRAG executed (possible anti-forensic cleanup)

Phase 4 — Final Ops (Aug 27)
├── USB device connected (possible exfil / tool staging)
├── NetStumbler wardriving executed
├── Cain & Abel re-executed
├── Ethereal packet capture active
├── Tools re-downloaded from security FTP
└── Final browsing session
```

---

*Generated from forensic analysis of SCHARDT:001 disk image | Examiner: Olawale John Fagade*
