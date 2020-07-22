###### methods
```
- HEAD GET  POST  OPTIONS  PUT  DELETE  TRACE  CONNECT 
```
###### uri
```
https://0x.34044@www.example.com:123/forum/questions/?tag=networking&order=newwest#top
|___| |_____________________________||______________||___________________________||__| 
  |                 |                        |                   |                  |
scheme          authority                  path                query            fragment   
```
###### HTTP Request
```
	GET /example.html 
	HTTP/1.1Accept: image/gif, */*
	Accept-Language: en-us
	Accept-Encoding: gzip, deflate
	User-Agent: Mozilla/4.0 Host: 192.168.123.144
	Connection: Keep-Alive
```	

###### HTTP Response
```
	HTTP/1.1 200 OKDate: Sat, 25 May 2002 21:10:32 GMT
	Server: Apache/1.3.19 (Unix) 
	Last-Modified: Sat, 25 May 2002 20:51:33 GMT
	ETag: "56497-51-3ceff955"
	Accept-Ranges: bytes
	Content-Length: 81
	Keep-Alive: timeout=15, max=100Connection: Keep-Alive
	Content-Type: text/html
	
		<HTML><BODY><H1>Internet Lab</H1>
		Click <a href="http://www.tcpip-lab.net/index.html">here</a> for the Internet Lab webpage.
		</BODY>
		</HTML>
```
###### headers
```
Accept-Charset
Accept-Encoding
Access-Control-Request-Headers
Access-Control-Request-Method
Connection
Content-Length
Cookie
Cookie2
Date
DNT
Expect
Host
Keep-Alive
Origin
Referer
TE
Trailer
Transfer-Encoding
Upgrade
User-Agent
Via
```
######  http status codes 
```
+-----+--------------------------------------------------------+
| 1xx | Informational                                          |
+-----+--------------------------------------------------------+
| 100 | Continue                                               |
| 101 | Switching Protocols                                    |
| 102 | Processing (WebDAV; RFC 2518)                          |
+-----+--------------------------------------------------------+

+-----+--------------------------------------------------------+ 
| 2xx | Success                                                |
+-----+--------------------------------------------------------+
| 200 | OK                                                     |
| 201 | Created                                                |
| 202 | Accepted                                               |
| 203 | Non-Authoritative Information (since HTTP/1.1)         |
| 204 | No Content                                             |
| 205 | Reset Content                                          |
| 206 | Partial Content                                        |
| 207 | Multi-Status (WebDAV; RFC 4918)                        |
| 208 | Already Reported (WebDAV; RFC 5842)                    |
| 226 | IM Used (RFC 3229)                                     |
+-----+--------------------------------------------------------+

+-----+--------------------------------------------------------+ 
| 3xx | Redirection                                            |
+-----+--------------------------------------------------------+
| 300 | Multiple Choices                                       |
| 301 | Moved Permanently                                      |
| 302 | Found                                                  |
| 303 | See Other (since HTTP/1.1)                             |
| 304 | Not Modified                                           |
| 305 | Use Proxy (since HTTP/1.1)                             |
| 306 | Switch Proxy                                           |
| 307 | Temporary Redirect (since HTTP/1.1)                    |
| 308 | Permanent Redirect (approved as experimental RFC])[11] |
+-----+--------------------------------------------------------+
 
+-----+--------------------------------------------------------+
| 4xx | Client Error                                           |
+-----+--------------------------------------------------------+
| 400 | Bad Request                                            |
| 401 | Unauthorized                                           |
| 402 | Payment Required                                       |
| 403 | Forbidden                                              |
| 404 | Not Found                                              |
| 405 | Method Not Allowed                                     |
| 406 | Not Acceptable                                         |
| 407 | Proxy Authentication Required                          |
| 408 | Request Timeout                                        |
| 409 | Conflict                                               |
| 410 | Gone                                                   |
| 411 | Length Required                                        |
| 412 | Precondition Failed                                    |
| 413 | Request Entity Too Large                               |
| 414 | Request-URI Too Long                                   |
| 415 | Unsupported Media Type                                 |
| 416 | Requested Range Not Satisfiable                        |
| 417 | Expectation Failed                                     |
| 418 | I'm a teapot (RFC 2324)                                |
| 420 | Enhance Your Calm (Twitter)                            |
| 422 | Unprocessable Entity (WebDAV; RFC 4918)                |
| 423 | Locked (WebDAV; RFC 4918)                              |
| 424 | Failed Dependency (WebDAV; RFC 4918)                   |
| 424 | Method Failure (WebDAV)[13]                            |
| 425 | Unordered Collection (Internet draft)                  |
| 426 | Upgrade Required (RFC 2817)                            |
| 428 | Precondition Required (RFC 6585)                       |
| 429 | Too Many Requests (RFC 6585)                           |
| 431 | Request Header Fields Too Large (RFC 6585)             |
| 444 | No Response (Nginx)                                    |
| 449 | Retry With (Microsoft)                                 |
| 450 | Blocked by Windows Parental Controls (Microsoft)       |
| 451 | Unavailable For Legal Reasons (Internet draft)         |
| 494 | Request Header Too Large (Nginx)                       |
| 495 | Cert Error (Nginx)                                     |
| 496 | No Cert (Nginx)                                        |
| 497 | HTTP to HTTPS (Nginx)                                  |
| 499 | Client Closed Request (Nginx)                          |
+-----+--------------------------------------------------------+
 
+-----+--------------------------------------------------------+
| 5xx | Server Error                                           |
+-----+--------------------------------------------------------+
| 500 | Internal Server Error                                  |
| 501 | Not Implemented                                        |
| 502 | Bad Gateway                                            |
| 503 | Service Unavailable                                    |
| 504 | Gateway Timeout                                        |
| 505 | HTTP Version Not Supported                             |
| 506 | Variant Also Negotiates (RFC 2295)                     |
| 507 | Insufficient Storage (WebDAV; RFC 4918)                |
| 508 | Loop Detected (WebDAV; RFC 5842)                       |
| 509 | Bandwidth Limit Exceeded (Apache bw/limited extension) |
| 510 | Not Extended (RFC 2774)                                |
| 511 | Network Authentication Required (RFC 6585)             |
| 598 | Network read timeout error (Unknown)                   |
| 599 | Network connect timeout error (Unknown)                |
+-----+--------------------------------------------------------+
```

