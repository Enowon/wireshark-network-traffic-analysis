# Wireshark Network Traffic Analysis Report

## Introduction

This project demonstrates the use of Wireshark to capture and analyze network traffic generated during normal web browsing activity.

The objective of the project was to observe DNS queries, TCP connection establishment, encrypted web traffic, and communication with external servers.

---

## Environment

Operating System: Ubuntu Desktop (Virtual Machine)

Network Interface: enp0s3

Tool Used: Wireshark

---

## Traffic Capture Procedure

A live packet capture was started using Wireshark on the enp0s3 interface.

To generate traffic, the following actions were performed:

1. The capture was started.
2. A web browser was opened.
3. The website google.com was visited.
4. The website bbc.com was then visited.
5. After the pages loaded, the packet capture was stopped.

The packets generated during this browsing activity were used for analysis.

Total packets captured: 13,382 packets.

---

## DNS Analysis

DNS queries were analyzed to identify domain names requested during the browsing session.

Examples of observed domains include:

www.google.com  
push.services.mozilla.com  
www.irishexaminer.com  
www.stylist.co.uk  

DNS requests were sent from the client host 10.0.2.15 to the DNS resolver 192.168.28.1.

---

## TCP Connection Analysis

TCP packets reveal the three-way handshake used to establish communication between systems.

The handshake consists of:

SYN  
SYN-ACK  
ACK

This process ensures a reliable connection before data transmission begins.

---

## Encrypted Web Traffic

Most web communication observed in the capture used encrypted protocols.

Traffic analysis revealed QUIC protocol traffic over UDP port 443, which indicates HTTP/3 communication.

---

## Endpoint Analysis

Endpoint statistics were used to identify external servers communicating with the client host.

These servers included cloud infrastructure and content delivery networks associated with modern web services.

---

## Protocol Hierarchy Analysis

Wireshark’s Protocol Hierarchy statistics were used to analyze the protocol distribution within the captured packets.

A display filter (`udp.port == 443`) was applied in order to focus specifically on traffic associated with QUIC, the transport protocol used by HTTP/3.

The protocol hierarchy observed in the capture shows the following layered protocol structure:

Frame  
→ Ethernet  
→ Internet Protocol Version 4 (IPv4)  
→ User Datagram Protocol (UDP)  
→ QUIC IETF

This indicates that the packets captured in this filtered view consist of UDP traffic carrying QUIC protocol data over port 443.

QUIC is designed to replace traditional TCP-based HTTPS connections by combining transport and encryption mechanisms into a single protocol. This approach reduces latency and improves web performance, particularly for modern browsers communicating with large web services.

The presence of QUIC traffic confirms that the browser used HTTP/3 communication while accessing the visited websites.

---
## Conclusion

This project demonstrates practical network traffic analysis using Wireshark.

The investigation revealed DNS resolution activity, TCP connection establishment, encrypted communication, and interaction with external network servers.

These techniques are fundamental skills used in cybersecurity and network forensics.
