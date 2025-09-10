# Week 2 – Vulnerability Assessment & Penetration Testing (VAPT) Lab

This repository documents my **Week 2 hands-on labs for Vulnerability Assessment and Penetration Testing (VAPT)**.  
The labs were performed in a **controlled environment** with the following setup:

- **Attacker Machine:** Kali Linux  
- **Target Machine:** Metasploitable2  
- **Network Configuration:** Both systems were configured in **Bridge Adapter Mode** on the same subnet to simulate real-world attacker-victim communication.

---

## 🎯 Objectives
1. Understand and perform vulnerability scanning with industry-standard tools.  
2. Conduct reconnaissance and OSINT to map attack surfaces.  
3. Exploit discovered vulnerabilities to validate risks.  
4. Perform post-exploitation tasks such as privilege escalation and evidence collection.  
5. Document findings in both technical (PTES) and non-technical reports.  
6. Gain practical experience in simulating a full VAPT cycle.

---

## 🛠 Tools Used
- **Scanning:** Nmap, OpenVAS, Nikto  
- **Reconnaissance:** Maltego, Shodan, Sublist3r, Wappalyzer  
- **Exploitation:** Metasploit Framework, sqlmap, Burp Suite  
- **Post-Exploitation:** Meterpreter, Volatility, sha256sum  
- **Reporting:** Google Docs, Google Sheets, GitHub  

---

## 📌 Lab Activities & Results

### 1. Vulnerability Scanning
- **Activity:** Scanned the Metasploitable2 target with Nmap, OpenVAS, and Nikto.  
- **Key Results:**  
  - Port 80 – Apache web server vulnerable to **CVE-2021-41773** (Critical)  
  - Port 445 – SMB service exposed (Medium risk)  
- **Prioritization:** Vulnerabilities were scored with CVSS and organized in a tracking table.  
- **Outcome:** Generated detailed reports in `.txt`, `.pdf`, and `.xlsx` formats for documentation.

---

### 2. Reconnaissance
- **Activity:** Performed OSINT to gather intelligence about the target system.  
- **Findings:**  
  - **Shodan:** Detected exposed SSH service on `192.168.1.50`  
  - **Maltego:** Identified subdomain `dev.example.com`  
  - **Sublist3r & WHOIS:** Revealed additional domain information  
  - **Wappalyzer:** Detected target’s technology stack  
- **Documentation:** Recon logs and checklists recorded in `.md` and `.txt` files.  
- **Outcome:** Built a clear map of the attack surface to support exploitation.

---

### 3. Exploitation
- **Activity:** Exploited critical vulnerabilities identified during scanning.  
- **Example Exploit:**  
  - Used Metasploit’s `exploit/multi/http/tomcat_mgr_login` → achieved **Java reverse shell**.  
  - Verified SQL Injection on DVWA using **sqlmap**.  
- **Validation:** Compared results against Exploit-DB Proof-of-Concepts (PoCs).  
- **Outcome:** Confirmed vulnerabilities were exploitable and documented logs in `exploit_results.txt`.

---

### 4. Post-Exploitation
- **Activity:** Gained persistence, escalated privileges, and collected evidence.  
- **Steps Taken:**  
  - Privilege escalation with Metasploit’s UAC bypass module.  
  - Extracted and hashed sensitive files using `sha256sum` for integrity verification.  
- **Evidence Example:**
| Item        | Description | Collected By | Date       | SHA256 Hash          |
| ----------- | ----------- | ------------ | ---------- | -------------------- |
| target.conf | Config File | VAPT Analyst | 2025-08-18 | \<hash\_value\_here> |


- **Outcome:** Demonstrated the potential impact of full system compromise.

---

### 5. Capstone – Full VAPT Cycle
- **Activity:** Conducted an end-to-end penetration test following **PTES methodology**.  
- **Steps:** Recon → Scanning → Exploitation → Post-Exploitation → Reporting.  
- **Simulation:**  
- Exploited SQL Injection on DVWA with sqlmap.  
- OpenVAS confirmed multiple vulnerabilities.  
- **Reporting:**  
- Drafted a **200-word PTES-style report**.  
- Wrote a **100-word non-technical summary** for management.  
- Composed a **developer email** explaining PoCs and remediation.  
- **Outcome:** Full pentest cycle successfully executed and documented.

---

## 📂 Repository Structure
Week/
├── Week2/Vulnerability_Scanning/
│ ├── nmap_report.txt
│ ├── openvas_report.pdf
│ └── scan_tables.xlsx
├── Reconnaissance/
│ ├── recon_logs.md
│ ├── osint_checks.md
├── Exploitation/
│ ├── exploit_results.txt
│ └── validation_summary.md
├── Post-Exploitation/
│ ├── privilege_escalation_logs.txt
│ └── collected_evidence.md
├── Docs_and_Workflow/
│ ├── PTES_report.pdf
│ ├── summary.md
│ ├── checklist.txt
│ └── screenshots/
└── README.md

---

## 📑 Key Learnings
1. **Scanning is not enough** – Exploitation validates risks and demonstrates real-world impact.  
2. **Reconnaissance is critical** – OSINT revealed hidden assets and services.  
3. **Privilege escalation** highlights how quickly attackers can gain persistence.  
4. **Structured reporting (PTES)** ensures professional communication of findings.  
5. **Lab simulations** with Kali and Metasploitable2 build practical, job-ready skills.  

---

⚠️ **Disclaimer**  
All work in this repository was conducted in a **controlled lab environment** for learning purposes only.  
These steps must **not** be attempted on unauthorized systems.
