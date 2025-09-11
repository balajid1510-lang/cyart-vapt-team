OSINT Checks Report

This document summarizes the Open Source Intelligence (OSINT) activities performed during the reconnaissance phase of the assessment. The goal of these checks is to gather publicly available information about the target environment without direct exploitation.

1. WHOIS Lookup

Objective: To identify the registrar, domain ownership, and registration details.
Process: A WHOIS query was performed on the target domain.
Findings:

The domain is registered with GoDaddy.

WHOIS privacy protection has been enabled, masking registrant details.

The domain has been active for more than 3 years, indicating a long-standing presence.

Risk Consideration: Attackers may use WHOIS data to perform social engineering against listed contacts if privacy protection is disabled.

2. DNS Enumeration

Objective: To identify DNS records such as A, MX, TXT, and NS.
Process: Conducted DNS lookups using the dig and nslookup utilities.
Findings:

A record → Resolves to 192.168.29.155.

MX record → Mail server found at mail.target.com.

TXT record → Includes SPF policy, but incomplete configuration was noted.

Risk Consideration: Misconfigured or leaked DNS entries may expose infrastructure details useful for attackers.

3. Subdomain Enumeration

Objective: To identify accessible subdomains that may host vulnerable services.
Process: Tools like Sublist3r and crt.sh were used.
Findings:

dev.target.com → Running Apache Tomcat 5.5 (outdated).

test.target.com → Accessible over HTTP, possibly a staging or testing environment.

Risk Consideration: Development and test environments are often less secure and can be leveraged for initial compromise.

4. Shodan Search

Objective: To discover exposed services and banner information indexed by Shodan.
Process: Queried the target IP and domain on Shodan.
Findings:

Port 21 (FTP) running vsftpd 2.3.4 – known backdoor vulnerability (CVE-2011-2523).

Port 445 (SMB) running Samba 3.0.20 – vulnerable to remote code execution.

Risk Consideration: These outdated services represent high-risk entry points for attackers.

5. Google Dorking

Objective: To identify sensitive files or directories exposed to search engines.
Process: Used Google search operators such as site:target.com filetype:txt.
Findings:

A robots.txt file was identified.

The file revealed disallowed entries such as /admin/, indicating the existence of an admin portal.

Risk Consideration: Attackers may bypass weak access controls and attempt brute-force or directory traversal on exposed paths.

6. Technology Fingerprinting

Objective: To understand the underlying technology stack of the target.
Process: Used Wappalyzer and manual banner grabbing.
Findings:

Web server → Apache/2.2.8 (outdated and vulnerable).

Backend → PHP 5.2, no longer supported and missing critical security updates.

Risk Consideration: Running outdated technologies increases the attack surface and exposes known vulnerabilities.

Summary Table of OSINT Findings
Timestamp	Tool	Check Type	Finding
2025-09-10 09:30:00	WHOIS	Domain Info	Domain registered with GoDaddy, privacy enabled
2025-09-10 09:45:00	Shodan	Service Banner	FTP (vsftpd 2.3.4), SMB (Samba 3.0.20)
2025-09-10 10:00:00	Sublist3r	Subdomains	dev.target.com, test.target.com
2025-09-10 10:15:00	Google	Dorking	/admin/ path revealed in robots.txt
2025-09-10 10:30:00	Wappalyzer	Tech Stack	Apache/2.2.8, PHP 5.2
Overall Assessment

The OSINT phase revealed several critical exposures such as outdated FTP and SMB services, publicly accessible development/test subdomains, and directory disclosures through robots.txt. These findings will guide the next steps of vulnerability scanning and exploitation.
