Week 2 - Phase 1: Footprinting with Kali Tools
## Cybersecurity & Ethical Hacking Project (Batch B082)

## 📜 Disclaimer

> **Warning:** This project is for **educational purposes only**. All activities were performed on **networkwalks.com** with **written permission** from the owner as part of the Networkwalks Cybersecurity Internship (Batch B082).  
> Unauthorized use of these techniques on systems you do not own is **illegal** and may lead to criminal charges.

## 📌 Project Overview
This phase demonstrates **passive reconnaissance (footprinting)** using Kali Linux tools. The goal is to collect publicly available information about a target domain (`networkwalks.com`) without directly interacting with its systems.


## 🛠️ Tools Used
| Tool | Purpose |
|------|---------|
| `whois` | Domain ownership & registrar info |
| `whatweb` | Web technologies & version detection |
| `nslookup` | DNS resolution to IP |
| `wafw00f` | WAF detection |
| `dnsrecon` | DNS record enumeration |


## 🔍 Step-by-Step Guide

### Step 1: whois — Domain Registration Lookup

#### 📖 Definition
`whois` queries domain registration records to reveal the owner, registrar, creation/expiry dates, and name servers. This helps identify the hosting provider and potential points of contact.

#### 🖥️ Command
```bash
whois networkwalks.com

📊 Result

· Registrar: GoDaddy.com, LLC
· Creation Date: 2019-11-06
· Registry Expiry Date: 2027-11-06
· Name Servers: NS6135.HOSTGATOR.COM, NS6136.HOSTGATOR.COM
· Domain Status: clientDeleteProhibited, clientRenewProhibited, clientTransferProhibited, clientUpdateProhibited

📸 Screenshot
<img width="1920" height="1019" alt="whois1" src="https://github.com/user-attachments/assets/6a52b51d-4abc-4c55-b22f-a70cb6adc46e" />


Step 2: whatweb — Web Technology Fingerprinting

📖 Definition

whatweb identifies the CMS, frameworks, web server, and other technologies used by a website. This information is used to find known vulnerabilities in the technology stack.

🖥️ Command

```bash
whatweb networkwalks.com
```

📊 Result

· CMS: WordPress 7.0.4
· Framework: Bootstrap 7.0.4
· Web Server: Apache
· Email: info@networkwalks.com
· IP Address: 192.232.216.135
· HTTP Headers: permissions-policy, referrer-policy, upgrade-insecure-requests

📸 Screenshot
<img width="1920" height="1019" alt="whatweb" src="https://github.com/user-attachments/assets/facd38c8-acb2-4b68-b483-f15a3e377841" />

Step 3: nslookup — DNS Resolution

📖 Definition

nslookup translates a domain name into its corresponding IP address. This reveals the server's location and infrastructure, which is used for further scanning and targeting.

🖥️ Command

```bash
nslookup networkwalks.com
```

📊 Result

· Domain: networkwalks.com
· IP Address: 192.232.216.135
· DNS Server: 192.168.153.2

📸 Screenshot

<img width="1920" height="1019" alt="nslookup" src="https://github.com/user-attachments/assets/950a9240-16cb-48ce-b88a-3bff071fb3ad" />

Step 4: wafw00f — WAF Detection

📖 Definition

wafw00f sends specific HTTP requests to a target and analyzes responses to detect if a Web Application Firewall (WAF) is protecting the website. This is critical for planning future attacks, as some techniques are blocked by WAFs.

🖥️ Command

```bash
wafw00f networkwalks.com
```

📊 Result

· WAF Detected: ModSecurity (SpiderLabs)
· Requests Made: 2

📸 Screenshot


<img width="1920" height="1019" alt="wafw00f" src="https://github.com/user-attachments/assets/fbce9299-e3c7-43a0-ad82-c2f67305e239" />

Step 5: dnsrecon — DNS Enumeration

📖 Definition

dnsrecon queries DNS records (A, MX, NS, TXT, SRV) to map the target's infrastructure, including mail servers, name servers, and SPF records. This helps identify potential entry points and attack vectors.

🖥️ Command

```bash
dnsrecon -d networkwalks.com
```

📊 Result

· SOA Record: ns6135.hostgator.com (50.87.144.87)
· NS Records: ns6135.hostgator.com, ns6136.hostgator.com
· Bind Version: 9.16.23-RH
· MX Record: mail.networkwalks.com (192.232.216.135)
· A Record: networkwalks.com (192.232.216.135)
· TXT Records:
  · google-site-verification=...
  · v=spf1 +a+mx +ip4:50.87.144.87 +include:websitewelcome.com ~all

📸 Screenshot

<img width="1920" height="1019" alt="dnsrecon" src="https://github.com/user-attachments/assets/a72f86fe-5e8e-4793-a8e0-b31b044c5fa5" />

📂 Project Structure

```
networkwalks-B082-week2-Footprinting/
├── README.md
├── screenshots/
│   ├── 1-whois.png
│   ├── 2-whatweb.png
│   ├── 3-nslookup.png
│   ├── 4-wafw00f.png
│   └── 5-dnsrecon.png
├── outputs/
│   ├── whois.txt
│   ├── whatweb.txt
│   ├── nslookup.txt
│   ├── wafw00f.txt
│   └── dnsrecon.txt
└── LICENSE
```

---

🔐 Security & Ethics

This lab was performed in a controlled environment with explicit permission.
All findings are based on publicly available information. No systems were exploited or harmed.

---

💡 Key Learnings

· Footprinting is the foundation of ethical hacking.
· Public data reveals more than expected (domain owner, hosting, WAF).
· WAF detection helps plan future assessments.
· DNS enumeration provides a map of the target's infrastructure.

---

👨‍💻 Author

· Name: Ikram Ullah
· Batch: B082
· GitHub: ikram141
· LinkedIn: Ikram Ullah
