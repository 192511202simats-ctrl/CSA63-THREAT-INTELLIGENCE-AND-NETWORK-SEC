**EXPERIMENT-1**
**PYTHON CODE**
```
# Caesar Cipher - Encryption and Decryption
# Demonstrates Confidentiality

def encrypt(text, shift):
    result = ""

    for char in text:
        if char.isalpha():
            if char.isupper():
                result += chr((ord(char) - ord('A') + shift) % 26 + ord('A'))
            else:
                result += chr((ord(char) - ord('a') + shift) % 26 + ord('a'))
        else:
            result += char

    return result


def decrypt(text, shift):
    result = ""

    for char in text:
        if char.isalpha():
            if char.isupper():
                result += chr((ord(char) - ord('A') - shift) % 26 + ord('A'))
            else:
                result += chr((ord(char) - ord('a') - shift) % 26 + ord('a'))
        else:
            result += char

    return result


# Main Program
message = input("Enter the message: ")
shift = int(input("Enter the shift value: "))

encrypted = encrypt(message, shift)
decrypted = decrypt(encrypted, shift)

print("\nOriginal Message :", message)
print("Encrypted Message:", encrypted)
print("Decrypted Message:", decrypted)
```
**SAMPLE CODE**
```
Enter the message: HELLO WORLD
Enter the shift value: 3

Original Message : HELLO WORLD
Encrypted Message: KHOOR ZRUOG
Decrypted Message: HELLO WORLD
