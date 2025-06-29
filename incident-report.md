# Identifying Attack Type
Based on network logs & the behavior observed, the timeout errors are probably the result of a denial of service (DoS) attack. 
The logs more specifically suggest that the server stops to respond after being overwhelmed with TCP connection attempts, primarily SYN packets.
This is indicative of a SYN flood attack, a type of DoS attack where an attacker sends a very large amount of initial connection requests,
exhausting the server's ability to handle actual traffic.

# Technical Analysis of SYN Flood Attack & Impact On Web Server
When a user tries to establish a connection w/ a web server over TCP, the three-way handshake occurs
### Three Way Handshake Explanation
1. Client sends a SYN (synchronize) packet to server
2. Server responds with a SYN-ACK packet (synchronize acknowledge), allocating server resources
3. Client finally responds with an ACK (acknowledge) packet and establishes the connection.

In a SYN Flood Attack, the malicious actor would send a stream of SYN packets without completing the handshake. Because the server still
allocates memory and resources for each SYN request while awaiting ACK, the half-open connections quickly accumulate. When the backlog of connections
is full, it becomes unable to process new attempts.

The logs confirm this behavior. THe web server became saturated with uncompleted connection attempts and is unable to respond to new 
packets, resulting in connection timeouts even for genuine visitors.
