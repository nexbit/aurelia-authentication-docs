# Quick api overview

```js
// signup into server with credentials and optionally logs in
signup(credentials: Object)): Promise<Response>
 // log into server with credentials. Stores token if successful
login(credentials: Object): Promise<Response>
// deletes stored tokens
logout([redirectUri: string]): Promise<>
// manually refresh token. Needs refreshToken options to be configured
updateToken(): Promise<Response> {
// link thrird-party accounts or use it to log into server. Stores token if successful
authenticate(provider: string[, redirectUri: string][, userData: Object]): Promise<Response>
// unlink third-party
unlink(provider: string): Promise<Response>
// get profile
getMe([criteria: Object|string|number]): Promise<Response>
// update profile
updateMe(data: Object[,criteria: Object|string|number]): Promise<Response>
// check if token is available and, if applicable, not expired
isAuthenticated(): boolean
// get token if available
getTokenPayload(): string
```
