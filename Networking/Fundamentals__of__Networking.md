# Networking Basics — Learning Notes

This file contains the networking concepts I have learned as part of my cybersecurity learning journey. Understanding networking is important because cybersecurity professionals need to understand how devices communicate and how networks can be protected from threats.

---

# 1. IP Addresses

An **IP (Internet Protocol) address** is a unique logical address used to identify a device on a network and allow it to communicate with other devices.

## IPv4

IPv4 addresses are 32-bit addresses written as four decimal numbers separated by periods.

Example:

```text id="4u8vpy"
192.168.1.10
```

Each part can have a value from `0` to `255`.

IPv4 addresses are commonly divided into:

* **Private IP addresses** → Used inside local networks.
* **Public IP addresses** → Used to identify networks/devices on the public internet.

Example private address:

```text id="a6a4v5"
192.168.1.10
```

## IPv6

IPv6 was developed to provide a much larger number of IP addresses than IPv4.

Example:

```text id="3ckl4u"
2001:0db8:85a3::8a2e:0370:7334
```

## Private IP Address Ranges

Common private IPv4 ranges include:

```text id="kwt7c8"
10.0.0.0 – 10.255.255.255
172.16.0.0 – 172.31.255.255
192.168.0.0 – 192.168.255.255
```

## Why IP Addresses Matter in Cybersecurity

IP addresses can help security professionals:

* Identify devices
* Analyze network connections
* Investigate suspicious traffic
* Identify the source or destination of network traffic
* Configure network security controls

---

# 2. TCP/IP

**TCP/IP (Transmission Control Protocol/Internet Protocol)** is a collection of networking protocols used for communication between devices across networks.

The TCP/IP model is commonly described using four layers:

```text id="p4w9vh"
Application
Transport
Internet
Network Access
```

## Application Layer

Provides network services used by applications.

Examples:

```text id="g0z7pf"
HTTP
HTTPS
DNS
SSH
FTP
```

## Transport Layer

Provides communication between applications on different devices.

Two important protocols are:

### TCP

TCP provides reliable, connection-oriented communication.

It helps ensure that data arrives correctly and in the proper order.

### UDP

UDP provides faster, connectionless communication but does not guarantee delivery.

## Internet Layer

Responsible for addressing and routing packets between networks.

An important protocol at this layer is:

```text id="z7b1y3"
IP
```

## Network Access Layer

Responsible for communication over the physical and local network.

Examples include Ethernet and Wi-Fi technologies.

---

# 3. Network Protocols

A **network protocol** is a set of rules that determines how devices communicate and exchange information over a network.

Some important protocols include:

| Protocol | Purpose                                          |
| -------- | ------------------------------------------------ |
| HTTP     | Transfers web content                            |
| HTTPS    | Secure web communication                         |
| DNS      | Translates domain names into IP addresses        |
| SSH      | Secure remote access                             |
| FTP      | Transfers files                                  |
| TCP      | Reliable transport communication                 |
| UDP      | Fast connectionless communication                |
| IP       | Addressing and routing packets                   |
| DHCP     | Automatically assigns network configuration      |
| ICMP     | Used for network diagnostics and error reporting |

## Example

When you visit:

```text id="0gq0d3"
https://example.com
```

DNS can help resolve the domain name to an IP address, and HTTPS can then be used to communicate securely with the web server.

---

# 4. Network Security

**Network security** involves protecting networks, devices, and data from unauthorized access, misuse, attacks, and disruption.

The main goals of network security include:

* Confidentiality
* Integrity
* Availability

These are commonly known as the **CIA triad**.

## Confidentiality

Ensures that information is accessible only to authorized users.

Example:

```text id="5k1v9j"
Encryption
```

## Integrity

Ensures that information is not improperly modified or altered.

Example:

```text id="1j1e0f"
File integrity monitoring
```

## Availability

Ensures that systems and network resources remain available when needed.

Example:

```text id="1c9p7j"
Protection against denial-of-service attacks
```

## Common Network Security Controls

* Firewalls
* Intrusion detection systems
* Intrusion prevention systems
* Encryption
* Authentication
* Access controls
* Network monitoring
* Security policies

---

# 5. Firewalls

A **firewall** is a security control that monitors and filters network traffic based on defined rules.

A firewall can allow or block traffic based on factors such as:

* IP address
* Port
* Protocol
* Direction of traffic
* Network interface

## Example

A firewall rule could allow HTTPS traffic:

```text id="3xg0yh"
Protocol: TCP
Port: 443
Action: Allow
```

It could also block unwanted traffic:

```text id="q9p8v5"
Protocol: TCP
Port: 23
Action: Block
```

Port 23 is commonly associated with Telnet, which does not provide the same protections as secure remote-access protocols such as SSH.

## Types of Firewalls

Common firewall types include:

* Network firewalls
* Host-based firewalls
* Stateful firewalls
* Next-generation firewalls

Firewalls are an important layer of network defense, but they are not the only security control required to protect a network.

---

# 6. Network Threats

A **network threat** is a potential danger that can compromise the confidentiality, integrity, or availability of network systems or data.

Common network threats include:

## Malware

Malicious software designed to damage systems, steal information, or perform unauthorized activities.

Examples:

* Viruses
* Worms
* Trojans
* Ransomware
* Spyware

## Phishing

An attacker attempts to trick users into revealing sensitive information or performing an unsafe action.

## Denial-of-Service (DoS)

An attack that attempts to make a system or service unavailable by overwhelming it with traffic or requests.

## Distributed Denial-of-Service (DDoS)

A DDoS attack uses multiple systems to generate traffic against a target.

## Man-in-the-Middle (MitM)

An attacker attempts to intercept or manipulate communication between two parties.

## Password Attacks

Attackers may attempt to obtain or guess passwords to gain unauthorized access.

## Network Scanning

Attackers may scan systems and networks to identify available hosts, services, ports, or potential weaknesses.

---

# 7. Network Vulnerabilities

A **network vulnerability** is a weakness in a network, device, application, configuration, or security process that could potentially be exploited.

Common examples include:

## Weak Passwords

Weak or reused passwords can make accounts easier to compromise.

## Unpatched Systems

Systems that have not received important security updates may contain known vulnerabilities.

## Misconfigured Firewalls

Incorrect firewall rules can accidentally expose services or allow unwanted traffic.

## Unnecessary Open Ports

Open ports can expose network services that are not required.

## Insecure Protocols

Some older protocols transmit information without adequate protection.

For example:

```text id="v1d0fs"
HTTP
FTP
Telnet
```

Secure alternatives may be available depending on the use case.

## Poor Access Controls

Incorrect permissions or access rules can allow unauthorized users to access network resources.

## Default Credentials

Leaving default usernames and passwords unchanged can create an unnecessary security risk.

---

# 8. Threat vs Vulnerability

It is important to understand the difference between a **threat** and a **vulnerability**.

### Threat

A threat is something that could potentially cause harm.

Example:

```text id="s7p1kq"
An attacker attempting to access a server.
```

### Vulnerability

A vulnerability is a weakness that could potentially be exploited.

Example:

```text id="y2xv9h"
An unpatched server with a known security vulnerability.
```

A threat may exploit a vulnerability to cause damage or gain unauthorized access.

---

# 9. My Learning

Through my networking studies, I learned about:

* IP addresses
* IPv4 and IPv6
* TCP/IP
* TCP and UDP
* Network protocols
* Network security
* Firewalls
* Network threats
* Network vulnerabilities
* CIA triad
* Basic network security controls

Understanding these concepts has helped me build a foundation for further cybersecurity learning.

---

# Key Takeaway

Networking is an important foundation of cybersecurity because security professionals need to understand how devices communicate and how network traffic can be protected and monitored.

The main concepts I learned are:

```text id="b9t1z4"
IP Addresses
      ↓
TCP/IP
      ↓
Network Protocols
      ↓
Network Security
      ↓
Firewalls
      ↓
Network Threats
      ↓
Network Vulnerabilities
```

I will continue building my networking knowledge through hands-on practice and cybersecurity labs.
