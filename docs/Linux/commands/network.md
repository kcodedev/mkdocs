# Network Commands

## ifconfig
Configure network interfaces.

- `ifconfig` : Display network interfaces
- `ifconfig eth0` : Show specific interface

## ip
Modern replacement for ifconfig.

- `ip addr show` : Show IP addresses
- `ip route show` : Show routing table

## ping
Test connectivity to a host.

- `ping google.com` : Ping a host
- `ping -c 4 google.com` : Ping 4 times

## traceroute
Trace the route packets take to a host.

- `traceroute google.com` : Trace route

## netstat
Display network connections and statistics.

- `netstat -tuln` : Show listening ports
- `netstat -an` : Show all connections

## ss
Socket statistics (replacement for netstat).

- `ss -tuln` : Show listening sockets

## curl
Transfer data from or to a server.

- `curl http://example.com` : Fetch webpage
- `curl -I http://example.com` : Get headers only

## wget
Download files from the web.

- `wget http://example.com/file.zip` : Download file

## nslookup
Query DNS for domain information.

- `nslookup google.com` : DNS lookup

## dig
DNS lookup utility.

- `dig google.com` : Detailed DNS info

## lsof
List open files, including network sockets.

- `lsof -i tcp:PORT_NUMBER` : List processes using a TCP port
- `lsof -i :80` : List processes using port 80