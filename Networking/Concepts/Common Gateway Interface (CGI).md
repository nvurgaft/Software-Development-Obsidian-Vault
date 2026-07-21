[^1]An HTTP server is often used as a gateway to a legacy information system; for example, an existing body of documents or an existing database application. The Common Gateway Interface is an agreement between HTTP server implementers about how to integrate such gateway scripts and programs.

It is typically used in conjunction with HTML forms to build database applications.

[^2]The Common Gateway Interface (CGI) specification was introduced to enable and standardize the interface between Web servers and external programs. The CGI is a relatively simple, platform and language independent, industry-standard interface for Web application development. Programs that implement the CGI standard are commonly called CGI programs.

The purpose of CGI is to extend the capability of an HTTP server by providing framework in which an HTTP server can interface with a program that is specified on a URL. The format of the URL allows parameters to be passed to the CGI program. On the server side, the interface describes how the program is started by the HTTP server and how parameters for the program are passed using a combination of standard-input and environment variables. It also describes how output information (such as HTML elements) are passed back to the HTTP server using standard output. Thus, in its simplest form, a CGI program can be defined as a program that:

1. Can be called as an executable program and run as a child process of the HTTP server.
2. Is able to read from the standard input.
3. Is able to access environment variables.
4. Is able to write to the standard output.
5. Is able to access command- line arguments passed to the program.

The administrator controls which CGI programs the system can run by using the server directives. The server recognizes a URL that contains a request for a CGI program, commonly called a CGI script. (Throughout the documentation, we use the terms CGI program and CGI script to mean the same thing.) Depending on the server directives, the server calls that program on behalf of the client.

[^1]: https://www.w3.org/CGI/
[^2]: https://www.ibm.com/docs/en/i/7.6.0?topic=functionality-cgi
