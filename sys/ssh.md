###### explain shell
```
https://explainshell.com/explain?cmd=ssh+-L+127.0.0.1%3A2222%3A192.168.1.3%3A2345+root%40192.168.1.2#
```
ssh
```
Local Port Forwarding
ssh -L 8080:www.ubuntuforums.org:80 <host>
ssh -L 8080:www.ubuntuforums.org:80 -L 12345:ubuntu.com:80 <host>
ssh -L 5900:localhost:5900 <host>

Remote Port Forwarding
ssh -R 5900:localhost:5900 guest@joes-pc

Dynamic Port Forwarding
ssh -C -D 1080 laptop

Forwarding GUI Programs
ssh -X laptop
firefox &
ssh -f -T -X laptop firefox
ssh -fTXC joe@laptop firefox


links --> https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding
```

###Single hop tunelling:
```
ssh -f -N -L 9906:127.0.0.1:3306 user@dev.example.com
where,

-f puts ssh in background
-N makes it not execute a remote command
This will forward all local port 9906 traffic to port 3306 on the remote dev.example.com server
```
###Multi-Hop Tunelling:
```

Tunnel from localhost to host1 and from host1 to host2:

ssh -L 9999:localhost:9999 host1 ssh -L 9999:localhost:1234 -N host2
This will open a tunnel from localhost to host1 and another tunnel from host1 to host2. 
However the port 9999 to host2:1234 can be used by anyone on host1. This may or may not be a problem.

Another Example:

Assume you have you have a web server running on 10.1.0.93 in a private network on port 80 ..
..which is reachable by a gateway server 198.1.1.34, here is how to open the ssh tunnel:

ssh -L 80:localhost:80 root@198.1.1.34 -t ssh -L 80:localhost:80 root@10.1.0.93
Example SSH Config:

Host cwg
  HostName 198.0.218.179
  Port 22
  User root
  IdentityFile ~/.ssh/id_rsa
Access cw sync on localhost:9292
[[Enable]]: ssh -f -N cw_tunnel
Host cw_tunnel
  HostName 198.0.218.179
  User root
  IdentityFile ~/.ssh/id_rsa
  LocalForward 9292 127.0.0.1:9292

# auto tunelling to securehost (remote host) via jumphost (gateway)
# we tell ssh that when it establishes a connection to securehost to do so using
# the stdin/stdout of the ProxyCommand as a transport. The ProxyCommand then tells
# the system to first ssh to our bastion host and open a netcat connection to host
# %h (hostname supplied to ssh) on port %p (port supplied to ssh).
Host jumphost
  ProxyCommand none
Host securehost
  ProxyCommand ssh jumphost -W %h:%p
```
  
  
proxy chains
```

```
