In a cross-site request forgery (CSRF) attack, an attacker tricks the user or the browser into making an HTTP request to the target site from a malicious site. The request includes the user's credentials and causes the server to carry out some harmful action, thinking that the user intended it.

In general, a CSRF attack is possible if your website:

- Uses HTTP requests to change some state on the server.
- Uses only cookies to validate that the request came from an authenticated user.
- Uses only parameters in the request that an attacker can predict.

### Defenses against CSRF

- The first primary defense is to [use _CSRF tokens_](https://developer.mozilla.org/en-US/docs/Web/Security/Attacks/CSRF#csrf_tokens) embedded in the page. This is the most common method if you're issuing state-changing requests from form elements, as in our example above.
- The second is to use Fetch metadata HTTP headers to check whether or not the state-changing request is being issued cross-site.
- The third is to ensure that state-changing requests are [not _simple requests_](https://developer.mozilla.org/en-US/docs/Web/Security/Attacks/CSRF#avoiding_simple_requests), so that cross-origin requests are blocked by default. This method is appropriate if you're issuing state-changing requests from JavaScript APIs like [`fetch()`](https://developer.mozilla.org/en-US/docs/Web/API/Window/fetch "fetch()").

Source: https://developer.mozilla.org/en-US/docs/Web/Security/Attacks/CSRF