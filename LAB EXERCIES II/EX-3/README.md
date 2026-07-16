# ex-3
```
from google.colab import files

print("Upload log file")
uploaded = files.upload()

filename = list(uploaded.keys())[0]

threshold = 10

ip_count = {}

with open(filename, "r") as file:
    for line in file:
        ip = line.strip()

        if ip:
            ip_count[ip] = ip_count.get(ip, 0) + 1

print("\nPossible DoS Attack:")

found = False

for ip, count in ip_count.items():
    if count >= threshold:
        print(ip, "->", count, "requests")
        found = True
```
# sample output
```
Upload log file
intell.txt
intell.txt(text/plain) - 147 bytes, last modified: 7/14/2026 - 100% done
Saving intell.txt to intell (1).txt

Possible DoS Attack:
No suspicious activity detected.
```

if not found:
    print("No suspicious activity detected.")
