# Assignment 11: Ncat Chat Terminal

## Aim
Create a simple chat system between two computers using basic networking tools like `nc` and `ncat`.

---

## Objective

This project demonstrates how to establish a terminal-based chat connection between two machines — a macOS host and a Kali Linux virtual machine — using Netcat (`nc`) and Ncat (`ncat`).  

It is designed to help understand core networking concepts such as:
- IP addressing  
- Port communication  
- Client-server architecture  
- Terminal-based message exchange  

---

## Setup

- **Machine 1 (Server):** Kali Linux VM  
- **Machine 2 (Client):** macOS Host  
- Ensure both systems are on the same network and can communicate.

---
``` bash
## Script: kali_listener.sh
# Purpose: Listen for incoming Netcat connections on port 12345.
 Line 1: Use 'nc' in listen mode.
 Line 2: '-l' activates listen mode.
 Line 3: '-v' provides verbose output for connection details.
 Line 4: '-p 12345' specifies the listening port.
nc -lvp 12345
Line 5: This terminal will now wait for a connection.

# Script: mac_connector.sh
# Purpose: Connect to the Netcat listener and send/receive messages.
 Line 6: Use 'ncat' to connect.
 Line 7: Specify the target IP address (Kali's IP: 172.16.213.191).
 Line 8: Specify the target port (matching the listener's port: 12345).
ncat 172.16.213.191 12345
 Line 9: Upon successful connection, this terminal is ready for chat.
 Line 10: Type messages and press Enter to send.
 
```
## How It Works

- **Kali** listens on port `12345` using `nc` (Netcat) in listen mode.
- **Mac** initiates a connection to Kali’s IP address on port `12345` using `ncat`.
- Once the connection is established:
  - Anything typed in one terminal is instantly sent to the other.
  - Both terminals act as sender and receiver simultaneously.
- This simulates a **bidirectional TCP chat** session between two machines.

