#### protocol suite
```    
    +--------------------+-------------------+----------------------------------+
    |      OSI MODEL     |    TCP/IP MODEL   |       TCP/IP Protocol Suite      |
    +--------------------+-------------------+------+---+---+---+---+---+-------+
    |  Application Layer |                   |      |   |   |   |   |   |       |
    |                    |                   |      |   | T |   |   |   |       |
    +--------------------+                   |   H  | S | E | F | D | R |   S   |
    | Presentation Layer | Application Layer |   T  | M | L | T | N | I |   N   |
    |                    |                   |   T  | T | N | P | S | P |   M   |
    +--------------------+                   |   P  | P | E |   |   |   |   P   |
    |      Session Layer |                   |      |   | T |   |   |   |       |
    |                    |                   |      |   |   |   |   |   |       |
    +--------------------+-------------------+------+---+---+---+---+---+-------+
    |                                                                           |
    +--------------------+-------------------+------------------+---------------+
    |   Transport Layer  |  Transport Layer  |        TCP       |      UDP      |
    +--------------------+-------------------+------------------+---------------+
    |                                                                           |
    +--------------------+-------------------+------------------+-------+-------+
    |                    |                   |                  |  IGMP |  ICMP |
    |    Network Layer   |   Internet Layer  +------+     IP    +-------+-------+
    |                    |                   |  ARP |                           |
    +--------------------+-------------------+------+---------------------------+
    |                                                                           |
    +--------------------+-------------------+----------+-------+-------+-------+
    |   Data Link Layer  |      Network      |          |       |       |       |
    +--------------------+      Access       | Ethernet | Token |  ATM  | Frame |
    |   Physical Layer   |       Layer       |          |  Ring |       | Relay |
    +--------------------+-------------------+----------+-------+-------+-------+
```

#### physical
```
1-Wire	
ARINC 818 Avionics Digital Video Bus
Bluetooth physical layer	
CAN bus	(controller area network) physical layer
DSL
EIA RS-232 also: EIA-422, EIA-423, RS-449, RS-485
Etherloop	
Ethernet physical layer	10BASE-T, 10BASE2, 10BASE5, 100BASE-TX, 100BASE-FX, 100BASE-T, 1000BASE-T, 1000BASE-SX and others
GSM air interface physical layer
G.hn/G.9960 physical layer
I²C, I²S	
IEEE 1394 interface	
ISDN	
IRDA physical layer
ITU	
Mobile Industry Processor Interface physical layer
OTN Optical Transport Network
SPI	
SMB	
Telephone network modems	
USB physical layer
```

#### data 
```
ARP			Address Resolution Protocol
ARCnet	
ATM	
CDP			Cisco Discovery Protocol
CAN			Controller Area Network
Econet	
Ethernet	
EAPS			Ethernet Automatic Protection Switching
FDDI			Fiber Distributed Data Interface
Frame Relay	
HDLC			High-Level Data Link Control
IEEE 802.2		provides LLC functions to IEEE 802 MAC layers
IEEE 802.11		wireless LAN
I²C	
LattisNet	
LAPD			Link Access Procedures, D channel
LLDP			Link Layer Discovery Protocol
LocalTalk	
MIL-STD-1553	
MPLS			Multiprotocol Label Switching
NDP			Nortel Discovery Protocol
SDN			OpenFlow
PPP			Point-to-Point Protocol
Profibus	
SpaceWire	
SLIP			Serial Line Internet Protocol (obsolete)
SMLT			Split multi-link trunking
IEEE 802.1aq		
Spanning Tree Protocol	
StarLan	
Token ring	
UDLD			Unidirectional Link Detection
UNI/O	
1-Wire
```

#### network 
```
+-----------+--------------------------------------------+
| DDP       | Datagram Delivery Protocol                 |
| DVMRP     | Distance Vector Multicast Routing Protocol |
| ICMP      | Internet Control Message Protocol          |
| IGMP      | Internet Group Management Protocol         |
| IPsec     | Internet Protocol Security                 |
| IPv4/IPv6 | Internet Protocol                          |
| IPX       | Internetwork Packet Exchange               |
| PIM-DM    | Protocol Independent Multicast Dense Mode  |
| PIM-SM    | Protocol Independent Multicast Sparse Mode |
| RSMLT     | Routing Information Protocol               |
| SPB       | Shortest Path Bridging                     |
+-----------+--------------------------------------------+
```

#### transport 
```
+----------+--------------------------------------+
| ATP      | AppleTalk Transaction Protocol       |
| CUDP     | Cyclic UDP                           |
| DCCP     | Datagram Congestion Control Protocol |
| FCP      | Datagram Congestion Control Protocol |
| IL       | Fibre Channel Protocol               |
| MPTCP    | IL Protocol                          |
| RDP      | Multipath TCP                        |
| RUDP     | Reliable User Datagram Protocol      |
| SCTP     | Stream Control Transmission Protocol |
| SPX      | Sequenced Packet Exchange            |
| SST      | Structured Stream Transport          |
| TCP      | Transmission Control Protocol        |
| UDP      | User Datagram Protocol               |
| UDP-Lite | User Datagram Protocol               |
| µTP      | Micro Transport Protocol             |
+----------+--------------------------------------+
```

#### Session
```
+---------+----------------------------------------------------+
| ADSP    | AppleTalk Data Stream Protocol                     |
| ASP     | AppleTalk Session Protocol                         |
| H.245   | Call Control Protocol for Multimedia Communication |
| ISO-SP  | OSI session-layer protocol (X.225, ISO 8327)       |
| iSNS    | Internet Storage Name Service                      |
| L2F     | Layer 2 Forwarding Protocol                        |
| L2TP    | Layer 2 Tunneling Protocol                         |
| NetBIOS | Network Basic Input Output System                  |
| PAP     | Password Authentication Protocol                   |
| PPTP    | Point-to-Point Tunneling Protocol                  |
| RPC     | Remote Procedure Call Protocol                     |
| RTCP    | Real-time Transport Control Protocol               |
| SMPP    | Short Message Peer-to-Peer                         |
| SCP     | Session Control Protocol                           |
| SOCKS   | the SOCKS internet protocol, see Internet socket   |
| ZIP     | Zone Information Protocol                          |
| SDP     | Sockets Direct Protocol                            |
+---------+----------------------------------------------------+
```

#### presentation
```
+-------+--------------------------------------------+
| CASE  | common application service element         |  
| ACSE  | Association Control Service Element        |  
| ROSE  | Remote Operation Service Element           |  
| CCR   | Commitment Concurrency and Recovery        |  
| RTSE  | Reliable Transfer Service Element          |  
| SASE  | specific application service element       |  
| FTAM  | File Transfer, Access and Manager          |  
| VT    | Virtual Terminal                           |  
| MOTIS | Message Oriented Text Interchange Standard |  
| CMIP  | Common Management Information Protocol     |  
| JTM   | Job Transfer and Manipulation              |  
| MMS   | Manufacturing Messaging Service            |  
| RDA   | Remote Database Access                     |  
| DTP   | Distributed Transaction Processing         |  
+-------+--------------------------------------------+
```

#### application 
```
+--------------------+---------------------------------------------------------------------------------------+
| 9P                 | Plan 9 from Bell Labs distributed file system protocol                                | 
| AFP                | Apple Filing Protocol                                                                 | 
| APPC               | Advanced Program-to-Program Communication                                             | 
| AMQP               | Advanced Message Queuing Protocol                                                     | 
| Atom               | Publishing Protocol                                                                   | 
| BEEP               | Block Extensible Exchange Protocol                                                    | 
| Bitcoin            | Digital currency                                                                      | 
| BitTorrent         | peer-to-peer file sharing                                                             | 
| CFDP               | Coherent File Distribution Protocol                                                   | 
| CoAP               | Constrained Application Protocol                                                      | 
| DDS                | Data Distribution Service                                                             | 
| DeviceNet          | automation industry protocol                                                          | 
| eDonkey            | classic file sharing protocol                                                         | 
| ENRP               | Endpoint Handlespace Redundancy Protocol                                              | 
| FastTrack          | filesharing, known from KaZaa and more                                                | 
| Finger             | User Information Protocol                                                             | 
| Freenet            | censorship resistant p2p network                                                      | 
| FTAM               | File Transfer Access and Management                                                   | 
| Gopher             | Gopher protocol                                                                       | 
| HL7                | Health Level Seven                                                                    | 
| HTTP               | HyperText Transfer Protocol                                                           | 
| H.323              | Packet-Based Multimedia Communications System                                         | 
| IRCP               | Internet Relay Chat Protocol                                                          | 
| Kademlia           | p2p hashtables                                                                        | 
| LDAP               | Lightweight Directory Access Protocol                                                 | 
| LPD                | Line Printer Daemon Protocol                                                          | 
| MIME               | (S-MIME)	Multipurpose Internet Mail Extensions and Secure MIME                        |
| Modbus             | Serial communications protocol                                                        | 
| MQTT               | Protocol	MQ Telemetry Transport                                                       |
| Netconf            | Network Configuration Protocol                                                        | 
| NFS                | Network File System                                                                   | 
| NIS                | Network Information Service                                                           | 
| NNTP               | Network News Transfer Protocol                                                        | 
| NTCIP              | National Transportation Communications for Intelligent Transportation System Protocol | 
| NTP                | Network Time Protocol                                                                 | 
| OSCAR              | AOL Instant Messenger Protocol                                                        | 
| PNRP               | Peer Name Resolution Protocol                                                         | 
| RDP                | Remote Desktop Protocol                                                               | 
| RELP               | Reliable Event Logging Protocol                                                       | 
| RIP                | Routing Information Protocol                                                          | 
| Rlogin             | Remote Login in UNIX Systems                                                          | 
| RPC                | Remote Procedure Call                                                                 | 
| RTMP               | Real Time Messaging Protocol                                                          | 
| RTP                | Real-time Transport Protocol                                                          | 
| RTPS               | Real Time Publish Subscribe                                                           | 
| RTSP               | Real Time Streaming Protocol                                                          | 
| SAP                | Session Announcement Protocol                                                         | 
| SDP                | Session Description Protocol                                                          | 
| SIP                | Session Initiation Protocol                                                           | 
| SLP                | Service Location Protocol                                                             | 
| SMB                | Server Message Block                                                                  | 
| SMTP               | Simple Mail Transfer Protocol                                                         | 
| SNTP               | Simple Network Time Protocol                                                          | 
| SSH                | Secure Shell                                                                          | 
| SSMS               | Secure SMS Messaging Protocol                                                         | 
| TCAP               | Transaction Capabilities Application Part                                             | 
| TDS                | Tabular Data Stream                                                                   | 
| Tor                | anonymity network                                                                     | 
| TSP                | Time Stamp Protocol                                                                   | 
| VTP                | Virtual Terminal Protocol                                                             | 
| Whois (and RWhois) | Remote Directory Access Protocol                                                      | 
| WebDAV             | Web Distributed Authoring and Versioning                                              | 
| X.400              | Message Handling Service Protocol                                                     | 
| X.500              | Directory Access Protocol (DAP)                                                       | 
| XMPP               | Extensible Messaging and Presence Protocol                                            | 
+--------------------+---------------------------------------------------------------------------------------+
```
