# OSI Model

The **OSI (Open Systems Interconnection) model** is a conceptual model that explains how data travels between devices over a network.

It has **7 layers**, from the physical connection at Layer 1 to applications at Layer 7.

## 7 Layers of the OSI Model

| Layer | Name         | What it does                                              | Example              |
| ----- | ------------ | --------------------------------------------------------- | -------------------- |
| 7     | Application  | Provides network services to applications                 | HTTP, HTTPS, DNS     |
| 6     | Presentation | Handles data format, encryption, and compression          | TLS, encryption      |
| 5     | Session      | Establishes and manages communication sessions            | Session management   |
| 4     | Transport    | Provides end-to-end data delivery                         | TCP, UDP             |
| 3     | Network      | Handles logical addressing and routing                    | IP, routers          |
| 2     | Data Link    | Handles communication between devices on the same network | Ethernet, MAC        |
| 1     | Physical     | Transmits raw bits through physical media                 | Cables, radio, Wi-Fi |

### Easy Way to Remember

From **Layer 7 → Layer 1**:

```text
Application
Presentation
Session
Transport
Network
Data Link
Physical
```

Mnemonic:

> **A P S T N D P**

---

## Example: Opening a Website

When you open:

```text
https://example.com
```

the data passes through the OSI layers.

```text
Layer 7 — Application
HTTPS request is created

Layer 6 — Presentation
Data can be encrypted/formatted

Layer 5 — Session
Communication session is managed

Layer 4 — Transport
TCP manages reliable delivery

Layer 3 — Network
IP addresses are used for routing

Layer 2 — Data Link
Frames and MAC addresses are used on the local network

Layer 1 — Physical
Bits travel through Wi-Fi, cables, or another physical medium
```

---

## Why the OSI Model Is Important in Cybersecurity

The OSI model helps cybersecurity professionals understand **where network communication and security problems occur**.

For example:

* **Layer 1:** Physical security issues
* **Layer 2:** MAC-related attacks and local network issues
* **Layer 3:** IP-based attacks and routing issues
* **Layer 4:** Port and TCP/UDP-based attacks
* **Layer 7:** Web application attacks

Understanding the OSI model makes it easier to analyze network traffic, troubleshoot network problems, and understand different types of attacks.

---

## OSI vs TCP/IP

The OSI model has **7 layers**, while the commonly used TCP/IP model is usually represented with **4 layers**.

```text
OSI Model              TCP/IP Model

7 Application  ┐
6 Presentation │
5 Session      ├──→ Application
               │
4 Transport    ├──→ Transport
               │
3 Network      ├──→ Internet
               │
2 Data Link    ┐
1 Physical     ┴──→ Network Access
```

The OSI model is mainly used as a **conceptual framework for understanding networking**, while TCP/IP is the protocol architecture used by the Internet.

---

## My Learning

I learned that the OSI model breaks network communication into seven layers, making it easier to understand how data moves between devices and where different network technologies and security issues operate.

### Key Takeaway

```text
7 → Application
6 → Presentation
5 → Session
4 → Transport
3 → Network
2 → Data Link
1 → Physical
```

The OSI model is an important networking foundation for cybersecurity because it helps me understand **network communication, protocols, troubleshooting, and security threats at different layers**.
