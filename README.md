# 🛡️ eJPT Study Notes

Personal study notes compiled while preparing for the **eLearnSecurity Junior Penetration Tester (eJPT)** certification. These notes cover the full penetration testing methodology — reconnaissance, scanning, enumeration, vulnerability assessment, and exploitation — with practical command references, tool usage, and step-by-step lab walkthroughs.

> ⚠️ **Disclaimer:** These are personal study notes for educational purposes only. All techniques referenced are intended for use in **authorized lab environments** (e.g. INE labs, personal test labs, CTFs) only. Do not use any of this information against systems you do not own or do not have explicit written permission to test. Unauthorized access to computer systems is illegal.

---

## 📑 Table of Contents

- [About This Repo](#-about-this-repo)
- [Contents](#-contents)
- [Topics Covered](#-topics-covered)
- [Penetration Testing Methodology](#-penetration-testing-methodology)
- [Tools Referenced](#-tools-referenced)
- [How I Use These Notes](#-how-i-use-these-notes)
- [Exam Prep Tips](#-exam-prep-tips)
- [Resources](#-resources)
- [Feedback / Contributing](#-feedback--contributing)

---

## 📘 About This Repo

The **eJPT (eLearnSecurity Junior Penetration Tester)** is an entry-level, 100% practical penetration testing certification focused on hands-on skills rather than theory. This repository is my personal knowledge base built while working through the course modules and labs — organized so I (and hopefully others studying for the same exam) can quickly reference commands, workflows, and gotchas during practice or the exam itself.

Each file corresponds to a specific exam domain or lab module and includes:
- Step-by-step command sequences taken from real lab walkthroughs
- Tool syntax and flag explanations
- "Gotchas" and troubleshooting notes (things that didn't work and what to try instead)
- Key terminology and concept explanations

---

## 📖 Contents

| # | Topic | File | Covers |
|---|-------|------|--------|
| 1 | Information Gathering | [1. Information Gathering](1__Information_Gathering.md) | Passive/active recon, WHOIS, DNS recon, OSINT, Google dorking, Shodan, email harvesting |
| 2 | Footprinting & Scanning | [2. Footprinting & Scanning](2__Footprinting___Scanning.md) | Host discovery, Nmap scan types, service/OS fingerprinting |
| 3 | Enumeration | [3. Enumeration](3__Enumeration.md) | FTP, SMB, HTTP, MySQL, SSH, SMTP enumeration via MSF auxiliary modules |
| 4 | Vulnerability Assessment | [4. Vulnerability Assessment](4__Vulnerability_Assessment.md) | Manual & automated scanning, Nessus, WMAP, WebDAV, EternalBlue, BlueKeep, Pass-the-Hash, Shellshock |
| 5 | Exploitation | [4. Exploitation](4__Exploitation.md) | Banner grabbing, Nmap NSE vulnerability scripts |
| 6 | System & Host Based Attacks | [1. System & Host Based Attacks](1__System_Host_Based_Attacks.md) | Local attack vectors and host-level techniques |
| 7 | Network Based Attacks | [2. Network Based Attacks](2__Network_Based_Attacks.md) | SMB/NetBIOS & SNMP enumeration, pivoting, proxychains, DNS/SMB relay attacks |
| 8 | The Metasploit Framework (MSF) | [3. The Metasploit Framework](3__The_Metasploit_Framework__MSF_.md) | Workspaces, database integration, module usage, sessions |
| 9 | Web Application Penetration Testing | [Web Application Penetration Testing](Web_Application_Penetration_Testing.md) | HTTP methods, Burp Suite, Nikto, DIRB/Gobuster, WPScan, LFI indicators |
| 10 | Auditing Fundamentals | [Auditing Fundamentals](Auditing_Fundamentals.md) | Core auditing concepts and methodology |

---

## 🧭 Topics Covered

### 🔎 Reconnaissance (Passive & Active)
- OSINT techniques: WHOIS, `robots.txt` / `sitemap.xml`, Wayback Machine, Google Hacking Database (GHDB)
- DNS reconnaissance: `dnsrecon`, `dnsenum`, `fierce`, zone transfers (`AXFR`), DNS record types (A, AAAA, MX, NS, CNAME, TXT, SOA, SRV, PTR)
- Subdomain enumeration: `Sublist3r`
- Technology fingerprinting: Wappalyzer, BuiltWith, `whatweb`
- Email/username harvesting: `theHarvester`
- Internet-connected device discovery: Shodan
- Breach data lookups: Have I Been Pwned

### 📡 Footprinting & Scanning
- Host discovery: `nmap -sn`, `netdiscover` (ARP-based)
- Port scanning: TCP/UDP scans, full port range, fast scans, service version detection (`-sV`)
- OS fingerprinting (`-O`), NSE default scripts (`-sC`), combined aggressive scan (`-A`)
- Scan output formats (`-oN`, `-oX`) for reporting and MSF import

### 🔬 Enumeration (via Metasploit Auxiliary Modules)
- **FTP:** version detection, brute-force login, anonymous access checks
- **SMB:** version detection, user enumeration, share enumeration, login brute-force, `smbclient`
- **HTTP/Web:** version & header grabbing, `robots.txt` checks, directory/file brute-forcing, login brute-forcing, Apache user directory enumeration
- **MySQL:** version detection, login brute-force, schema dumping, direct SQL query execution
- **SSH:** version detection, login brute-force, user enumeration
- **SMTP:** version detection, user enumeration

### 🧪 Vulnerability Assessment
- Manual vuln identification via Nmap + `searchsploit`
- Automated scanning with **Nessus** (scan types, report export, MSF import)
- Web app scanning with **WMAP** inside Metasploit
- WebDAV exploitation: `davtest`, `cadaver`, web shell upload
- **CVE-specific labs:**
  - MS17-010 / EternalBlue (manual + Metasploit automated exploitation)
  - CVE-2019-0708 / BlueKeep
  - Shellshock (manual Burp Suite exploitation + Metasploit module)
- **Pass-the-Hash attacks:** `kiwi`/Mimikatz hash dumping, `psexec`, `crackmapexec`

### 💥 Exploitation
- Banner grabbing via Nmap scripts and raw `netcat` connections
- Targeted NSE vulnerability scripts (e.g. Shellshock detection)

### 🖧 Network Based Attacks
- SMB & NetBIOS enumeration (`nbtscan`, `nmblookup`, NSE SMB scripts)
- SNMP enumeration (`snmpwalk`, NSE SNMP scripts, SNMP brute-force)
- **Pivoting:** `autoroute`, SOCKS proxy setup, `proxychains`
- DNS spoofing + ARP spoofing + SMB relay attack chains

### 🧰 Metasploit Framework (MSF) Core Skills
- Database setup (`postgresql`, `db_status`)
- Workspace management (`workspace -a`)
- Importing Nmap/Nessus scan data (`db_import`, `db_nmap`)
- Global variables (`setg`) for faster module configuration
- Session management, backgrounding, and `sessions -i`

### 🌐 Web Application Penetration Testing
- HTTP method enumeration (`OPTIONS`, `PUT`, `DELETE`) and file upload abuse
- Traffic interception & modification with **Burp Suite** (Proxy, Repeater, Intruder concepts)
- Vulnerability scanning with **Nikto**
- Content discovery with **DIRB** and **Gobuster** (dir, vhost, DNS modes)
- WordPress-specific testing with **WPScan** (version/user enum, brute-force)
- LFI indicators, sensitive file/directory patterns (`.git`, `.env`, `/backup`, `config.php`)
- Burp Suite vs OWASP ZAP comparison; crawling vs spidering

### 📋 Auditing Fundamentals
- Core auditing principles and how they relate to the broader pentest methodology

---

## 🔄 Penetration Testing Methodology

The notes generally follow this workflow, which mirrors the eJPT exam structure:
Information Gathering → Passive & active recon, OSINT
Footprinting & Scanning → Host discovery, port/service scanning
Enumeration → Service-specific deep dives (FTP, SMB, HTTP, SQL, SSH...)
Vulnerability Assessment → Identify exploitable weaknesses (manual + automated)
Exploitation → Gain access using identified vulnerabilities
Post-Exploitation → Privilege escalation, pivoting, lateral movement
Reporting → Document findings (auditing fundamentals)

**General Web App Pentest Flow:**
`Nmap` → `Nikto` → `DIRB`/`Gobuster` → `Burp Suite`/`curl` (manual testing)

**General WordPress Pentest Flow:**
Identify (Wappalyzer) → Enumerate (`wpscan`) → User enum (`wpscan -eu`) → Exploit/brute-force

---

## 🛠️ Tools Referenced

| Category | Tools |
|---|---|
| Scanning | `Nmap`, `netdiscover`, `nbtscan` |
| Exploitation Framework | `Metasploit Framework (msfconsole)` |
| Web Recon | `whatweb`, `Wappalyzer`, `BuiltWith`, `Sublist3r`, `theHarvester` |
| DNS Recon | `dnsrecon`, `dnsenum`, `fierce`, `dig`, `whois` |
| Web App Testing | `Burp Suite`, `Nikto`, `DIRB`, `Gobuster`, `WPScan` |
| Password Attacks | `Hydra`, `crackmapexec` |
| Traffic Analysis | `Wireshark`, `tcpdump` |
| WebDAV | `davtest`, `cadaver` |
| Credential/Hash Tools | Metasploit `kiwi` (Mimikatz), `psexec` |
| OSINT | `Shodan`, `Have I Been Pwned`, Google Dorks, Wayback Machine |
| Vulnerability Scanners | `Nessus`, `WMAP` (Metasploit plugin) |

---

## 📝 How I Use These Notes

- **Before labs:** Skim the relevant module file for command syntax and flags I tend to forget.
- **During labs:** Keep the file open as a live reference for exact Metasploit module paths and option names.
- **After labs:** Add any new "gotchas" or error fixes I ran into (e.g. wrong wordlist paths, services not starting) back into the notes.
- **Before the exam:** Review the "High-Yield Exam Tips" sections and the full methodology flow end-to-end.

---

## 🎯 Exam Prep Tips

A few recurring lessons captured across these notes:

- Always confirm `service postgresql start` and `db_status` before relying on Metasploit's database features — a lot of wasted time comes from skipping this.
- Use `setg RHOSTS <ip>` early in a workspace to avoid retyping the target IP for every module.
- When a default wordlist doesn't yield results (FTP/SSH/HTTP brute-force), don't give up — try enumerating valid usernames first to narrow the attack surface.
- Always check for **anonymous/guest access** (FTP, SMB) before brute-forcing — it's often enabled by mistake in lab environments.
- If Zone Transfer (`AXFR`) fails, fall back to brute-force subdomain discovery with `fierce`.
- Watch for **HTTP PUT** being enabled — it's a fast path to uploading a web shell.
- Document scans as you go (`-oN`, `-oX`) — you'll need this for reporting and re-importing into Metasploit.

---

## 📚 Resources

- [eLearnSecurity eJPT Official Page](https://elearnsecurity.com/product/ejpt-certification/)
- [Metasploit Unleashed (Offensive Security)](https://www.offensive-security.com/metasploit-unleashed/)
- [HackTricks](https://book.hacktricks.xyz/)
- [GTFOBins](https://gtfobins.github.io/)
- [Google Hacking Database (GHDB)](https://www.exploit-db.com/google-hacking-database)

---

## ⭐ Feedback / Contributing

These are personal study notes, but if you spot an error, outdated command, or want to suggest an addition, feel free to open an issue or submit a pull request.

---

🧑‍💻 *Maintained as part of my eJPT certification prep journey.*
