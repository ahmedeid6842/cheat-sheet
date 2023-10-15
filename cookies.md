<h1 align="center"> Cookies </h1>

<div align="center"><img src="https://oko.uk/wp-content/uploads/2019/12/cookie-types.jpg" alt="cookit image"/></div>

## Overview

An **HTTP cookie** (web cookie, browser cookie) is a small piece of data that a server sends to a user's web browser. The browser may store the cookie and send it back to the same server with later requests. Typically, an HTTP cookie is used to tell if two requests come from the same browser—keeping a user logged in.

<aside>

🔥 Cookies were invented in 1994 by Netscape company's employees to store customer shopping cart data until purchase instead of storing on the server which cost more money. 

By default, cookies are sent with every request. The maximum size is 4KB. By default when you close the browser, all cookies are deleted.

</aside>

### Useful Video Overview:

- [HTTP Cookies - Hussein Nasser](https://www.youtube.com/watch?v=sovAIX4doOE&t=3275s) 

## Creating Cookies

There are two main ways to create cookies:

- **Server-side:** By adding a `Set-Cookie` header in the response. When the browser sees this header, it will set the cookie.

- **Client-side:** By accessing `document.cookie` in JavaScript.

## Cookie Properties

### Domain

The `domain` property specifies which domain the cookie should be sent to. For example, setting `domain=example.com` means the cookie will only be sent for requests to `example.com`, not `www.example.com`. 

To make the cookie available to all subdomains, set it to `.example.com`.

### Path

The `path` property controls what endpoints the cookie is sent to. Setting `path=/api` would restrict the cookie only to `/api` routes.

### Expires

By default, cookies are deleted when the browser is closed. The `expires` property allows setting an expiration date to persist cookies across sessions.

### SameSite

The `SameSite` property controls when cookies are sent on cross-site requests:

- `strict` - Only send on same-site requests 
- `lax` - Don't send on cross-site GET requests
- `none` - Always send 
- (empty) - Treat as `lax` on Chrome, `none` on other browsers
  [SameSite explaination](https://www.youtube.com/watch?v=aUF2QCEudPo)

### HttpOnly 

The `HttpOnly` property prevents JavaScript access to cookies. This is useful for security sensitive cookies.

## Third-Party Cookies

Third-party cookies are set by domains other than the one you are visiting directly. This allows advertisers and analytics services to track you across sites. 

Browsers now block third-party cookies by default for privacy. Popular techniques like cookie syncing are used to get around these restrictions.

[Third-Party video](https://www.youtube.com/watch?v=47b4kJ2XDqI)

## Useful Resources

1. [HTTP Cookies hussein nasser](https://www.youtube.com/watch?v=sovAIX4doOE&t=3275s)
2. [video aobut cookies,localstorage and session storage](https://www.youtube.com/watch?v=AwicscsvGLg)
3. [article about cookies,localstorage and session storage](https://www.kirupa.com/hodgepodge/cookies_local_session_storage.htm)
4. [samesite cookies](https://www.youtube.com/watch?v=aUF2QCEudPo&t=458s)
5. [Please Stop Using Local Storage (article)](https://dev.to/rdegges/please-stop-using-local-storage-1i04)
6. [zombie cookies](https://www.youtube.com/watch?v=lq6ZimHh-j4&t=309s)
7. [how third party  cookies tracking you](https://stackoverflow.com/questions/13897472/how-do-third-party-tracking-cookies-work)
8. [how cookies track you](https://www.youtube.com/watch?v=QWw7Wd2gUJk)
9. [third party cookies mechanism](https://www.youtube.com/watch?v=m4vatwFryI8)
