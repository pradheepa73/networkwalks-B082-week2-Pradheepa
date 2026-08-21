
# 🛡️ Offensive Security Reconnaissance: Week 2 Field Manual

> *"The quieter you become, the more you are able to hear." — Kali Linux Philosophy*

---

## 📋 Project Brief

**Objective:** Conduct a comprehensive external reconnaissance engagement against `networkwalks.com` and perform host discovery on an isolated lab network.

**Engagement Type:** Passive Footprinting & Active Network Discovery

**Classification:** Educational / Authorized Testing

**Date of Execution:** 17–21 August 2026

**Intern:** Pradheepa.M | Batch B082

---

## 🗺️ Engagement Scope

| Target | Type | Activity |
|--------|------|----------|
| `networkwalks.com` | External | Passive OSINT, DNS enumeration, WAF fingerprinting |
| `10.0.0.0/24` | Internal (Lab) | ICMP host discovery (Ping Scan) |

> 📌 **Authorization:** This engagement was performed under the Networkwalks Letter of Authorization (LOA) for Batch B082. All activities were limited to passive reconnaissance and non-intrusive scanning.

---

## 🧰 Arsenal Deployed

### Phase 1: External Footprinting

| Tool | Function | Outcome |
|------|----------|---------|
| `whois` | Domain registry intelligence | Registrar: GoDaddy |
| `whatweb` | Technology stack profiling | WordPress 7.0.4 / WP Download Manager 3.3.58 |
| `nslookup` | DNS resolution | Server IP identified |
| `curl -I` | HTTP header forensics | Apache / WP REST API exposed |
| `wafw0f` | WAF identification | ModSecurity (SpiderLabs) |
| `dnsrecon` | Full DNS enumeration | BIND 9.16.23-RH / 31 subdomains |

### Phase 2: OSINT & Open-Source Correlation

| Tool | Function | Outcome |
|------|----------|---------|
| **GHDB** | Google dorking (technique demonstration) | 10 exposed cameras / 10 open directories identified via public search results |
| **Maltego** | Entity relationship mapping | Hunter transform: 0 additional emails |
| **theHarvester** | Aggregated source harvesting | 1 email / 31 subdomains / 3 ASNs |

### Phase 3: Local Network Discovery

| Tool | Function | Outcome |
|------|----------|---------|
| **Zenmap** | Ping Sweep (`-sn`) | 2 live hosts on `10.0.0.0/24` |

---

## 🔍 Key Intelligence Highlights

| Finding | Severity | Notes |
|---------|----------|-------|
| WordPress 7.0.4 | Informational | Version disclosure |
| WP Download Manager 3.3.58 | Informational | Version disclosure |
| ModSecurity (SpiderLabs) WAF | Informational | Vendor fingerprintable |
| BIND version disclosure (9.16.23-RH) | Informational | Version disclosure |
| 31 subdomains exposed | Informational | Expanded external attack surface |
| `info@networkwalks.com` | Informational | Generic contact point |
| 10 exposed cameras (GHDB) | Informational | Third-party public search discovery |
| 10 open directories | Informational | Third-party public search discovery |
| DNSSEC not enabled | Informational | DNS spoofing risk (theoretical) |
| 2 live hosts (Lab) | N/A | Tester's own network |

---

## 🧠 Attacker Mindset Analysis

```text
[!] WordPress versioning may expose CVE attack surface for future disclosures.
[!] WAF vendor identification narrows bypass technique selection.
[!] 31 subdomains identified, expanding the organization's observable external attack surface and requiring further authorized security assessment.
[!] cpanel/webdisk/webmail = high-value authentication targets for potential credential-based attacks.
[!] BIND version disclosure enables version-specific exploit research.
```

---

## 📁 Repository Topography

```
📂 networkwalks-B082-week2-Pradheepa/
│
├── 📄 README.md
│
├── 📂 W2-PM1_Kali_Tools/
│   ├── 📂 Screenshots/        # Terminal output captures
│   └── 📂 Outputs/            # Raw text dumps
│
├── 📂 W2-PM2_GHDB/
│   ├── 📂 Screenshots/        # Dork discovery evidence
│   └── 📂 Outputs/            # Camera + ebook tables
│
├── 📂 W2-PM3_Maltego/
│   ├── 📂 Screenshots/        # Graph & transform execution
│   └── 📂 Outputs/            # Maltego session file
│
├── 📂 W2-PM4_theHarvester/
│   ├── 📂 Screenshots/        # Task 1 & 2 execution
│   └── 📂 Outputs/            # Combined results
│
├── 📂 W2-PM5_Zenmap/
│   ├── 📂 Screenshots/        # Scan config & output
│   └── 📂 Outputs/            # Network topology PDF
│
└── 📂 W2-PM_FINAL_Report/
    └── 📄 Penetration_Testing_Report_B082_Pradheepa.pdf
```

---

## 📊 Execution Summary

```
┌─────────────────────────────────────────────────────────────┐
│  PHASE                │  TOOLS              │  STATUS      │
├───────────────────────┼─────────────────────┼──────────────┤
│  External Footprinting│  6 Kali Tools       │  ✅ COMPLETE │
│  OSINT Correlation    │  GHDB/Maltego/Harvester │ ✅ COMPLETE│
│  Network Discovery    │  Zenmap             │  ✅ COMPLETE │
│  Reporting            │  Final Report       │  ✅ COMPLETE │
└─────────────────────────────────────────────────────────────┘

OVERALL ENGAGEMENT STATUS: ✅ 100% COMPLETE
```

---

## 🏁 Lessons Learned

1. **API dependency matters** – theHarvester's multi-source run was constrained by missing premium API keys (BuiltWith, Censys, DNSDumpster, etc.). A future run with full key provisioning would yield a more complete external footprint.

2. **Version ≠ Vulnerability** – WordPress 7.0.4 and WP Download Manager 3.3.58 were current releases at the time of assessment, correcting the template's initial assumption.

3. **WAF fingerprinting is trivial** – ModSecurity detection took only 2 requests. While the WAF is a positive security control, its vendor is identifiable, which may enable targeted bypass research.

4. **Subdomain enumeration reveals exposure** – 31 subdomains were discovered, including cpanel, webdisk, and webmail—high-value assets that should be reviewed for access controls and necessity of public exposure.

5. **Passive recon is powerful** – No active exploitation was performed, yet a complete infrastructure map was generated from public data alone.

---

## 🧾 Final Report

The full penetration testing report is available here:

📄 [Penetration_Testing_Report_B082_Pradheepa.pdf.pdf](https://github.com/user-attachments/files/31301220/Penetration_Testing_Report_B082_Pradheepa.pdf.pdf)


---

## 🔒 Ethical Compliance

> ⚠️ **Disclaimer**
>
> This repository documents **educational research** conducted under explicit written authorization. All targets were either:
>
> 1. `networkwalks.com` – owned and authorized by Networkwalks Academy
> 2. `10.0.0.0/24` – the tester's own lab environment
>
> **No exploitation, data exfiltration, or service disruption occurred.**
>
> This work is intended solely for defensive cybersecurity education.
>
> **Note on GHDB findings:** The Google Hacking Database results were discovered through public search engine queries. No cameras or directories were accessed, tested, or confirmed to be active. These findings are presented purely as a technique demonstration and are not client-specific vulnerabilities.

---

## 👤 About the Author

**Pradheepa.M** is a cybersecurity enthusiast and intern at Networkwalks Academy (Batch B082). With a strong foundation in network security, penetration testing, and OSINT reconnaissance, Pradheepa is passionate about understanding attacker methodologies to build better defenses.

**Areas of Interest:**
- 🔍 Offensive Security & Penetration Testing
- 🌐 OSINT & Passive Reconnaissance
- 🛡️ Network Security & Defense
- 📊 Security Reporting & Documentation

**Certifications Pursuing:**
- Networkwalks Cybersecurity Internship
- Ethical Hacking

**Connect:**
- LinkedIn: [https://www.linkedin.com/in/pradheepa-m-051728372](https://www.linkedin.com/in/pradheepa-m-051728372?utm_source=share_via&utm_content=profile&utm_medium=member_android)
- GitHub: [https://github.com/pradheepa73](https://github.com/pradheepa73)

---

## 🙏 Acknowledgments

- **Networkwalks Academy** – For curating this hands-on internship program
- **Waqas Karim (CCIE)** – For technical mentorship and industry perspective
- **Batch B082 Cohort** – For collaborative troubleshooting and shared insights

---

> *"Know thy enemy and know thyself; in a hundred battles, you will never be defeated." — Sun Tzu, The Art of War*

---

> *"Every security professional should think like an attacker to defend like a guardian." — Pradheepa.M*

---

**© 2026 Pradheepa.M | Networkwalks Cybersecurity Internship | Batch B082**
```


