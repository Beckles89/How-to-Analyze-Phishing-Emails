**how to analyze phishing emails on a Virtual Machine in VirtualBox** — with **detailed steps, tools used, and skills learned**.

---

## **Repository Name**

`phishing-email-analysis-virtualbox`

---

## **Repository Description**

A step-by-step guide on how to safely analyze phishing emails within a secure virtual environment using VirtualBox. This project demonstrates setting up an isolated virtual machine, installing email analysis tools, examining email headers, detecting malicious attachments, and identifying phishing indicators. Includes lessons learned and skills developed during the process.

---

## **README.md Content**

````markdown
# Phishing Email Analysis in VirtualBox

## 📌 Overview
This repository documents the process of safely analyzing phishing emails inside an **isolated Virtual Machine** running in **VirtualBox**.  
The goal is to simulate a secure analysis environment to investigate suspicious emails without risking the host system.

---

## 🛠 Tools & Technologies Used
- **VirtualBox** – Virtualization platform
- **Ubuntu / Kali Linux VM** – Analysis operating system
- **Thunderbird / Evolution Mail Client** – Email inspection
- **Wireshark** – Network monitoring
- **PhishTool / Email Header Analyzer** – Header and metadata analysis
- **ClamAV** – Malware scanning
- **VirusTotal** – Online malware scanning and file analysis
- **OLEtools / PDFid** – Attachment analysis
- **Python** (optional) – Script-based email parsing

---

## 🖥 Virtual Machine Setup

### 1. Install VirtualBox
- Download and install [VirtualBox](https://www.virtualbox.org/wiki/Downloads) on your host machine.

### 2. Create a New Virtual Machine
- Select **Linux → Ubuntu 64-bit** or **Kali Linux**.
- Allocate at least:
  - **RAM:** 4 GB  
  - **CPU:** 2 cores  
  - **Disk Space:** 25 GB

### 3. Networking Configuration
- Use **NAT Network** or **Host-Only Adapter** to prevent direct exposure to the internet.
- This ensures the VM is **isolated** from the host and external networks.

---

## 📥 Installing Email Analysis Tools

Inside the VM:

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install thunderbird wireshark clamav python3-pip -y
pip3 install extract-msg
````

Optional security tools:

```bash
sudo apt install oletools pdfid
```

---

## 📧 Analyzing a Phishing Email

### Step 1: Open Email Safely

* Import the **.eml** file into Thunderbird.
* DO NOT click any links or download attachments without scanning first.

### Step 2: Examine Email Headers

* Use **View → Headers → All** in Thunderbird.
* Look for:

  * **"From" address** vs **Return-Path** mismatch
  * **Received** path anomalies
  * **SPF/DKIM/DMARC** failures

### Step 3: Check Links

* Hover over links (DO NOT CLICK).
* Copy and paste into a safe link scanner such as [VirusTotal](https://www.virustotal.com) or [URLScan.io](https://urlscan.io).

### Step 4: Analyze Attachments

* Save attachments to a test folder inside the VM.
* Scan with ClamAV:

  ```bash
  clamscan suspicious_file
  ```
* For Office documents:

  ```bash
  olevba suspicious.doc
  ```
* For PDFs:

  ```bash
  pdfid suspicious.pdf
  ```

### Step 5: Monitor Network Activity

* Use Wireshark to watch outbound connections when opening files in a sandbox.
* Filter suspicious traffic (`http`, `dns`, `tcp.port==443`).

---

## 🧠 Skills Learned

While working on this project, I developed:

1. **Virtualization Skills** – Configuring secure virtual environments for malware analysis.
2. **Email Forensics** – Extracting and interpreting email headers to detect spoofing.
3. **Malware Analysis Basics** – Identifying and scanning malicious attachments.
4. **Network Traffic Analysis** – Using Wireshark to detect suspicious connections.
5. **Cybersecurity Hygiene** – Working in isolated, non-persistent environments to prevent contamination.
6. **Tool Proficiency** – Using ClamAV, oletools, VirusTotal, and other forensic tools effectively.
7. **Threat Intelligence Skills** – Recognizing phishing tactics and attack indicators.

---

## ⚠️ Disclaimer

This project is for **educational purposes only**. All samples analyzed should be obtained from trusted, safe sources such as malware sample repositories designed for researchers.

---

## 📚 References

* [VirtualBox Documentation](https://www.virtualbox.org/manual/UserManual.html)
* [Email Header Analysis Guide](https://mxtoolbox.com/Public/Content/EmailHeaders/)
* [VirusTotal](https://www.virustotal.com)
* [Wireshark](https://www.wireshark.org/)

```
