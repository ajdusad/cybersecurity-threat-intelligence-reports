Technical Analysis Report

Case: pausitefin.site Malicious Domain

Analyst: Anurag Dusad  
Date: 08 February 2025  
Classification: Public  

---

## Discovery

While helping a friend troubleshoot their laptop, I noticed something unusual - a website automatically loaded and immediately went fullscreen without any user interaction. The domain was pausitefin.site. This behavior immediately raised red flags as legitimate websites don't force fullscreen mode without permission.

The unauthorized fullscreen activation, combined with the suspicious automatic behavior, prompted me to conduct a deeper investigation.

---

## Investigation Process

### DNS Analysis

I started with basic DNS reconnaissance to understand the domain infrastructure:
```bash
nslookup pausitefin.site
dig pausitefin.site
```

**What I found:**
- Domain: pausitefin.site
- Uses .site TLD (which I've noticed is often abused by malicious actors)
- The domain appeared to be inactive when I checked later

### IP Information

Through DNS lookups, I identified the IP address: **86.54.24.187**

I ran a WHOIS query to gather more details about the hosting:
```bash
whois 86.54.24.187
```

This gave me information about the geolocation and hosting provider.

---

## Network Scanning

I used Nmap to scan the identified IP for open ports and services:
```bash
nmap -sV -sC 86.54.24.187
```

The scan helped me identify what services were running and potential attack surfaces. I documented the open ports and service versions for the report.

---

## Understanding the Threat

### What I Observed

The most concerning behavior was the **forced fullscreen activation**:
- Happened automatically when the page loaded
- No permission dialog
- No warning message
- User had no control

This type of behavior is typically seen in:
- Scareware (fake virus warnings)
- Tech support scams
- Browser locker attacks
- Phishing campaigns

### My Assessment

Based on my analysis, I classified this as:
- **Type:** Malicious website with potential malware delivery
- **Severity:** Medium (concerning but no confirmed data breach)
- **Confidence:** High (behavior is clearly malicious)

The forced fullscreen technique is designed to panic users and prevent them from easily closing the tab or window.

---

## Infrastructure Findings

### Domain Details

- **Domain:** pausitefin.site
- **Status:** Went offline shortly after discovery
- **Pattern:** Short-lived domain, typical of malicious campaigns

The fact that it went offline so quickly suggests either:
1. It was part of a temporary campaign
2. It got detected and taken down
3. The attackers rotated to a new domain

### Network Information

- **IP Address:** 86.54.24.187
- Hosting details gathered through WHOIS
- Geolocation data documented

---

## Additional Research

I checked several threat intelligence sources to see if this domain was already known:

- **VirusTotal** - Checked for previous scans
- **URLhaus** - Searched malicious URL database
- **PhishTank** - Checked phishing reports
- **AbuseIPDB** - Looked up IP reputation

The limited historical data suggested this was a new or very short-lived campaign.

---

## Indicators of Compromise (IOCs)

Here's what security teams should block:

**Domain:**
```
pausitefin.site
```

**IP Address:**
```
86.54.24.187
```

**Behavioral Signatures:**
- Automatic fullscreen trigger
- No user interaction required
- Immediate activation on page load

**Detection Rules (for Snort/Suricata):**
```
alert dns any any -> any any (msg:"Malicious Domain pausitefin.site"; dns_query; content:"pausitefin.site"; nocase; sid:1000001;)
alert ip any any -> 86.54.24.187 any (msg:"Connection to Malicious IP 86.54.24.187"; sid:1000002;)
```

---

## Timeline

Here's how the investigation unfolded:

| Time | What I Did |
|------|------------|
| Initial | Friend showed me the strange fullscreen behavior |
| +5 min | Started DNS lookups |
| +15 min | Ran Nmap scan |
| +30 min | Completed WHOIS investigation |
| +45 min | Checked threat intelligence databases |
| +60 min | Documented all findings |
| +90 min | Submitted report to Cyber Crime Portal |

---

## Actions Taken

### What I Did
- Documented the domain and IP
- Extracted all IOCs
- Filed report with National Cyber Crime Portal (Acknowledgment: 2190228001720)
- Created this public documentation

### Recommendations

**For regular users:**
1. Keep your browser updated
2. Use ad blockers and security extensions (like uBlock Origin)
3. Be suspicious of unexpected fullscreen behavior
4. Report anything unusual

**For organizations:**
1. Add pausitefin.site to your DNS blocklists
2. Block IP 86.54.24.187 at firewall level
3. Train users to recognize these patterns
4. Monitor for similar suspicious domains

**For the security community:**
5. Share these IOCs with threat intel platforms
6. Watch for similar domain patterns
7. Track this threat actor's infrastructure

---

## What I Learned

This investigation taught me several important lessons:

**1. Act Fast**
Malicious domains don't stay up long. If I'd waited even a day, I might have lost critical evidence.

**2. Documentation Matters**
Taking detailed notes during the investigation made it much easier to write this report and submit to authorities.

**3. Report Everything**
Even if a threat seems "small" or is already offline, reporting it helps build the bigger picture of threat campaigns.

**4. Use Multiple Channels**
I didn't just report to one place - I'm documenting publicly and plan to submit to multiple threat intel platforms.

---

## Conclusion

I successfully identified, analyzed, and reported this malicious domain. The forced fullscreen behavior is consistent with scareware and malware delivery techniques I've studied.

The domain went offline quickly (probably detected by security systems or part of a rotating campaign), but the IOCs and behavioral patterns I documented can help detect similar threats.

I've shared this analysis publicly to help others recognize these patterns and contribute to community defense.

### What's Next

I plan to:
- Keep monitoring for this domain reactivating
- Watch for similar registration patterns
- Submit IOCs to URLhaus, VirusTotal, and other platforms
- Continue documenting threats I encounter

---

**Report Status:** Complete  
**Date:** February 2025  
**Shared:** Public domain for community benefit
