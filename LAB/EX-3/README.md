**EXPERIMENT-3**
**PYTHON CODE**
```
import socket

# Function to scan ports
def scan_ports(host, start_port, end_port):
    print(f"\nScanning {host} from port {start_port} to {end_port}...\n")

    for port in range(start_port, end_port + 1):
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(1)

        result = sock.connect_ex((host, port))

        if result == 0:
            print(f"Port {port}: OPEN")

        sock.close()

# Main Program
host = input("Enter the target host (IP address or hostname): ")
start_port = int(input("Enter the starting port: "))
end_port = int(input("Enter the ending port: "))

scan_ports(host, start_port, end_port)
```
**SAMPLE CODE**
```
Enter the target host (IP address or hostname): scanme.nmap.org
Enter the starting port: 1
Enter the ending port: 100

Scanning scanme.nmap.org from port 1 to 100...

Port 22: OPEN
Port 80: OPEN
```
