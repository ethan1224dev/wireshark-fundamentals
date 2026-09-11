# Wireshark Fundamentals
Hands-on network traffic analysis, protocol inspection, and security personal experiments using Wireshark.

# Wireshark Fundamentals & Network Analysis

A collection of hands-on packet analysis experiments exploring core network protocols, browser behavior, and the security implications of plaintext vs. encrypted traffic using Wireshark.

## 🛠️ Tools & Environment
* **Packet Analyzer:** Wireshark
* **Protocols Inspected:** DNS, HTTP, HTTPS / TLS 1.3, TCP, ICMP
* **Environment:** Local Wi-Fi Interface / Web Browser / Terminal CLI

# Experiment 1: Plaintext HTTP vs. Encrypted HTTPS Payload Inspection
## Objective
Compare unencrypted HTTP traffic against encrypted HTTPS (TLS 1.3) traffic to analyze payload visibility over the wire.

# Methodology & Steps
Initiated a live Wireshark packet capture on the active Wi-Fi interface.

Navigated to an unencrypted HTTP site (http://httpforever.com) in the browser.

Applied the display filter http to isolate unencrypted web traffic.

(<img width="980" height="459" alt="Screenshot 2026-09-11 130018" src="https://github.com/user-attachments/assets/63d02e19-83e3-4ee5-b482-4ce128165b17" />)


# Key Findings
Unencrypted HTTP Visibility: Full HTML source code, headers, and request details were completely visible in plain text. Any network listener can observe the payload contents.

<img width="808" height="636" alt="Screenshot 2026-09-11 130758" src="https://github.com/user-attachments/assets/fd6c4f8a-eb0a-48ed-92f2-32d5b39e46cc" />


Encrypted HTTPS Behavior: Traffic payload appeared as scrambled, high-entropy binary text. While protocol metadata (such as IP addresses and ports) remains visible, the payload itself is protected by symmetric session encryption generated during the TLS handshake.

Display Filters Used
http: This isolates unencrypted HTTP request and response packets.

tls: This displays encrypted Transport Layer Security traffic.
Selected the GET / HTTP/1.1 request packet, right-clicked, and selected Follow > HTTP Stream.

Navigated to an encrypted HTTPS site (https://youtube.com) and attempted to inspect the raw UDP stream via Follow > UDP Stream.
<img width="974" height="191" alt="image" src="https://github.com/user-attachments/assets/b92f63e4-62ad-45d9-96b5-39519f1cd87b" />

<img width="735" height="712" alt="image" src="https://github.com/user-attachments/assets/ff34f579-a954-469c-a76b-5c499d2f7323" />



