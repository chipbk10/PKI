# JWT

## SessionID + Cookies
- Login
  - client sends username & password request. The server validates the credential against the database.
  - if the credential is correct, the server will generate a session token which is a unique identifier that represents the user's session.
  - the server stores the session token in the Session Management (like a database), and associate it with user's account
  - the client stores the session token in the cookie, and will send together with subsequent requests
- Logout:
  - the client sends a logout request, and remove the sessionToken from the cookie
  - the server removes the sessionToken from Session Management

- Benefits:
  - we can invalidate a token easily by deleting the session token from Session Management

- Cons:
  - Not easy to scale, because we have to maintain the Session Management. Let say, Session Management is using a database, when we scale up our application, we have to replicate this database on several servers. When a session token is generated on a database, we have to replicate this change on all databases (on different servers)

## JWT
- Login:
  - client sends username & password request. The server validates the credential agains the database.
  - if the credential is correct, the server will generate a JWT token, and send it back to the client
  - JWT contains information about the user, such as their user ID, email, or role, and a signature to verify its authenticity.
  - the client includes JWT in the authorization header of subsequent requests to the server
  - the server uses the signature to verify the JWT's authenticity and extract the user information from it.
  - JWT token also contains the expiration info. The server also checks this info to see if the token is still valid.

- Logout:
  - the client simply discards the JWT. Since JWTs are stateless, the server does not need to maintain any session information, so there is no need to invalidate the token on the server side.

- Benefits:
  - JWT tokens are stateless, we don't have to maintain the Session Management. It's easier to scale the application and distribute load across multiple servers.
  - JWT token are signed using a secret key making them tamper-proof and resistant to attacks like [CSRF]() and [XSS]().
 
- Cons:
  - in case, we suspect that a token which is compromised by hacker, we want to revoke this token, we have to add this token to a black list. Maintaining and using this blacklist for every request will impact the performance and scale up, because normaly the blacklist is stored in a database. To solve this problem, we just make the token as a short-live token (few minutes to few hours)
 
## Access Token & Refresh Token

- We call the JWT token to authenticate and authorize as an Access Token which is a short-lived token (few minutes to few hours).
- A refresh token is a long-lived token that is used to obtain a new access token when the current access token expires. The refresh token is issued along with the access token and is typically valid for a longer period, such as days or weeks. The refresh token is also signed using a secret key to prevent tampering.
- When the access token expires, the client sends a request to the server with the refresh token to obtain a new access token. The server validates the refresh token, generates a new access token, and returns it to the client along with a new refresh token.
- Using a refresh token allows the client to obtain new access tokens without requiring the user to re-enter their credentials. This improves the user experience and reduces the risk of credential theft or interception.
    
## JWT structure


## Source

- [What is JWT authorization really about](https://www.youtube.com/watch?v=soGRyl9ztjI&ab_channel=JavaBrains)
- [What is the structure of a JWT](https://www.youtube.com/watch?v=_XbXkVdoG_0&t=2s&ab_channel=JavaBrains)
- [ChatGPT]()
