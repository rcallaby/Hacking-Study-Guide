## Introduction: Capture The Flag (CTF) Study Section

Welcome to the **Capture The Flag (CTF)** section of your Hacking Study Notes repository. This directory serves as a centralized, structured knowledge base for tracking challenges, documenting exploitation methodologies, and refining the offensive security techniques learned across various platforms.

Whether you are honing foundational Linux command-line skills, reversing binaries, analyzing web application vulnerabilities, or executing multi-step privilege escalations, this section documents the practical application of cybersecurity theory into repeatable workflows.


### Repository Structure & Target Environments

The study notes in this section are organized by the platforms and lab environments used for hands-on practice:

* Building VMs - Notes and configuration guides on provisioning, hardening, and attacking local lab environments (e.g., VirtualBox, VMware, custom vulnerable Vagrant boxes, and isolated Docker networks) to simulate real-world enterprise topologies.
* OverTheWire - Walkthroughs and command references for wargames (such as *Bandit*, *Leviathan*, and *Natas*) focused on Linux command-line proficiency, SSH tunneling, file permissions, and basic web vulnerabilities.
* picoCTF - Solutions and methodology breakdowns for beginner-to-advanced challenges spanning **Cryptography**, **Reverse Engineering**, **Binary Exploitation**, **Web Exploitation**, and **Forensics**.
* VulnHub - End-to-end penetration testing write-ups for boot2root VMs. This includes systematic enumeration workflows (Nmap, Gobuster), vulnerability assessment, initial access vectors, and kernel or misconfiguration-based privilege escalation (Linux/Windows).
* HackerSmarterLabs - Targeted lab notes and attack-path documentation focusing on specialized security concepts, defensive evasion, and structured exploitation scenarios.


### Methodology & Documentation Standard

To ensure these notes remain a valuable reference for future study, technical instruction, or professional engagements, each challenge or lab write-up follows a consistent documentation pattern:

1. **Objective & Scope:** What is the target, what are the constraints, and what is the primary learning goal?
2. **Reconnaissance & Enumeration:** Detailed logs of port scans, service fingerprinting, directory brute-forcing, and information gathering.
3. **Vulnerability Analysis:** The hypothesized weakness, source code review (if applicable), or misconfiguration identified during assessment.
4. **Exploitation & Access:** Step-by-step reproduction of the exploit, payload delivery, or credential harvesting required to achieve initial access.
5. **Privilege Escalation & Remediation:** The path to root/SYSTEM access, root-cause analysis of the vulnerability, and concrete defensive recommendations to secure the environment.
