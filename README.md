# Web Reconnaissance & Credential Harvesting Lab

A four-part hands-on penetration testing exercise covering webserver reconnaissance, social engineering-based credential harvesting with SIEM detection, secure FTP server configuration, and credential cracking via dictionary attack.

## Background

This lab walks the full offense/defense loop from a single point of view: performing reconnaissance and attacks as a penetration tester, while also standing up the detection side (Splunk SIEM) to observe what those same attacks look like from a defender's perspective.

## Lab Environment

- Kali Linux VM (attacker)
- Windows Server 2016 (target — FTP server)
- Detection Lab (Domain Controller, Windows Event Forwarding, Windows 10, Splunk logger)

## Contents

- [`01-webserver-reconnaissance.md`](./01-webserver-reconnaissance.md) — Skipfish-based web application security reconnaissance against a target webserver, including vulnerability analysis (directory traversal, DOM-based XSS, SSL/TLS downgrade risk)
- [`02-credential-harvesting-siem-detection.md`](./02-credential-harvesting-siem-detection.md) — cloning a login page with the Social Engineering Toolkit (SET), harvesting submitted credentials, and detecting the attack via Splunk SIEM log analysis
- [`03-ftp-server-hardening.md`](./03-ftp-server-hardening.md) — building and hardening an FTP server on Windows Server 2016: user isolation, virtual directories, firewall rule configuration
- [`04-credential-cracking-dictionary-attack.md`](./04-credential-cracking-dictionary-attack.md) — scanning for and exploiting the FTP service using Nmap and a Hydra-based dictionary attack

## Tools

Skipfish, Social Engineering Toolkit (SET), Splunk, Windows Server 2016 FTP role, Nmap, Hydra

## Disclaimer

Completed as a personal hands-on lab exercise in an isolated virtual lab environment — no production systems or third-party targets involved.
