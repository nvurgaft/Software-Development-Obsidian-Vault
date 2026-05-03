Cookies are small pieces of data that a website stores in your browser.  
They are sent by the server via HTTP responses and automatically included in future requests to the same domain.  

Cookies help websites remember state in an otherwise [[Stateless protocol]] (HTTP).  
Common uses include session management (e.g., login [[Sessions]]), personalization, and tracking.  
There are session cookies (deleted when the browser closes) and persistent cookies (stored for a set time).  

Security flags like HttpOnly, Secure, and SameSite control access and transmission.  
Cookies are domain-specific and can have path restrictions.  
They are limited in size (usually ~4KB per cookie).  
Improper use can lead to vulnerabilities like session hijacking or [[CSRF (Cross-Site Request Forgery)]].