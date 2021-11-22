OAuth Technical Study
======================

This is a tec study to learn how to use OAuth to add login to a web page using a third party supplier for authentication.



Search on the term
----------------------

We start with a (Google) search on the following terms, just to get a starting point.

* OAuth
* OAuth standard
* OAuth GitHub
* OAuth GitLab
* OAuth Google account
* OAuth Facebook account
* OAuth Twitter account
* OAuth PHP library
* OAuth JavaScript Node library



### General

A general description of OAuth can be found on [Wikipedia](https://en.wikipedia.org/wiki/OAuth) and on the [OAuth.net site](https://oauth.net/2/).

An overview of the general frol of OAuth.

![https://upload.wikimedia.org/wikipedia/commons/7/72/Abstract-flow.png](Abstract Flow of OAuth)

History of versions.

* OAuth 1.0 was released 2010.
* OAuth 2.0 was released 2012 and is not backward compatible.
* OAuth 2.1 is in draft stage.

The specifications is available as RFC.

* [rfc6749: The OAuth 2.0 Authorization Framework](https://datatracker.ietf.org/doc/html/rfc6749)
* [rfc6745: The OAuth 2.0 Authorization Framework: Bearer Token Usage](https://datatracker.ietf.org/doc/html/rfc6745)


The general flow for OAuth 2.0 is sketched like this.

```text
+--------+                               +---------------+
|        |--(A)- Authorization Request ->|   Resource    |
|        |                               |     Owner     |
|        |<-(B)-- Authorization Grant ---|               |
|        |                               +---------------+
|        |
|        |                               +---------------+
|        |--(C)-- Authorization Grant -->| Authorization |
| Client |                               |     Server    |
|        |<-(D)----- Access Token -------|               |
|        |                               +---------------+
|        |
|        |                               +---------------+
|        |--(E)----- Access Token ------>|    Resource   |
|        |                               |     Server    |
|        |<-(F)--- Protected Resource ---|               |
+--------+                               +---------------+
```



### GitLab

GitLab has an article on how to implement OAuth 2 with GitLab, "[GitLab: OAuth 2.0 identity provider API](https://docs.gitlab.com/ee/api/oauth2.html)".

Depending on the application, GitLab suggests the following techniques.

* [Authorization code with Proof Key for Code Exchange (PKCE)](https://tools.ietf.org/html/rfc7636#section-1.1): Most secure. Without PKCE, you’d have to include client secrets on mobile clients, and is recommended for both client and server apps.

* [Authorization code](https://tools.ietf.org/html/rfc6749#section-4.1): Secure and common flow. Recommended option for secure server-side apps.



### GitHub

GitHub has a pretty easy to read article on how to implement OAuth with GitHub, "[Authorizing OAuth Apps](https://docs.github.com/en/developers/apps/building-oauth-apps/authorizing-oauth-apps)".

Depending on the application, GitLab suggests the following techniques.

* [Standard authorization code grant type](https://tools.ietf.org/html/rfc6749#section-4.1).

* [OAuth 2.0 Device Authorization Grant](https://tools.ietf.org/html/rfc8628) for apps that don't have access to a web browser.

The web application flow to authorize users for your app is:

1. Users are redirected to request their GitHub identity
2. Users are redirected back to your site by GitHub
3. Your app accesses the API with the user's access token



### Twitter

Twitter has a beta support for OAuth 2.0.

![https://cdn.cms-twdigitalassets.com/content/dam/developer-twitter/docs/OAuth.png.twimg.1920.png](Twitter OAuth flow)

How it works is laied out in the follwong articles.

* [BETA] OAuth 2.0 User Context](https://developer.twitter.com/en/docs/authentication/oauth-2-0/user-context)
* [[BETA] OAuth 2.0 User Context - Making requests on behalf of users](https://developer.twitter.com/en/docs/authentication/oauth-2-0/user-context-making-requests-on-behalf-of-users)

A [code sample in Python](https://gist.github.com/JessicaGarson/d08dcfe364e28c6249f3ab6ba9151185) for use with Twitter oAuth authentication.



Related
----------------------

### OpenID

* https://en.wikipedia.org/wiki/OpenID
* https://openid.net/

The difference between OpenID and OAuth.

![https://upload.wikimedia.org/wikipedia/commons/3/32/OpenIDvs.Pseudo-AuthenticationusingOAuth.svg](OpenId versus OAuth)



Read more
----------------------

* [Vad är skillnaden mellan OAuth, OpenID Connect och SAML?](https://www.okta.com/se/identity-101/whats-the-difference-between-oauth-openid-connect-and-saml/)

* [BankID](https://support.bankid.com/sv)

* [Digitala signaturer och certifikat](https://support.microsoft.com/sv-se/office/digitala-signaturer-och-certifikat-8186cd15-e7ac-4a16-8597-22bd163e8e96)

* [Sunet: Allmänna frågor om eduSIGN](https://wiki.sunet.se/pages/viewpage.action?pageId=98861084)

* [SUNET: Getting Started with SWAMID](https://wiki.sunet.se/display/SWAMID/Getting+Started+with+SWAMID)



Considerations
----------------------

You should/need to use HTTPS for the redirection URL.

You need to have the system running on a public server.
