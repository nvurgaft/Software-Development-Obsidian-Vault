Cookies are small pieces of data that are created and stored inside your browser.  
They are sent by the server via HTTP responses and automatically included in future requests to the same domain.  

Cookies help websites remember state in an otherwise [[Stateless protocol]] (HTTP).  
Common uses include session management (e.g., login [[Sessions]]), personalization, autocomplete and tracking user preferences (shopping cart).

### Types of Cookies

1. Session cookies, deleted when the browser closes. 
2. Persistent cookies (stored for a set time).  
3. Secure cookie, is a cookie that can only be transmitted over a secure connection (HTTPS), set the `Secure` flag to enable.
4. Http-only cookies are cookies that are transmitted over secure connections (HTTPS) and can not be accessed from Javascript API's inside the browser (commonly used in tandem with [[JSON Web Tokens (JWT)]]), set the `HttpOnly` flat to enable.
5. Same-Site cookies, the browser would only send cookies to a target domain that is the same as the origin domain. This would effectively mitigate [[CSRF (Cross-Site Request Forgery)]] attacks. set the `SameSite` flag to enable.
6. Supercookies are cookies that are enabled over to level domain such as `.com` or `.gov.uk`. they are extremely susceptible to attacks and are rarely used.

Security flags like `HttpOnly`, `Secure`, and `SameSite` control access and transmission.  

Cookies are domain-specific and can have path restrictions.  

Cookies are limited in size (usually ~4KB per cookie).  

Improper use can lead to vulnerabilities like session hijacking, man in the middle attacks or data theft or [[CSRF (Cross-Site Request Forgery)]].