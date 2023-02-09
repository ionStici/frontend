[&larr; Back](./README.md)

# Web Security

## Penetration Testing

[Penetration testing](https://csrc.nist.gov/glossary/term/penetration_testing) (pen testing & ethical hacking) is a growing practice where a cyberattack is simulated in order to identify security vulnerabilities so that they can be discoverted and remediated.

## Security Principles

_CIA stands for Confidentiality, Integrity, and Availability._

**Confidentiality** refers to protecting private information from eyes that shouldn’t have access to it. It’s the need to enforce access - who can see this, and who shouldn’t? Examples of enforcing confidentiality include implementing robust user authentication and encryption of important user data.

**Integrity** refers to data integrity here. We need security controls that protect data from being changed or deleted, and that the damage can be reversed if done accidentally. Some techniques related to integrity are database security, keeping backups and using cryptography to check for changes.

**Availability** refers to data being consistently, reliably available to those authorized. For example, social media websites ensure that even with high traffic or when a server is compromised, information gets to a user’s screen. This is accomplished through constant maintenance of hardware and software, monitoring servers and networks, and having a plan for any disasters.

## 2017 OWASP Top 10

[OWASP (Open Web Application Security Project)](https://owasp.org/) is a great resource for developers, effering tools, security education and manuals.

**OWASP** is a respected authority in the field of web security.

The [OWASP Top Ten](https://owasp.org/www-project-top-ten/) is a project maintained by the OWASP. Top Ten is a collection of the ten most serious vulnerabilities for web applications.

1. **Injection** is when an attacker injects malicious code into an interpreter in order to gain access to information or damage a system (through input fields).

2. **Broken Authentication** refers to vulnerabilities that allow attackers to impersonate other user accounts.

3. Handling **Sensitive Data Exposure** with insufficient protections (insecure storage, transmission of sensitive data, revealing sensitive data to unauthorized parties).

   The stolen information from Sensitive Data Exposure gets sold and resold on the dark web, often ending up in sets of personal information known as _fullz_. Fullz contain information someone could use to commit the kinds of fraud that can ruin a victim’s life for years, and most of this information is on sale for $25 or less.

4. **XML External Entities (XXE)** is a type of vulnerability that allows maliciously crafted data to produce unintended behavior on the baclend of a website. XXE involves an attacker to unload a maliciously crafted XML file. Simplest solution: don't use XML.

5. **Broken Access Control** is when authorization is improperly enforced, allowing users access to privileges they should not have. Mitigations: rate limits for logins, ensuring server-side validation of requests, implementing default-deny for permissions.

6. **Security Misconfiguration:** forgetting to protect cloud storage, leaving unnecessary features enabled on server software, disabling automatic updates, displaying overly detailed error messages that give details about the way the backend is set up. Preventing security misconfiguration requires regular review of configurations.

7. **Cross-Site Scripting (XSS)** is a web vulnerability that targets the browser-side of the website, rather than the server-side. XSS happens when a browser is tricked into running malicious javascript. It usually happens when a website allows user input without sanitizing and unarming dangerous input. If this happens, an attacker can pass input to the website that a victim’s browser will run as javascript.

   XSS can be a severe vulnerability, particularly when the malicious input is stored by the website and displayed to many users. XSS has a wide range of uses, from defacing websites to bypassing authentication to stealing passwords.

   Preventing XSS involves making sure that special characters like <, >, ", =, and more are properly escaped to prevent a browser from parsing them as code rather than regular text.

8. **Insecure Deserialization**

   Serialization is the process of turning an object within a program into formatted data. Deserialization is the process of turning formatted data into an object within code. Insecure Deserialization is when this process can be exploited to cause unintended behavior.

   If an attacker is able to modify the data that is going to be deserialized, they can change the resulting object, modifying data or adding malicious behaviors. In the worst case, this can allow for arbitrary code execution.

   Don't trust user input! Especially if that user input will interact directly with your server.

   The easiest and most reliable solution is to just not deserialize external data.

9. **Using Components with Known Vulnerabilities** means using software of package versions that are known to be vulnerable. Vulnerabilities are common in software, but they usually get patched as new updates are released. However, older versions of the software remain vulnerable!

   This can be prevented by keeping software such as operating systems, hosts, database software, etc up to date. If a piece of software is abandoned, it’s time to find a new, actively-maintained replacement.

10. **Insufficient Logging and Monitoring** refers to an overall lack of tools that monitor, record, and report events within a system. Events include logins and login attempts, webpage requests, and more. Having these logs allows monitoring software to scan for suspicious behavior, such as 1000 login attempts in 5 seconds or connections to or from known malicious IP addresses.

    When logging and monitoring is insufficient, it’s more difficult to investigate attacks. Insufficient logging and monitoring also gives attackers more time to do damage before they are detected.
