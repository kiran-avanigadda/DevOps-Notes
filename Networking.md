## Networking Notes

#### What is OSI and its layers?
Ans: It is a 7 layer framework that defines the journey of a request from a client to a server.

#### Layers:  [ A P S T N D P ]

- Application Layer: Layer-7: It is closest to user. Provides network to the applications. (HTTP, HTTPS, SSH, FTP)
- Presentation Layer: Layer-6: This layer encryptes the data. (SSL/TLS)
- Session Layer: Layer-5: Manages sessions/communication between systems. (Cache/Cookies)
- Transport Layer: Layer-4: Message will be broken to packets and ensures end to end delivery of data and handles error recovery. (TCP/UDP)
- Network Layer: Layer-3: This layer handles routing and IP addressing. (ipv4/ipv6)
- Data Layer: Layer-2: This layer handles MAC address and error detection.
- Presentation Layer: Layer-1: This layer deals with physical connection (cables, signals)

---

**- Forward Proxy:** It is a kind of middle man that sits between client and internet and routes our requests. It can block/accept the requeats to internet.
**- Forward Proxy:** It is a server that sits in front of 1 (or) more backend services and acts on behalf of the server.

---
