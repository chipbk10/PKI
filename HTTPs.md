# HTTPS

## Https Hand Shake

- Client pings the server
- The server will return a certificate
- The client will check if the certificate is issued by a trusted CA (Certificate Authority)
- If the certificate is valid, the client will use the public key in the certificate to encrypt a secret key, and send back to the server
- The server will use its private key to decrypt this key
- From now on, the client and server use this secret key to encrypt and decrypt the data which is transferred between them

## Https Session

- We can use Https Session which allows the client and the server to reuse the same encryption key from a previous session, without the need to repeat the entire key exchange process. This can help reduce the overhead of establishing a new HTTPS session and improve performance.
- At the end of the handshake of the first https request, the server will send a session ID to the client
- When a client receives a session ID from the server, it can store the session ID in a cookie and send the cookie back to the server with subsequent requests.
- This allows the server to recognize the client and resume the same session, using the session ID to look up the **session state** and encryption key associated with the session.
- Note that the client also needs to remember the encrypted key of the previous session, store it somewhere (like cookies), and re-use it to encrypt data for the next request.
- A Https Session can be expired. The expiration time of a Https session will be defined from the server side

## Https Tikets

- Https Tickets contains the **session state** (like the encrypted key from the previous session, the client IP address, expiration time, timestamp, etc.)
- The server encrypts the session ticket using a secret key that is shared with the client
- The client uses this encrypted session ticket together with the subsequent requests
- The server will look up the encrypted session ticket in a table or cache of **active session tickets** and their associated shared secret keys
- The server uses the shared secret key to decrypt the session ticket to get the session state and resume the https session
- While session tickets themselves are stateless in the sense that they do not require server-side state storage, the server does need to maintain a cache or table of active session tickets and their associated secret keys in order to efficiently handle session resumption requests.
- However, the amount of state information that needs to be stored on the server is typically much smaller than for traditional server-side session management, which requires the server to maintain full session state for each client. Session tickets provide a lightweight and efficient mechanism for session resumption that can help reduce the burden on the server and improve performance.
