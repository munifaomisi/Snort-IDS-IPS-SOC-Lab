# Snort IDS/IPS — SOC Traffic Analysis Lab

Hands-on learning portfolio documenting network traffic inspection, packet logging, PCAP investigation, and introductory detection engineering with **Snort 2** in a TryHackMe training environment.

> **Scope:** Educational lab documentation. Example rules below are illustrative; they are not claimed to have been deployed in production. Lab screenshots and packet captures should be reviewed for sensitive information before publication.

## Learning objectives
- Inspect packet metadata: source/destination IPs and ports, TTL, IP ID, TCP flags, ACK values.
- Capture and review network traffic using Snort's packet logger.
- Read offline packet captures and interpret Snort summaries.
- Understand how custom Snort rules match protocol, addresses, ports, and flags.

## Repository layout
| Path | Purpose |
| --- | --- |
| `docs/lab-notes.md` | Reproducible commands and observations |
| `docs/rule-anatomy.md` | Snort rule structure and safe examples |
| `rules/example.rules` | Educational Snort 2 rules |
| `evidence/README.md` | Screenshot checklist and evidence hygiene |

## Example commands
```bash
snort -V
sudo snort -dev -l .
sudo snort -r sample.pcap -n 10 -v
sudo snort -c /etc/snort/snort.conf -A full -l . -r sample.pcap
```

`sample.pcap` is a placeholder. Use authorized lab files only.

## Observed training work
During the Snort training exercise, packet logging and offline analysis were used to inspect packet IDs, TCP fields, and source ports. One exercise identified UDP source port `3009` for traffic to destination port `53`; another identified IP ID `49313` in the tenth packet of a supplied capture. These are training-specific observations, not general indicators of compromise.

## Limitations and next steps
- Add screenshots of actual commands, rule tests, and alert output with timestamps.
- Validate each sample rule against authorized test traffic before claiming detection performance.
- Document false positives, expected matches, and differences between IDS and IPS configurations.

## Attribution
This independent learning portfolio was prepared following a **TryHackMe Snort** lab. TryHackMe materials and original cheat sheets are not redistributed here. This repository is not affiliated with TryHackMe or Snort.

**Author:** Munif Alomisi
