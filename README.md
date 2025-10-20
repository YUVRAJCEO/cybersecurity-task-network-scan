# Cybersecurity Task 1 – Nmap Network Scan

A focused network enumeration of a local host to identify exposed services, assess risk, and provide actionable hardening steps.

## Overview

This repository contains sanitized outputs from an Nmap scan performed against a single internal host for lab/reporting purposes. Sensitive IPs and MACs have been masked for privacy. The goal is to enumerate open ports, map them to common services, evaluate risk, and document remediations.

## Scan Summary

* Host detected: 10.x.x.2 (masked)
* Open ports found: 53/tcp, 80/tcp, 443/tcp, 2000/tcp
* Key observations: Standard DNS and web services are accessible; TCP/2000 may be related to Cisco SCCP or a device/application port and should be validated.

## Findings Table

| Host     | Port     | Protocol | Service           | Typical Use                | Risk Level |
| -------- | -------- | -------- | ----------------- | -------------------------- | ---------- |
| 10.x.x.2 | 53/tcp   | TCP      | DNS               | Name resolution            | Medium     |
| 10.x.x.2 | 80/tcp   | TCP      | HTTP              | Web service (unencrypted)  | Medium     |
| 10.x.x.2 | 443/tcp  | TCP      | HTTPS             | Secure web service         | Low        |
| 10.x.x.2 | 2000/tcp | TCP      | Cisco SCCP/custom | Device communication/admin | Medium     |

## Observations

* Multiple standard web and DNS services are detected.
* Port 2000 may belong to management or VoIP services.
* Open ports should be validated and only required services should be exposed.

## Recommendations

1. Restrict access to trusted internal clients via firewall or ACLs.
2. Close or disable unused ports to reduce attack surface.
3. Keep all software patched and up-to-date.
4. Enforce HTTPS and security headers on web services.
5. Periodically audit network services with tools like Nmap to ensure compliance.

## Instructions for Reproduction

1. Run a TCP SYN scan with service detection:

   ```bash
   nmap -sS -sV -Pn -T4 10.x.x.2
   ```
2. Probe version details and scripts for web and DNS:

   ```bash
   nmap -sV --version-all -p 53,80,443,2000 10.x.x.2
   nmap --script http-enum,http-headers -p80,443 10.x.x.2
   nmap --script dns-recursion,dns-service-discovery -p53 10.x.x.2
   ```
3. Verify listening services on the host:

   * Linux: `ss -tulpn | grep -E ':53|:80|:443|:2000'`
   * Windows: `netstat -ano | findstr ":53" ":80" ":443" ":2000"`

## Deliverables

* `README.md` (this file)
* `network_scan_sanitized.txt` (sanitized Nmap output)


