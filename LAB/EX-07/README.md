**EXPERIMENT-7**
**PYTHON CODE**
```
from google.colab import files

# Upload the login log file
uploaded = files.upload()

# Get the uploaded file name
filename = list(uploaded.keys())[0]

failed_logins = {}

# Read the log file
with open(filename, "r") as file:
    for line in file:
        data = line.strip().split()

        if len(data) == 2:
            ip, status = data

            if status.upper() == "FAILED":
                failed_logins[ip] = failed_logins.get(ip, 0) + 1

# Display the results
print("\nFailed Login Attempts Per IP Address:\n")

if failed_logins:
    for ip, count in failed_logins.items():
        print(f"{ip} : {count}")
else:
    print("No failed login attempts found.")
```
**SAMPLE OUTPUT**
```
intell.txt
intell.txt(text/plain) - 147 bytes, last modified: 7/14/2026 - 100% done
Saving intell.txt to intell (1).txt

Failed Login Attempts Per IP Address:

192.168.1.10 : 2
192.168.1.30 : 2
192.168.1.20 : 1
```
