# Click Jacking

- [Introduction](#introduction)
- [Understanding ClickJacking](#understanding-clickjacking)
- [How ClickJacking Works](#how-clickjacking-works)
- [Impact on Website Security](#how-clickjacking-works)
- [Mitigating ClickJacking Attacks](#mitigating-clickjacking-vulnerabilities)
- [Tutorials on ClickJacking](#tutorials-for-click-jacking)
- [Payloads for ClickJacking](#payloads-for-click-jacking)

# Introduction:
In the world of bug bounty hunting and penetration testing, security researchers play a crucial role in identifying vulnerabilities that could be exploited by malicious actors. Clickjacking is one such website vulnerability that has gained significant attention due to its potential for abuse. This article aims to provide an in-depth understanding of clickjacking, its impact on website security, and how it can be utilized effectively in bug bounty hunting and penetration testing.

## Understanding Clickjacking:
Clickjacking, also known as UI redressing or UI overlay attack, is a technique where an attacker tricks a user into clicking on a seemingly innocuous element of a website while actually interacting with a hidden or invisible element from another page or application. The attacker essentially "hijacks" the user's clicks and can make them unknowingly perform actions they did not intend to.

### How Clickjacking Works:
Clickjacking typically involves the manipulation of iframes, which are HTML elements used to embed one document within another. The attacker designs a malicious webpage that contains transparent iframes or overlays, often positioned strategically to conceal the actual page content. By luring the user to click on specific areas of the malicious page, the attacker can execute unintended actions on behalf of the user, such as transferring funds, enabling access to sensitive data, or performing social media actions without their consent.

#### Impact on Website Security:
Clickjacking poses significant risks to website security, as it can be used to carry out various malicious activities, including:

Unauthorized Operations: Clickjacking can trick users into unknowingly performing actions that may compromise their accounts or sensitive information.

Social Engineering: Attackers can exploit clickjacking to trick users into sharing confidential information, clicking on misleading advertisements, or unknowingly participating in scams.

Identity Theft: By overlaying malicious forms on legitimate websites, attackers can deceive users into entering their credentials, leading to potential identity theft or account compromise.

Utilizing Clickjacking in Bug Bounty Hunting and Penetration Testing:
Bug bounty hunters and penetration testers can leverage clickjacking to identify vulnerabilities and help organizations improve their website security. Here's how:

Identifying Vulnerable Applications: By attempting to manipulate iframes, testers can determine if a website is susceptible to clickjacking attacks. They can analyze the behavior of the page and verify if the website's defenses are sufficient to prevent clickjacking attempts.

Assessing Impact: Testers can explore the consequences of a successful clickjacking attack by emulating scenarios that could lead to unauthorized actions, data exposure, or account compromise. This assessment helps organizations understand the potential risks and prioritize their mitigation efforts accordingly.

Reporting Vulnerabilities: When testers discover clickjacking vulnerabilities, they should document their findings accurately and provide detailed steps to reproduce the issue. Reporting such vulnerabilities to the website owners or participating bug bounty platforms is crucial for remediation and rewarding ethical hackers for their efforts.

### Mitigating Clickjacking Vulnerabilities:
To mitigate clickjacking vulnerabilities effectively, website owners and developers should implement the following preventive measures:

X-Frame-Options Header: Setting the X-Frame-Options header in the website's HTTP response can prevent the site from being embedded within an iframe on other domains.

Content Security Policy (CSP): Implementing a robust CSP can limit the sources from which iframes can be loaded, preventing unauthorized embedding.

Frame Busting Techniques: Techniques like JavaScript-based frame-busting code can prevent iframes from hijacking user clicks.

User Awareness and Education: Educating users about the risks associated with clicking on untrusted links and the importance of verifying the authenticity of websites can significantly reduce the success rate of clickjacking attacks.

# Conclusion:
Clickjacking presents a substantial threat to website security, enabling attackers to manipulate user interactions and perform unauthorized actions. However, by understanding how clickjacking works and utilizing it in bug bounty hunting and penetration testing, security researchers can play a pivotal role in identifying vulnerabilities and improving website defenses. By implementing preventive measures, organizations can safeguard their users from clickjacking attacks and maintain a secure online environment.

### Tutorials for Click Jacking

### Payloads for Click Jacking