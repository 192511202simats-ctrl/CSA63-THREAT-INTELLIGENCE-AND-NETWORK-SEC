# ex-4
```
#!pip install scapy
from scapy.all import sniff

def packet_callback(packet):
    print(packet.summary())

print("Capturing 10 packets...\n")

sniff(prn=packet_callback, count=10)
```
# sample output
```
Capturing 10 packets...

Ether / IP / TCP 172.28.0.12:8080 > 172.28.0.1:51668 PA / Raw
Ether / IP / TCP 172.28.0.1:51668 > 172.28.0.12:8080 A
Ether / IP / TCP 172.28.0.12:8080 > 172.28.0.1:51668 PA / Raw
Ether / IP / TCP 172.28.0.1:51668 > 172.28.0.12:8080 A
Ether / IP / TCP 172.28.0.12:8080 > 172.28.0.1:51668 PA / Raw
Ether / IP / TCP 172.28.0.1:51668 > 172.28.0.12:8080 A
Ether / IP / TCP 172.28.0.12:8080 > 172.28.0.1:51668 PA / Raw
Ether / IP / TCP 172.28.0.1:51668 > 172.28.0.12:8080 A
Ether / IP / TCP 172.28.0.12:8080 > 172.28.0.1:51668 PA / Raw
Ether / IP / TCP 172.28.0.1:51668 > 172.28.0.12:8080 A
<Sniffed: TCP:10 UDP:0 ICMP:0 Other:0>
```
