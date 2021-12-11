# Authentication & Production Server 

## JSON Web Tokens
JSON Web Token: open standard that defines a compact and self-contained way for securely transmitting information between parties as a JSON object.
- Signed tokens can verify the integrity of the claims contained within it, while encrypted tokens hide those claims from other parties.
- When JWTs are useful:
  - Authorization: Onece the user is logged in, each subsequent request will include the JWT, allowing the user to access routes, services, and resources that are permitted with that token.
  - Information Exchange: JWTs are a secure way to tramsmit data. Becausethey can be signed, you can verify the senders are who they say they are. You can also verify the content has not been tampered with. 
- JWTs consist of three parts (separated by dots):
  - Header
  - Payload
  - Signature
  - Looks like the following: xxxxx.yyyyy.zzzzz
- Example of header (consisting of token type and the signing algo used:
```
{
  "alg": "HS256",
  "typ": "JWT"
}
```
- Payload contains the claims, which are statements about an entity (usually the user) and additional data. Types of claims:
  - Registered: Predefined claims which are not required. They provide a set of useful claims. Ex.: iss(issuer), exp(expiration), sub(subject). 
  - Public: Can be defined at will. Sound be defined in IANA JSON Web Token Registry or as a URI that contains a collision resistant namespace.
  - Private: Custom claims created to share information between parties that agree on using them. 
- Payload example:
```
{
  "sub": "1234567890",
  "name": "John Doe",
  "admin": true
}
```
- Signature is created by taking the encoded header, encoded payload, a secret, the algo from the header, and sign it. Using HMAC SHA256, this is an example of signature creation:
```
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  secret)
```
- Steps on how a JWT is obtained and used to access APIs or resources:
```
1. The application or client requests authorization to the authorization server. This is performed through one of the different authorization flows. For example, a typical OpenID Connect compliant web application will go through the /oauth/authorize endpoint using the authorization code flow.

2. When the authorization is granted, the authorization server returns an access token to the application.
 
3. The application uses the access token to access a protected resource (like an API).
```


