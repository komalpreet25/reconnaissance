# 02. Passive vs Active Reconnaissance

## 1. Introduction

Reconnaissance is an important part of cybersecurity and penetration testing. It involves collecting information about a target to understand its infrastructure, network, services, and potential attack surface.

There are two major approaches to reconnaissance:

1. Passive Reconnaissance
2. Active Reconnaissance

Both approaches help security professionals gather information, but they differ in how information is collected and whether the target's systems are directly contacted.

During my cybersecurity training, I learned that understanding the difference between passive and active reconnaissance is important before performing information-gathering activities or security assessments.

## 2. What Is Passive Reconnaissance?

Passive reconnaissance is an information-gathering technique in which information about a target is collected from publicly available sources without directly probing the target's infrastructure.

The main objective is to gather useful information while minimizing direct interaction with the target's systems.

### 2.1 How Passive Reconnaissance Works

Passive reconnaissance uses existing public information rather than sending scanning or probing requests directly to the target's systems.

Common information sources include:

- Search engines
- WHOIS databases
- Public DNS information
- Social media platforms
- Public websites
- Certificate Transparency logs
- Public code repositories
- Internet search engines and archives
- Publicly available threat intelligence platforms

### 2.2 Information Collected Through Passive Reconnaissance

| Information | Description |
|---|---|
| Domain Information | Domain names and registration details |
| IP Information | Publicly associated IP address information |
| DNS Records | Public DNS records and name servers |
| Email Addresses | Publicly available organizational email addresses |
| Subdomains | Subdomains discovered through public sources |
| Technologies | Publicly identifiable web technologies |
| Employee Information | Public professional information |
| Metadata | Information embedded in publicly available files |
| Certificates | Certificate information associated with domains |

### 2.3 Common Passive Reconnaissance Tools

| Tool | Purpose |
|---|---|
| WHOIS | Retrieves domain registration information |
| theHarvester | Collects publicly available emails, hosts, and related information |
| Maltego | Visualizes relationships between information sources |
| SpiderFoot | Automates OSINT information gathering |
| Shodan | Searches for internet-connected devices and services |
| Google Search | Finds publicly indexed information |
| Wappalyzer | Identifies website technologies |
| crt.sh | Searches Certificate Transparency records |
| Sherlock | Searches for usernames across social platforms |

### 2.4 Practical Commands for Passive Reconnaissance

**Example 1: WHOIS Lookup**

```bash
whois example.com
```

Purpose:
- Retrieves publicly available domain registration information.
- May identify the registrar and name servers.
- May show domain creation and expiration dates.

**Example 2: DNS Lookup**

```bash
nslookup example.com
```

Purpose:
- Queries DNS to resolve a domain.
- May return the associated IP address.
- Uses DNS infrastructure rather than a port scan.

**Example 3: Using dig**

```bash
dig example.com
```

Purpose:
- Retrieves DNS query information.
- Helps understand DNS responses.
- Can be used to inspect different DNS record types.

**Example 4: Certificate Transparency Search**

Visit:

https://crt.sh/

Search for:

```text
%.example.com
```

Purpose:
- Searches certificate records associated with a domain.
- May reveal domain names and subdomains included in publicly logged certificates.

**Important:** Passive reconnaissance does not necessarily mean zero interaction with external services. WHOIS servers, DNS resolvers, search engines, and OSINT platforms may receive your queries. The distinction is that you are not directly probing the target's infrastructure.

## 3. What Is Active Reconnaissance?

Active reconnaissance involves directly interacting with a target system or network to collect technical information.

Unlike passive reconnaissance, active reconnaissance sends requests, packets, or probes to the target.

Its purpose is to identify reachable hosts, open ports, running services, network configurations, and other technical details.

### 3.1 How Active Reconnaissance Works

Active reconnaissance typically involves sending network requests or probes and analyzing the responses.

Common activities include:

- Host discovery
- Port scanning
- Service and version detection
- Operating system fingerprinting
- Network mapping
- DNS enumeration
- Web server analysis
- Directory and endpoint discovery

### 3.2 Information Collected Through Active Reconnaissance

| Information | Description |
|---|---|
| Active Hosts | Identifies reachable systems |
| Open Ports | Identifies ports accepting connections |
| Running Services | Identifies services operating on ports |
| Service Versions | Attempts to identify software versions |
| Operating Systems | Estimates the operating system |
| Network Configuration | Helps understand network accessibility |
| Web Directories | Identifies accessible web paths |
| HTTP Responses | Provides information about web server behavior |

### 3.3 Common Active Reconnaissance Tools

| Tool | Purpose |
|---|---|
| Nmap | Host discovery, port scanning, and service detection |
| Masscan | High-speed port scanning |
| Netcat | Network connection testing |
| Telnet | Tests TCP connectivity to services |
| Gobuster | Directory and DNS discovery |
| FFUF | Web content and endpoint discovery |
| DNSenum | DNS enumeration |
| DNSrecon | DNS reconnaissance |
| Burp Suite | Web application request and response analysis |
| WhatWeb | Web technology identification |

### 3.4 Practical Commands for Active Reconnaissance

Perform these examples only against systems you own or have explicit permission to test.

**Example 1: Host Discovery**

```bash
nmap -sn 192.0.2.0/24
```

Explanation:

- `nmap` – Starts the Nmap scanning tool.
- `-sn` – Performs host discovery without a port scan.
- `192.0.2.0/24` – Documentation-only example network range.

Purpose:
- Checks for responsive hosts in the specified range.
- Helps identify potentially active systems.

**Example 2: TCP Port Scanning**

```bash
nmap -sT 192.0.2.10
```

Explanation:

- `-sT` – Performs a TCP connect scan.
- `192.0.2.10` – Documentation-only example IP address.

Purpose:
- Attempts to establish TCP connections to identify open ports.

**Example 3: Service Version Detection**

```bash
nmap -sV 192.0.2.10
```

Purpose:
- Attempts to identify services running on open ports.
- May identify software versions and service details.

**Example 4: Operating System Detection**

```bash
sudo nmap -O 192.0.2.10
```

Purpose:
- Attempts to estimate the target operating system using network responses.
- May require elevated privileges.
- Results are estimates and are not always accurate.

**Example 5: Web Technology Identification**

```bash
whatweb https://example.com
```

Purpose:
- Analyzes a website's responses.
- Attempts to identify technologies such as web servers, frameworks, and CMS platforms.

Only run this against an authorized website. Although the example domain is reserved for documentation, actual testing should use a permitted lab target.

## 4. Passive vs Active Reconnaissance: Key Differences

| Feature | Passive Reconnaissance | Active Reconnaissance |
|---|---|---|
| Interaction | No direct probing of target systems | Direct interaction with target systems |
| Information Source | Publicly available sources | Target responses |
| Network Traffic | Usually lower direct target traffic | Generates traffic toward target |
| Detection Risk | Generally lower at target | Generally higher |
| Information | Public and indirect information | Technical and direct information |
| Accuracy | May be outdated or incomplete | Provides direct observations, but has limitations |
| Tools | WHOIS, Shodan, Maltego | Nmap, Netcat, Gobuster |
| Main Purpose | Collect publicly available information | Identify technical details of target systems |
| Example | Searching public DNS records | Scanning authorized target ports |

## 5. Advantages and Disadvantages

### 5.1 Passive Reconnaissance

**Advantages**

- Usually does not generate direct scanning traffic toward the target.
- Lower risk of triggering target-side scanning alerts.
- Can collect information without testing the target's infrastructure.
- Helps build an initial understanding of the target.
- Useful for identifying publicly exposed information.

**Disadvantages**

- Information may be outdated.
- Public sources may contain incomplete information.
- Some assets may not appear in public databases.
- Findings may require further verification.
- Public information does not always reflect the current target infrastructure.

### 5.2 Active Reconnaissance

**Advantages**

- Provides direct technical observations.
- Helps identify reachable hosts and open ports.
- Supports service and version identification.
- Helps understand network and application behavior.
- Can reveal assets that public sources do not identify.

**Disadvantages**

- Generates traffic that may be detected by security monitoring systems.
- May trigger firewalls or intrusion detection systems.
- Can be blocked by network security controls.
- Improper scanning may affect system performance.
- Requires clear authorization and defined testing scope.

## 6. Real-World Reconnaissance Scenario

Consider a company named `example.com` that wants to understand its external attack surface.

A security professional may use both passive and active reconnaissance as part of an authorized assessment.

### Step 1: Passive Reconnaissance

The security professional collects publicly available information.

Activities:

- Search for domain registration information.
- Review publicly available DNS records.
- Search Certificate Transparency logs.
- Identify publicly documented subdomains.
- Review public website technologies.

Possible findings:

```text
Target Domain: example.com

Public Information:
- Domain registration details
- Name servers
- Public DNS records
- Certificate records
- Publicly identified subdomains
```

### Step 2: Active Reconnaissance

After receiving authorization and confirming the testing scope, the security professional performs technical checks.

Activities:

- Identify reachable hosts.
- Scan permitted IP addresses.
- Identify open ports.
- Detect running services.
- Analyze authorized web applications.

Possible findings:

```text
Target: Authorized Test Host

Host Status: Reachable
Port: 443/tcp
Service: HTTPS
Port: 80/tcp
Service: HTTP
```

### Step 3: Analyze the Results

The information from both approaches is combined to develop a better understanding of the target's external infrastructure.

The findings can then be used to plan further security assessments.

## 7. When Should Each Approach Be Used?

| Situation | Recommended Approach |
|---|---|
| Initial information gathering | Passive |
| Public domain research | Passive |
| Public email discovery | Passive |
| Certificate Transparency research | Passive |
| Identifying reachable hosts | Active |
| Identifying open ports | Active |
| Service version detection | Active |
| Network mapping | Active |
| Building an external asset inventory | Both |
| Authorized penetration testing | Both, according to scope |

A professional security assessment may combine both approaches. Passive reconnaissance often helps identify areas for further investigation, while active reconnaissance helps validate technical observations.

## 8. Common Mistakes

1. Assuming passive reconnaissance means absolutely no network communication.
2. Assuming active reconnaissance always requires exploitation.
3. Treating every result from public databases as accurate.
4. Performing active scans without authorization.
5. Confusing DNS lookups with port scanning.
6. Assuming that a successful host discovery proves all services are accessible.
7. Ignoring the assessment scope.
8. Treating discovered open ports as confirmed vulnerabilities.

## 9. Key Takeaways

- Reconnaissance has two major approaches: passive and active.
- Passive reconnaissance gathers information through public and indirect sources.
- Active reconnaissance interacts directly with target systems.
- Passive reconnaissance generally has a lower risk of target-side detection.
- Active reconnaissance provides direct technical observations but generates traffic.
- Tools such as WHOIS, Shodan, and theHarvester support passive information gathering.
- Tools such as Nmap, Gobuster, and Netcat support active reconnaissance.
- Both approaches are useful during authorized penetration testing.
- Authorization and scope must be established before active testing.

## 10. Interview Questions

**Q1. What is passive reconnaissance?**

Passive reconnaissance is the process of gathering information about a target using publicly available sources without directly probing its systems.

**Q2. What is active reconnaissance?**

Active reconnaissance involves directly interacting with target systems or networks to collect technical information.

**Q3. What is the main difference between passive and active reconnaissance?**

Passive reconnaissance relies on public and indirect information sources, whereas active reconnaissance sends requests or probes directly to target systems.

**Q4. Is WHOIS considered passive reconnaissance?**

Yes. WHOIS lookup is generally considered passive reconnaissance because it retrieves publicly available domain registration information through a lookup service.

**Q5. Is Nmap considered an active reconnaissance tool?**

Yes. Nmap can send network probes to identify hosts, open ports, and running services.

**Q6. Which type of reconnaissance is harder for the target to detect?**

Passive reconnaissance is generally harder for the target to detect because it does not directly probe the target's infrastructure.

**Q7. Can active reconnaissance trigger security alerts?**

Yes. Network scans, connection attempts, and other probing activities may be detected by firewalls, intrusion detection systems, and security monitoring solutions.

**Q8. Does active reconnaissance involve exploitation?**

No. Active reconnaissance focuses on information collection through direct interaction. Exploitation is a separate activity.

**Q9. Can both reconnaissance approaches be used together?**

Yes. They are often combined to gather public information and validate technical details during an authorized security assessment.

**Q10. Give an example of passive and active reconnaissance.**

Passive: Searching for publicly available DNS information.

Active: Using Nmap to scan an authorized host for open ports.

## 11. References and Further Learning

- [Nmap Documentation](https://nmap.org/book/man.html)
- [Shodan](https://www.shodan.io/)
- [WHOIS Lookup - ICANN](https://lookup.icann.org/)
- [Certificate Transparency Search](https://crt.sh/)
- [OWASP Web Security Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [MITRE ATT&CK - Reconnaissance](https://attack.mitre.org/tactics/TA0043/)

---

**Learning Note:** This document is part of my cybersecurity training notes. It covers the two major reconnaissance approaches, their working principles, commonly used tools, and practical examples to strengthen my understanding of information gathering and security assessments.
