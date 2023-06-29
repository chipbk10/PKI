## HTTPS

- Client pings the server
- The server will return a certificate
- The client will check if the certificate is issued by a trusted CA (Certificate Authority)
- If the certificate is valid, the client will use the public key in the certificate to encrypt a secret key, and send back to the server
- The server will use its private key to decrypt this key
- From now on, the client and server use this secret key to encrypt and decrypt the data which is transferred between them
