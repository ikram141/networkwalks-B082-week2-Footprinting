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




## 🧪 Phase 2: GHDB (Google Hacking Database)

---

### Task 2a: Security Cameras
**Dorks Used:** Multiple webcam dorks  
**Total Live Cameras Found:** 9

| No. | Link | Relevant Dork |
|-----|------|---------------|
| 1 | `http://109.233.191.130:8080/` | `intitle:"webcamXP" inurl:8080` |
| 2 | `https://www.shodan.io/host/184.57.102.6#5400` | `intitle:"webcamXP 5" inurl:8080 'Live'` |
| 3 | `http://75.149.26.30:1024/?src=1&mode=0` | `intitle:"webcamXP 5" -download` |
| 4 | `https://www.shodan.io/host/184.57.102.6` | `intitle:"yawcam" "It's a webcam!" "user" "pass"` |
| 5 | `http://n3enm.dyndns.org:8888/` | `intitle:"Webcam" inurl:WebCam.htm` |
| 6 | `http://99.114.240.169:8080/` | `intitle:"webcamXP 5" inurl:admin.html` |
| 7 | `http://85.93.53.175:8080/gallery.html?page=6` | `intitle:"WEBCAM 7" -inurl:/admin.html` |
| 8 | `http://95.255.183.164:8080/multi.html` | `intitle:"WEBCAM 7" -inurl:/admin.html` |
| 9 | `http://62.202.21.238:8081/` | `intitle:"webcamXP" inurl:8080` |

---

### Task 2b: Mathematics eBooks (PDF)
**Dork Used:** `intitle:index.of "parent directory" mathematics pdf`  
**Total PDFs Found:** 4

| No. | Link |
|-----|------|
| 1 | `http://erewhon.superkuh.com/library/Math/A%20Concise%20Introduction%20to%20Mathematical%20Logic_%203rd%20ed_%20Wolfgang%20Rautenberg_%202009.pdf` |
| 2 | `http://erewhon.superkuh.com/library/Math/An%20Introduction%20to%20Tensors%20and%20Group%20Theory%20for%20Physicists_%20Nadir%20Jeevanjee_%202011.pdf` |
| 3 | `http://erewhon.superkuh.com/library/Math/Direct%20Methods%20in%20the%20Calculus%20of%20Variations_%20Enrico%20Giusti_%202005.pdf` |
| 4 | `http://erewhon.superkuh.com/library/Math/Learning%20and%20Teaching%20Mathematics%20Simulations_%20Dieter%20Ross_%202011.pdf` |

## 🧪 Phase 3: Maltego — Email Harvesting

### Task: Find Email Addresses Related to Target Domain

#### 📖 Definition
Maltego is an OSINT (Open Source Intelligence) tool used for gathering information about a target. It can find email addresses, domains, and relationships between entities.

#### 🖥️ Steps
1. Open Maltego and create a new graph.
2. Add a **Domain** entity and set it to `networkwalks.com`.
3. Run email-related transforms to harvest email addresses.

#### 📊 Result
- **Emails Found:** (Count likho, e.g., 5-10)
- **Status:** Error encountered (Error ID: 586302bc0c0e492397d260b746433af5). Resolution in progress.

#### 📸 Screenshot
<img width="837" height="319" alt="email domain" src="https://github.com/user-attachments/assets/2665bc4c-ba2e-44b2-9301-50afe258d3bb" /><img width="1920" height="1080" alt="maltego" src="https://github.com/user-attachments/assets/ff4e322d-f90d-4bc0-b2a1-857c4ebd8a87" />



## 🧪 Phase 4: theHarvester — Email Harvesting

### Task: Gather Emails & Subdomains

#### 📖 Definition
`theHarvester` is a passive reconnaissance tool that collects emails, subdomains, and hosts from public sources like search engines, PGP key servers, and Shodan.

#### 🖥️ Command
```bash
theHarvester -d microsoft.com -l 500 -b baidu
```

📊 Result

· Target Domain: microsoft.com
· Source Used: Baidu
· Emails Found: (Count likho)
· Hosts/Subdomains Found: (Count likho)

📸 Screenshot
<img width="1920" height="1080" alt="50" src="https://github.com/user-attachments/assets/50bd590d-4423-41a1-9218-159fe9f0960f" />
<img width="1920" height="1080" alt="theharvester" src="https://github.com/user-attachments/assets/5e29446c-2f4c-41b6-b522-0b380ff05180" />


🧪 Phase 5: Zenmap — Network Scanning

Task: Ping Scan on Local Network

📖 Definition

Zenmap is the official GUI for Nmap. A ping scan (-sn) discovers live hosts on a network without scanning ports.

🖥️ Command

```bash
nmap -sn 10.70.91.246
```

📊 Result

· Target IP: 10.70.91.246
· Status: Host is up
· Time: 2.12 seconds

📸 Screenshot

<img width="1920" height="1080" alt="namp1" src="https://github.com/user-attachments/assets/bc0207a8-4f73-4c57-ba13-963eae70dce1" />
<img width="821" height="706" alt="nmap" src="https://github.com/user-attachments/assets/abae1e9a-3c44-478c-b61d-3d2e04deec7c" />

👨‍💻 Author

· Name: Ikram Ullah
· Batch: B082
· GitHub: ikram141
· LinkedIn: Ikram Ullah
