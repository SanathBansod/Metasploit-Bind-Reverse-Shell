# Bind & Reverse Shell using Metasploit

> Hands-on cybersecurity laboratory demonstrating msfvenom payloads, Metasploit Multi/Handler, Reverse TCP, Bind TCP, Meterpreter sessions, and post-exploitation in an authorized virtual lab environment.

---

## 📌 Project Overview

This project demonstrates different shell and payload concepts using the Metasploit Framework in a controlled and authorized cybersecurity laboratory environment.

The practical focuses on understanding how an attacker and target can establish sessions using different communication models and how Meterpreter can be used for controlled post-exploitation enumeration.

The following topics are covered:

- msfvenom Payload
- Metasploit Multi/Handler
- Reverse TCP
- Bind TCP
- Meterpreter
- Post-Exploitation

---

## 🧪 Lab Environment

| Component | Details |
|---|---|
| Attacker Machine | Kali Linux |
| Target Machine | Authorized Laboratory VM |
| Framework | Metasploit Framework |
| Payload Generator | msfvenom |
| Session Handler | Multi/Handler |
| Assessment Type | Authorized Laboratory Assessment |
| Virtualization | VMware |

---

## 🔐 Authorization

All activities documented in this repository are performed only against systems owned by or explicitly authorized for security testing.

The practical is conducted inside an isolated laboratory environment for educational and cybersecurity training purposes.

No unauthorized systems are targeted.

---

# 🔎 Practical Methodology

The practical is divided into six major sections:

    msfvenom Payload
          ↓
    Multi/Handler
          ↓
    Reverse TCP
          ↓
    Bind TCP
          ↓
    Meterpreter
          ↓
    Post-Exploitation

---

# 1️⃣ msfvenom Payload

## Objective

Understand how `msfvenom` is used to generate Metasploit-compatible payloads for an authorized laboratory environment.

## Tool

    msfvenom

## Key Concepts

A payload defines the functionality delivered after successful execution on the authorized target.

Important payload concepts include:

- Payload type
- Architecture
- Platform
- Connection method
- Listener configuration
- Local host
- Local port

## Example Payload Concept

For the laboratory environment, a Linux Meterpreter reverse TCP payload can be generated using an appropriate Metasploit payload.

The payload configuration must correspond to the target operating system and architecture.

## Security Relevance

Understanding payload generation helps security professionals understand how exploitation frameworks establish communication channels after code execution.

---

# 2️⃣ Metasploit Multi/Handler

## Objective

Understand how Metasploit's `exploit/multi/handler` module receives connections from a compatible payload in an authorized laboratory environment.

## Module

    exploit/multi/handler

## Important Options

    PAYLOAD
    LHOST
    LPORT

The handler configuration must match the payload configuration.

## Workflow

    Payload
       ↓
    Target Execution
       ↓
    Connection
       ↓
    Multi/Handler
       ↓
    Session

## Security Relevance

A handler provides the listener component required to receive a compatible session.

---

# 3️⃣ Reverse TCP

## Objective

Understand the Reverse TCP communication model in which the authorized target initiates a connection back toward the configured listener.

## Communication Model

    Target
       |
       |  Outbound TCP Connection
       ↓
    Attacker / Listener

## Key Parameters

    LHOST
    LPORT

`LHOST` represents the address used by the listener, while `LPORT` represents the TCP port on which the listener waits for the incoming connection.

## Workflow

    1. Configure payload
    2. Configure listener
    3. Execute payload in authorized lab
    4. Target initiates connection
    5. Handler receives connection
    6. Session is established

## Security Relevance

Reverse connections are important to understand because many security tools and real-world attack techniques use outbound connections from a compromised host.

---

# 4️⃣ Bind TCP

## Objective

Understand the Bind TCP communication model in which the target listens for an incoming connection.

## Communication Model

    Attacker
       |
       |  Incoming TCP Connection
       ↓
    Target Listener

Unlike a reverse connection, the target creates a listening endpoint and the connecting system initiates the connection toward that endpoint.

## Key Concept

The primary difference is the direction in which the session connection is initiated.

### Reverse TCP

    Target → Attacker

### Bind TCP

    Attacker → Target

## Security Relevance

Understanding both connection models helps security professionals recognize different network communication patterns during penetration testing and incident investigation.

---

# 5️⃣ Meterpreter

## Objective

Understand the Meterpreter environment and perform controlled enumeration after establishing an authorized laboratory session.

## Meterpreter

Meterpreter is an advanced Metasploit payload that provides an interactive session with capabilities useful for authorized security testing and post-exploitation assessment.

## Example Enumeration Commands

    sysinfo

    getuid

    pwd

    ls

    ipconfig

    ps

    netstat

## Information Collected

The enumeration can provide information about:

- Operating system
- Architecture
- Current user
- Working directory
- Filesystem
- Network interfaces
- Running processes
- Network connections

## Security Relevance

Meterpreter demonstrates how a successful session can provide additional visibility into the security state of an authorized laboratory system.

---

# 6️⃣ Post-Exploitation

## Objective

Perform controlled post-exploitation enumeration after obtaining an authorized Meterpreter session.

## Enumeration Areas

### System Information

    sysinfo

Used to identify operating system and architecture information.

### User Context

    getuid

Used to determine the security context of the current session.

### Filesystem

    pwd
    ls

Used to understand the current location and filesystem structure.

### Network

    ipconfig
    netstat

Used to identify network interfaces and active/listening connections.

### Processes

    ps

Used to identify running processes and services.

## Security Assessment

Post-exploitation enumeration helps an assessor understand the impact of a successful compromise without unnecessarily modifying or disrupting the target system.

---

# 🔄 Reverse TCP vs Bind TCP

| Feature | Reverse TCP | Bind TCP |
|---|---|---|
| Listener | Attacker | Target |
| Connection Initiated By | Target | Attacker |
| Direction | Target → Attacker | Attacker → Target |
| Main Concept | Callback connection | Target-side listener |
| Typical Lab Purpose | Demonstrate reverse connection | Demonstrate bind connection |

---

# 📊 Practical Workflow

    ┌───────────────────────┐
    │   msfvenom Payload    │
    └───────────┬───────────┘
                ↓
    ┌───────────────────────┐
    │   Multi/Handler       │
    └───────────┬───────────┘
                ↓
       ┌────────┴────────┐
       ↓                 ↓
    Reverse TCP       Bind TCP
       ↓                 ↓
       └────────┬────────┘
                ↓
        Meterpreter Session
                ↓
       Post-Exploitation
                ↓
          Evidence & Report

---

# 📸 Evidence

Detailed practical evidence will be maintained under the `evidence/` directory.

Planned evidence sections:

1. msfvenom Payload
2. Multi/Handler
3. Reverse TCP
4. Bind TCP
5. Meterpreter
6. Post-Exploitation

Screenshots from the authorized laboratory environment will be stored under the `screenshots/` directory.

---

# 📂 Repository Structure

    Metasploit-Bind-Reverse-Shell/
    │
    ├── README.md
    │
    ├── evidence/
    │   ├── 01-msfvenom-payload.md
    │   ├── 02-multi-handler.md
    │   ├── 03-reverse-tcp.md
    │   ├── 04-bind-tcp.md
    │   ├── 05-meterpreter.md
    │   └── 06-post-exploitation.md
    │
    └── screenshots/
        ├── 01-msfvenom-payload.png
        ├── 02-multi-handler.png
        ├── 03-reverse-tcp.png
        ├── 04-bind-tcp.png
        ├── 05-meterpreter.png
        └── 06-post-exploitation.png

---

# 🎯 Skills Demonstrated

- Metasploit Framework
- msfvenom
- Payload concepts
- Multi/Handler
- Reverse TCP
- Bind TCP
- Meterpreter
- Linux enumeration
- Network enumeration
- Post-exploitation
- Security documentation
- Evidence collection

---

# 🧠 Key Learning Outcomes

This practical demonstrates the relationship between payloads, listeners, communication direction, sessions, and post-exploitation.

The major concepts learned are:

    Payload
       ↓
    Listener
       ↓
    Connection
       ↓
    Session
       ↓
    Enumeration
       ↓
    Security Assessment

Understanding these components provides a foundation for analyzing how exploitation frameworks establish and manage sessions during authorized penetration testing.

---

# ⚠️ Disclaimer

This project is intended strictly for authorized cybersecurity education and laboratory testing.

The techniques, tools, payloads, and commands documented in this repository must only be used against systems for which explicit authorization has been obtained.

No unauthorized systems are targeted.
