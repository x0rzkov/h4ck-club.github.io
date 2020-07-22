# znc
```
/usr/local/bin/znc --makeconf
# server --> znc --makepass
# on the server --> cat ~/.znc/znc.pem | openssl x509 -sha512 -fingerprint -noout | tr -d ':'| tr 'A-Z' 'a-z' | cut -d = -f 2
# client --> irc.server.znc.ssl_fingerprint 

```
