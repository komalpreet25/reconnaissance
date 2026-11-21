# 03. Reconnaissance Methodology

## 1. Introduction

Reconnaissance methodology refers to a structured approach used to collect, organize, verify, and analyze information about a target during a cybersecurity assessment.

Instead of collecting information randomly, security professionals follow a systematic process to understand the target environment and identify assets that may require further investigation.

During my cybersecurity training, I learned that effective reconnaissance is not just about using tools or running commands. It also involves planning, defining the assessment scope, selecting appropriate information sources, analyzing results, and maintaining proper documentation.

A well-organized reconnaissance methodology helps security professionals avoid unnecessary activities and focus on relevant information.

## 2. What Is Reconnaissance Methodology?

Reconnaissance methodology is a step-by-step process followed to gather information about a target system, organization, network, or application.

It provides a structured way to:

- Define the target and assessment objectives.
- Understand the authorized testing scope.
- Collect publicly available information.
- Identify domains, subdomains, and IP addresses.
- Discover network hosts and services.
- Identify technologies and infrastructure.
- Analyze and verify collected information.
- Document findings for further security assessment.

The methodology may vary depending on the assessment type, organization, and testing requirements.

## 3. Objectives of Reconnaissance Methodology

The main objectives include:

| Objective | Description |
|---|---|
| Target Identification | Understand which organization, system, or application is being assessed. |
| Scope Definition | Identify the assets and activities permitted for testing. |
| Information Collection | Gather relevant technical and public information. |
| Asset Discovery | Identify domains, IP addresses, hosts, and applications. |
| Service Identification | Understand which services are running on discovered systems. |
| Technology Identification | Identify operating systems, frameworks, and web technologies. |
| Information Verification | Check the accuracy and reliability of collected information. |
| Documentation | Organize findings for reporting and future analysis. |

## 4. Steps Involved in Reconnaissance Methodology

A typical reconnaissance methodology can be divided into the following stages:

```text
        Target Identification
                |
                v
         Scope Definition
                |
                v
       Information Gathering
                |
                v
         Domain and DNS
            Discovery
                |
                v
        Network Discovery
                |
                v
       Service Identification
                |
                v
       Technology Detection
                |
                v
       Information Analysis
                |
                v
       Verification and Review
                |
                v
          Documentation
```

Let's understand each stage.

### 4.1 Target Identification

The first step is identifying the target that needs to be assessed.

A target may be:

- An organization
- A domain name
- A website
- A network
- An IP address
- A web application
- A cloud environment

**Example:**

```text
Target Organization: Example Organization
Primary Domain: example.com
Assessment Type: External Security Assessment
```

At this stage, the objective is to understand what needs to be investigated.

### 4.2 Scope Definition

Scope definition determines which systems and activities are included in the assessment.

It is one of the most important steps because not every asset associated with an organization is automatically authorized for testing.

Scope information may include:

- Approved domain names
- Authorized IP addresses and network ranges
- Applications permitted for testing
- Testing dates and time windows
- Allowed reconnaissance techniques
- Restricted systems and activities
- Emergency contact information

**Example:**

```text
Assessment Scope

In Scope:
- example.com
- staging.example.com
- Approved test IP addresses

Out of Scope:
- Third-party payment services
- External vendor infrastructure
- Systems not listed in the authorization
```

All active reconnaissance must remain within the approved scope.

### 4.3 Information Gathering

After defining the scope, information is collected using passive and active reconnaissance techniques, according to the approved assessment plan.

**Passive Information Gathering**

Sources may include:

- Search engines
- WHOIS databases
- Public DNS information
- Certificate Transparency logs
- Public websites
- Public code repositories
- OSINT platforms

Example:

```bash
whois example.com
```

This command retrieves publicly available domain registration information.

**Active Information Gathering**

Authorized activities may include:

- DNS queries
- Host discovery
- Port scanning
- Service detection
- Web server analysis

Example:

```bash
nslookup example.com
```

This command queries DNS to resolve the domain name.

Note that DNS queries may contact external DNS infrastructure and are not necessarily invisible to the queried services.

### 4.4 Domain and DNS Discovery

Domain and DNS discovery helps understand how an organization uses domain names and related infrastructure.

Information that may be collected includes:

- Primary domain
- Subdomains
- IPv4 addresses
- IPv6 addresses
- Mail servers
- Name servers
- Text records
- DNS zone information

Useful commands:

**Check A Record**

```bash
dig example.com A
```

**Check MX Record**

```bash
dig example.com MX
```

**Check NS Record**

```bash
dig example.com NS
```

**Check TXT Record**

```bash
dig example.com TXT
```

These commands help identify DNS information associated with a domain.

### 4.5 Network Discovery

Network discovery involves identifying reachable hosts and understanding the network environment.

It may help identify:

- Active hosts
- IP addresses
- Network ranges
- Network devices
- Accessible systems

Example using Nmap:

```bash
nmap -sn 192.0.2.0/24
```

Explanation:

- `nmap` – Starts the Nmap tool.
- `-sn` – Performs host discovery without a port scan.
- `192.0.2.0/24` – Documentation-only example network range.

The results can help identify hosts that respond to the discovery probes. However, a host that does not respond is not necessarily offline; firewalls and network configurations may affect the results.

### 4.6 Service Identification

After identifying authorized hosts, the next step may involve understanding which services are running.

Common services include:

| Port | Service | Purpose |
|---|---|---|
| 21 | FTP | File transfer |
| 22 | SSH | Secure remote administration |
| 25 | SMTP | Email transmission |
| 53 | DNS | Domain name resolution |
| 80 | HTTP | Web communication |
| 443 | HTTPS | Encrypted web communication |
| 3306 | MySQL | Database service |
| 3389 | RDP | Remote Desktop Protocol |

Example:

```bash
nmap -sV 192.0.2.10
```

The `-sV` option attempts to identify the services and versions running on open ports.

Identifying a service does not automatically mean that it contains a vulnerability.

### 4.7 Technology Detection

Technology detection helps identify the technologies used by a website or application.

Examples include:

- Web servers
- Programming languages
- Content Management Systems
- JavaScript frameworks
- Backend technologies
- CDN providers
- Web application frameworks

Common tools include:

- Wappalyzer
- WhatWeb
- BuiltWith
- Burp Suite

Example:

```bash
whatweb https://example.com
```

WhatWeb analyzes website responses to identify technologies and other characteristics.

### 4.8 Information Analysis

After collecting information, it must be organized and analyzed.

The purpose is to understand what the collected information represents and whether it is useful for the assessment.

For example:

```text
Domain: example.com

Discovered Information:
- Domain registration information
- DNS records
- Public IP addresses
- Identified subdomains
- Web server technologies
- Accessible services
```

During analysis, security professionals should:

- Identify duplicate information.
- Separate verified findings from assumptions.
- Check whether assets belong to the authorized scope.
- Identify outdated or unreliable information.
- Highlight areas that require further investigation.

### 4.9 Verification and Review

Not every result produced by a reconnaissance tool is accurate.

Verification helps reduce false positives and incorrect assumptions.

For example:

- Confirm whether a discovered subdomain currently resolves.
- Check whether an IP address belongs to the intended organization.
- Verify service identification results.
- Compare information from multiple reliable sources.
- Check whether the asset is within the authorized scope.

A finding should not be treated as a confirmed vulnerability simply because a reconnaissance tool reports it.

### 4.10 Documentation and Reporting

The final stage is documenting the collected information.

A professional reconnaissance report may include:

- Assessment objective
- Authorized scope
- Information sources
- Tools used
- Commands executed
- Discovered domains and IP addresses
- DNS information
- Identified hosts and services
- Technology information
- Observations and limitations
- Recommendations for further assessment

Proper documentation helps other security professionals understand the work performed and continue the assessment.

## 5. Common Tools Used in Reconnaissance Methodology

| Tool | Purpose | Common Usage |
|---|---|---|
| WHOIS | Domain registration lookup | Domain research |
| nslookup | DNS queries | DNS resolution |
| dig | Detailed DNS queries | DNS record analysis |
| theHarvester | OSINT gathering | Public information collection |
| Nmap | Network discovery | Host and port scanning |
| DNSenum | DNS enumeration | DNS information gathering |
| DNSrecon | DNS reconnaissance | DNS analysis |
| Subfinder | Subdomain discovery | Domain asset discovery |
| Amass | Attack surface mapping | Asset discovery |
| WhatWeb | Technology identification | Website analysis |
| Gobuster | Content and DNS discovery | Authorized discovery |
| Burp Suite | Web application analysis | Request and response inspection |

Tool selection depends on the target, assessment objectives, authorization, and scope.

## 6. Example: Complete Reconnaissance Methodology Scenario

Consider an organization named `example.com` that has authorized an external reconnaissance assessment.

The security professional follows a structured process.

### Step 1: Identify the Target

```text
Organization: Example Organization
Primary Domain: example.com
Assessment: External Reconnaissance
```

### Step 2: Define the Scope

```text
Authorized Assets:
- example.com
- staging.example.com
- Approved test IP addresses

Restrictions:
- No third-party infrastructure testing
- No exploitation
- No denial-of-service testing
```

### Step 3: Collect Public Information

```bash
whois example.com
```

Purpose: Review publicly available domain registration information.

### Step 4: Analyze DNS Records

```bash
dig example.com A
dig example.com MX
dig example.com NS
```

Purpose: Understand the domain's DNS configuration.

### Step 5: Perform Authorized Network Discovery

```bash
nmap -sn 192.0.2.0/24
```

Purpose: Identify responsive hosts within the authorized example network.

### Step 6: Identify Services

```bash
nmap -sV 192.0.2.10
```

Purpose: Identify services and their versions on the authorized test host.

### Step 7: Analyze Technologies

```bash
whatweb https://example.com
```

Purpose: Identify technologies exposed by the website.

### Step 8: Review and Document Findings

```text
Reconnaissance Summary

Target: example.com

Collected Information:
- Domain registration details
- DNS records
- Authorized network discovery results
- Identified services
- Web technology information

Status: Information gathering completed.

Next Step: Review findings and determine areas
requiring further authorized security assessment.
```

The above is an illustrative workflow. The example IP addresses are reserved for documentation and are not real target systems.

## 7. Factors Affecting Reconnaissance

Several factors can affect the quality and completeness of reconnaissance.

| Factor | Impact |
|---|---|
| Firewall Rules | May block or filter network probes. |
| DNS Configuration | May limit available DNS information. |
| Rate Limiting | May restrict repeated requests. |
| WHOIS Privacy | May hide registration details. |
| CDN and WAF | May obscure the origin infrastructure. |
| Cloud Infrastructure | Assets may change dynamically. |
| Network Segmentation | May restrict visibility into internal systems. |
| Outdated Data | May result in incorrect conclusions. |

Understanding these limitations is important when analyzing reconnaissance results.

## 8. Best Practices

1. Always define the assessment scope before starting.
2. Begin with appropriate passive information gathering.
3. Use reliable information sources.
4. Choose tools according to the assessment requirements.
5. Verify important findings.
6. Avoid unnecessary scanning.
7. Maintain a record of commands and observations.
8. Respect rate limits and testing restrictions.
9. Separate observations from confirmed vulnerabilities.
10. Document limitations and recommendations.

## 9. Common Mistakes

- Performing reconnaissance without defining the target scope.
- Using tools without understanding their purpose.
- Assuming that every discovered asset belongs to the target.
- Ignoring false positives.
- Treating open ports as confirmed vulnerabilities.
- Skipping information verification.
- Failing to document findings.
- Performing active testing outside the approved scope.

## 10. Key Takeaways

- Reconnaissance methodology provides a structured approach to information gathering.
- Scope definition is essential before performing security testing.
- Passive and active reconnaissance can be combined.
- Domain, DNS, network, and web information are important parts of reconnaissance.
- Tool outputs must be analyzed and verified.
- Documentation makes reconnaissance findings useful for further assessment.
- Every activity must follow the agreed authorization and testing boundaries.

## 11. Interview Questions

**Q1. What is reconnaissance methodology?**

It is a structured process used to collect, organize, verify, and analyze information about a target during a security assessment.

**Q2. Why is scope definition important?**

It establishes which assets and activities are authorized for testing and prevents unauthorized assessment activities.

**Q3. What is the first step in reconnaissance methodology?**

Identifying the target and understanding the assessment objectives, followed by defining the authorized scope.

**Q4. What is asset discovery?**

Asset discovery is the process of identifying systems, domains, subdomains, IP addresses, applications, and other resources associated with a target.

**Q5. What is service identification?**

It is the process of determining which services are running on discovered systems and, where possible, identifying their versions.

**Q6. Why is information verification important?**

It helps identify inaccurate results, outdated information, and false positives before using findings in an assessment.

**Q7. What is the role of Nmap in reconnaissance?**

Nmap helps discover hosts, scan ports, identify services, and gather network information.

**Q8. What is the difference between asset discovery and vulnerability assessment?**

Asset discovery identifies systems and resources, whereas vulnerability assessment evaluates those assets for potential security weaknesses.

**Q9. Why is documentation important in reconnaissance?**

It provides a record of the information collected, tools used, observations, and limitations for future analysis and reporting.

**Q10. Can reconnaissance be performed without active scanning?**

Yes. Passive reconnaissance can gather considerable information using public sources without directly scanning target systems.

## 12. References and Further Learning

- [Nmap Official Documentation](https://nmap.org/book/man.html)
- [OWASP Web Security Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [MITRE ATT&CK - Reconnaissance](https://attack.mitre.org/tactics/TA0043/)
- [Amass Documentation](https://owasp.org/www-project-amass/)
- [ProjectDiscovery Documentation](https://docs.projectdiscovery.io/)

---

**Learning Note:** This document is part of my cybersecurity training notes. I documented the reconnaissance methodology to understand how security professionals plan information gathering, identify assets, analyze technical information, verify findings, and prepare reports during authorized security assessments.
