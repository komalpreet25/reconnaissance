# Email and People OSINT

## 1. Introduction

Email and People OSINT is a branch of Open-Source Intelligence (OSINT) that focuses on collecting and analyzing publicly available information related to email addresses, online identities, and digital footprints.

During cybersecurity reconnaissance, email addresses and publicly available identity information can help understand an organization's external exposure. This information may also support security awareness, phishing investigations, and defensive threat intelligence.

The purpose of this document is to understand how email and people-related OSINT works, which tools are commonly used, and how to perform responsible information gathering.

> **Important:** This document is for educational and defensive cybersecurity purposes. All activities must respect privacy, applicable laws, and authorized scope.

---

## 2. What Is Email OSINT?

Email OSINT is the process of gathering and analyzing publicly available information associated with an email address.

An email address may provide useful clues about:

- The organization or domain associated with it
- Publicly available profiles
- Possible data breach exposure
- Email infrastructure
- Domain configuration and security
- Whether the address appears in publicly indexed sources

Email OSINT does not automatically reveal the complete identity of an email owner. Findings must be verified using reliable sources.

### Example

Consider a fictional email address:

`analyst@example.com`

Possible investigation areas include:

- Identifying the domain `example.com`
- Checking the domain's DNS records
- Reviewing publicly available information about the domain
- Checking whether the address appears in a legitimate breach-notification service
- Looking for publicly published professional information

The address is used only as a documentation example.

---

## 3. What Is People OSINT?

People OSINT involves collecting and analyzing publicly available information about an online identity or person.

It may include information from:

- Professional networking platforms
- Public websites and blogs
- Public social media profiles
- Published articles and presentations
- Public GitHub profiles
- Conference or event pages
- Public business directories

People OSINT is commonly used in:

- Security awareness and risk assessment
- Investigations of publicly reported cyber incidents
- Digital footprint analysis
- Brand and impersonation monitoring
- Authorized security assessments

The goal is to understand publicly exposed information, not to invade someone's privacy.

---

## 4. Email OSINT vs People OSINT

| Email OSINT | People OSINT |
|---|---|
| Starts with an email address or email domain | Starts with a publicly known online identity or name |
| Focuses on email and domain-related exposure | Focuses on publicly available digital footprints |
| May include DNS and email security analysis | May include professional profiles and public publications |
| Can support email security investigations | Can support identity and exposure assessments |

Both techniques can be combined during an authorized reconnaissance assessment.

---

## 5. Email OSINT Methodology

A structured investigation helps prevent inaccurate conclusions.

### Step 1: Define the Objective

Before collecting information, identify the purpose of the investigation.

Examples:

- Assessing an organization's publicly exposed email infrastructure
- Checking a company's email security configuration
- Investigating a reported phishing email
- Reviewing an authorized organization's public digital footprint

### Step 2: Identify the Email Domain

Separate the email address into its local part and domain.

Example:

`security@example.com`

- Local part: `security`
- Domain: `example.com`

The domain can be investigated using public DNS and registration information.

### Step 3: Review Public Sources

Look for information published through legitimate public sources.

Possible sources include:

- Official company websites
- Public professional profiles
- Public contact pages
- Security advisories
- Public repositories
- Reputable breach-notification services

### Step 4: Check Domain and Email Infrastructure

Review DNS records that may help explain how the domain handles email.

Important records include:

| Record | Purpose |
|---|---|
| MX | Identifies mail servers responsible for receiving email |
| SPF | Specifies authorized sending hosts through a DNS TXT policy |
| DKIM | Uses cryptographic signatures to help verify email authenticity |
| DMARC | Defines policy and reporting for SPF/DKIM alignment failures |

### Step 5: Verify Findings

Do not treat a single search result as proof.

Confirm important findings using multiple reliable sources whenever possible.

### Step 6: Document the Results

Record:

- Source
- Date of collection
- Finding
- Confidence level
- Relevance to the assessment
- Recommended defensive action

---

## 6. Common Email OSINT Tools

### 6.1 TheHarvester

TheHarvester is an OSINT tool used to gather publicly available information such as email addresses, subdomains, and hostnames from supported sources.

Example:

```bash
theHarvester -d example.com -b crtsh
```

Explanation:

- `-d` specifies the domain
- `-b` specifies the source or data provider

The available sources and command options may vary by installed version.

### 6.2 WHOIS / RDAP

WHOIS and RDAP can provide domain registration information.

Example:

```bash
whois example.com
```

Useful information may include:

- Registrar
- Registration dates
- Nameservers
- Domain status

Some registration details may be hidden or privacy-protected.

### 6.3 DNS Lookup Tools

DNS tools help identify email-related domain configuration.

Using `dig`:

```bash
dig example.com MX
```

To inspect TXT records:

```bash
dig example.com TXT
```

To inspect nameservers:

```bash
dig example.com NS
```

These commands help identify mail infrastructure and domain policies.

### 6.4 Have I Been Pwned

Have I Been Pwned is a breach-notification service that allows users to check whether an email address appears in known data breaches.

Website:

https://haveibeenpwned.com/

Use the service according to its access requirements and privacy rules.

A breach result does not mean the account is currently compromised. It indicates that the address was found in a reported breach dataset.

---

## 7. People OSINT Methodology

### Step 1: Define the Scope

Identify the person or online identity that is relevant to an authorized investigation.

Avoid collecting unrelated personal information.

### Step 2: Identify Public Profiles

Search for publicly available professional or organizational profiles.

Examples:

- LinkedIn
- GitHub
- Official company biography pages
- Public conference profiles
- Personal websites or blogs

### Step 3: Review Publicly Published Information

Relevant information may include:

- Professional role
- Publicly listed organization
- Technical publications
- Public projects
- Conference presentations
- Public business contact details

### Step 4: Cross-Reference Information

Compare information across sources to identify whether profiles likely refer to the same public identity.

Do not assume that two accounts with the same name belong to the same person.

### Step 5: Assess Digital Exposure

Identify information that may create security risks, such as:

- Publicly exposed business email addresses
- Overshared organizational details
- Publicly accessible credentials accidentally committed to repositories
- Impersonation accounts
- Sensitive information unintentionally published

If credentials or secrets are discovered, do not attempt to use them. Follow the organization's responsible disclosure process.

### Step 6: Prepare a Report

Document only relevant findings and provide practical defensive recommendations.

---

## 8. Common People OSINT Sources

| Source | Information that may be available |
|---|---|
| LinkedIn | Public professional details and employment information |
| GitHub | Public repositories, usernames, and technical contributions |
| Official websites | Public staff biographies and contact information |
| Public blogs | Articles, technical interests, and published opinions |
| Conference websites | Speaker profiles and presentations |
| Search engines | Publicly indexed pages and documents |

**Note:** The availability of information depends on the person's privacy settings and the platform's policies.

---

## 9. Practical Lab: Email Domain Investigation

### Objective

Understand how to collect basic email-domain information using public DNS records.

### Lab Target

`example.com`

This domain is reserved for documentation and examples.

### Step 1: Identify the MX Records

```bash
dig example.com MX
```

### Step 2: Check TXT Records

```bash
dig example.com TXT
```

### Step 3: Review Nameservers

```bash
dig example.com NS
```

### Step 4: Check Domain Registration Information

```bash
whois example.com
```

### Step 5: Record the Findings

Create a small investigation table.

| Item | Observation |
|---|---|
| Domain | example.com |
| MX records | Record the returned result |
| TXT records | Record relevant policies |
| Nameservers | Record the returned result |
| Registration information | Record available public details |

### Expected Learning

After completing this lab, I should be able to:

- Identify the domain associated with an email address
- Understand basic email-related DNS records
- Use public sources responsibly
- Document findings in a structured format

---

## 10. Email Security Concepts

Email OSINT can also help understand common email security mechanisms.

### SPF — Sender Policy Framework

SPF is a DNS-based mechanism that specifies which hosts are authorized to send email for a domain.

### DKIM — DomainKeys Identified Mail

DKIM uses cryptographic signatures to help receivers verify that certain parts of an email have not been altered and that the message is associated with a signing domain.

### DMARC — Domain-based Message Authentication, Reporting and Conformance

DMARC builds on SPF and DKIM by applying domain alignment rules and defining how receivers should handle authentication failures.

These mechanisms help reduce email spoofing, but they do not eliminate every phishing or email-related threat.

---

## 11. Common Mistakes in Email and People OSINT

- Assuming an email address reveals the complete identity of its owner
- Treating an old breach result as proof of current compromise
- Confusing similar usernames or profiles
- Trusting a single unverified source
- Collecting unnecessary personal information
- Attempting to access private accounts
- Using discovered credentials
- Ignoring the investigation's scope and authorization
- Reporting findings without recording their source

---

## 12. Privacy and Ethical Considerations

Email and People OSINT can involve personal information. Responsible handling is essential.

Follow these principles:

1. Collect only information relevant to the authorized objective.
2. Use legitimate public sources.
3. Do not bypass privacy controls.
4. Do not attempt account access using discovered information.
5. Avoid publishing personal information in reports or repositories.
6. Protect investigation notes and collected data.
7. Follow applicable laws, platform terms, and organizational policies.
8. Report security exposures through appropriate channels.

Public availability does not automatically mean information can be used for every purpose.

---

## 13. Key Takeaways

- Email OSINT focuses on email addresses, domains, and email-related exposure.
- People OSINT focuses on publicly available information associated with online identities.
- DNS records can reveal useful details about email infrastructure.
- TheHarvester, WHOIS, DNS utilities, and breach-notification services can support investigations.
- Findings must be verified before being reported.
- Privacy, authorization, and ethical handling are essential throughout the process.

---

## 14. Interview Questions

### Q1. What is Email OSINT?

Email OSINT is the process of gathering and analyzing publicly available information associated with email addresses and their domains.

### Q2. What is People OSINT?

People OSINT involves collecting and analyzing publicly available information about an online identity or person.

### Q3. What is TheHarvester used for?

TheHarvester is used to collect publicly available information such as email addresses, subdomains, and hostnames from supported sources.

### Q4. What is an MX record?

An MX record identifies the mail servers responsible for receiving email for a domain.

### Q5. What is SPF?

SPF is a DNS-based email authentication mechanism that specifies authorized sending hosts for a domain.

### Q6. What is DKIM?

DKIM uses cryptographic signatures to help verify email authenticity and message integrity.

### Q7. What is DMARC?

DMARC defines how a domain handles email authentication failures and supports reporting based on SPF and DKIM alignment.

### Q8. Does finding an email address in a breach mean the account is hacked?

No. It means the address appeared in a reported breach dataset. It does not automatically prove current account compromise.

### Q9. Why is verification important in OSINT?

Verification helps reduce false positives, incorrect identity matches, and unreliable conclusions.

### Q10. What precautions should be taken during People OSINT?

Use only relevant public information, respect privacy, remain within authorized scope, and avoid accessing private accounts or misusing collected data.

---

## 15. References

- TheHarvester: https://github.com/laramies/theHarvester
- Have I Been Pwned: https://haveibeenpwned.com/
- ICANN Lookup: https://lookup.icann.org/
- Google Search: https://www.google.com/
- LinkedIn: https://www.linkedin.com/
- GitHub: https://github.com/
- RFC 7208 — SPF: https://www.rfc-editor.org/rfc/rfc7208
- RFC 6376 — DKIM: https://www.rfc-editor.org/rfc/rfc6376
- RFC 7489 — DMARC: https://www.rfc-editor.org/rfc/rfc7489

---

## 16. Learning Note

During my cybersecurity training, I learned how email addresses and publicly available online information can support reconnaissance and security assessments.

I explored the importance of domain investigation, DNS records, email security mechanisms, public information sources, and responsible OSINT practices.

This document is part of my ongoing cybersecurity learning and practical training notes.

**Learning | Practicing | Improving**
