#  Cybersecurity Internship – Task 1

##  Task: Scan Your Local Network for Open Ports

This task involves performing a TCP SYN scan on a local device using *Nmap* to discover open ports and understand potential security risks.

---

##  Tools Used

- [Nmap](https://nmap.org/)
- Windows Command Prompt

---

##  Steps Performed

1. *Installed Nmap* from the official website.
2. Used ipconfig to find my local IP address: 192.168.1.69
3. Identified the network range as: 192.168.1.0/24
4. Ran the TCP SYN scan:
   ```bash
   nmap -sS 192.168.1.69
   
   #  Scan Summary

| Port  | State     | Service       |
|-------|-----------|----------------|
| 25    | filtered  | smtp           |
| 110   | filtered  | pop3           |
| 135   | open      | msrpc          |
| 139   | open      | netbios-ssn    |
| 445   | open      | microsoft-ds   |
| 548   | filtered  | afp            |
| 2869  | open      | icslap         |

---

#  Security Risk Analysis

- *Port 135 (MSRPC)*  
  - Allows remote procedure calls on Windows. If not patched, may allow attackers to execute code remotely.

- *Port 139 (NetBIOS-SSN)*  
  - Used for file and printer sharing. May expose shared files or printers to the local network or attackers.

- *Port 445 (Microsoft-DS/SMB)*  
  - Vulnerable to malware like WannaCry if exposed. Should be blocked or protected with a firewall.

- *Filtered Ports (25, 110, 548)*  
  - Good sign. Your firewall or system is blocking access to these potentially risky ports.

- *Port 2869 (ICSLAP)*  
  - Used by UPnP/ICS services. Not critical, but may allow network configuration changes if exploited.

---

*It’s recommended to:
- Close unused ports
- Disable SMB sharing unless needed
- Use firewalls to filter traffic
- Keep your system updated
