**EXPERIMENT-6**
**PYTHON CODE**
```
# List of known malicious IP addresses (IoCs)
malicious_ips = [
    "192.168.1.100",
    "10.0.0.5",
    "203.0.113.50"
]

# Get IP address from the user
ip = input("Enter the IP address: ")

# Check whether the IP is malicious
if ip in malicious_ips:
    print("\nResult: ALERT! Malicious IP Detected.")
else:
    print("\nResult: Safe IP Address.")
```
**SAMPLE OUTPUT**
```
Enter the IP address: 140.82.121.3

Result: Safe IP Address.
```
