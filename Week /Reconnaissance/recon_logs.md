evidence/whois_example.com.txt
2025-08-18 09:50:12
whois example.com

Domain Name: EXAMPLE.COM
Registry Domain ID: 2336799_DOMAIN_COM-VRSN
Registrar: EXAMPLE REGISTRAR, INC.
Registrar WHOIS Server: whois.example-registrar.com
Registrar URL: http://www.example-registrar.com

Updated Date: 2024-07-01T12:34:56Z
Creation Date: 1995-08-13T04:00:00Z
Registry Expiry Date: 2026-08-13T04:00:00Z
Name Server: NS1.EXAMPLE.COM
Name Server: NS2.EXAMPLE.COM
Registrant Organization: Example Corp
Registrant Country: US
DNSSEC: unsigned

evidence/dig_example.com.txt
2025-08-18 09:52:03
dig +noall +answer example.com A
example.com. 3600 IN A 192.0.2.10

dig +noall +answer example.com NS
example.com. 3600 IN NS ns1.example.com.
example.com. 3600 IN NS ns2.example.com.

dig +noall +answer _dmarc.example.com TXT
_dmarc.example.com. 3600 IN TXT "v=DMARC1; p=none; rua=mailto:dmarc@example.com"

evidence/crtsh_example.com.txt
2025-08-18 09:55:21
crt.sh search for %.example.com

Found certificates:

dev.example.com — Issued: 2025-06-15 — Expires: 2026-06-14

www.example.com
 — Issued: 2024-09-01 — Expires: 2025-09-01

mail.example.com — Issued: 2025-01-10 — Expires: 2026-01-09

Notes: dev.example.com certificate indicates a public subdomain not listed in DNS zone transfer.

evidence/amass_example.com.txt
2025-08-18 10:05:34
amass enum -d example.com -o evidence/amass.txt

Found subdomains:
dev.example.com
staging.example.com
api.example.com
www.example.com

mail.example.com

Passive sources:

crtsh: dev.example.com

VirusTotal: staging.example.com

DNS brute force: api.example.com

evidence/sublist3r_example.com.txt
2025-08-18 10:08:12
sublist3r -d example.com -o evidence/sublist3r.txt

Subdomain Enumeration Results:
www.example.com

api.example.com
shop.example.com
dev.example.com

Total Unique Subdomains Found: 4

evidence/shodan_203.0.113.5.txt
2025-08-18 10:00:00
shodan host 203.0.113.5

Host: 203.0.113.5
Organization: Example Hosting
OS: Linux 4.x
Open Ports:
22/tcp OpenSSH 7.4p1 (protocol 2.0)
80/tcp Apache httpd 2.4.18
443/tcp nginx 1.14.0
Banner snippets:
SSH-2.0-OpenSSH_7.4
Server: Apache/2.4.18 (Ubuntu)

Notes: SSH accessible; hosting provider appears to be Example Hosting.

evidence/masscan_192.0.2.0-24.txt
2025-08-18 10:12:43
masscan 192.0.2.0/24 -p1-65535 --rate=1000 -oG evidence/masscan.gnmap

Masscan report

Host: 192.0.2.5 Ports: 22/open/tcp////,80/open/tcp////,443/open/tcp////,8080/open/tcp////
Host: 192.0.2.10 Ports: 80/open/tcp////,443/open/tcp////
Host: 192.0.2.50 Ports: 22/open/tcp////

evidence/nmap_192.0.2.10.txt
2025-08-18 10:15:02
nmap -sC -sV -p22,80,443,8080 192.0.2.10 -oN evidence/nmap_192.0.2.10.txt

Starting Nmap 7.92 ( https://nmap.org
 )
Nmap scan report for 192.0.2.10
Host is up (0.0010s latency).
PORT STATE SERVICE VERSION
22/tcp open ssh OpenSSH 7.4p1 Debian 10 (protocol 2.0)
80/tcp open http Apache httpd 2.4.18 ((Ubuntu))
| http-title: Example Domain
|_Requested resource was /, returned 200
443/tcp open ssl/http nginx 1.14.0
| ssl-cert: Subject: commonName=www.example.com

8080/tcp open http Apache Tomcat/Coyote JSP engine 1.1

Service detection performed. 4 services scanned.

evidence/whatweb_www_example_com.txt
2025-08-18 10:18:40
whatweb http://www.example.com
 -v

http://www.example.com
 [200 OK] Apache, PHP, jQuery, Google Analytics, WordPress
Headers:
Server: Apache/2.4.18 (Ubuntu)
X-Powered-By: PHP/7.2.24
WordPress: version 5.2.4 detected

evidence/ffuf_example_com.txt
2025-08-18 10:25:11
ffuf -u http://www.example.com/FUZZ
 -w /usr/share/wordlists/dirb/common.txt -t 20 -o evidence/ffuf.txt

[10:25:11] Starting ffuf
Found:
/admin Status: 200, Size: 4521
/.git Status: 403, Size: 20
/robots.txt Status: 200, Size: 48
/wp-login.php Status: 200, Size: 4023

Notes: /admin and /wp-login.php reachable — further brute force or auth testing only if in-scope.

evidence/maltego_summary.txt
2025-08-18 10:30:00
Maltego graph export (summary):

Entities found:

example.com (Domain)

www.example.com
 (A record -> 192.0.2.10)

dev.example.com (A record -> 192.0.2.20)

mail.example.com (MX -> mail server 192.0.2.30)

Contact email: admin@example.com
 (from LinkedIn/OSINT transform)

Transforms run:

DNS to A records

Certificate to subdomains

WHOIS to registrant data

Export note: Graph PNG saved as evidence/maltego_graph.png

evidence/slack_friendly_log_table.txt
2025-08-18 10:35:00

Timestamp	Tool	Finding
2025-08-18 10:00:00	Shodan	Exposed SSH on 203.0.113.5 (OpenSSH 7.4)
2025-08-18 10:05:34	Amass	Subdomain: dev.example.com
2025-08-18 10:12:43	Masscan	192.0.2.5 has ports 22,80,443,8080 open
2025-08-18 10:18:40	WhatWeb	WordPress 5.2.4 detected on www.example.com

2025-08-18 10:25:11	FFUF	Found /admin and /wp-login.php on www.example.com

evidence/screenshots_notes.txt
2025-08-18 10:40:00
Screenshots taken:

Maltego graph (evidence/maltego_graph.png)

Shodan host page (evidence/shodan_203.0.113.5.png)

FFUF results terminal screenshot (evidence/ffuf_ww.png)

Nmap output showing Tomcat on port 8080 (evidence/nmap_192.0.2.10.png)
