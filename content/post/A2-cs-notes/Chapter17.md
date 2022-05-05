+++
author = "WNO-IQ"
title = "Chapter 17: Communication and Internet technologies"
date = "2021-12-03"
description = "My A2 Computer Science notes"
tags = [
    "Notes",
    "Study"
]
keywords = ["CIE","Alevel","A2","Computer Science","Notes"]
categories = [
    "A2-CS-notes"
]

+++

# Chapter 17: Communication and Internet technologies

## Transmission modes

### Circuit switching

- Circuit switching is the method used in the traditional telephone system.
- When a telephone call `has finished` there is a definite end to the call with `removal of the links`. However, for `a leased-line data connection there might be a permanent circuit established.`

### Packet switching

- allows data transmission without a circuit being established.
  Data cannot be sent in a continuous stream
- A packet consists of a header which contains instructions for delivery plus the data body.
- a router acts as a node and supports packet switching
- If a `connectionless service` is provided, a packet is dispatched with `no knowledge of whether or not the receiver is ready to accept the packet`
- In a `connection-oriented service` the first packet sent `includes a request` for an acknowledgement
  <br>

## Protocols

- a set of rules for data transmission which are agreed by sender and receiver
- Protocol suite - contains more than one individual protocol.
- The complexity of networking requires many individual protocols.
  <br>

## A protocol stack

- Each layer can only accept input from `the next higher layer or the next lower layer.`
- There is a defined interface between adjacent layers which constitutes the only
  interaction allowed between layers.
- `A layer is serviced by the actions of lower layers.`
- With the possible exception of the `lowest layer` the functioning of a layer is `created by installed soft ware.`
- `A layer may comprise sub-layers.`
- Any user interaction will take place using protocols associated with the highest level layer
  in the stack.
- Any direct access to hardware is confined to the lowest layer in the stack.
  <br>

## The TCP/IP protocol suite

![](cs-note-img/Pastedimage20211116204613.png)

- `An application` can run on one end-system and behave as though there was a direct connection with an application running on a different end-system.
- The `application layer protocol` on the sender end-system sends a ‘message’ to the transport layer protocol on the same system.
- The `transport layer protocol` then initiates a process which results in the identical ‘message’ being `delivered to the receiver end-system.`
- On the receiver end-system, the `final stage` is the `transport layer protocol delivering the ‘message’ to the application layer protocol.`
- The TCP/IP suite comprises a number of protocols, including the following:
  - application layer: HTTP, SMTP, DNS, FTP, POP3, IMAP
  - transport layer: TCP, UDP, SCTP
  - network layer: IP, IGMP, ICMP, ARP.

### TCP (Transmission Control Protocol)

- ‘message’ is to be sent to a different end-system by an application layer protocol
- The TCP protocol operating in the transport layer
- Each packet consists of a header plus the user data.
- TCP has to ensure that any response
- The header is the port number which identifies the application layer protocol.

### IP (Internet Protocol)

- The function of the network layer, and in particular of the IP, is to ensure correct routing over the Internet.

### The router

<br>

## The Ethernet protocol stack

- The routing table for every router has details of any current problems with any of the options for the next transmission step. This ensures that packets are delivered to their destination in the shortest possible time available.
- The major distinction between a switch and a router as a node in a network is that when a frame arrives at a switch, it is transmitted on without any routing decision. A switch operates in the data-link layer but has no access to the network layer.
  <br>

## The Ethernet protocol stack

- Ethernet is the most likely protocol to be used to provide the functionality required of the two lower layers.
- Logically the Ethernet suite can be viewed as comprising two sub-layers for each of the Data link and Physical layers.
  ![](cs-note-img/Pastedimage20211117073242.png)
- The Logical Link Control (LCC) protocol is responsible for the interaction with the Network layer. It manages data transmissions and ensures the integrity of data transmissions.
- The Medium Access Control (MAC) protocol is responsible for assembling the Ethernet packet which is referred to as a frame.
- In addition the MAC protocol initiates frame transmission and handles recovery from transmission failure due to a collision (possibly using CSMA/CD).
- The Physical Coding Sublayer (PCS) protocol is responsible for coding data ready for transmission or decoding data received. It either receives a frame from the MAC protocol or sends one to it.
- The Physical Medium Attachment (PMA) protocol is responsible for signal transmitting and receiving.

### MAC addresses

- A MAC address is the one which uniquely defines one NIC.
- 48 bits
  <br>

## Application-layer protocols associated with TCP/IP

### HTTP (HyperText Transfer Protocol)

### Email protocols

- The email sender acting as a client has a connection to a mail server. This server then has to function as a client in the transmission to the mail server used by the email receiver acting as a client.
  ![](cs-note-img/Pastedimage20211117075940.png)
- With IMAP the emails are not downloaded; they remain stored on the server but remain accessible from the client.
- The major advantage for IMAP is that the server can be accessed from any client. This makes it suitable for anyone on the move or if someone is using a system other than that normally used.

### FTP (File Transfer Protocol)

- FTP (File Transfer Protocol) is the application-layer protocol that can handle any file transfer between two end-systems.
  <br>

## Peer-to-peer (P2P) file sharing

- Peers act as both clients and servers and each peer is just one end-system. When a peer acts as a server it is called a ‘seed’.
- The BitTorrent protocol is the most used protocol because it allows fast sharing of files. There are three basic problems to solve if end-systems are using BitTorrent.

1. How does a peer find others that have the wanted content?
   - Every content provider should provide a content description, called a torrent, which is a file that contains the name of the tracker (a server that leads peers to the content) and a list of the chunks that make up the content. The torrent file is at least three orders of magnitude smaller than the content so can be transferred quickly. The tracker is a server that maintains a list of all the other peers (the ‘swarm’) actively downloading and uploading the content.
2. How do peers replicate content to provide high-speed downloads for everyone?
   - Peers download and upload chunks at the same time, but peers have to exchange lists of chunks and aim to download rare chunks for preference. Each time a rare chunk is downloaded it automatically becomes less rare!
3. How do peers encourage other peers to provide content rather just using the protocol to download for themselves?
   - This requires dealing with the free-riders or ‘leechers’ who only download. The solution is for a peer to initially randomly try other peers but then to only continue to upload to those peers that provide regular downloads. If a peer is not downloading or only downloading slowly, the peer will eventually be isolated or ‘choked’.
