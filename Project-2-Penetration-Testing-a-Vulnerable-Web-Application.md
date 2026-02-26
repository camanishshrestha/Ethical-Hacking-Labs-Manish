
# Project 2: Web Application Penetration Testing Using OWASP Juice Shop

## Introduction
In this project, I performed penetration testing on OWASP Juice Shop, a deliberately vulnerable web application designed for security training. My objective was to identify and exploit common web vulnerabilities in a controlled and authorized lab environment.

This hands-on project helped me understand how real-world web applications can be tested for security weaknesses using industry-standard tools.

---

## Lab Environment

### Setup Overview

Attacker Machine: Kali Linux  
Target Application: OWASP Juice Shop (running locally via Docker)

Kali Linux ↔ OWASP Juice Shop (localhost:3000)

---

## Tools Used

- Kali Linux (penetration testing operating system)
- OWASP Juice Shop (intentionally vulnerable web application)
- Burp Suite (web application interception proxy)
- Nmap (network scanning tool)
- Docker (to deploy Juice Shop locally)

---

## Environment Installation

### 1. Installing Docker

```bash
sudo apt-get update
sudo apt-get install docker.io
sudo systemctl start docker
sudo systemctl enable docker
```

### 2. Pulling OWASP Juice Shop Image

```bash
sudo docker pull bkimminich/juice-shop
```

### 3. Running OWASP Juice Shop

```bash
sudo docker run -d -p 3000:3000 bkimminich/juice-shop
```

I accessed the application via:

```
http://localhost:3000
```

---

## Security Testing Activities

### 1. Identifying Open Ports

I first scanned the target machine to identify open ports:

```bash
nmap 192.168.1.100
```

This allowed me to confirm exposed services and validate that the web application was reachable.

---

### 2. SQL Injection Testing

Using Burp Suite as an interception proxy (127.0.0.1:8080), I intercepted the login request.

I tested authentication bypass using the following payload:

```
' OR '1'='1
```

This demonstrated how improper input validation can allow attackers to bypass authentication mechanisms.

---

### 3. Cross-Site Scripting (XSS)

I tested reflected input fields (such as the search bar) using a basic XSS payload:

```
<script>alert('XSS')</script>
```

The execution of the script confirmed the presence of client-side input validation weaknesses.

---

### 4. File Upload Vulnerability Testing

I navigated to the profile upload feature and tested file upload restrictions by attempting to upload modified or potentially unsafe files.

This helped me analyze:
- File validation mechanisms
- Server-side filtering controls
- Execution risks

---

### 5. Directory Traversal Testing

Using Burp Suite, I intercepted HTTP requests and modified parameters to test directory traversal:

```
../../../etc/passwd
```

This demonstrated how improper path validation can allow unauthorized file access.

---

### 6. Cross-Site Request Forgery (CSRF)

I created a basic HTML form designed to perform an action on behalf of an authenticated user.

When executed while logged in, it demonstrated how the absence of anti-CSRF tokens could allow unauthorized state-changing actions.

---

## Key Skills Demonstrated

- Web application reconnaissance
- Intercepting and modifying HTTP requests
- SQL Injection testing
- Cross-Site Scripting (XSS) testing
- File upload security assessment
- Directory traversal testing
- CSRF attack simulation
- Understanding insecure design patterns

---

## Conclusion

Through this project, I gained hands-on experience identifying and exploiting common web vulnerabilities in a safe lab environment. This exercise strengthened my understanding of web application security testing methodologies and improved my ability to analyze insecure implementations from an attacker’s perspective while maintaining ethical standards.
