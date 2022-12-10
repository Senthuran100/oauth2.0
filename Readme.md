
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

### Grant Types in OAuth 2.0

In OAuth 2.0, grants are the set of steps a Client has to perform to get resource access authorization.

##### Client Credentials Grant Flow
The client credentials grant provides a specific grant flow in which the resource owner is not involved. 

When using this grant, the client application requests an access token only with its own credentials (the identifier and secret) or an assertion, and uses the access token on behalf of the client application itself. 

This grant flow is best-suited when a service provider wants to provide some API methods that are to be used by the client application in general, instead of methods that apply to a certain resource owner, for example, API methods for maintenance. 

This way of using an API is also referred to as userless access.

![Client Credentials Grant Flow](https://github.com/Senthuran100/oauth2.0/blob/main/gif/Client_Credentials.gif)

##### Resource Owner Password Credentials Grant Flow.
The Resource Owner Password Credentials flow allows exchanging the username and password of a user for an access token.

The resource owner password credentials grant type is suitable in cases where the resource owner has a trust relationship with the client.

The user’s password is accessible to the application so this requires strong trust of the application by the user.

![Resource Owner Password Credentials Grant Flow](https://github.com/Senthuran100/oauth2.0/blob/main/gif/Password_Grant.gif)

##### Authorization Code Grant Flow.

The authorization code grant is used when an application exchanges an authorization code for an access token.

After the user returns to the application via the redirect URL, the application will get the authorization code from the URL and use it to request an access token.

![Authorization Code Grant Flow](https://github.com/Senthuran100/oauth2.0/blob/main/gif/Authorization_Code.gif)

##### Implicit Grant Flow
The Implicit Grant Type is a way for a single-page JavaScript app to get an access token without an intermediate code exchange step.

It was originally created for use by JavaScript apps (which don’t have a way to safely store secrets) but is only recommended in specific situations.

In the Implicit Grant flow, your integration requests an access token directly. This is potentially less secure because the access token must be stored on the user’s device, but it does not require that the integration have access to a web server.


![Implicit Grant Flow](https://github.com/Senthuran100/oauth2.0/blob/main/gif/Implicit_Flow.gif)

#### When to use which grant type

**Is the Client the Resource Owner?**

The first decision point is about whether the party that requires access to resources is a machine. In the case of machine-to-machine authorization, the Client is also the Resource Owner, so no end-user authorization is needed.

Eg:- A cron job that uses an API to import information to a database.
In this example, the cron job is the Client and the Resource Owner since it holds the Client ID and Client Secret and uses them to get an Access Token from the Authorization Server.

In this case **Client Credential Flow** is most appropriate.

**Is the Client absolutely trusted with user credentials ?**

This decision point may result in the Resource Owner Password Credentials Grant. 

In this flow, the end-user is asked to fill in credentials (username/password), typically using an interactive form. This information is sent to the backend and from there to Authorization server. 

It is therefore imperative that the Client is absolutely trusted with this information.

**Is the Client a web app executing on the server?**




