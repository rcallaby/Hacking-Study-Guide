# Password OSINT

As a penetration tester, one of your primary objectives is to assess the security posture of your clients' systems and networks. A critical part of this process is password OSINT (Open-Source Intelligence): evaluating password policy strength, identifying weak points, and spotting risks that an attacker could exploit. This guide outlines a practical workflow for conducting password OSINT and highlights the tools commonly used in the field.

## Step-by-Step Process

### 1. Identify Your Target
Before beginning a password OSINT assessment, define the target clearly. This could be a single user, a department, or an entire organization. You should also establish the scope of the evaluation, such as whether you are reviewing password policies for one group or for the entire environment.

### 2. Gather Information
The next step is to collect publicly available information that could help identify or predict passwords. This may include usernames, email addresses, social media activity, public profiles, and historical breach data. Useful sources include search engines, social media platforms, and breach databases.

### 3. Analyze the Data
Once relevant information has been gathered, review it for weak patterns. Common indicators include reused passwords, predictable personal details such as birthdays or pet names, and credential reuse across multiple services. These patterns can reveal exploitable weaknesses in the target's password strategy.

### 4. Use Password-Cracking Tools
There are numerous tools available to test password strength under controlled conditions. These tools may use brute-force, dictionary, or rainbow-table techniques. Common examples include John the Ripper, Hashcat, and Aircrack-ng.

### 5. Generate Strong Passwords
A useful way to test password resilience is to generate new randomized passwords that are difficult to guess or reproduce. Password generators can help simulate stronger credentials for comparison and policy validation. Examples include LastPass and KeePass.

### 6. Test Password Strength
Once new passwords have been created, evaluate their strength using password-testing utilities. These tools provide insight into whether a password is likely to withstand brute-force or dictionary attacks. Popular examples include How Secure Is My Password and Password Meter.

### 7. Report Findings
Finally, document your findings in a clear, professional report. Include any discovered weaknesses, their potential impact, and recommended improvements to password policy, user education, and overall security posture.

Password OSINT is an essential skill in a penetration tester's toolkit. By identifying weaknesses in a target's password practices, you can help clients reduce the likelihood of compromise and improve their defensive posture. When performed carefully and ethically, password OSINT offers valuable insight into real-world security risks.

## Tools and Resources

### 1. Privacy-Preserving & Free Verification APIs
Before querying breach databases, it is important to confirm whether credentials or hashes have already been exposed without compromising privacy or violating security boundaries.

- Have I Been Pwned (HIBP) – Pwned Passwords API
  - Type: Free / Open API
  - Use case: Checking whether specific passwords appear in known data breaches.
  - Why it’s reliable: Built by Troy Hunt, it uses a k-Anonymity model. When querying a password hash, only the first 5 characters of the SHA-1 hash are sent to the API, and the local client matches the remainder. This means your plaintext password or full hash never leaves your system.

### 2. Open-Source Footprinting & Account Discovery Tools (Free / OSS)
Password OSINT often begins by mapping an individual's or organization's digital footprint to determine where credentials may be reused or where accounts exist.

- Holehe
  - Type: Open Source (GitHub) / Free
  - Use case: Checks whether an email address is linked to accounts across hundreds of websites, including social media, developer platforms, and forums, using unauthenticated API endpoints.
  - Pentest value: Useful for phase-zero OSINT to map an attack surface and identify shadow IT or personal accounts used by employees.

- Sherlock / Maigret
  - Type: Open Source (GitHub) / Free
  - Use case: Username OSINT across hundreds of social networks and technical platforms.
  - Pentest value: Helps correlate usernames to uncover profile reuse, password reuse patterns, and secondary contact vectors.

### 3. Repository & Code Leak Scanners (Free / OSS)
Credentials frequently appear in public code repositories, CI/CD logs, and misconfigured cloud storage or infrastructure.

- Gitleaks
  - Type: Open Source (GitHub) / Free
  - Use case: Fast, lightweight static analysis tool for detecting hardcoded secrets, API keys, and passwords in Git repositories or files.
  - Pentest value: Useful for reviewing client codebases or public GitHub/GitLab organizations for leaked internal credentials.

- TruffleHog
  - Type: Open Source (GitHub) / Free (with enterprise tiers)
  - Use case: Scans Git repositories (including history) and local filesystem locations for high-entropy secrets and verified credentials.
  - Pentest value: Helpful for identifying exposed secrets before they can be abused.

### 4. Aggregated Credential Intelligence Platforms (Inexpensive / Paid APIs)
For authorized assessments, professional credential intelligence platforms are often used to determine whether client-domain credentials have been exposed in third-party breaches.

- DeHashed
  - Type: Paid / Inexpensive API & Search Tiers
  - Use case: Search engine for indexed data breaches, leaks, and credentials.
  - Pentest value: Allows security testers to query specific corporate domains with explicit client authorization to determine whether employee credentials have appeared in prior breaches.

- Intelligence X (IntelX)
  - Type: Freemium / Paid API
  - Use case: Search engine and data archive indexing public data, darknet content, WHOIS records, pastebins, and document leaks.
  - Pentest value: Valuable for deep historical searches and tracking credential dumps or corporate leaks.

### 5. Local Hash Analysis & Auditing (Free / OSS)
When analyzing password strength or reviewing hash dumps obtained under authorized conditions, local auditing tools are essential.

- Hashcat & John the Ripper
  - Type: Open Source / Free
  - Use case: Advanced password recovery and hash auditing.
  - Pentest value: Considered the standard for evaluating password policy strength, complexity requirements, length, and reuse patterns using wordlists and rule sets in a controlled environment.

## Best Practices for Ethical Password OSINT

- Scope and Authorization: Always ensure that credential searches or corporate-domain checks are explicitly authorized under a signed Rules of Engagement (RoE) or Statement of Work (SOW).

- Data Handling: If handling breach data or customer hashes, use secure storage, strict isolation, and secure disposal procedures in compliance with applicable data privacy laws such as GDPR or CCPA.

- Minimization: Collect only the data required for the assessment and avoid unnecessary exposure of personal or sensitive information.

- Documentation: Maintain clear records of the tools, sources, and findings used during the assessment to support reporting and legal defensibility.

- Responsible Reporting: Present findings in a concise, actionable format, including risk severity, affected assets, and remediation guidance.
