# OSINT & Packet Analysis Lab

## Overview

This lab combined two foundational security exercises:

1. collecting publicly available technical information about an organization; and
2. inspecting HTTP traffic from an intentionally vulnerable web application with Wireshark.

The work was limited to training/public information and controlled lab traffic.

## What I Practiced

### Public-source reconnaissance
- Domain and hosting research
- Technology identification
- WAF/load-balancer checks
- Public certificate/subdomain sources
- Subdomain enumeration and reachability validation
- Reviewing publicly indexed exposure data

### Packet analysis
- Capturing traffic in Wireshark
- Filtering HTTP POST traffic
- Following an HTTP stream
- Observing how unencrypted HTTP can expose submitted credentials in clear text

## Tools

Netcraft, IP2Location, Wappalyzer, `wafw00f`, Subfinder, Assetfinder, crt.sh, httprobe/httpx, Shodan, and Wireshark.

## Evidence

- [OSINT methodology](./docs/osint-methodology.md)
- [Packet-analysis notes](./docs/packet-analysis.md)
- [Screenshot evidence](./screenshots/README.md)
- [Original lab notes](./docs/original-lab-notes.pdf)

## Status

**Completed as a training lab** — public-source reconnaissance and HTTP packet inspection were practiced and documented.
