SSH Incident Response Lab

Incident Summary
Multiple failed SSH login attempts were detected from a single IP address.  
The behavior indicated a potential brute-force attempt.  
The suspicious source was blocked using a firewall containment rule.

Detection
SSH logs were reviewed using:
sudo journalctl -u ssh
Repeated failed login attempts were observed from:
192.168.159.128

Investigation
Focused log analysis confirmed:

- Multiple failed authentication attempts
- No confirmed unauthorized successful login

Commands used:
sudo journalctl -u ssh | grep 192.168.159.128
last

Containment Action
Firewall rule added:
sudo iptables -A INPUT -s 192.168.159.128 -j DROP

Verification:
sudo iptables -L
Result:
Traffic from the suspicious IP is blocked.

Outcome
No compromise detected.  
Containment successful.  
System monitoring continued.

Lessons Learned
- SSH logs reveal brute-force behavior patterns
- Incident containment reduces exposure
- Firewall rules provide rapid protection
- Log analysis is critical in incident response

Skills Demonstrated
- Log analysis
- Incident investigation
- Host-based firewall containment
- Security documentation
