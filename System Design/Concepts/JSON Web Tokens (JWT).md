JWT (JSON Web Token) is a compact way to represent user identity and claims between systems, commonly used for authentication in APIs and web apps.
## Structure of a JWT

A JWT has 3 parts separated by dots:

```text
header.payload.signature
```

Example:

```text
eyJhbGciOiJIUzI1NiJ9
.
eyJzdWIiOiIxMjMiLCJyb2xlIjoiQURNSU4ifQ
.
abc123signature
```
## 1. Header

Contains metadata about the token:

```json
{
  "alg": "HS256",
  "typ": "JWT"
}
```

- `alg` → signing algorithm
- `typ` → token type
## 2. Payload

Contains claims and/or data used for the current session 

```json
{
  "username": "nick",
  "role": "ADMIN",  
  "iat": 1422779638,
  "exp": 1715550000
}
```

The data can be anything, but some claims are necessary for session maintenance (state with the server). 

Some common claims are

- `username` → subject/user ID
- `exp` → expiration time
- `iat` → issued at
- `role` → custom application claim

Important:  
The payload is **Base64 encoded, not encrypted**. Anyone can read it.

## 3. Signature

The signature is used to verify the authenticity of the request and user.
The signature is created using some cryptographic algorithm.
Some common algorithms are [HMAC](https://en.wikipedia.org/wiki/HMAC "HMAC") with [SHA-256](https://en.wikipedia.org/wiki/SHA-256 "SHA-256") (HS256) and [RSA signature](https://en.wikipedia.org/wiki/Digital_signature "Digital signature") with SHA-256 (RS256).

```javascript
HMACSHA256(
    base64UrlEncode(header) + "." + base64UrlEncode(payload),
    secret
)
```

Will return a signature that looks like this

```
SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
```

This prevents tampering.

If someone changes the payload, the signature becomes invalid and the server side can easily discover the tempering.

## Security concerns

### Minimize Access to token

Note that storing the JWT Token in the browser's local storage is generally discouraged as it could be accessed from by Javascript, even from running 3rd party browser extension.
Therefor, storing the token inside an HTTP-Only cookie is encouraged as it will be sent to the server on an encrypted channel and could not be read by the browser.

### Never store sensitive data in JWT payload

Do not store authentication data because the token payload can be easily examined

```json
{
  "password": "123456"
}
```

### Use HTTPS

The token is only hashed and signed, the stored data is not encrypted. Use an encrypted carrier such as SSL/TLS over HTTPS, tokens can easily intercepted and read by a man in the middle. 

### Keep expiration short

JWTs are hard to revoke before expiration. Use refresh tokens to prolong your authenticated state with the server.

### Validate signature properly

Signing is a crucial step in ensuring proper authentication and identity with the server side.
Never trust unsigned tokens !

# Authentication Flow

## Step 1 — User logs in

Client sends credentials:

```http
POST /login
```

Server validates username/password.
## Step 2 — Server creates JWT

Server generates token:

```json
{
  "sub": "42",
  "role": "USER",
  "exp": ...
}
```

Signs it with a secret key.

The header, payload and signature all combined for the final token, this will be sent back to the client.

```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.  
eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvbiBEb2UiLCJyb2xlIjoiYWRtaW4ifQ.  
SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
```
## Step 3 — Client stores token

Usually in:

1. Memory - The token is stored on the browser but not in any storage.
2. HTTP-only cookie - Token is stored in a special encrypted cookie, readable only to the server and the browser.
3. localStorage (less secure) - Accessible by all

## Step 4 — Client sends token on requests

```http
Authorization: Bearer eyJhbGciOi...
```

Has to be attached to every HTTP request to the server. 
This is usually implemented on both sides using filters.
## Step 5 — Server validates token

Server:

1. Verifies signature
2. Checks expiration,
3. Extracts claims
4. Authenticates request

JWT acts as an alternative to common server side [[Sessions]]. Username and password lookup inside a database may still be required.
# Motivation

## Stateless authentication

Server does not store sessions. All the necessary session data is stored inside the token and is passed between the server and client.

This scales well in distributed systems/microservices (e.g. [[Sessions#Sticky Sessions|Sticky Sessions]]).

# Refresh Token

A JWT refresh token is a long-lived token used to obtain a new access token when the current one expires (as denoted by the `exp` claim). This allows users to stay logged in without needing to re-enter their credentials and re-authenticate frequently.
### Access Token

Are relatively short-lived (5–30 mins) and sent on every authenticated request. 
### Refresh Token

Are long-lived and used to obtain new access tokens

## How Refresh Tokens Work

### Token Lifecycle

1. Login: When a user logs in, the server issues both an access token and a refresh token.
2. Access Token Usage: The access token is used to access protected resources. It typically has a short lifespan (e.g., minutes to hours).
3. Token Expiration: Once the access token expires, the user must use the refresh token to obtain a new access token.
4. Refreshing the Token: The client sends the refresh token to the server, which verifies it and issues a new access token (and possibly a new refresh token).

### Security Features

- Short-lived Access Tokens: Access tokens expire quickly to minimize the risk of unauthorized access.
- Long-lived Refresh Tokens: Refresh tokens last longer, allowing users to maintain their sessions without frequent logins.
- Secure Storage: Refresh tokens should be stored securely, often in HTTP-only cookies, to prevent unauthorized access.

## Benefits of Using Refresh Tokens

- Improved User Experience: Users can remain logged in without repeated authentication.
- Enhanced Security: By limiting the lifespan of access tokens, the risk of misuse is reduced.
- Seamless Session Management: Refresh tokens allow for smooth transitions between sessions, especially in mobile and web applications.

In summary, JWT refresh tokens play a crucial role in maintaining secure and user-friendly authentication processes in modern applications.

# JWT vs Sessions

| JWT                         | Sessions                        |
| --------------------------- | ------------------------------- |
| Stateless                   | Stateful                        |
| Scales easily               | Requires shared session storage |
| Good for APIs/microservices | Simpler revocation              |
| Harder logout/revocation    | Easier invalidation             |
