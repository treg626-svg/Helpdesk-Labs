# Raspberry Pi Helpdesk Lab – DNS Troubleshooting

## Objective
Simulate and troubleshoot a network connectivity issue caused by DNS misconfiguration.

## Environment
- Raspberry Pi (Raspberry Pi OS)
- Remote access via SSH from Windows
- Linux command line tools (ping, nslookup, dig)

## Scenario
A user reports: "Internet is not working."

## Troubleshooting Steps

### 1. Verify Connectivity
Tested network connectivity using:

ping -c 4 google.com

**Initial test confirmed internet access was working.**

### 2. Simulate Issue (DNS Failure)
Editted DNS configuartion file:
sudo nano/etc/resolv.conf
changed: nameserver 192.168.1.1
To: nameserver 0.0.0.0
This caused the DNS to show failure

### 3. Identify the Issue

Tested domain vs IP connectivity:
ping google.com
Result: Succesful

Conclusion:
Network Connectivitiy is working
DNS resolution was the issue

### 4. Restore DNS Configuration

Updated DNS to a valid server:
nameserver 8.8.8.8
ping google.com

Result: Successsful

### 5. DNS Performance Comparison
Compared DNS response times using:
nslookup google.com
dig google.com

Findings:
Local DNS (192.168.1.1) responded faster than public DNS (8.8.8.8)
Likely due to lower latency and fewer movements

## Key Takaways
Determined difference between IP connectivity and DNS resolution
DNS configuartion in Linux
Ability to compare and evaluate DNS performance

## Skills Demonstrated
- Network troubleshooting
- Linux command line
- DNS configuration and analysis
- Remote system support via SSH

## Commands Used
- ping google.com
- ping 8.8.8.8
- ip a
- nslookup google.com
- dig google.com
- sudo nano /etc/resolv.conf

## Outcome
Successfully diagnosed and resolved a DNS issue by isolating the problem and restoring proper configuration.
Identified DNS misconfiguration within minutes by comparing IP and domain-based connectivity tests.
