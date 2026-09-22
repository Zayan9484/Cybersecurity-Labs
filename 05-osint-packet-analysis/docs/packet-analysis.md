# Packet Analysis

Wireshark was used against an intentionally vulnerable training web application.

The lab workflow was:
1. start a packet capture;
2. submit test credentials to the vulnerable login page;
3. filter for the HTTP POST request;
4. follow the HTTP stream; and
5. inspect the request contents.

The exercise demonstrated a basic but important security point: credentials sent over unencrypted HTTP can be visible to someone who can capture the traffic. HTTPS is designed to prevent this kind of plaintext exposure in transit.
