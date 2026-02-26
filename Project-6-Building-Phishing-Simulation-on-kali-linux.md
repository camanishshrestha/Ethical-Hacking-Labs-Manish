# Project 6: Simulating and Defending Against Phishing Attacks on Kali Linux

## Introduction
In this project, I simulated phishing attacks using Kali Linux and Gophish to understand how attackers trick users into revealing sensitive information. My goal was to safely create phishing campaigns for educational purposes and learn how to implement effective defenses against these attacks.

This exercise strengthened my knowledge of social engineering techniques and reinforced cybersecurity awareness strategies.

---

## Lab Environment

### Setup Overview

Attacker Machine: Kali Linux  
Target Machine: Lab test victim machine (authorized environment)

Kali Linux ↔ Victim Machine

---

## Tools Used

- Kali Linux (penetration testing OS)
- Gophish (open-source phishing framework)
- Email account (for sending simulated phishing emails)
- Web server (Apache or similar for hosting landing pages)
- Browser for campaign testing and monitoring

---

## Environment Setup

### Installing Gophish

1. Download the latest Gophish release from the [official repository](https://github.com/gophish/gophish/releases).  
2. Extract the package:

```bash
tar -xvzf gophish-vX.X.X-linux-64bit.tar.gz
```

3. Navigate to the extracted directory and run Gophish:

```bash
cd gophish
sudo ./gophish
```

4. Access the Gophish web interface:

```
https://localhost:3333
```

Default credentials: `admin` / `gophish`.

---

## Activities Performed

### 1. Setting Up a Phishing Campaign

- Created a target user group with authorized test email addresses.  
- Designed a phishing email template.  
- Configured a landing page to capture credentials.  
- Launched a phishing campaign using the user group, template, and landing page.

Expected Outcome: A functional phishing campaign ready to send simulated emails.

---

### 2. Launching the Phishing Campaign

I created a convincing phishing email template:

```html
<html>
<body>
  <h2>Dear User,</h2>
  <p>We have noticed suspicious activity on your account. Please verify your account information by clicking the link below:</p>
  <p><a href="http://192.168.1.100:8080/verify">Verify Account</a></p>
  <p>If you do not verify your account within 24 hours, your account will be locked.</p>
  <p>Thank you,<br>Your Company Support Team</p>
</body>
</html>
```

Expected Outcome: Users are prompted to click the link, simulating real-world phishing behavior in a controlled lab.

---

### 3. Analyzing Phishing Campaign Results

I reviewed the captured campaign data to identify which users “fell” for the phishing simulation and analyzed submitted credentials.  

Expected Outcome: A detailed report on campaign effectiveness and insights into user susceptibility.

---

### 4. Defending Against Phishing Attacks

I implemented and recommended measures to improve defenses:

- Educated users to recognize phishing emails.  
- Enabled email filtering to block suspicious messages.  
- Implemented multi-factor authentication (MFA).  
- Ensured systems are updated and patched regularly.

Expected Outcome: Improved security awareness and reduced risk of phishing attacks.

---

### 5. Phishing Awareness Program

I designed a recurring phishing awareness program:

- Scheduled regular phishing simulations using Gophish.  
- Tracked user performance and improvements over time.  

Expected Outcome: Enhanced employee awareness and stronger organizational resilience against phishing threats.

---

## Key Skills Demonstrated

- Setting up phishing campaigns in a lab environment  
- Crafting convincing email templates and landing pages  
- Collecting and analyzing phishing campaign data  
- Implementing technical and educational defenses against phishing  
- Designing phishing awareness programs for security education

---

## Conclusion

Through this project, I gained hands-on experience in both creating and defending against phishing attacks in a safe environment. This strengthened my understanding of social engineering threats and demonstrated the importance of combining technical controls with user education to enhance cybersecurity.

---

## References

- [Gophish Documentation](https://getgophish.com/)  
- Kali Linux Documentation  
- Anti-Phishing Working Group  
- Phishing Defense Guides
