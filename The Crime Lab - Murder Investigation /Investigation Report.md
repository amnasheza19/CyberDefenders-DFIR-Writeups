# 📱 Mobile Forensics Investigation: Crime Lab DFIR Challenge

## 📌 Platform  
CyberDefenders DFIR Lab : Crime Lab

---

# 🧾 Scenario Overview
A murder investigation revealed that the victim’s **Android mobile device** may contain critical evidence related to the events leading up to the incident.

Witness statements suggested the victim had recently been involved in **financial trading activities**, had accumulated **significant debt**, and had been **avoiding calls from creditors**. Additionally, the victim had left home unexpectedly on **September 20, 2023**, without informing family members of their destination.

The device was extracted and provided for forensic analysis. Investigators were tasked with examining digital artifacts from the phone to reconstruct the victim’s activities and identify relevant leads.

Using mobile forensic techniques and artifact analysis, the goal of this investigation was to uncover evidence related to:

- Financial activity
- Suspicious communications
- Location data
- Social interactions
- Travel plans

---

# 🎯 Investigation Objectives
- Identify the trading application used by the victim  
- Determine the amount of debt owed  
- Identify the individual demanding repayment  
- Determine the victim’s location on September 20, 2023  
- Identify the victim’s travel destination  
- Determine the planned meeting location  

---

# 🛠 Tools Used
- ALEAPP (Android Logs Events And Protobuf Parser)
- Android artifact analysis
- OSINT verification for locations

---

# 🔍 Forensic Analysis & Findings

## 1️⃣ Trading Application Identification
Using ALEAPP:

Installed Applications → Application Metadata

The extracted Android filesystem was parsed to identify installed applications and their associated metadata. Android applications are uniquely identified using **package names** and can be verified using **cryptographic hashes**.

**Finding:**

Trading application package name:

