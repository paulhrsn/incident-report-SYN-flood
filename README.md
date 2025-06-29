# SYN Flood Cybersecurity Incident Report

Simulated network incident analysis case study involving an apparent SYN flood attack, causing connection timeout errors on a web server. The goal of this investigation was to determine the type of attack, determine its impact on the system, and recommend specific immediate defensive actions.

The attack was identified based on a high number of incomplete TCP connection requests in the form of SYN packets from a single IP address, which led to a significant loss  of server resources.

---

## Tools Used
- Packet sniffer (Wireshark)

---

## Findings
- Large number of TCP SYN packets were sent from IP `203.0.113.0` to port 443 of `192.0.2.1`
- Very few (or no) ACK responses from that IP address, which is an indicator of incomplete TCP handshakes
- Server returned HTTP 504 Gateway Timeout in response to actual user requests
- Log shows repeated SYNs without completion of the three-way handshake

---

## Project Contents
- `incident-report.md`: Cybersecurity analysis & incident report explaining the attack and its effects
- `syn-attack-log.txt`: Packet data showing repeated SYN requests (lines 47–214+)

---

## Skills Demonstrated
- Identifying denial-of-service (DoS) behavior from packet logs
- Understanding of the TCP 3-way handshake and how SYN floods break it
- Using real-time packet capture tools to determine attack sources
- Documenting and communicating cybersecurity incidents clearly
