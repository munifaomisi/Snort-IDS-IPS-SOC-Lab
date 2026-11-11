# Hands-on Lab Notes — Snort 2.x

## 1. Verify installation

```bash
snort -V
```

The lab screenshot showed **Snort 2.9.7.0 GRE**.

## 2. Capture and log packets

```bash
mkdir -p ~/snort-lab
cd ~/snort-lab
sudo snort -dev -l .
```

`-d` prints payload data, `-e` prints Ethernet headers, `-v` prints packet details, and `-l .` selects the current log directory. Stop with `Ctrl+C`.

In the lab, a file named `snort.log.<timestamp>` was created and owned by `root`. Inspect ownership and size:

```bash
ls -lh ~/snort-lab
```

## 3. Generate authorized traffic

In another terminal, the lab used:

```bash
ping -c 5 8.8.8.8
```

The observed test had **100% packet loss**; this does not by itself mean capture failed. The TryHackMe lab also provides a `traffic-generator.sh` script to generate exercise traffic.

## 4. Inspect captured packets

```bash
sudo snort -r /path/to/snort.log.TIMESTAMP -n 10 -v
```

For the provided exercise file (where present in the TryHackMe VM):

```bash
sudo snort -r ~/Desktop/Task-Exercises/Exercise-Files/TASK-6/snort.log.1640048004 -n 10 -v
```

Look for the IPv4 `ID` field, TCP flags and acknowledgement number, and HTTP headers such as `Referer`. Do not confuse packet order with arbitrary grep matches unless each output line maps to exactly one packet.

## 5. ASCII logging

```bash
sudo snort -dev -K ASCII -l .
```

When run with `sudo`, generated directories may be owned by root. Inspect them with `sudo ls -l <directory>` instead of changing permissions unnecessarily.

## 6. PCAP analysis

```bash
sudo snort -c /etc/snort/snort.conf -A full -l . -r /path/to/sample.pcap
```

Compare the alert counts and protocol statistics from the output summary. Numbers vary by input capture and configuration.

## 7. Investigation checklist

- Identify source and destination IPs and ports.
- Identify protocol, TCP flags, and sequence/ACK values.
- Inspect relevant HTTP metadata without exposing sensitive content.
- Review rule IDs (`sid`), revisions (`rev`), and alert messages.
- Record exact commands, configuration, capture filename, and output evidence.

## Learning takeaway

Snort alerts are evidence to investigate, not proof of compromise. Correlate network findings with logs, endpoint context, and known baselines.
