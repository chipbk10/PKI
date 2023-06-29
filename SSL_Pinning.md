## Why is HTTPs still not secured?

- HTTPS is still not secured enough, because when the client receive a certificate, it only checks if the certificate is issued by a trusted CA
- A hacker can play a role as a man in the middle who sends a fake certificate to the client to receive the key, and then use the public key from the server to decrypt this key, and send back to the server
- A fake certificate can be installed on the client’s device, and the OS system will trust the communication.

## SSL-Pinning

- To fix this issue, there should be a way through which the client can identify that this is a fake certificate, or not the certificate of the server that the client wants to communicate with

### SSL-Pinning Certificate

- We can pin the certificate of the server into the bundle of the application. Because the actual certificate of the server, we can access to it, we can download and put it into the bundle of the app
- When our app starts a https connection, and receives a certificate, we will compare this certificate with the one we have in the bundle
- Cons: we need to release a new build whenever the certificate is expired 

### SSL-Pinning Public Key

- We keep the public key of the server’s certificate in our code
- We do the same, we compare the public key of the certificate with the one we have in our code
- Pros: we don’t need to release a new build, because the public key remains the same, even if the certificate is changed
