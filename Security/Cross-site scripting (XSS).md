A cross-site scripting (XSS) attack is one in which an attacker is able to get a target site to execute malicious code as though it was part of the website.

A web browser downloads code from many different websites and runs it on the user's computer. Some of these websites will be highly trustworthy, and the user may use them for sensitive operations, such as financial transactions or medical advice. With others, such as a casual gaming site, the user may have no such trust relationship. The foundation of the browser's security model is that these sites should be kept separate from each other, so code from one site should not be able to access objects or [credentials](https://developer.mozilla.org/en-US/docs/Glossary/Credential) in another site. This is called the [same-origin policy](https://developer.mozilla.org/en-US/docs/Web/Security/Defenses/Same-origin_policy).

In a successful XSS attack, the attacker is able to subvert the same-origin policy by tricking the target site into executing malicious code within its own context, as though it were same-origin. The code can then do anything that the site's own code can do, including, for example:

- Access and/or modify all the content of the site's loaded pages, and any content in local storage
- Make HTTP requests with the user's credentials, enabling them to impersonate the user or access sensitive data

All XSS attacks depend on a website doing two things:

1. Accepting some input that could have been crafted by an attacker
2. Including this input in a page without _sanitizing_ it: that is, without ensuring that it won't be executable as JavaScript.

Taken from https://developer.mozilla.org/en-US/docs/Web/Security/Attacks/XSS