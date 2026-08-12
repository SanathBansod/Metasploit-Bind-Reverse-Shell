# Evidence 05 — Meterpreter Session

## Objective

The objective of this step was to verify and demonstrate a Meterpreter session established through the authorized laboratory environment.

Meterpreter provides an interactive session that can be used for controlled security assessment and post-exploitation enumeration.

## Meterpreter

Meterpreter is a Metasploit payload that provides an interactive session after successful payload execution and connection establishment.

In this practical, Meterpreter was demonstrated using the authorized laboratory environment.

## Session Establishment

The session was established after the configured payload successfully communicated with the Metasploit handler.

Depending on the communication model used:

### Reverse TCP

    Target → Multi/Handler

### Bind TCP

    Multi/Handler → Target

Both communication models can result in a Meterpreter session when the payload and handler configuration are compatible.

## Session Verification

After the session was established, the available sessions were reviewed using:

    sessions

The active Meterpreter session was then accessed.

## System Information

The following command was used:

    sysinfo

This command provides information about the target system, including:

- Computer name
- Operating system
- Architecture
- Meterpreter platform

## User Context

The current security context was checked using:

    getuid

The command identifies the user associated with the Meterpreter session.

## Current Directory

The current working directory was checked using:

    pwd

This provides the current location within the target filesystem.

## Filesystem Enumeration

Basic filesystem information was reviewed using:

    ls

The command displays files and directories available in the current location.

## Network Information

The target network configuration can be reviewed using:

    ipconfig

This provides information about the network interfaces and IP addresses available on the target.

## Process Information

Running processes can be reviewed using:

    ps

This provides information about active processes on the target system.

## Network Connections

Network connections can be reviewed using:

    netstat

This can provide information about active connections and listening network services.

## Security Relevance

A Meterpreter session provides an assessor with an interactive interface for controlled security assessment.

The information available through the session can help determine:

- Target operating system
- System architecture
- Current user context
- Filesystem structure
- Network configuration
- Running processes
- Network connections

All enumeration performed during this practical was limited to the authorized laboratory environment.

## Evidence Screenshot

The following screenshot provides evidence of the established Meterpreter session.

![Meterpreter Session](../screenshots/05-meterpreter.png)

## Result

A Meterpreter session was successfully established in the authorized laboratory environment.

The session was verified and basic system information was collected using Meterpreter commands.

## Conclusion

The Meterpreter practical demonstrated how a successful payload connection can result in an interactive security-assessment session.

The session provided the foundation for the subsequent post-exploitation enumeration phase.

## Authorization

This activity was performed exclusively within an authorized cybersecurity laboratory environment for educational and security-training purposes.

No unauthorized systems were targeted.
