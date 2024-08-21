#!/bin/bash
ENCRYPTED_FILE="/home/puspa_raj_regmi/vm_folder/encrypted_sample.txt"
PRIVATE_KEY="/home/puspa_raj_regmi/vm_folder/host-private.pem"
DECRYPTED_FILE="/home/puspa_raj_regmi/vm_folder/decrypted_sample_puspa.txt"
if [ ! -f "$ENCRYPTED_FILE" ]; then
    echo "Error: Encrypted file not found: $ENCRYPTED_FILE"
    exit 1
fi
if [ ! -f "$PRIVATE_KEY" ]; then
    echo "Error: Private key file not found: $PRIVATE_KEY"
    exit 1
fi
# Decrypt the file
echo "Decrypting the file..."
if openssl pkeyutl -decrypt -inkey "$PRIVATE_KEY" -in "$ENCRYPTED_FILE" -out "$DECRYPTED_FILE>
    echo "Decryption successful."
else
    echo "Error: Decryption failed."
    exit 1
fi
# Verify the decryption
if [ -f "$DECRYPTED_FILE" ]; then
    echo "Contents of $DECRYPTED_FILE:"
    cat "$DECRYPTED_FILE"
else
    echo "Error: Decrypted file not found: $DECRYPTED_FILE"
    exit 1
fi

