Sends HTTPS requests towards a target on the web

```shell
curl http://www.google.com`
```

Will send a `GET` request (default) to google

```shell
curl -X GET http://www.yahoo.com
```

Will send a `GET` request (explicitly) to yahoo

```shell
curl https://www.some_site.org
```

Will return a warning because of a lack of authentication schema provided to access an https site.

```shell
curl -k https://www.some_site.org
```

May succeed at times because  `-k` will tell curl to trust all certificates.

You can append headers using the `--header` or `-H` flags

```shell
curl http://hostname/resource -X GET 
	-H "Accept: application/json" 
	-H "Content-Type: application/json"
```
