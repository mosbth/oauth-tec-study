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

![Abstract Flow of OAuth](https://upload.wikimedia.org/wikipedia/commons/7/72/Abstract-flow.png)

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

![Twitter OAuth flow](https://cdn.cms-twdigitalassets.com/content/dam/developer-twitter/docs/OAuth.png.twimg.1920.png)

How it works is outlined in the follwong articles.

* [BETA OAuth 2.0 User Context](https://developer.twitter.com/en/docs/authentication/oauth-2-0/user-context)
* [BETA OAuth 2.0 User Context - Making requests on behalf of users](https://developer.twitter.com/en/docs/authentication/oauth-2-0/user-context-making-requests-on-behalf-of-users)

A [code sample in Python](https://gist.github.com/JessicaGarson/d08dcfe364e28c6249f3ab6ba9151185) for use with Twitter oAuth authentication.



### Google

Google APIs use the OAuth 2.0 protocol for authentication and authorization. Google supports common OAuth 2.0 scenarios such as those for web server, client-side, installed, and limited-input device applications, read about "[Using OAuth 2.0 to Access Google APIs](https://developers.google.com/identity/protocols/oauth2)".

This is how Google sees the protocol flow for web server applications.

![Google OAuth flow](https://developers.google.com/identity/protocols/oauth2/images/flows/authorization-code.png)

Google has some [client libraries](https://developers.google.com/identity/protocols/oauth2#libraries) that can be used when doing OAuth, they support for example Python, PHP, JavaScript. The client libraries comes with examples and documentation on how to use it.



### Facebook

Facebook supports "Facebook Login" which can be used without being reviewed, if we only access public profile and the email.

Facebook Login is described here.

* [Facebook Login Overview](https://developers.facebook.com/docs/facebook-login/overview)
* [Facebook Login for the Web with the JavaScript SDK](https://developers.facebook.com/docs/facebook-login/web)

One can also read about how to "[Manually Build a Login Flow](https://developers.facebook.com/docs/facebook-login/manually-build-a-login-flow)" using the basic OAuth flow.

There is an article "[What You Need To Know About OAuth2 And Logging In With Facebook](https://www.smashingmagazine.com/2017/05/oauth2-logging-in-facebook/)" about the Facebook Login, it is written 2017 (unsure if it is still valid). The article also provides some general background of different authentication prior to OAuth2.



Libraries
----------------------

OAuth has a [list of libraries](https://oauth.net/code/) that can be used to implement OAuth.

On Packagist we can see the [most downloaded OAuth libraries for PHP](https://packagist.org/packages/league/oauth2-client?query=OAuth2).

On NPM we can see the [most downloaded OAuth libraries for JavaScript](https://www.npmjs.com/search?q=oauth2).

[Passport is an authentication solution](http://www.passportjs.org/) for Node and Express solutions.

[Laravel (PHP) has a Passport implementation](https://laravel.com/docs/8.x/passport).

> Laravel Passport provides a full OAuth2 server implementation for your Laravel application in a matter of minutes. Passport is built on top of the League OAuth2 server that is maintained by Andy Millington and Simon Hamp.

Symfony (PHP) supports [several ways of authenticating users](https://symfony.com/doc/current/security.html#security-authenticators). This includes an external [module HWIOAuthBundle](https://github.com/hwi/HWIOAuthBundle) that implements OAuth.



Related
----------------------

### OpenID

* https://en.wikipedia.org/wiki/OpenID
* https://openid.net/

The difference between OpenID and OAuth.

![OpenId versus OAuth](https://upload.wikimedia.org/wikipedia/commons/3/32/OpenIDvs.Pseudo-AuthenticationusingOAuth.svg)



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

What are we asking to get from the login provider?

* Email
* Profile data such as name?

Should we use OAuth or OpenID/BankID and was is the implications?
