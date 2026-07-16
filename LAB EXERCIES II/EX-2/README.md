# ex-2
```
import re

url = input("Enter URL: ")

suspicious_words = [
    "login",
    "verify",
    "bank",
    "secure",
    "update",
    "paypal",
    "account"
]

score = 0

if len(url) > 75:
    score += 1

if re.search(r'\d+\.\d+\.\d+\.\d+', url):
    score += 1

if url.count('-') > 1:
    score += 1

for word in suspicious_words:
    if word in url.lower():
        score += 1

print("\nRisk Score:", score)

if score >= 3:
    print("Possible Phishing URL")
else:
    print("Likely Safe URL")
```
# sample output
```
Enter URL: https://secure-login-paypal-update.com

Risk Score: 5
Possible Phishing URL
```
