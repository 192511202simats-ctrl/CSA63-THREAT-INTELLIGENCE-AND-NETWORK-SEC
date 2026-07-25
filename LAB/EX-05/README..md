**EXPERIMENT-5**
**PYTHON CODE**
```
import socket

# Get domain name from the user
domain = input("Enter the domain name: ")

try:
    # Resolve domain to IP address
    ip_address = socket.gethostbyname(domain)

    print("\nDomain Name :", domain)
    print("IP Address  :", ip_address)

except socket.gaierror:
    print("\nInvalid domain name or unable to resolve.")
```
**SAMPLE OUTPUT**
```
Enter the domain name: github.com

Domain Name : github.com
IP Address  : 140.82.121.3
```
