**EXPERIMENT-2**
**PYTHON CODE**
```
from google.colab import files

uploaded = files.upload()
import hashlib

# Function to calculate SHA-256 hash
def calculate_hash(filename):
    sha256 = hashlib.sha256()

    with open(filename, "rb") as file:
        while True:
            data = file.read(4096)
            if not data:
                break
            sha256.update(data)

    return sha256.hexdigest()


# Main Program
filename = input("Enter the file name (Example: sample.txt): ")

try:
    # Calculate original hash
    original_hash = calculate_hash(filename)

    print("\nOriginal Hash:")
    print(original_hash)

    input("\nModify the file if you want to test tampering, then press Enter...")

    # Calculate new hash
    new_hash = calculate_hash(filename)

    print("\nNew Hash:")
    print(new_hash)

    # Compare hashes
    if original_hash == new_hash:
        print("\nIntegrity Verified: File has NOT been tampered with.")
    else:
        print("\nWarning! File has been tampered with.")

except FileNotFoundError:
    print("\nError: File not found!")
    print("Make sure you have uploaded the file to Google Colab.")
   ```
**SAMPLE CODE**
```
sample.txt
sample.txt(text/plain) - 10 bytes, last modified: 7/14/2026 - 100% done
Saving sample.txt to sample (3).txt
Enter the file name (Example: sample.txt): sample.txt

Original Hash:
9579ef1969682000a662d08a656bccf063bb58231690df9077a29e7c67e73ddf

Modify the file if you want to test tampering, then press Enter...

New Hash:
9579ef1969682000a662d08a656bccf063bb58231690df9077a29e7c67e73ddf

Integrity Verified: File has NOT been tampered with
```
