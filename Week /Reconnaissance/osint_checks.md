PLANNING & AUTHORIZATION

Confirm scope and written authorization for the domain(s) you will investigate.

Note date/time, team contacts, and allowed techniques in the Google Doc.

INITIAL DOMAIN INFO
3) WHOIS lookup: whois example.com → save registrar, creation/expiry, name servers, registrant email (if available).
4) Passive DNS / Certificate search: crt.sh?q=%.example.com (record results) and save cert names.
5) DNS records: dig @8.8.8.8 example.com ANY +short and dig +noall +answer example.com A/NS/MX/TXT.

SUBDOMAIN ENUMERATION
6) Run Amass: amass enum -d example.com -o evidence/amass.txt
7) Run Sublist3r: sublist3r -d example.com -o evidence/sublist3r.txt
8) Use crt.sh & Censys for additional names; consolidate and deduplicate.

SERVICE & PORT DISCOVERY
9) Shodan search (web/CLI): shodan host 192.0.2.1 or via web UI; record exposed ports/services and banners.
10) Run masscan/nmap on discovered IPs (respect scope): masscan -p1-65535 <ip-range> --rate=1000 -oG evidence/masscan.gnmap; then nmap -sV -sC -p<ports> <ip> -oA evidence/nmap/<ip>.

TECH STACK & FINGERPRINTING
11) Wappalyzer / WhatWeb / builtwith: whatweb http://example.com
 -v and browser Wappalyzer to capture frameworks, server, CMS, JS libs.
12) Capture HTTP headers and robots.txt: curl -I http://example.com
 and curl http://example.com/robots.txt

WEB APP MAPPING & ENDPOINTS
13) Directory bruteforce: ffuf -u http://example.com/FUZZ
 -w /usr/share/wordlists/dirb/common.txt -o evidence/ffuf.txt
14) Crawl with Burp/OWASP ZAP (passive only unless in-scope) to map endpoints and parameters.

WHOLE-ASSET MAPPING
15) Correlate subdomains → IPs → open services → owner/org (use Shodan/WHOIS) and build a CSV or sheet.
16) Create asset map diagram in Google Docs (or draw.io) linking domains, subdomains, IPs, services.

SOCIAL & INFRASTRUCTURE OSINT
17) Search social platforms and LinkedIn for employee names; note role/title that could help pivot.
18) Google dorking: filetype:sql site:example.com OR inurl:admin OR intitle:"login" site:example.com — record interesting hits.

MALTEGO USAGE
19) Run Maltego transforms on domain & company names; capture subdomain transform outputs and export graph as PNG/PDF.
20) Export key nodes (domains, IPs, emails) into your Google Doc.

LOGGING & EVIDENCE
21) Use a Slack-friendly log table in Google Docs:
Timestamp | Tool | Finding
YYYY-MM-DD HH:MM:SS | Shodan | Exposed SSH on 192.168.1.50
22) Save raw outputs (nmap, amass, sublist3r, shodan, ffuf) in evidence/ with filenames and a README index.
23) Take screenshots of Maltego graph, Shodan host page, and any interesting web pages.

VALIDATION & PRIORITIZATION
24) Verify critical findings manually (e.g., login pages reachable, services actually responding).
25) Prioritize assets by exposure & business impact; tag as Critical/High/Medium/Low.

REPORT PREPARATION
26) Summarize findings in 50-word recon summary and place at top of Google Doc.
27) Add methodology, tools, commands used, timestamps, and remediation suggestions.

ETHICS & OPSEC
28) Never exploit or auth-bypass unless explicitly in scope and authorized.
29) Redact sensitive personal info before sharing externally; secure Google Doc access.
30) Record and retain chain-of-custody for evidence; archive encrypted when storing offsite.

COMMON COMMANDS (examples)
31) whois example.com
32) dig +noall +answer example.com A NS MX TXT
33) amass enum -d example.com -o evidence/amass.txt
34) sublist3r -d example.com -o evidence/sublist3r.txt
35) shodan host 203.0.113.5
36) whatweb http://example.com
 -v
37) ffuf -u http://example.com/FUZZ
 -w /usr/share/wordlists/dirb/common.txt
38) masscan -p1-65535 192.0.2.0/24 --rate=1000 -oG evidence/masscan.gnmap
39) nmap -sC -sV -p22,80,443,8080 192.0.2.5 -oA evidence/nmap/192.0.2.5

CLEANUP & FOLLOW-UP
40) Review Google Doc with a peer; remove any accidental sensitive disclosures.
41) Schedule re-scan or continuous monitoring for high-risk assets.
