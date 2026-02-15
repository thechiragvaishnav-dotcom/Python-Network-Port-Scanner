# Python-Network-Port-Scanner

* Network reconnaissance & the Architecture of Port scanners
  1. the identification of active services on a target System.
  2. A port-scanner programmatically $$\color{orange}{\text{interacts with}}$$ a target's $$\color{orange}{\text{TCP/IP stack}}$$ to determine which ports are $$\color{orange}{\text{listening}}$$ & conseequently, which $$\color{orange}{\text{applications are accessible}}$$.
 
* Theoretical Framework: Sockets & the TCP Handshake
  1. At the fundamental level, network communication in operating system is handled through $$\color{orange}{\text{sockets}}$$
  2. A socket is an endpoint for sending or receiving data across a computer network
  3. In Python, the $$\color{orange}{\text{socket}}$$ module provides an interface to the Berkeley sockets API, allowing the developer to control low-level network interactions
 
* TCP Three-Way Handshake\
  
  1. When a client wishes to connect to a server, the following exchange occurs:\
  $$\color{red}{\text{1. SYN:}}$$ the client sends a segment with the SYN(Synchronize) flag set.\
  $$\color{red}{\text{2. SYN-ACK:}}$$ if the part is Open, the server acknowledges the request with a SYN_ACK segment\
  $$\color{red}{\text{3. ACK:}}$$ The client responds with an ACK, establishing the connection.
  2. A basic $$\color{orange}{\text{connect scan}}$$, which is the focus of this beginner project, attempts to complete this entire handshake.
  3. If the $$\color{orange}{\text{connection succeeds}}$$, the $$\color{orange}{\text{port is Open}}$$
  4. If the server responds with a $$\color{orange}{\text{RST (Reset)}}$$ packet or if the $$\color{orange}{\text{request time out}}$$, the $$\color{orange}{\text{port}}$$ is considered $$\color{orange}{\text{closed or filtered}}$$.

| Socket Parameter | Functionality | Security Implication |
| :---: | :---: | :---: |
| <code>AF_INET</code> | Specifies the IPv4 address family. | Limits scanning to standard 32-bit IP addresses; ignores IPv6 infrastructure |
| <code>SOCK_STREAM</pre> | specifies the TCP protocol. | Ensures reliable, connection-oriented scanning (as opposed to UDP). |
| <code>connect_ex()</code> | connect() variant that returns an error code. | Return <code>0</code> on Success preventing the script from crashing on closed ports (Error Handling) |
| <code>Settimeout()</code> | defines the wait time for a response | Critical for performance; prevents the scanner from hanging on unresponsive firewalls. |

# Process

* $$\color{orange}{\text{Step-1: Open Any Linux Terminal}}$$
  ![My Terminal](https://github.com/thechiragvaishnav-dotcom/Python-Network-Port-Scanner/issues/2#issue-3943769399)
  1. type in this code 
  2. <code>cat > portscan.py</code> 
  3. Enter
  4. Ctrl + C
  5. <code>ls</code>
