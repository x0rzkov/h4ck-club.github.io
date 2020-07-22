###### openssl

```bash
# List available TLS cipher suites, openssl client is capable of:
openssl ciphers -v
# Generate a new private key and Certificate Signing Request
openssl req -out CSR.csr -new -newkey rsa:2048 -nodes -keyout privateKey.key
# Generate a self-signed certificate (see How to Create and Install an Apache Self Signed Certificate for more info)
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout privateKey.key -out certificate.crt
# Generate a certificate signing request (CSR) for an existing private key
openssl req -out CSR.csr -key privateKey.key -new
# Generate a certificate signing request based on an existing certificate
openssl x509 -x509toreq -in certificate.crt -out CSR.csr -signkey privateKey.key
# Remove a passphrase from a private key
openssl rsa -in privateKey.pem -out newPrivateKey.pem
# Generate an RSA key:
openssl genrsa -out example.key [bits]
# Print public key or modulus only:
openssl rsa -in example.key -pubout
openssl rsa -in example.key -noout -modulus
# Print textual representation of RSA key:
openssl rsa -in example.key -text -noout
# Generate new RSA key and encrypt with a pass phrase based on AES CBC 256 encryption:
openssl genrsa -aes256 -out example.key [bits]
# Check your private key. If the key has a pass phrase, you’ll be prompted for it:
openssl rsa -check -in example.key
# Remove passphrase from the key:
openssl rsa -in example.key -out example.key
# Encrypt existing private key with a pass phrase:
openssl rsa -des3 -in example.key -out example_with_pass.key
# Generate ECDSA key. curve is to be replaced with: prime256v1, secp384r1, secp521r1, or any other supported elliptic curve:
openssl ecparam -genkey -name [curve] | openssl ec -out example.ec.key
# Print ECDSA key textual representation:
openssl ec -in example.ec.key -text -noout
# List available EC curves, that OpenSSL library supports:
openssl ecparam -list_curves
# Generate DH params with a given length:
openssl dhparam -out dhparams.pem [bits]
```
