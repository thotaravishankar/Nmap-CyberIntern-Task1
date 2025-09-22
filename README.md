# Nmap-CyberIntern-Task1


Task 1 — Scan Your Local Network for Open Ports

Cyber Security Internship — Network Reconnaissance (Nmap)

Objective:
      Discover open ports and services on devices in your local network to understand network exposure and potential security risks.

Tools:
Nmap - network mapper
Wireshark — packet capture & analysis (
OS used: kali linux

Environment / Network Details(these details are not true . for example purpose only):
  Machine hostname: student-pc
  OS & version: Ubuntu 22.04 LTS
  Local IP / subnet detected: 192.168.1.21/24
  Target IP range scanned: 192.168.1.0/24

Setup & Installation:

Install Nmap:
sudo apt update && sudo apt install nmap

Verify Nmap:
nmap --version


Commands I Ran in kali linux:
sudo nmap -sS 192.168.1.0/24 -oN scan_results.txt

sudo nmap -sS -sV --top-ports 1000 192.168.1.0/24 -oN scan_top_ports.txt

UDP scan for one host (takes longer):

sudo nmap -sU 192.168.1.10 -oN udp_scan_host.txt


Open Ports:
80/tcp (http) — Router admin panel
443/tcp (https) — Secure router interface
Host: 192.168.1.10 (Linux Server)

Open Ports:

22/tcp (ssh) — Secure Shell service

3306/tcp (mysql) — MySQL database

Host: 192.168.1.15 (Windows Laptop)

Open Ports:

445/tcp (microsoft-ds) — SMB file sharing

139/tcp (netbios-ssn) — NetBIOS

Host: 192.168.1.25 (IoT Camera)

Open Ports:

554/tcp (rtsp) — Real Time Streaming Protocol

80/tcp (http) — Camera web interface

Risk Assessment

22/tcp (SSH) — Risk of brute-force login attempts if weak passwords are used.

3306/tcp (MySQL) — Should not be exposed unless required; risk of database leakage.

445/tcp (SMB) — High-risk; many known exploits (e.g., EternalBlue).

80/tcp (HTTP) — If outdated firmware/software, could have vulnerabilities.

RTSP (554) — May expose live video streams without proper authentication.

Mitigation Recommendations

Close unnecessary ports or restrict them with firewalls.Use strong authentication (SSH keys instead of passwords).Update services regularly (patch management).Restrict access by IP (e.g., allow SSH only from trusted admin system).Isolate IoT devices on separate VLAN to reduce attack surface.

Wireshark Observations:

Captured multiple TCP SYN packets during scan. Hosts replied with SYN-ACK on open ports, and RST on closed ports. Some hosts showed ICMP unreachable messages for filtered UDP ports.
