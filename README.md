# nmap-port-scan-task
network port scanning with Nmap and Wireshark

# Task 1-2: Network Port Scanning with Nmap

## Objective
Discover open ports on devices in my local network to understand network exposure.

## Tools Used
- **Nmap** – for scanning the network and finding open ports
- **Wireshark** – for capturing and inspecting the scan traffic

## What I Did
1. Installed Nmap and confirmed it worked (`nmap --version`).
2. Found my local IP range using `ipconfig` → `192.168.1.0/24` (home Wi-Fi network).
3. Ran a TCP SYN scan: `nmap -sS 192.168.1.0/24`
4. Found 4 active devices: my router (`192.168.1.1`), my own PC (`192.168.1.103`), and two phones (`192.168.1.100`, `192.168.1.104`).
5. Captured the scan traffic with Wireshark and filtered it to the router's IP.
6. Reviewed the open ports found and noted potential risks.

## Results
Full output is in [`results/results/nmap-scan.txt`](results/results/nmap-scan.txt).
Wireshark capture is in [`results/results/wireshark-capture1.pcapng`](results/results/wireshark-capture1.pcapng), with a screenshot in [`results/results/Screenshot 2026-10-02 215713.png`](results/results/Screenshot%202026-10-02%20215713.png).

### Key Findings
| Device | Notable Open Ports | Risk Note |
|---|---|---|
| Router (192.168.1.1) | 80 (http), 443 (https), 1900 (upnp) | Admin page reachable over unencrypted HTTP; UPnP can open ports automatically |
| My PC (192.168.1.103) | 445 (microsoft-ds), 3306 (mysql) | SMB file sharing exposed on LAN; MySQL server running and listening |
| Phones (192.168.1.100, .104) | None found | All ports filtered or closed — expected, good result |

## Outcome
Practiced basic network reconnaissance: discovering devices on a network, identifying open ports, and understanding what those ports expose.
