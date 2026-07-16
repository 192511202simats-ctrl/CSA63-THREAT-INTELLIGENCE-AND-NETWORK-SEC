# ex-1
```
import hashlib
from google.colab import files

# Upload file
print("Upload a file to scan")
uploaded = files.upload()

filename = list(uploaded.keys())[0]

# Calculate SHA-256
sha256 = hashlib.sha256()

with open(filename, "rb") as file:
    while True:
        data = file.read(4096)
        if not data:
            break
        sha256.update(data)

file_hash = sha256.hexdigest()

print("\nSHA-256 Hash:")
print(file_hash)

# Known malicious hashes
malicious_hashes = [
    "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "bbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbb"
]

if file_hash in malicious_hashes:
    print("\nMalware Detected!")
else:
    print("\nFile appears Safe.")
```
# sample output
```
Upload a file to scan
intell.txt
intell.txt(text/plain) - 147 bytes, last modified: 7/14/2026 - 100% done
Saving intell.txt to intell.txt

SHA-256 Hash:
57694f4fae9c12a33b05708ca8d6993740279d7c99823791b26ec60781b70545

File appears Safe.
```
