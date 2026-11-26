# WHOIS Lookup

## 1. Introduction

WHOIS is an important technique used in cybersecurity reconnaissance and OSINT to collect information about domain names, IP address allocations, and internet resources.

It helps security professionals understand domain registration details, identify registrar information, examine name servers, and investigate publicly available registration records.

During reconnaissance, WHOIS lookup is often performed during the initial information gathering stage to understand the ownership and registration history of a domain.

This document explains the WHOIS protocol, its purpose, working process, common commands, practical examples, limitations, and cybersecurity applications.

---

## 2. What Is WHOIS?

**WHOIS** is a query and response protocol used to retrieve registration and allocation information about internet resources.

It can provide information about:

- Domain names
- Domain registrars
- Registration and expiration dates
- Domain status
- Name servers
- Registrant information, when publicly available
- IP address allocation records
- Autonomous System Number (ASN) allocation information

WHOIS is commonly used in domain reconnaissance, network research, incident response, and threat intelligence.

### Simple Definition

WHOIS is a service that allows users to query registration information associated with a domain name or certain internet resources.

---

## 3. Why Is WHOIS Used in Cybersecurity?

WHOIS lookup helps security professionals collect basic information about a target's internet presence.

### Common Uses

1. **Domain Reconnaissance:** Collect domain registration details.
2. **Registrar Identification:** Identify the company managing a domain registration.
3. **Name Server Discovery:** Find name servers associated with a domain.
4. **Registration Timeline Analysis:** Review creation, update, and expiration dates.
5. **Threat Intelligence:** Investigate suspicious domains.
6. **Incident Response:** Gather registration information related to malicious domains.
7. **Infrastructure Research:** Examine publicly available IP allocation information.
8. **Digital Footprint Analysis:** Understand the registration-related information associated with an organization.

WHOIS does not directly identify every system belonging to an organization. It provides registration-related information that can support further research.

---

## 4. How Does WHOIS Work?

WHOIS works through a query-and-response process.

When a user submits a WHOIS query, the request is directed to an appropriate WHOIS server or service.

The server returns available registration information for the requested resource.

### Basic Workflow

```text
        User
         |
         v
  WHOIS Query
         |
         v
  WHOIS Client or
  Lookup Website
         |
         v
  Appropriate WHOIS Server
         |
         v
 Registration Information
         |
         v
  Result Analysis
```

### Example

A user wants to investigate the domain:

```text
example.com
```

The user performs a WHOIS lookup.

The result may contain:

- Registrar name
- Domain creation date
- Domain expiration date
- Domain status
- Name servers

The user then reviews the information and records relevant findings.

---

## 5. WHOIS Protocol and Port

Traditional WHOIS uses the TCP protocol.

| Property | Details |
|---|---|
| Protocol | TCP |
| Default Port | 43 |
| Communication | Query and response |
| Common Use | Domain and internet resource registration lookup |

The traditional WHOIS protocol is text-based and does not provide built-in encryption.

Modern registration data services may use other technologies, including RDAP, which provides a structured alternative.

---

## 6. Information Available Through WHOIS

The information returned by a WHOIS query depends on the domain registry, registrar, privacy settings, and lookup service.

### A. Domain Name

The domain being queried.

Example:

```text
Domain Name: example.com
```

### B. Registrar

The organization through which the domain is registered.

Example:

```text
Registrar: Example Registrar
```

This is an illustrative value.

### C. Creation Date

The date when the domain was originally registered.

Example:

```text
Creation Date: 2020-01-01
```

### D. Expiration Date

The date when the current registration period is scheduled to expire.

Example:

```text
Registry Expiry Date: 2027-01-01
```

### E. Updated Date

The date when registration information was last updated.

### F. Name Servers

Name servers identify the DNS servers responsible for providing authoritative DNS information for the domain.

Example:

```text
Name Server: ns1.example.com
Name Server: ns2.example.com
```

These are illustrative names.

### G. Domain Status

Domain status values indicate certain registration or transfer conditions.

Examples include:

- `clientTransferProhibited`
- `clientUpdateProhibited`
- `serverTransferProhibited`

Status values should be interpreted according to the relevant registry and registrar documentation.

### H. Registrant Information

Registrant information may include:

- Name
- Organization
- Email address
- Country
- Administrative contact details

However, this information may be hidden or replaced with privacy-protection details.

---

## 7. WHOIS vs RDAP

RDAP stands for **Registration Data Access Protocol**.

It was developed as a modern alternative to traditional WHOIS registration data services.

| WHOIS | RDAP |
|---|---|
| Traditional text-based protocol | Structured HTTP-based protocol |
| Commonly uses TCP port 43 | Uses HTTP/HTTPS |
| Response format may vary | Standardized JSON response structure |
| Limited standardization | Supports standardized data representation |
| Privacy handling varies by service | Supports structured access and data handling |

RDAP is increasingly used by registries and registrars to provide registration information.

### Why Is RDAP Important?

- Provides structured data.
- Supports standardized responses.
- Works with modern web infrastructure.
- Helps improve consistency in registration data access.

WHOIS remains widely used, but RDAP is an important modern registration data lookup technology.

---

## 8. WHOIS Lookup Methods

WHOIS information can be collected using different methods.

### Method 1: Online WHOIS Websites

Online lookup services allow users to search for domain registration information through a web browser.

Examples:

- [ICANN Lookup](https://lookup.icann.org/)
- [Whois.com](https://www.whois.com/whois/)
- [DomainTools WHOIS](https://whois.domaintools.com/)

These services may display information from registries, registrars, or other registration data sources.

### Method 2: WHOIS Command-Line Tool

Linux distributions such as Kali Linux and Parrot Security OS may provide a command-line WHOIS utility.

Example:

```bash
whois example.com
```

This command queries available WHOIS services for the domain.

### Method 3: RDAP Lookup

RDAP services can also be used to retrieve domain registration information.

ICANN provides a lookup service:

https://lookup.icann.org/

---

## 9. Practical WHOIS Commands

The following commands demonstrate basic WHOIS usage.

### A. Basic Domain Lookup

```bash
whois example.com
```

Purpose:

- Retrieve available registration information.
- Identify the registrar.
- Review registration dates.
- Examine domain status.

### B. Lookup a Domain with a Specific TLD

```bash
whois example.org
```

Different top-level domains may use different registration data services.

### C. Check WHOIS Tool Availability

On Debian-based Linux distributions:

```bash
which whois
```

This checks whether the WHOIS command is available in the system's executable path.

### D. Install WHOIS on Debian-Based Systems

```bash
sudo apt update
sudo apt install whois
```

This installs the WHOIS command-line utility on compatible Debian-based systems.

Installation requirements may vary depending on the Linux distribution.

---

## 10. Practical Lab: WHOIS Lookup in Kali Linux

### Lab Objective

Learn how to perform a basic WHOIS lookup and understand the information returned by the command.

### Requirements

- Kali Linux or another compatible Linux distribution
- Terminal
- WHOIS utility
- Internet connection

### Step 1: Open the Terminal

Open the terminal in Kali Linux.

### Step 2: Check Whether WHOIS Is Installed

```bash
which whois
```

If the command is available, the terminal may display a path such as:

```text
/usr/bin/whois
```

### Step 3: Perform a WHOIS Lookup

```bash
whois example.com
```

### Step 4: Review the Output

Look for:

- Domain name
- Registrar
- Creation date
- Expiration date
- Updated date
- Domain status
- Name servers

### Step 5: Record the Findings

Use the following table:

| Field | Information |
|---|---|
| Target Domain | example.com |
| Registrar | Record the returned value |
| Creation Date | Record the returned value |
| Expiration Date | Record the returned value |
| Name Servers | Record the returned values |
| Domain Status | Record the returned values |

### Step 6: Analyze the Results

Consider the following questions:

- Which registrar manages the domain?
- When was the domain registered?
- Which name servers are listed?
- Is registrant information publicly available?
- Are any registration details hidden?

**Lab Note:** `example.com` is a reserved example domain used for documentation. The results may vary depending on the lookup service.

---

## 11. Understanding WHOIS Output

WHOIS output may contain several fields.

Example:

```text
Domain Name: example.com
Registrar: Example Registrar
Creation Date: 2020-01-01
Updated Date: 2026-01-01
Registry Expiry Date: 2027-01-01
Name Server: ns1.example.com
Name Server: ns2.example.com
Domain Status: clientTransferProhibited
```

The above output is illustrative and is not a live WHOIS result.

### Output Interpretation

| Field | Meaning |
|---|---|
| Domain Name | The domain being queried |
| Registrar | The domain registration provider |
| Creation Date | Original registration date |
| Updated Date | Most recent registration data update |
| Expiry Date | Scheduled registration expiration |
| Name Server | DNS server information |
| Domain Status | Registration-related status |

### Important Observation

A domain's registration date does not necessarily indicate when its website was created.

Similarly, the expiration date does not guarantee that the domain will become available to the public on that date. Registrations may be renewed or enter additional lifecycle stages.

---

## 12. WHOIS in Reconnaissance Workflow

WHOIS is commonly used during the early stages of reconnaissance.

### Example Workflow

```text
Target Identification
        |
        v
Domain Name Collection
        |
        v
WHOIS Lookup
        |
        v
Registrar and Date Analysis
        |
        v
Name Server Identification
        |
        v
DNS Enumeration
        |
        v
Further Authorized Reconnaissance
```

WHOIS information can help identify useful starting points for DNS and domain research.

However, WHOIS alone does not provide a complete view of an organization's infrastructure.

---

## 13. WHOIS and DNS: Difference

WHOIS and DNS are related but serve different purposes.

| WHOIS | DNS |
|---|---|
| Provides registration information | Resolves domain names and provides DNS records |
| Identifies registrar and registration dates | Identifies IP addresses, mail servers, and name servers |
| Used for registration research | Used for name resolution and service discovery |
| Does not directly resolve a hostname to an IP address | Can resolve a hostname to an IP address |

### Example

WHOIS command:

```bash
whois example.com
```

DNS command:

```bash
dig example.com A
```

The first retrieves registration-related information. The second queries the domain's DNS A record.

---

## 14. Limitations of WHOIS

WHOIS is useful, but it has several limitations.

### A. Privacy Protection

Domain owners may use privacy-protection services to hide personal registration details.

### B. Incomplete Information

Some WHOIS servers may return limited information.

### C. Outdated Records

Registration data may not always reflect recent changes immediately.

### D. Different Formats

WHOIS responses may differ between registries and registrars.

### E. Rate Limiting

Some WHOIS servers restrict the number of queries from a user or IP address.

### F. Ownership Attribution

A registrar or name server does not necessarily identify the actual owner of every website or system associated with a domain.

### G. No Vulnerability Detection

WHOIS does not identify software vulnerabilities or prove that a domain is insecure.

---

## 15. Common WHOIS Errors and Troubleshooting

### Error 1: `whois: command not found`

Possible reason:

The WHOIS utility is not installed.

Solution:

```bash
sudo apt update
sudo apt install whois
```

### Error 2: No Information Returned

Possible reasons:

- The registry does not provide the requested information.
- The domain extension uses a different lookup service.
- The server limits queries.
- The lookup service is temporarily unavailable.

Solution:

Try an official registration lookup service such as ICANN Lookup.

### Error 3: Connection Timeout

Possible reasons:

- Network connectivity issues.
- WHOIS server unavailability.
- Firewall restrictions.
- Rate limiting.

Solution:

Check the network connection and try again later or use an appropriate RDAP lookup service.

---

## 16. Legal and Ethical Considerations

WHOIS lookup is generally a registration information query, but the information obtained must be handled responsibly.

### Important Guidelines

- Use WHOIS for legitimate research.
- Respect privacy and applicable data protection requirements.
- Do not misuse personal registration information.
- Do not use collected information for harassment or impersonation.
- Avoid excessive queries that violate service restrictions.
- Verify information before reporting it.
- Follow the scope of an authorized assessment.

**Important:** Publicly available registration information should not be treated as permission to conduct further testing against the domain.

---

## 17. Common Mistakes

1. Assuming WHOIS always reveals the domain owner's identity.
2. Treating registration information as a complete infrastructure map.
3. Confusing registrar information with website hosting information.
4. Assuming a domain expiration date means the domain is immediately available.
5. Ignoring privacy-protection services.
6. Trusting outdated registration data without verification.
7. Treating WHOIS results as proof of a vulnerability.
8. Forgetting to record the collection date.

---

## 18. Best Practices

- Use reliable WHOIS or RDAP lookup services.
- Record the domain and collection date.
- Review important fields carefully.
- Verify name servers through DNS queries.
- Compare information from multiple sources when necessary.
- Respect privacy-protection mechanisms.
- Avoid unnecessary personal data collection.
- Keep findings organized.
- Follow authorization and legal requirements.

---

## 19. Key Takeaways

- WHOIS is used to retrieve registration information about internet resources.
- It can provide registrar, registration dates, domain status, and name server information.
- Traditional WHOIS commonly uses TCP port 43.
- RDAP is a modern structured alternative to traditional WHOIS.
- WHOIS is useful during domain reconnaissance and OSINT.
- Privacy services may hide registrant information.
- WHOIS and DNS serve different purposes.
- WHOIS does not directly identify vulnerabilities.
- Collected registration information should be verified and handled responsibly.

---

## 20. Interview Questions and Answers

### Q1. What is WHOIS?

**Answer:** WHOIS is a query and response protocol used to retrieve registration and allocation information about domain names and certain internet resources.

### Q2. What is the default port of WHOIS?

**Answer:** Traditional WHOIS commonly uses TCP port 43.

### Q3. What information can WHOIS provide?

**Answer:** It can provide registrar information, domain creation and expiration dates, domain status, name servers, and registrant information when publicly available.

### Q4. What is the purpose of WHOIS in reconnaissance?

**Answer:** WHOIS helps collect registration-related information about a domain and supports further domain and DNS research.

### Q5. What is the difference between WHOIS and RDAP?

**Answer:** WHOIS is a traditional text-based protocol, while RDAP is a modern HTTP-based protocol that provides structured registration data.

### Q6. What is a domain registrar?

**Answer:** A domain registrar is an organization accredited or authorized to provide domain name registration services.

### Q7. What are name servers?

**Answer:** Name servers provide authoritative DNS information for a domain and help direct DNS queries to the appropriate records.

### Q8. Why might WHOIS not show the domain owner's personal information?

**Answer:** The registrant may use privacy protection, or the registry may restrict the display of personal information.

### Q9. Does WHOIS identify the hosting server of a website?

**Answer:** Not directly. WHOIS provides registration information. DNS queries and other techniques are used to investigate hosting and infrastructure details.

### Q10. What is the difference between WHOIS and DNS lookup?

**Answer:** WHOIS retrieves registration-related information, while DNS lookup retrieves records used for domain name resolution and related services.

### Q11. Can WHOIS identify vulnerabilities?

**Answer:** No. WHOIS provides registration information and does not perform vulnerability detection.

### Q12. What is RDAP used for?

**Answer:** RDAP is used to access registration data through a structured protocol and is a modern alternative to traditional WHOIS services.

---

## 21. References and Learning Resources

- [ICANN Lookup](https://lookup.icann.org/)
- [ICANN Registration Data Access Protocol (RDAP)](https://www.icann.org/rdap)
- [WHOIS Protocol – RFC 3912](https://www.rfc-editor.org/rfc/rfc3912)
- [RDAP – RFC 9082](https://www.rfc-editor.org/rfc/rfc9082)
- [RDAP JSON Responses – RFC 9083](https://www.rfc-editor.org/rfc/rfc9083)
- [Whois.com](https://www.whois.com/)
- [Kali Linux Documentation](https://www.kali.org/docs/)
- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework)

---

## 22. Learning Note

During my cybersecurity training, I learned how WHOIS lookup can be used to collect domain registration information during reconnaissance.

I practiced understanding the purpose of fields such as registrar, creation date, expiration date, domain status, and name servers.

I also learned that WHOIS information may be incomplete or protected by privacy services, and that registration data should be verified before drawing conclusions.

This document is part of my ongoing cybersecurity learning and training notes.

**Learning | Practicing | Improving**
