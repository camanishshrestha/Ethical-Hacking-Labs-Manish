# Project 4: Deploying and Monitoring a Cowrie Honeypot on Kali Linux

## Introduction
In this project, I deployed and monitored a Cowrie honeypot on Kali Linux to study attacker behavior in a controlled lab environment. My objective was to simulate exposed SSH/Telnet services, capture unauthorized access attempts, and analyze malicious activity logs.

This project helped me understand how honeypots work as defensive security tools and how security teams collect threat intelligence from real-world attack patterns.

---

## Lab Environment

### Setup Overview

Attacker Machine: Simulated attacker (local testing)  
Honeypot Server: Cowrie (Docker container on Kali Linux)

Attacker ↔ Cowrie Honeypot (SSH:2222 / Telnet:2223)

---

## Tools Used

- Kali Linux (security testing OS)
- Cowrie (SSH/Telnet medium-interaction honeypot)
- Docker (containerized deployment)
- Splunk (SIEM for log monitoring and alerting)
- jq (JSON log parsing tool)

---

## Environment Setup

### 1. Installing Docker

```bash
sudo apt-get update
sudo apt-get install docker.io
sudo systemctl start docker
sudo systemctl enable docker
```

### 2. Pulling Cowrie Docker Image

```bash
sudo docker pull cowrie/cowrie
```

### 3. Running the Cowrie Container

```bash
sudo docker run -d -p 2222:2222 -p 2223:2223 --name cowrie cowrie/cowrie
```

Cowrie was now listening on:
- Port 2222 (SSH)
- Port 2223 (Telnet)

---

## Activities Performed

### 1. Verifying Honeypot Deployment

I confirmed the container was running:

```bash
sudo docker ps
```

This verified that the honeypot service was active.

---

### 2. Simulating an SSH Attack

To test the honeypot, I attempted an SSH login:

```bash
ssh root@localhost -p 2222
```

I entered random credentials to simulate a brute-force attempt.  
Cowrie responded with a fake shell environment while logging all activity.

---

### 3. Monitoring Honeypot Logs

I reviewed real-time logs using:

```bash
sudo docker logs cowrie
```

This showed:
- Username attempts
- Password attempts
- Source IP information
- Commands executed

---

### 4. Analyzing Captured Session Data

I accessed the container shell:

```bash
sudo docker exec -it cowrie /bin/bash
cd /srv/cowrie/var/log/cowrie
```

Then I analyzed structured logs:

```bash
cat cowrie.json | jq '.'
```

This provided detailed JSON entries of captured attack sessions.

---

## Log Forwarding and SIEM Integration

### 5. Forwarding Logs to Splunk

I configured Cowrie to forward logs to Splunk:

```bash
sudo docker exec -it cowrie /bin/bash
nano /srv/cowrie/cowrie.cfg
```

I added:

```
[output_splunk]
enabled = true
token = <SPLUNK_HEC_TOKEN>
http_event_collector = https://<SPLUNK_IP>:8088/services/collector/event
sourcetype = cowrie
```

Then I restarted the container:

```bash
sudo docker restart cowrie
```

This enabled centralized log monitoring.

---

### 6. Creating Custom Alerts in Splunk

Inside Splunk, I searched for honeypot events:

```
sourcetype="cowrie"
```

I configured alerts for:
- Multiple failed login attempts
- Suspicious command execution
- Repeated access from the same IP

This allowed automated detection of suspicious behavior.

---

### 7. Visualizing Honeypot Data

I created dashboards in Splunk to visualize:
- Number of login attempts
- Top attacking IP addresses
- Most common commands executed
- Attack frequency over time

This provided insight into attacker behavior patterns.

---

## Key Skills Demonstrated

- Deploying a containerized honeypot
- SSH/Telnet attack simulation
- Log monitoring and analysis
- JSON log parsing
- SIEM integration
- Creating detection alerts
- Security event visualization
- Understanding attacker behavior patterns

---

## Conclusion

Through this project, I gained practical experience deploying and monitoring a honeypot to collect threat intelligence in a controlled lab environment. I learned how security teams detect and analyze malicious activity using centralized logging and SIEM tools.

This project strengthened my understanding of:
- Defensive security monitoring
- Threat detection workflows
- Real-world attack simulation
- Incident response preparation

All activities were conducted in an authorized and isolated lab environment for educational and research purposes.
