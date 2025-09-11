# Capstone Project: Full VAPT Cycle

## Objective
Simulate a complete Vulnerability Assessment and Penetration Testing (VAPT) cycle using Kali Linux and Metasploitable2/DVWA targets. The goal is to identify vulnerabilities, exploit them ethically, collect evidence, and document findings in a structured PTES-compliant report.

## Tools Used
- Kali Linux (attacker machine)
- Metasploitable2 / DVWA (target machines)
- Metasploit (exploitation)
- OpenVAS (vulnerability scanning)
- sqlmap (SQL injection testing)
- Google Docs (documentation)

## 1. Vulnerability Assessment
- OpenVAS scan performed on target IPs to identify vulnerabilities.
- Findings logged in a structured table:

| Timestamp            | Target IP      | Vulnerability | PTES Phase      |
|----------------------|----------------|---------------|----------------|
| 2025-08-18 12:00:00  | 192.168.1.200  | XSS           | Exploitation   |

## 2. Exploitation Simulation
- Target: DVWA (Damn Vulnerable Web Application)
- Task: SQL Injection
- Tool: sqlmap
- Demonstrated extraction of database information using SQL injection without causing damage.
- Verified exploit with OpenVAS findings.

## 3. Reporting
- PTES-compliant report drafted in Google Docs, including:
  - Executive summary
  - Vulnerability findings
  - Exploitation evidence
  - Remediation recommendations
- 100-word non-technical summary created for management.

## 4. Key Learning
- Complete VAPT cycle demonstrates discovery, validation, exploitation, and reporting.
- Reinforced structured PTES methodology and importance of documenting findings and mitigation steps.

## 5. Evidence / Notes
- Screenshots and logs saved for OpenVAS and SQLmap.
- CVSS scores used for prioritization.
- All work conducted in a lab environment with authorization.
