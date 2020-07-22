###### curl
```
+--------------------------------+-----------------------------------------------------------------------------------------------------------------+
| http methods                   | curl -XTRACE  <url>                                                                                             |
| x-forwarded-for                | curl -H "X-Forwarded-For: 10.0.0.1" <url>                                                                       |
| basic authentication           | curl -u <user>:<password> <url>                                                                                 |
| post form                      | curl -XPOST --form "b=4_1" <url>                                                                                |
| cookie                         | curl --cookie "PHPSESSID=5ved46gn34dopkjhstrrfgdkk1;" <url>                                                     |
| cookie files (save & send)     | curl -c /tmp/cookie.txt -b /tmp/cookie.txt <url>                                                                |
| set user-agent                 | curl -A "Mozilla" <url>                                                                                         |
| referer                        | curl -H "Referer: https://www.cnn.com" <url>                                                                    |
| json                           | curl -XPOST -H "Content-Type: application/json" -d "[[\"create\", {\"type\":\"trial\",\"name\":\"bug\"}]] <url> |
| silent                         | curl -s <url>                                                                                                   |
| verbose                        | curl -v <url>                                                                                                   |
| ignore certifikate issues      | curl -k <url>                                                                                                   |
| follow redircts                | curl -L <url>                                                                                                   |
| redirect output into file      | curl -o <file> <url>                                                                                            |
| curl with proxy                | curl -x <proxy>:<port> <url>                                                                                    |
| curl SSL V3                    | curl -k -v --sslv3 <url>                                                                                        |
| curl max time (4 seconds)      | curl -m4 <url>                                                                                                  |
| file upload                    | curl -XPOST -F ul=30000 -F location=/tmp/upload-form-data.txt -F userfile=@/tmp/upload-file.txt <url>           |
| shell-shock                    | curl -k -L -H 'User-Agent: () { :;}; curl -L  <return-server>;'  <url>                                          |
| post data from file            | curl -data '@<filename>' <url>                                                                                  |
| curl output response time      | curl -o /dev/null -w%{time_connect}:%{time_starttransfer}%{time_total} <url>                                    |
| curl output request size       | curl -o /dev/null -w%{size_request} %{size_upload} <url>                                                        |
| curl output http status code   | curl -o /dev/null -w%%{http_code} <url>                                                                         |
| curl resolve ip from other dns | curl --resolve "www.cnn.com:80:8.8.8.8" http://www.cnn.com                                                      |
+--------------------------------+-----------------------------------------------------------------------------------------------------------------+
```
======wget=====
```
```
======w3m=====
```
```
