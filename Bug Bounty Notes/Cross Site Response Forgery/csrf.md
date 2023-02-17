# Cross Site Response Forgery (CSRF)

Cross-site request forgery (CSRF) is a type of web security vulnerability that allows an attacker to perform actions on behalf of an authenticated user without their knowledge or consent. In a CSRF attack, the attacker crafts a request that appears to be from the user, but actually originates from a different website or domain that the user has visited or is currently visiting.

From the perspective of a penetration tester, the goal is to identify potential CSRF vulnerabilities in a web application, and to demonstrate how an attacker could exploit them. To do this, the tester will typically follow a set of steps, such as:

Identifying the input parameters that are used to perform sensitive actions on the target application, such as making a payment or changing the user's account settings.

Creating a proof-of-concept HTML page that includes a form that submits a request to the target application with the necessary parameters to perform the sensitive action. The form will typically be hidden from the user, or disguised as a legitimate form on the attacker's site.

Persuading the victim to visit the attacker's site, typically by sending them a phishing email or directing them to a malicious ad or link.

When the victim visits the attacker's site, the hidden form is automatically submitted in the background, sending the sensitive action to the target application without the victim's knowledge.

Here is an example scenario of how a CSRF attack might work in practice:

Let's say that an online banking website allows users to transfer money between accounts by submitting a form that includes the source account number, destination account number, and the amount to be transferred.

An attacker creates a malicious website that includes a hidden form that submits a request to transfer money from the victim's account to the attacker's account. The form is disguised as a legitimate form on the attacker's site, such as a survey or a prize giveaway.

The attacker sends a phishing email to the victim, enticing them to visit the malicious site. When the victim clicks the link, the hidden form is automatically submitted in the background, transferring money from the victim's account to the attacker's account without their knowledge.

To prevent CSRF attacks, web developers can implement various measures such as using anti-CSRF tokens, which are unique values that are included in each form submission and checked against the user's session to ensure that the request is legitimate. Developers can also use the SameSite attribute to prevent cookies from being sent in cross-site requests, and implement other security measures such as CORS (Cross-Origin Resource Sharing) restrictions.

## Tools to detect CSRF
[XSRFProbe](https://github.com/0xInfection/XSRFProbe) - This is the best tool to audit and exploit CSRF

