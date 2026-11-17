# Incident Response Lifecycle Simulation — Phishing & Malware Investigation

> Hands-on incident response lab using Kali Linux, Ubuntu, Wireshark, and ClamAV to investigate security threats, analyze network traffic, perform containment, and verify system recovery.

**Hands-on cybersecurity lab | Kali Linux · Ubuntu · Wireshark · ClamAV · VMware Workstation**

## Overview

Completed a controlled incident-response exercise that simulated a phishing-related event and an antivirus detection within an isolated two-VM lab. I configured the environment, collected network and endpoint evidence, assessed the incident, and demonstrated containment, eradication and recovery using the NIST incident-response lifecycle.

**Outcome:** Successfully captured HTTP evidence, detected a harmless EICAR antivirus test file with ClamAV, isolated the Ubuntu VM, removed the test file and restored connectivity. This was a **training simulation**—not a real credential theft or malware compromise.

**[View the complete 8-page PDF report with screenshots](Report.pdf)**

## Lab architecture

```text
              VMware VMnet1 — Host-only
                  192.168.50.0/24
                          |
            +-------------+-------------+
            |                           |
      Kali Linux                 Ubuntu Desktop
      192.168.50.10              192.168.50.20
      Lab HTTP server,           Simulated victim,
      Wireshark capture          log review, ClamAV
```

## Tools and technologies

| Technology | Purpose |
|---|---|
| VMware Workstation / VMnet1 | Isolated virtual network and test endpoints |
| Kali Linux | Hosted a **training-only** password-reset page; captured HTTP traffic |
| Ubuntu Linux | Investigated network connections, local logs and antivirus behavior |
| Wireshark | Inspected HTTP requests and response status codes |
| ClamAV and EICAR | Verified detection of a benign antivirus test signature |
| Linux utilities | `ss`, `journalctl`, `nmcli`, `ping` and Python's built-in HTTP server |

## Investigation workflow

1. **Preparation:** Configured host-only VMware networking, static IPv4 addresses and connectivity tests.
2. **Detection and analysis:** Inspected a lab-owned password-reset page, an HTTP `GET /` request returning `200 OK`, journal events and ClamAV output.
3. **Containment:** Disconnected Ubuntu's lab network adapter and observed loss of connectivity.
4. **Eradication:** Removed the EICAR test file and checked the relevant target with ClamAV.
5. **Recovery:** Reactivated the adapter, restored the static IP and verified four successful ping replies.
6. **Post-incident activity:** Documented scope, severity, screenshots, limitations and recommendations.

## Key findings

- Wireshark captured traffic from `192.168.50.20` to `192.168.50.10` and an HTTP `200 OK` response.
- ClamAV detected the **EICAR test signature**, not real malware.
- Observed severity was **low** because activity was intentional and isolated.
- Log evidence showed administrative activity; no unauthorized privilege escalation was established.
- Network isolation and restoration were verified with connectivity tests.

## Evidence

The [PDF report](Report.pdf) includes the incident summary, NIST lifecycle mapping, scope notes, and **12 screenshot exhibits** covering network setup, HTTP traffic, system logs, antivirus detection, containment, eradication and recovery.

**Evidence limitations:** Some original captures do not display a student ID/date-time overlay. A separate `.pcapng` file and a distinct browser view were not embedded in the report; do not treat the screenshots as a substitute for those files. Student ID was redacted from this public portfolio copy.

## Skills demonstrated

`Incident Response` · `NIST IR Lifecycle` · `Network Traffic Analysis` · `Wireshark` · `Linux Log Analysis` · `Endpoint Detection` · `Containment & Recovery` · `Technical Reporting`

---
*Educational lab using an isolated test environment. No real phishing emails, stolen credentials or active malware were used.*