# Homelab Networking Security

This project documents my anaylsis of a self-hosted Minecraft server running on MacOS.

I originally configured the server using traditional port forwarding. I am using this server as a practical environment to learn network security concepts including TCP/IP, packett anaylsis, NAT, firewall configuration, and secure remote access.

## Current Setup

- **Host OS: macOS**
- **Server: All the Mods 10 (ATM10)**
- **Protocol: TCP**
- **Port: 25565**
- **Remote Access: Router port forwarding**
- **Traffic Anaylsis: Wireshark**

## Network Topology

Current network configuration:

    Remote Minecraft Client 
            |
            |
            |
        Internet
            |
            v
        Home Router
            |
            | Nat / Port Forwarding
            v
        macOS Host
            |
            | TCP/25565
            v
        ATM10 Server

## Wireshark Traffic Anaylsis

I captured network traffic between a minecraft client and the server using wireshark. 

In order to isolate Minecraft traffic, I used the following filter within Wireshark
    tcp.port == 25565
This allowed me to see traffic strictly between the client and server. 

I observed bidirectional TCP traffic between the client and server. Network activity continued while the player was connected, and sometimes throwing a TCP Retransmission packet. Changes in network traffic occurred as the player interacted with the server. I compared TCP traffic during idle and active gameplay. Increased network activity was observed during player interactions, demonstrating the exchange of application data between the client and server.


192.168.86.26 (Client)
        |
        v
192.168.86.20 (ATM Server)

![Minecraft TCP Traffic captured in Wireshark](screenshots/TCP-Packets.png)


## Anaylsis 

The server is currently acccessible through TCP port 25565 using router port forwarding 

## Planned Objectives
- [x] Configure and operate the server
- [x] Configure remote access through port forwarding
- [x] Capture network traffic using Wireshark
- [] Capture and document the TCP three-way handshake
- [] Evaluate macOS firewall configurations
- [] Test external exposure of the Minecraft service
- [] Evaluate Tailscale as an alternative to public port forwarding
- [] Compare traffic and accessibility before and after security changes

## Skills and Concepts

This project begun as a fun hobby to host a server for a group of people. Overtime, it developed into a project to develop hands on experience with:

- TCP/IP
- Client-server networking
- Network ports
- NAT and port forwarding
- Wireshark
- Packet anaylsis 
- Network security fundamentals

