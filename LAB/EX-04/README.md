**EXPERIMENT-4**
**PTHON CODE**
```
# Python Program to Detect a Suspicious (Phishing) URL

url = input("Enter the URL: ")

print("\nChecking the URL...")

# Common phishing indicators
if "@" in url:
    print("Warning: '@' symbol found.")

if "-" in url:
    print("Warning: Hyphen (-) found in the domain.")

if url.count(".") > 3:
    print("Warning: Too many dots in the URL.")

if url.startswith("http://"):
    print("Warning: Uses HTTP instead of HTTPS.")

if len(url) > 75:
    print("Warning: URL is unusually long.")

# Final Result
if ("@" in url or
    "-" in url or
    url.count(".") > 3 or
    url.startswith("http://") or
    len(url) > 75):
    print("\nResult: This URL is likely a PHISHING link.")
else:
    print("\nResult: This URL appears to be SAFE.")
```
**SAMPLE OUTPUT**
```
Enter the URL: https://colab.research.google.com

Checking the URL...

Result: This URL appears to be SAFE.
```
