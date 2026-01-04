# AES Encryption/Decryption Tool

A simple Python implementation of AES (Advanced Encryption Standard) encryption and decryption using CBC (Cipher Block Chaining) mode.

## Overview

This project consists of two Python scripts that demonstrate AES encryption and decryption:
- **AESEncrypt.py** - Encrypts a message and saves it to a binary file
- **AESDecrypt.py** - Reads the encrypted file and decrypts the message

## Features

- AES-256 encryption (32-byte key)
- CBC (Cipher Block Chaining) mode
- PBKDF2 key derivation from password
- Automatic padding/unpadding
- Secure IV (Initialization Vector) generation

## Requirements

- Python 3.x
- pycryptodome library

## Installation

1. Install the required library using pip:

```bash
pip install pycryptodome
```

## Usage

### Step 1: Encrypt a Message

Run the encryption script to encrypt a message:

```bash
python AESEncrypt.py
```

This will:
- Encrypt the message using AES-256 in CBC mode
- Generate a random IV (Initialization Vector)
- Save the IV and encrypted data to `encrypted.bin`

### Step 2: Decrypt the Message

Run the decryption script to decrypt the message:

```bash
python AESDecrypt.py
```

This will:
- Read the IV and encrypted data from `encrypted.bin`
- Decrypt the message using the same password and salt
- Print the original message to the console

## How It Works

1. **Key Derivation**: The password is combined with a salt using PBKDF2 to generate a 32-byte (256-bit) encryption key
2. **Encryption**: 
   - A random IV is generated for each encryption
   - The message is padded to match AES block size (16 bytes)
   - The message is encrypted using AES-256-CBC
   - Both IV and encrypted data are saved to `encrypted.bin`
3. **Decryption**:
   - The IV (first 16 bytes) and encrypted data are read from the file
   - The same key is derived using the password and salt
   - The data is decrypted and unpadded
   - The original message is displayed

## Important Notes

⚠️ **Security Considerations**:
- The password and salt are currently hardcoded in both scripts
- For production use, consider:
  - Using environment variables or secure input methods for passwords
  - Generating a unique salt for each encryption
  - Implementing proper key management practices
  - Using secure file permissions for encrypted files

## File Structure

```
AES/
├── AESEncrypt.py      # Encryption script
├── AESDecrypt.py      # Decryption script
├── encrypted.bin      # Generated encrypted file (created after running AESEncrypt.py)
└── README.md          # This file
```

## Example Output

After running `AESDecrypt.py`, you should see:

```
b'Hello, India Won the World Cup!!'
```

## License

This is a demonstration project for educational purposes.

