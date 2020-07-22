Python 2.x
```
$ python -m SimpleHTTPServer 8000
```
Python 3.x
```
$ python -m http.server 8000
Twisted (Python)
$ twistd -n web -p 8000 --path .
Or:

$ python -c 'from twisted.web.server import Site; from twisted.web.static import File; from twisted.internet import reactor; reactor.listenTCP(8000, Site(File("."))); reactor.run()'
Depends on Twisted.
```
Ruby
```
$ ruby -rwebrick -e'WEBrick::HTTPServer.new(:Port => 8000, :DocumentRoot => Dir.pwd).start'
```
Ruby 1.9.2+
```
$ ruby -run -ehttpd . -p8000
```
adsf (Ruby)
```
$ gem install adsf   # install dependency
$ adsf -p 8000
```
Sinatra (Ruby)
```
$ gem install sinatra   # install dependency
$ ruby -rsinatra -e'set :public_folder, "."; set :port, 8000'
```
Perl
```
$ cpan HTTP::Server::Brick   # install dependency
$ perl -MHTTP::Server::Brick -e '$s=HTTP::Server::Brick->new(port=>8000); $s->mount("/"=>{path=>"."}); $s->start'
```
Plack (Perl)
```
$ cpan Plack   # install dependency
$ plackup -MPlack::App::Directory -e 'Plack::App::Directory->new(root=>".");' -p 8000
```
Mojolicious (Perl)
```
$ cpan Mojolicious::Lite   # install dependency
$ perl -MMojolicious::Lite -MCwd -e 'app->static->paths->[0]=getcwd; app->start' daemon -l http://*:8000
```
http-server (Node.js)
```

$ npm install -g http-server   # install dependency
$ http-server -p 8000
Note: This server does funky things with relative paths. For example, if you have a file /tests/index.html, 
it will load index.html if you go to /test, but will treat relative paths as if they were coming from /.

node-static (Node.js)
$ npm install -g node-static   # install dependency
$ static -p 8000
No directory listings.
```
PHP (>= 5.4)
```
$ php -S 127.0.0.1:8000
Credit: /u/prawnsalad and MattLicense

No directory listings.

```

Erlang

```
$ erl -s inets -eval 'inets:start(httpd,[{server_name,"NAME"},{document_root, "."},{server_root, "."},{port, 8000},{mime_types,[{"html","text/html"},{"htm","text/html"},{"js","text/javascript"},{"css","text/css"},{"gif","image/gif"},{"jpg","image/jpeg"},{"jpeg","image/jpeg"},{"png","image/png"}]}]).'
Credit: nivertech (with the addition of some basic mime types)

No directory listings.
```
busybox httpd
```
$ busybox httpd -f -p 8000
```
webfs
```
$ webfsd -F -p 8000
Depends on webfs.
```
IIS Express
```
C:\> "C:\Program Files (x86)\IIS Express\iisexpress.exe" /path:C:\MyWeb /port:8000
```
