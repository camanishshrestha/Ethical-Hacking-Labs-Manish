# Project 3: Cracking Password Hashes Using John the Ripper on Kali Linux

## Introduction
In this project, I explored password cracking techniques using John the Ripper on Kali Linux. My goal was to understand how password hashes can be analyzed and cracked in a controlled, legal lab environment. This exercise helped me identify weak passwords and understand the importance of enforcing strong password policies.

---

## Lab Environment

### Setup Overview

Attacker Machine: Kali Linux  
Target System: Sample hash files or shadow file (authorized lab environment)

Kali Linux ↔ Target System (hash files)

---

## Tools Used

- Kali Linux (penetration testing OS)
- John the Ripper (password cracking tool)
- Sample password hash files
- Optional: Shadow file from a lab system

---

## Verifying Installation

John the Ripper is pre-installed on Kali Linux. I verified or updated it using:

```bash
sudo apt-get update && sudo apt-get install john
```

---

## Activities Performed

### 1. Basic Password Cracking

I created a sample password hash file:

```bash
echo '$1$KpixtOtB$VVujBpNkbVnv1BjlBJl6S/' > passwords.txt
```

Then I ran John the Ripper to crack the hashes:

```bash
john passwords.txt
```

This allowed me to see how simple hashes can be decrypted if weak passwords are used.

---

### 2. Using a Custom Wordlist

I created a custom wordlist to test password variations:

```bash
echo -e "password\n123456\nletmein\nqwerty" > wordlist.txt
```

Then I ran John using the custom wordlist:

```bash
john --wordlist=wordlist.txt passwords.txt
```

This demonstrated the effectiveness of dictionary attacks.

---

### 3. Cracking Shadow File Hashes

For authorized lab practice, I extracted hashes from a sample shadow file:

```bash
unshadow /etc/passwd /etc/shadow > shadow_hashes.txt
```

Then I cracked the hashes using:

```bash
john shadow_hashes.txt
```

This helped me understand real-world password storage and hash cracking scenarios.

---

### 4. Incremental Mode Cracking

I experimented with brute-force attacks using John’s incremental mode:

```bash
john --incremental passwords.txt
```

This showed how exhaustive methods can recover passwords not in a wordlist.

---

### 5. Rules-Based Password Cracking

I applied rules-based attacks to enhance cracking efficiency:

```bash
john --rules passwords.txt
```

This allowed John to manipulate inputs based on common patterns to discover more passwords.

---

### 6. Analyzing Cracked Passwords

Finally, I analyzed the cracked passwords to identify weaknesses:

```bash
john --show passwords.txt
```

This provided insights into common password patterns and highlighted the importance of strong password policies.

---

## Key Skills Demonstrated

- Understanding of password hashing and encryption
- Hash extraction and management
- Using John the Ripper for dictionary, brute-force, and rules-based attacks
- Analyzing password security and patterns
- Applying ethical hacking principles in a controlled lab

---

## Conclusion

Through this project, I gained practical experience in cracking password hashes and evaluating password strength in a safe lab environment. This reinforced the importance of secure password creation and proper hash storage in cybersecurity practices.

---

## References

- [John the Ripper Documentation](https://www.openwall.com/john/)
- Kali Linux Documentation
- Password Security Best Practices
- Comparisons between Hashcat and John the Ripper
