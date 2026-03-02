Sends HTTPS requests towards a target on the web

`curl http://www.google.com`

Will send a GET request (default) to google

`curl -X GET http://www.yahoo.com`

Will send a GET request (explicitly) to yahoo

`curl https://www.some_site.org`

Will return a warning because of a lack of authentication schema provided to access an https site.

`curl -k https://www.some_site.org`

Will some times succeed because  `-k` will tell curl to trust all certificates.