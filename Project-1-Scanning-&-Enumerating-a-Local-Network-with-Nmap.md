# Project 1: Network Scanning and Enumeration Using Nmap on Kali Linux

## Introduction
In this project, I performed network scanning and enumeration using Nmap on Kali Linux within a controlled and authorized lab environment. My objective was to understand how devices on a local network can be discovered, how open ports and running services can be identified, and how operating system detection works in real-world reconnaissance scenarios.

This hands-on exercise strengthened my practical understanding of network discovery and information gathering techniques used in ethical hacking.

---

## Environment Setup

### Tools Used
- Kali Linux (penetration testing operating system)
- Nmap (network scanning and enumeration tool)
- Local lab network with multiple connected devices

### Verifying Nmap Installation

```bash
sudo apt-get update && sudo apt-get install nmap
```

---

## Activities Performed

### 1. Basic Network Discovery Scan

I performed a scan to discover active devices on my local subnet:

```bash
nmap 192.168.1.0/24
```

This allowed me to identify:
- Live hosts
- Open ports
- Basic service information

---

### 2. Scanning Specific Ports

To check which systems were running web services, I scanned specifically for port 80:

```bash
nmap -p 80 192.168.1.0/24
```

This helped me determine which devices had HTTP services exposed.

---

### 3. Service Version Detection

To gather detailed service information, I enabled version detection:

```bash
nmap -sV 192.168.1.0/24
```

This revealed:
- Service names
- Software versions
- Additional service details

Understanding versions is critical for identifying potential vulnerabilities.

---

### 4. Operating System Detection

Next, I performed OS fingerprinting:

```bash
sudo nmap -O 192.168.1.0/24
```

This allowed me to:
- Identify probable operating systems
- Understand device types within the network

---

### 5. Aggressive Scan

Finally, I conducted an aggressive scan combining multiple enumeration techniques:

```bash
sudo nmap -A 192.168.1.0/24
```

This included:
- OS detection
- Version detection
- Default script scanning
- Traceroute

This provided comprehensive intelligence about the network.

---

## Key Skills Demonstrated

- Network reconnaissance
- Port scanning and enumeration
- Service and version identification
- Operating system fingerprinting
- Interpreting scan results for security analysis

---

## Conclusion

Through this project, I developed practical experience using Nmap for network discovery and enumeration in a legal lab setup. This exercise improved my understanding of how attackers gather information during the reconnaissance phase and reinforced the importance of proper network security configurations.
