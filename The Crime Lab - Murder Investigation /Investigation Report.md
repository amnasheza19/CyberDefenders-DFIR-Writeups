# 📱 Mobile Forensics: Murder Crime Investigation 

## 📌 Platform  
CyberDefenders DFIR Lab : Crime Lab

---

# 🧾 Scenario Overview
A murder investigation revealed that the victim’s **Android phone might** contain key evidence related to the events before the incident. Witnesses reported that the victim had recently been involved in **online trading**, accumulated **significant debt**, and was avoiding calls from creditors.

- Financial activity
- Online trading
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

Trading application package name: **com.ticno.olymptrade**

Application SHA256: **4f168a772350f283a1c49e78c1548d7c2c6c05106d8b9feb825fdc3466e9df3c**

This confirms that the victim was using the **Olymp Trade trading application** for trading activities.

---

## 2️⃣ Debt Amount Identification
Using ALEAPP:

SMS Messages → Message Content

Analysis of the SMS database revealed a threatening message from an unknown number demanding repayment of money owed.

Message sender: **+201172137258**

The sender demanded repayment of **250,000 Egyptian Pounds**, indicating the victim was under financial pressure.

---

## 3️⃣ Creditor Identification
Using ALEAPP:

Contacts Database → Contact Mapping

The phone number identified in the SMS message was cross-referenced with the device's contact list.

The number **+201172137258** corresponds to **Shady Wahab**, confirming that he was the individual demanding repayment.

---

## 4️⃣ Victim Location Identification
Using ALEAPP:

Recent Tasks → Google Maps Activity

Android system artifacts showed that **Google Maps** was recently active on the device.

Timestamp recorded: **September 20, 2023 – 23:50:29**

The application snapshot revealed a highlighted location.

**The Nile Ritz-Carlton, Cairo**

This indicates the victim was located near this hotel shortly after leaving his residence.

---

## 5️⃣ Intended Travel Destination
Using ALEAPP:

Discord Chat Logs → Conversation Analysis

The victim had been communicating with contact named **rob1ns0n** regarding travel plans.

The conversation referenced:

- A booked flight on **October 1, 2023**
- A meeting arranged upon arrival
- The meeting place : The Mob Museum.

The meeting location mentioned in the conversation was verified through OSINT research.

**Las Vegas, Nevada**

This indicates the victim intended to travel to the United States.

---

## 6️⃣ Meeting Location Identification
Using Discord Chat Logs

The same conversation revealed the specific meeting point discussed between the victim and the contact.

**The Mob Museum – Las Vegas**

The contact instructed the victim to call after arriving at the location.

This suggests the victim had arranged to meet someone at this venue.

---

# ⏱ Investigation Timeline

| Stage | Activity |
|------|---------|
| Financial Activity | Victim invested money using Olymp Trade |
| Debt Conflict | Creditor demanded repayment of 250,000 EGP |
| Communication Avoidance | Victim ignored multiple calls |
| Travel Planning | Flight booked for October 1, 2023 |
| Movement | Victim traveled to Nile Ritz-Carlton |
| Planned Meeting | Meeting scheduled at The Mob Museum |

---

# 🚨 Investigation Insights
**Severity Level:** HIGH

Key findings include:

- Significant financial debt
- Threatening communication from creditor
- Suspicious travel plans
- Meeting arranged with unknown contact
- Potential connection between debt and victim's movements

These findings provide valuable leads that investigators can use to continue the case investigation.

---

# 🛡 Forensic Value of Evidence
The mobile device provided crucial evidence that allowed investigators to reconstruct the victim’s activities.

Artifacts recovered included:

- Installed application data  
- SMS communications  
- Contacts database  
- Google Maps activity logs  
- Discord chat conversations  

Correlating these artifacts enabled us to **build a timeline of events leading up to the incident**.

---

# 🧠 Skills Demonstrated
- Mobile device forensics  
- Android artifact analysis  
- Timeline reconstruction  
- SMS and chat log investigation  
- Location data analysis  
- Evidence correlation  
- Digital forensic reporting  

---

# 📚 Conclusion
This investigation highlights the importance of **mobile device forensics in modern criminal investigations**. By analyzing artifacts extracted from the victim’s Android phone, we were able to uncover critical information about the victim’s financial situation, communications, movements, and travel plans.

Using **ALEAPP**, multiple artifacts were parsed and correlated to reconstruct the victim’s timeline. The analysis revealed a substantial financial debt, threatening communications, and a planned meeting in Las Vegas.

This lab demonstrates how digital artifacts from mobile devices can provide valuable insights and serve as key evidence in forensic investigations.

---

🔗 Lab Source  
https://cyberdefenders.org/blueteam-ctf-challenges/achievements/shezasheriff08/the-crime/
 












