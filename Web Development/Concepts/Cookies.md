- [What are Cookies?](#what-are-cookies)
- [Cookie Limitations](#cookie-limitations)
- [Creating Cookies](#creating-cookies)
  - [Cookie Lifetimes](#cookie-lifetimes)
- [Security Concerns](#security-concerns)
  - [MitM Attacks](#man-in-the-middle-attacks)
  - [XSS Attacks](#xss-attacks)
  - [CSRF Attacks](#csrf-attacks)
- [Cookie Alternatives](#cookie-alternatives)
- [Sources](#sources)

[Read the full documentation on cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)

# What are Cookies?

HTTP is a stateless transfer protocol, meaning that information about the user is not remembered acrross HTTP requests. The user requests some data, the sever sends some data, then the connection is closed. However, most web applications need to remeber things about the user in order to function well. Such as facebook. It needs to remember that you're logged in, otherwise everytime you navigate to a new page on facebook, you would have to sign in again. That's were cookies come in. They allow us to create stateful sessions on the web.

Cookies are like the wrist band you get when visiting an amusement park. You check in and you recieve a wrist band to let the park know that you've already check in and can come and go as you please.

Similarly, this is what happens when you sign in to a web application. The server checks your username and password, creates and stores a session, generates a unique session id, and sends back a cookie with the session id. *The session id is not your password*, but is separate and generated on the fly.

When you make a request to a website you're signed into, your browser sends your cookie with your session id back to the sever. The server then checks for your session using your session id, then reutrns data for your request.

When you sign out of a website, the browser sends a sign out request with your cookie, the server removes your session, and lets your browser know to remove your session id cookie.

![](https://www.freecodecamp.org/news/content/images/size/w1000/2021/02/fireship-cookies.png)

# Cookie limitations

Cookies are pretty limited compared to other alternatives such as `localStorage` and `sessionStrogae`.

| | Cookies | Local Storage | Session Stroage |
|---|---|---|---|
| Capacity | 4KB | 10MB | 5MB |
| Accessible from | Any window | Any window | Same tab |
| Expires | Manually set | Never | On tab |
| Storage Location | Browser and server | Browser only | Browser only |
| Sent with requests | Yes | No | No |

# Creating Cookies

Cookies are really just strings with key/value pairs and you'll generally work with them on the backend. AFter recieing an HTTP request, you can send one or more `Set-Cookie` headers with the response. The browser will then store the information and send it with requests to the same server in a `Cookie` header. Information in a cookie is stored in key-value pairs, and a simple cookie is set like this:

```
Set-Cookie: <cooki-name>=<cookie-value>
```

Then, with every following request to the same server, the broswer sends all previously stored cookies back using the `Cookie` header, allowing us to store and use a session id to keep users login over multiple sessions.

## Cookie Lifetimes

A cookies lifetime can be defined in 2 ways

1. *Session* cookies that are deleted when the current session ends. The browser defines when the "current session" ends, and some broswers use *session restoring*, which can cause session cookies to last indefinitely.

2. *Permanent* cookies are delted at a date specified by the `Expires` attribute, or after a period of time specified by the `Max-Age` attribute.

```
Set-Cookie: id=a3fWa; Expires=Thu, 31 Oct 2021 07:28:00 GMT;
```

# Security Concerns

In general, cookies are very secure when implemented correctly, but there are still a few ways a bad actor can attept to steal your cookie and wreak havoc.

## Man-in-the-Middle Attacks

A man-in-the-middle (MitM) attack describes a category of attacks where the attacker sits between a client and a server and intercepts the data going between the two. This can be done by listening in on an insecure website, mimicking a public wifi router, DNS spoofing, or though malware/adware.

![](https://www.freecodecamp.org/news/content/images/size/w1000/2021/02/man-in-the-middle-attack-how-avoid.png)

You can greatly reduce the risk of MitM attacks by ensuring that you enable HTTPS on your server, use an SSL certificate from a trusted certificate authority, and ensure you code uses HTTPS instead of HTTP.

In terms of the cookies, you should add the `Secure` attribute so that the cookie can only be sent over HTTPS connections. This doesn't encrypt you cookie, only ensures that it can't be sent over HTTP.

You can also use the `HttpOnly` paramter to make it so that cookie can only be accessed by the server and not the browsers `Document.cookie` API. This is great for login sessions, where only server needs to know if you're signed in.

## XSS Attacks

An XSS (cross-site scripting) attack is a category of attacks where a bad actor inject unintended, potentially dangerous code into a website. These can affect every person that visits the site, making them ber problematic.

![](https://www.freecodecamp.org/news/content/images/2021/02/cross-site-scripting.svg)

As a developer, you'll want to ensure that your server enforces the Same Origin Policy, and that any input you receive from people is properly sanitized.

And just like the MitM attacks, you should set the `Secure` and `HttpOnly` parameters with any cookies you use.

## CSRF Attacks

A CSRF (cross-site request forgery) attack is when a bad actor tricks a person into carrying out an unintended, potentially malicious aciton.

For example, if you're signed into a site and click on a link in a comment, if that link is part of a CSRF attack, it may lead to you unintentionally changing your sign in details, or even deleting your account.

![](https://www.freecodecamp.org/news/content/images/2021/02/cross-site-request-forgery.svg)

The best way to protect your cookies from these attacks is with the `SameSite` flag. This can be set to either `Lax`, `Strict`, or `None`.

- `Lax` cookies are not sent for embedded content but are sent when you click on a link or send a request ot the origin the cookie is set for.

- `Strict` cookies are only sent when you click a link or send a request from the origin the cookie is set for.

- `None` cookies will be sent with every request regarless of context. If you use this value (which you should always avoid) you must also add the `Secure` attribute.

# Cookie Alternatives

A few alternatives to cookes are `sessionStorage` and `localStorage` that can be used for general information stored in cookies. For stateful sessions, you can use token bases authentication with things like JWT (JSON Web Tokens). There's also authentication-as-a-service providers like Auth0 that allow you to use cookies and tokens at the same time!

# Sources

- [freeCodeCamp article by Kris Koishigawa](https://www.freecodecamp.org/news/everything-you-need-to-know-about-cookies-for-web-development/)
- [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)
