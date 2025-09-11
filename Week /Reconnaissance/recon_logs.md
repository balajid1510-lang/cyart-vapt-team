Reconnaissance Logs

This document contains chronological logs of reconnaissance activities performed during the OSINT phase. Each log includes a timestamp, tool used, command executed (if applicable), and observations.

Log 1 – WHOIS Lookup
[2025-09-10 09:30:00]  
Command: whois target.com  
Output:  
  Registrar: GoDaddy.com, LLC  
  Creation Date: 2020-05-14  
  Updated Date: 2024-06-01  
  Registrant: Redacted for Privacy  
Observation: WHOIS privacy protection enabled. No direct email or phone contact disclosed.  

Log 2 – DNS Enumeration
[2025-09-10 09:40:00]  
Command: dig target.com any  
Output:  
  A record → 192.168.29.155  
  MX record → mail.target.com (Priority: 10)  
  TXT record → v=spf1 include:_spf.google.com ~all  
Observation: SPF record is present but lacks strict enforcement (-all).  

Log 3 – Subdomain Enumeration
[2025-09-10 10:00:00]  
Command: sublist3r -d target.com  
Output:  
  dev.target.com → Running Apache Tomcat 5.5  
  test.target.com → Accessible HTTP page with login form  
Observation: Dev/Test environments exposed; may contain weaker controls.  

Log 4 – Shodan Search
[2025-09-10 10:15:00]  
Tool: Shodan Web Interface  
Query: host:192.168.29.155  
Output:  
  Port 21 → vsftpd 2.3.4 (vulnerable)  
  Port 445 → Samba 3.0.20 (vulnerable)  
Observation: Outdated services, high likelihood of public exploits.  

Log 5 – Google Dorking
[2025-09-10 10:25:00]  
Query: site:target.com inurl:robots.txt  
Output:  
  robots.txt found → Disallowed: /admin/  
Observation: Existence of admin panel endpoint confirmed.  

Log 6 – Technology Fingerprinting
[2025-09-10 10:40:00]  
Tool: Wappalyzer (Browser Extension)  
Output:  
  Server → Apache/2.2.8  
  Language → PHP/5.2  
Observation: Outdated Apache and PHP versions in use, end-of-life software.  

Summary of Logs

The logs confirm that multiple reconnaissance techniques identified critical exposures: outdated services (FTP, SMB, Apache, PHP), publicly accessible subdomains, and an admin portal listed in robots.txt. These findings set the foundation for targeted vulnerability scanning and exploitation in later phases.
