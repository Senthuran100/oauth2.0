
# OAuth 2.0

### What is OAuth 2.0
Oauth 2.0 stands for "Open Authorization", is a standard designed to allow a website or application to access resources hosted by other web apps on behalf of a user.

OAuth enables third-party websites or apps to access user's data without requiring them to share their credentials.

It is a set of rules that makes access delegation possible and the user gets to authorize which resources an app can access and limits access accordingly.

### Principles of OAuth 2.0
OAuth 2.0 is an authorization protocol and **NOT an authentication protocol** and it is designed primarily as a means of granting access to a set of resources, for example, remote APIs or user data.

OAuth 2.0 uses Access Tokens. An Access Token is a piece of data that represents the authorization to access resources on behalf of the end-user.

### OAuth 2.0 Roles
The idea of roles is part of the core specification of the OAuth2.0 authorization framework.
* **Resource Owner**: The user or system that owns the protected resources and can grant access to them.
* **Client**: The client is the system that requires access to the protected resources. To access resources, the Client must hold the appropriate Access Token.
* **Authorization Server**: This server receives requests from the Client for Access Tokens and issues them upon successful authentication and consent by the Resource Owner. The authorization server exposes two endpoints: the Authorization endpoint, which handles the interactive authentication and consent of the user, and the Token endpoint, which is involved in a machine to machine interaction.
* **Resource Server**: A server that protects the user’s resources and receives access requests from the Client. It accepts and validates an Access Token from the Client and returns the appropriate resources to it.

### OAuth 2.0 Scopes

Scope is a mechanism in OAuth 2.0 to limit an application's access to a user's account.<br/>
An application can request one or more scopes, this information is then presented to the user in the consent screen, and the access token issued to the application will be limited to the scopes granted.<br/>

### How Does OAuth 2.0 Work?

At the most basic level, before OAuth 2.0 can be used, the Client must acquire its own credentials, a _client id _ and client secret, from the Authorization Server.

Using OAuth 2.0, access requests are initiated by the Client, e.g., a mobile app, website, smart TV app, desktop application, etc and it follows the below step.
1. The Client requests authorization request from the Authorization server, supplying the client id and secret to as identification; it also provides the scopes and an endpoint URI (redirect URI) to send the Access Token or the Authorization Code to.
2. The Authorization server authenticates the Client and verifies that the requested scopes are permitted.
3. The Resource owner interacts with the Authorization server to grant access.
4. The Authorization server redirects back to the Client with either an Authorization Code or Access Token, depending on the grant type, as it will be explained in the next section. A Refresh Token may also be returned.
5. With the Access Token, the Client requests access to the resource from the Resource server.

