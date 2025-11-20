# Implement-Cipher-Caser
Encrypting Project

def caesar_cipher(text, shift, mode):
    result = ""
    for char in text:
        if char.isalpha():
            ascii_offset = 65 if char.isupper() else 97
            if mode == "encrypt":
                shifted_char = chr((ord(char) - ascii_offset + shift) % 26 + ascii_offset)
            elif mode == "decrypt":
                shifted_char = chr((ord(char) - ascii_offset - shift) % 26 + ascii_offset)
            result += shifted_char
        else:
            result += char  # Non-alphabetical characters are unchanged
    return result

# User input
message = input("Enter your message: ")
shift_value = int(input("Enter shift value (integer): "))
operation = input("Type 'encrypt' to encrypt or 'decrypt' to decrypt: ").lower()

# Perform operation
if operation in ["encrypt", "decrypt"]:
    output_message = caesar_cipher(message, shift_value, operation)
    print(f"The {operation}ed message: {output_message}")
else:
    print("Invalid operation selected.")
