# Pickle Rick – TryHackMe CTF Report

## 1. Overview
- **Category:** Web Exploitation, Linux Privilege Escalation
- **Platform:** TryHackMe
- **Difficulty:** Easy
- **Objective:** Enumerate the target system, exploit web application weaknesses, and escalate privileges to retrieve the required artifacts.

---

## 2. Enumeration

### Network Enumeration
- Performed an initial network scan to identify open ports and running services.
- Discovered an HTTP service exposed on the target.

### Web Enumeration
- Accessed the web application through the browser.
- Reviewed page source and discovered comments indicating potential hidden directories.
- Enumerated directories using a wordlist-based approach, which revealed an administrative interface.

### Key Observations
- Web application lacked proper access controls.
- Input fields appeared to be passed directly to the system without sanitization.

---

## 3. Exploitation

### Web Exploitation
- Gained access to an administrative command execution feature.
- Identified that user-supplied input was executed directly on the system.
- Leveraged this behavior to execute system commands via the web interface.

### Initial Access
- Used command execution to explore the filesystem.
- Located files containing the first required artifact.
- Identified a user account with restricted privileges.

---

## 4. Privilege Escalation

### Enumeration for Privilege Escalation
- Enumerated sudo permissions and system binaries.
- Identified misconfigured permissions that allowed execution of commands with elevated privileges.

### Exploitation
- Used allowed commands to escalate from a low-privileged user to root-level access.
- Successfully accessed protected directories and files.

---

## 5. Result

- Retrieved all required challenge artifacts by combining:
  - Web-based command execution
  - Local enumeration
  - Privilege escalation techniques
- Confirmed full system compromise within the scope of the challenge.

*(Screenshots and evidence are stored in the screenshots/ directory.)*

---

## 6. Security Impact

If exploited in a real-world environment, these vulnerabilities could lead to:
- Remote Code Execution (RCE)
- Full system compromise
- Unauthorized access to sensitive data
- Complete loss of confidentiality, integrity, and availability

Severity: **High**

---

## 7. Mitigation & Recommendations

- Disable command execution functionality in web applications.
- Implement strict input validation and sanitization.
- Enforce proper authentication and authorization controls.
- Apply the principle of least privilege for system users.
- Regularly audit sudo permissions and system configurations.

---

## 8. Lessons Learned

- Proper enumeration is critical before exploitation.
- Even simple misconfigurations can lead to full compromise.
- Web vulnerabilities combined with privilege escalation significantly increase impact.
- Secure coding and system hardening are essential to prevent such attacks.

