# Snort Lab Notes

## Environment
- Training platform: TryHackMe Snort room
- Tool: Snort 2.9.x (as shown in training terminal)
- Host: Linux lab VM

## Packet logging
```bash
mkdir -p ~/snort-lab
cd ~/snort-lab
sudo snort -dev -l .
```
Use a separate authorized terminal to generate test traffic. Stop with Ctrl+C. Snort creates root-owned logs when run with `sudo`.

## Read a packet log
```bash
sudo snort -r ./snort.log.EXAMPLE -n 10 -v
```
Replace `snort.log.EXAMPLE` with the real filename. Check packet headers and packet order rather than treating every occurrence of `ID:` as the same field.

## Offline PCAP inspection
```bash
sudo snort -r ./sample.pcap -n 10 -dev
sudo snort -c /etc/snort/snort.conf -A full -l . -r ./sample.pcap
```
`sample.pcap` is a placeholder. Counts and alerts depend on rules, configuration, and capture contents.

## Lab observations
| Field | Observed training value | Interpretation |
| --- | --- | --- |
| UDP source port | 3009 | Source port of packet destined for UDP/53 in the exercise |
| IPv4 ID (packet 10) | 49313 | IP header identification field in the tenth recorded packet |

## Analyst checklist
1. Record command, capture name, and configuration used.
2. Note packet counts, alert totals, and exact filters.
3. Verify findings in raw packet details.
4. Separate observations from conclusions.
5. Redact private data before sharing evidence.
