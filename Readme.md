
# OAuth 2.0

### What is OAuth 2.0
Oauth 2.0 stands for "Open Authorization", is a standard designed to allow a website or application to access resources hosted by other web apps on behalf of a user.</br>

OAuth enables third-party websites or apps to access user's data without requiring them to share their credentials.</br>

It is a set of rules that makes access delegation possible and the user gets to authorize which resources an app can access and limits access accordingly.</br>

### Principles of OAuth 2.0
OAuth 2.0 is an authorization protocol and **NOT an authentication protocol** and it is designed primarily as a means of granting access to a set of resources, for example, remote APIs or user data.</br>

OAuth 2.0 uses Access Tokens. An Access Token is a piece of data that represents the authorization to access resources on behalf of the end-user.</br>

### OAuth 2.0 Roles
The idea of roles is part of the core specification of the OAuth2.0 authorization framework.</br>
* **Resource Owner**: The user or system that owns the protected resources and can grant access to them.
* **Client**: The client is the system that requires access to the protected resources. To access resources, the Client must hold the appropriate Access Token.
* **Authorization Server**: This server receives requests from the Client for Access Tokens and issues them upon successful authentication and consent by the Resource Owner. The authorization server exposes two endpoints: the Authorization endpoint, which handles the interactive authentication and consent of the user, and the Token endpoint, which is involved in a machine to machine interaction.
* **Resource Server**: A server that protects the user’s resources and receives access requests from the Client. It accepts and validates an Access Token from the Client and returns the appropriate resources to it.

### OAuth 2.0 Scopes

