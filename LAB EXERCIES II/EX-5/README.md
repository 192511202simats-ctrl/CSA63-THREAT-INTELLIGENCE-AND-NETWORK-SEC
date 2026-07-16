# ex-5
```
import socket

target = input("Enter Target IP or Domain: ")

print("\nScanning...\n")

ports = [20,21,22,23,25,53,80,110,135,139,143,443,445,3306,3389]

for port in ports:
    sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    sock.settimeout(1)

    result = sock.connect_ex((target, port))

    if result == 0:
        print("Port", port, "is OPEN")

    sock.close()

print("\nScan Completed")
```
# sample output
```
Enter Target IP or Domain: scanme.nmap.org

Scanning...

Port 22 is OPEN
Port 80 is OPEN

Scan Completed
```
