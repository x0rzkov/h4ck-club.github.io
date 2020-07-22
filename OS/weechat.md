# weechat
```
test run-without ssl
/server add freenode chat.freenode.net
/set irc.server.freenode.autoconnect on

relay
/relay add irc.freenode 9001 ### on server
/set relay.network.password "password"

/server add home 127.0.0.1/9001 ### on client
irc.server.home.password  ### on client
```

====bitlbee====
```
bitlbee runs on port 6667
/connect localhost 6667
/server add im localhost -autoconnect
register <password>
account add hangouts me@gmail.com 
&bitlbee identify <password>
account on
oauth
/set irc.server.im.command "/msg &bitlbee identify <password>"

##############################################################

twitter
account add twitter <yourusername>
account on
oauth
```
