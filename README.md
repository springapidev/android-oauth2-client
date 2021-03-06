# OAuth2 client

## Rationale

Android OAuth2 clients are plentiful. Oddly enough, they all seem to focus on the authorization code grant type. This library aims to provide a solution for the resource owner password grant type. 

## Usage

```java
import org.sdf.danielsz.OAuth2Client;
import org.sdf.danielsz.Token;

OAuth2Client client = new OAuth2Client("username", "password", "app-id", "app-secret", "site");
Token token = client.getAccessToken();

token.getResource(client, token, "/path/to/resource?name=value");
```
With this grant type, the client application doesn't need to store the username/password of the user. Those credentials are asked once and exchanged for an access token. This token can then be used to access protected resources. 

To check if a token has expired:

```java
token.isExpired();
```

To refresh a token:

```java
Token newToken = token.refresh(client);
```

A more involved example can be found [here](https://github.com/danielsz/oauth2-client).

### Assumptions

- Your OAuth server delivers access tokens bundled with refresh tokens.

### Contributions

I welcome all contributions insofar as they remain in the realm of the resource owner password grant type. 

### Acknowledgments

The public API of this library was inspired by Ruby's OAuth2 [library](https://github.com/intridea/oauth2). 
The IBM developerWorks [article](http://www.ibm.com/developerworks/security/library/se-oathjavapt1/index.html) on the subject of this particular grant type was very helpful, too.
## License

This software is released as open source under the LGPLv3 license. If you need a commercial license for private forks and modifications, we will provide you with a custom URL to a privately hosted jar with a commercial-friendly license. Please mail me for further inquiries.

## Donations

As most developers, I'm working on multiple projects in parallel. If this project is important to you, you're welcome to signal it to me by sending me a donation via paypal or gittip. For paypal, use the email address in my github profile and specify in the subject it's for the OAuth2 client. On [gittip](http://www.gittip.com/danielsz/ "Gittip"), my username is danielsz. Thank you.
