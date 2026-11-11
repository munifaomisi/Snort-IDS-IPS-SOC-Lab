# Snort IDS/IPS — SOC Traffic Analysis Lab

**Author:** Munif Alomisi  
**Platform:** TryHackMe — [Snort room](https://tryhackme.com/room/snort)  
**Focus:** SOC Level 1 · Network Traffic Analysis · Detection Engineering

## Overview

This repository documents a hands-on learning lab using **Snort 2.x** for packet sniffing, packet logging, PCAP investigation, IDS alert interpretation, and introductory detection-rule development. It is a learning portfolio, **not** a production IDS deployment.

## Learning objectives

- Understand Snort's sniffer, logger, and IDS/IPS modes.
- Capture and inspect TCP, UDP, ICMP, and HTTP traffic.
- Read packet captures and identify IPv4 IDs, TCP ACKs, and HTTP Referer headers.
- Interpret Snort alert summaries and packet counts.
- Understand rule headers, options, `sid`, and `rev`.

## Repository contents

| Path | Purpose |
| --- | --- |
| `docs/lab-notes.md` | Commands, observations, and analysis workflow |
| `docs/rule-anatomy.md` | Explanation of Snort rule fields |
| `rules/example.rules` | Educational example detection rules (not production-ready) |
| `evidence/README.md` | Suggested screenshots and evidence hygiene |

## Quick start (isolated training environment)

```bash
snort -V
sudo snort -dev -l .
# Stop with Ctrl+C after generating authorized lab traffic
sudo snort -r /path/to/snort.log.TIMESTAMP -n 10 -v
```

To analyze a provided PCAP with the lab's Snort configuration:

```bash
sudo snort -c /etc/snort/snort.conf -A console -r /path/to/sample.pcap
```

**Note:** Run only on networks or capture files you own or are authorized to inspect. Use a dedicated lab VM; logs may contain sensitive data.

## Evidence and status

The lab screenshots showed successful packet logging and investigation, including a Snort 2.9.7.0 environment and a root-owned log file. The most recently observed room progress was **79%**; this repository does not claim completion or a certificate.

## Credits and attribution

- Training content and original **Snort 101** cheatsheet: **TryHackMe**, [Snort room](https://tryhackme.com/room/snort).
- The user-supplied TryHackMe cheatsheet is a **reference**, not an original work by this repository's author. It is intentionally not redistributed here.
- Snort is a project of its respective maintainers. This repository is an independent educational write-up, not affiliated with TryHackMe or Snort.

## Next steps

- Add verified, redacted screenshots from each exercise.
- Document individual rule tests and alert results.
- Compare expected and observed detections; reduce false positives.
