# TryHackMe - TakeOver Walkthrough

## Overview

**TakeOver** is a beginner-friendly TryHackMe room focused on reconnaissance and subdomain enumeration. The challenge demonstrates how forgotten or misconfigured subdomains can expose organizations to potential subdomain takeover vulnerabilities.

## Objectives

* Perform subdomain enumeration.
* Discover hidden virtual hosts and subdomains.
* Analyze DNS records and web responses.
* Identify potential takeover opportunities.

## Tools Used

* ffuf
* Browser Developer Tools

## Methodology

### 1. Initial Enumeration

Started by identifying the target domain and gathering information about its DNS configuration.

### 2. Subdomain Discovery

Used wordlists and fuzzing techniques to enumerate hidden subdomains.
This revealed additional subdomains that were not immediately visible.

### 3. Validation

Each discovered subdomain was manually validated using browser requests and DNS lookups to understand its configuration and purpose.

### 4. Analysis

Examined DNS records, response headers, and page content to identify misconfigurations that could indicate a takeover scenario.

### 5. Flag Retrieval

After identifying the vulnerable asset, followed the challenge path to obtain the final flag.

## Key Learnings

* Importance of thorough subdomain enumeration.
* Understanding virtual host fuzzing.
* DNS record analysis and validation.
* Recognizing indicators of subdomain takeover vulnerabilities.
* Avoiding false positives during reconnaissance.

## Conclusion

TakeOver is an excellent room for learning practical reconnaissance techniques and understanding how subdomain misconfigurations can lead to security risks. It reinforces the importance of proper DNS hygiene and continuous asset management.

**Room:** TryHackMe - TakeOver
**Category:** Web Reconnaissance / Subdomain Enumeration

