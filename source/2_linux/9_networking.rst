###########
2.9 Network
###########

================
What is network?
================

A network is a group of two or more computer systems linked together. There are many types of computer networks, including the following:
- local-area networks (LANs): The computers are geographically close together (that is, in the same building).
- wide-area networks (WANs): The computers are farther apart and are connected by telephone lines or radio waves.
- campus-area networks (CANs): The computers are within a limited geographic area, such as a campus or military base.
- metropolitan-area networks MANs): A data network designed for a town or city.
- home-area networks (HANs): A network contained within a user's home that connects a person's digital devices.
- storage-area networks (SANs): A network of storage devices that provide data storage for servers.
- system-area networks (also known as cluster area networks): A network linking computers together within a room or building.
- enterprise private network (EPN): A computer network built by a business to interconnect its various company sites (such as production sites, offices and shops) in order to share computer resources.
- virtual private network (VPN): A network that is constructed by using public wires — usually the Internet — to connect to a private network, such as a company's internal network.

Networks are used to:
- Facilitate communication via email, video conferencing, instant messaging, etc.
- Enable multiple users to share a single hardware device like a printer or scanner
- Enable file sharing across the network
- Allow for the sharing of software or operating programs on remote systems
- Make information easier to access and maintain among network users
- Facilitate communications using a network card instead of a modem

Networking protocols:
- Ethernet
- LocalTalk
- Token Ring
- FDDI
- ATM
- Fiber Distributed-Data Interface (FDDI)
- X.25
- Frame Relay
- Asynchronous Transfer Mode (ATM)
- Integrated Services Digital Network (ISDN)
- Transmission Control Protocol/Internet Protocol (TCP/IP)
- Point-to-Point Protocol (PPP)
- File Transfer Protocol (FTP)
- Hypertext Transfer Protocol (HTTP)
- Telnet
- Gopher
- Simple Mail Transfer Protocol (SMTP)
- Post Office Protocol (POP)
- Internet Message Access Protocol (IMAP)
- Network News Transfer Protocol (NNTP)
- Network File System (NFS)
- Common Internet File System (CIFS)
- AppleTalk
- Xerox Network Systems (XNS)
- DECnet
- Open Systems Interconnection (OSI)

TCP/IP stack:
- Application layer
- Transport layer
- Internet layer
- Network access layer

OSI Stack:
- Application layer 
- Presentation layer
- Session layer
- Transport layer
- Network layer
- Data link layer
- Physical layer


Communication protocols mapped to OSI layers:

7.  Application layer

    NNTP, SIP, SSI, DNS, FTP, Gopher, HTTP, HTTPS, NFS, NTP, SMPP, SMTP, SNMP, Telnet, DHCP, NETCONF

6.  Presentation layer

    MIME, XDR, ASN.1, ASCII, PGP

5.  Session layer

    Named pipe(FIFO), NetBIOS, SAP, PPTP, RTP, SOCKS X.225[65]

4.  Transport layer

    TCP, UDP, SCTP, DCCP, SPX

3.  Network layer

    IP (IPv4 IPv6), ICMP, IPsec, IGMP, IPX, IS-IS, AppleTalk, X.25, PLP

2.  Data link layer

    ATM, ARP, SDLC, HDLC, CSLIP, SLIP, GFP, PLIP, IEEE 802.2, LLC, MAC, L2TP, IEEE 802.3, Frame Relay, ITU-T G.hn DLL, PPP, X.25 LAPB, Q.922 LAPF

1.  Physical layer

    RS-232, RS-449, ITU-T V-Series, I.430, I.431, PDH, SONET/SDH, PON, OTN, DSL, IEEE 802.3, IEEE 802.11, IEEE 802.15, IEEE 802.16, IEEE 1394, ITU-T G.hn PHY, USB, Bluetooth

TCP vs UDP:
- TCP is connection oriented – once a connection is established, data can be sent bidirectional. UDP is a simpler, connectionless Internet protocol. Multiple messages are sent as packets in chunks using UDP.
- TCP is heavy-weight. TCP requires three packets to set up a socket connection, before any user data can be sent. UDP is lightweight – data is sent as packets and no connection is established.
- TCP provides extensive error checking mechanisms. UDP has only the basic error checking mechanism using checksums.
- TCP is slower, as it requires three packets to set up a socket connection. UDP is faster, as it requires only one packet to set up a socket connection.
- TCP has acknowledgments, and sequencing. UDP has no acknowledgments, no guaranteed delivery and no sequencing.
- TCP is used when reliability is important. UDP is used when speed is important and error correction is not necessary.

TCP Handshake:
- SYN: The active open is performed by the client sending a SYN to the server. The client sets the segment's sequence number to a random value A.
- SYN-ACK: In response, the server replies with a SYN-ACK. The acknowledgment number is set to one more than the received sequence number i.e. A+1, and the sequence number that the server chooses for the packet is another random number, B.
- ACK: Finally, the client sends an ACK back to the server. The sequence number is set to the received acknowledgement value i.e. A+1, and the acknowledgement number is set to one more than the received sequence number i.e. B+1.
