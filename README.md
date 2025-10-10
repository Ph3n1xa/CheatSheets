# CheatSheets

Personal reference guides for penetration testing methodologies, tools, and techniques.

These cheat sheets are condensed notes from my HTB Academy training, labs, and practical experience.

---

## 📚 Available Cheat Sheets

### 🐧 [Linux Commands for Pentesting](./Linux-Commands.md)
Essential Linux commands for reconnaissance, exploitation, and post-exploitation.

**Topics Covered:**
- 20 Basics Pentesting Scripts
- File system navigation & manipulation
- User enumeration & permissions
- Process management & monitoring
- Network reconnaissance
- Privilege escalation techniques
- Data exfiltration methods

---

### 🌐 [Networking Fundamentals](./Networking-Basics.md)
Core networking concepts for penetration testing.

**Topics Covered:**
- OSI Model & TCP/IP stack
- Common ports & services
- Subnetting & CIDR notation
- Protocols (HTTP, FTP, SMB, SSH, RDP)
- Network scanning techniques
- Traffic analysis basics

---

### 🔍 [Nmap Cheat Sheet]
Comprehensive Nmap scanning reference.

**Topics Covered:**
- Nmap Basics Enumeration Pentester

---

### 🌐 [OWASP Top 10 Vulnerabilities](./OWASP-Top10.md)
Web application security vulnerabilities and exploitation techniques.

**Topics Covered:**
- Injection (SQLi, Command Injection, LDAP)
- Broken Authentication
- Sensitive Data Exposure
- XML External Entities (XXE)
- Broken Access Control
- Security Misconfiguration
- Cross-Site Scripting (XSS)
- Insecure Deserialization
- Using Components with Known Vulnerabilities
- Insufficient Logging & Monitoring

---

### 🪟 [Windows Privilege Escalation](./Windows-PrivEsc.md)
Techniques for escalating privileges on Windows systems.

**Topics Covered:**
- System enumeration commands
- Service exploitation (Unquoted paths, weak permissions)
- Token impersonation
- Registry exploitation
- Scheduled tasks abuse
- AlwaysInstallElevated
- Kernel exploits (suggesters)
- UAC bypass techniques

---

### 🐧 [Linux Privilege Escalation](./Linux-PrivEsc.md)
Techniques for escalating privileges on Linux systems.

**Topics Covered:**
- SUID/SGID binaries
- Sudo misconfigurations
- Cron job abuse
- PATH hijacking
- Kernel exploits
- Capabilities exploitation
- Docker/LXC container escapes
- NFS misconfigurations

---

### 🕵️ [Active Directory Attacks](./Active-Directory.md)
Common Active Directory enumeration and attack techniques.

**Topics Covered:**
- Domain enumeration (BloodHound, PowerView)
- Kerberoasting
- AS-REP Roasting
- Pass-the-Hash / Pass-the-Ticket
- Golden Ticket / Silver Ticket
- DCSync attacks
- LLMNR/NBT-NS poisoning
- Constrained/Unconstrained delegation

---

### 🔧 [Metasploit Framework](./Metasploit-Basics.md)
Essential Metasploit commands and workflows.

**Topics Covered:**
- MSFconsole navigation
- Module types (exploits, payloads, auxiliary)
- Meterpreter commands
- Post-exploitation modules
- Pivoting & port forwarding
- Database integration
- Resource scripts

---

### 🌐 [Burp Suite Essentials](./Burp-Suite.md)
Web application testing with Burp Suite.

**Topics Covered:**
- Proxy configuration
- Repeater workflows
- Intruder attack types
- Decoder & Comparer
- Extensions (common plugins)
- Session handling
- Collaboration features

---

### 🔐 [Cryptography Basics](./Cryptography-Basics.md)
Essential cryptography concepts for pentesting.

**Topics Covered:**
- Hash functions (MD5, SHA, bcrypt)
- Symmetric encryption (AES, DES)
- Asymmetric encryption (RSA, ECC)
- SSL/TLS vulnerabilities
- Certificate analysis
- Common crypto attacks (padding oracle, etc.)

---

### 📊 [SIEM & Log Analysis](./SIEM-Log-Analysis.md)
Log analysis and SIEM fundamentals for Blue Team perspective.

**Topics Covered:**
- Windows Event IDs (4624, 4625, 4688, 4720...)
- Sysmon Event IDs (1, 3, 7, 10...)
- Elastic/Splunk query syntax basics
- IOC detection patterns
- Threat hunting queries
- Log correlation techniques

---

## 🔄 Usage

**Quick Reference:**
```bash
# Clone repository
git clone https://github.com/Ph3n1xa/Cybersecurity-Portfolio

# Navigate to cheat sheets
cd Cheat-Sheets

# Open any markdown file
cat Linux-Commands.md
```

**Recommended Workflow:**
1. Browse cheat sheet before starting lab/assessment
2. Keep reference open during pentesting
3. Update with new techniques learned
4. Export to PDF if needed (Markdown → PDF converters)

---

## 📖 Sources & Credits

These cheat sheets are compiled from:
- **HTB Academy** modules (Junior Analyst + Pentester Path)
- **Offensive Security** training materials
- **Personal lab experience** (HTB, TryHackMe)
- **Community resources** (credited in individual sheets)
- **Claude IA**

---

## 🔄 Updates

Cheat sheets are regularly updated as I learn new techniques and tools.

**Last Update:** October 2025

**Recent Additions:**
- ✅ Linux Commands (Oct 2025)
- ✅ Networking Basics (Oct 2025)
- 🔄 OWASP Top 10 (In progress - Nov 2025)
- 📋 Windows PrivEsc (Planned - Nov 2025)

---

## 🤝 Contributions

Found an error or have a suggestion?
- Open an issue on GitHub
- Submit a pull request
- Contact me: ph3n1xa@proton.me

---

## ⚠️ Disclaimer

These cheat sheets are for **educational and authorized testing purposes only**.

Always obtain proper authorization before testing any systems or networks.

---

## 🔗 Related Resources

- [HTB Write-Ups](../HTB-WriteUps/) - Practical application of these techniques
- [Python Scripts](../Python-Pentesting/) - Automation tools
- [My LinkedIn](https://www.linkedin.com/in/elodie-moiraud-609059372/) - Professional profile

---

**💡 These are living documents - constantly evolving with my learning journey**

*For any corrections or suggestions, feel free to reach out!*
