## Lab 12

- Name: Keonje Paige
- Email: paige.34@wright.edu

## Part 1 - Linux Network Command Cheat Sheet

- `hostname - Sets or displays the name of the current host system.`
    - Resource on `hostname`:https://www.ibm.com/docs/vi/aix/7.2?topic=h-hostname-command
- `ifconfig - allows users to configure network interfaces, including setting IP addresses, netmasks, and broadcast addresses.
Enables users to change the MAC address of a network interface, which can be useful for security purposes or bypassing network 
restrictions.`
    - Resource on `ifconfig`: https://www.geeksforgeeks.org/ifconfig-command-in-linux-with-examples/
- `ip - allows users to interact with various networking components such as network interfaces, routing tables, addresses, and more.`
    - Resource on `ip`: https://www.geeksforgeeks.org/ip-command-in-linux-with-examples/
- `route - allows you to make manual entries into the network routing tables. It helps distinguishes between routes to hosts and routes to networks by interpreting the network address of the Destination variable, which can be specified either by symbolic name or numeric address. This resolves all symbolic names into addresses, using either the /etc/hosts file or the network name server.`
    - Resource on `route`: https://www.ibm.com/docs/en/aix/7.1?topic=r-route-command
- `iptables -L - Shows all rules in a chain.`
    - Resource on `iptables`: https://phoenixnap.com/kb/iptables-linux
- `curl <IP_or_hostname> - The CLI tool that enables data transfer over various network protocols. Helps communicate with a web or 
application server by specifying a relevant URL and the data that needs to be sent or received.`
    - Resource on `curl`: https://phoenixnap.com/kb/curl-commandping 
- `ping <IP_or_hostname> - The (Packet Internet or Inter-Network Groper) is a basic Internet program that allows a user to test and 
verify if a particular destination IP address exists and can accept requests in computer network administration. This helps ensure
that a host computer the user is trying to reach is operating.`
    - Resource on `ping`: https://www.techtarget.com/searchnetworking/definition/ping
- `nslookup <IP_or_hostname> -  The command that asks the internet domain name servers interactively.`
    - Resource on `nslookup`: https://www.ibm.com/docs/en/aix/7.2?topic=n-nslookup-command
- `traceroute <IP_or_hostname> - The command-line utility that one uses to trace the path that an Internet Protocol (IP) packet takes to its destination`
    - Resource on `traceroute`: https://support.microsoft.com/en-us/topic/how-to-use-tracert-to-troubleshoot-tcp-ip-problems-in-windows-e643d72b-2f4f-cdd6-09a0-fd2989c7ca8e
- `nmap -p <IP_or_hostname> : The linux command-line tool for network exploration and security auditing. used for the following 
purposes: 

Real time information of a network
Detailed information of all the IPs activated on your network
Number of ports open in a network
Provide the list of live hosts`
    - Resource on `nmap`: https://www.geeksforgeeks.org/nmap-command-in-linux-with-examples/ 
- `tcpdump -i <networkinterface> -n host <IP_or_hostname> - the command that allows users to capture and analyze network traffic 
going through a system. It is often used to help troubleshoot network issues, as well as a security tool.`
    - Resource on `tcpdump`: https://opensource.com/article/18/10/introduction-tcpdump#:~:text=Tcpdump%20is%20a%20command%20line,in%20a%20variety%20of%20cases.

## Part 2 - Network Info

### Network Info for <Your OS Here>

1. Hostname of the device: LAPTOP-RTQOR2FQ
2. MAC address of the NIC connected to the network: 08-D2-3E-DF-ED-A5
3. IPv4 address: 130.108.214.83
4. Subnet mask: 255.255.252.0
5. Gateway address: 130.108.212.1
6. Does the device use DHCP to receive a network address? (y/n): No
7. DNS server address: wright.edu
8. Public IPv4 address: 130.108.214.83

### Network Info for AWS Instance

1. Hostname of the device: ip-10-0-0-191
2. MAC address of the NIC connected to the network: 02:b8:47:73:d8:1d
3. IPv4 address: 10.0.0.191
4. Subnet mask: /24 --> 255.255.255.0
5. Gateway address: 10.0.0.1
6. Does the device use DHCP to receive a network address? (y/n):
7. DNS server address: 127.0.0.53
8. Public IPv4 address: 44.209.243.163

## Part 3 - Subnet Translation

Translate the below CIDR blocks to their IP ranges:
1. `130.108.0.0/16`
130.108.0.0 - 130.108.255.255
2. `34.117.59.81/32`
34.117.59.81 - 34.117.59.81
3. `10.25.121.90/8`
10.0.0.0 - 10.255.255.255
Translate the below IP ranges to their CIDR notation subnets:
1. `172.18.5.0 - 172.18.5.255`
172.18.5.0/24
2. `5.9.243.187 - 5.9.243.187`
5.9.243.187/32
3. `192.168.0.0 - 192.168.1.255`
192.168.0.0/23

## Part 4 - Security

Screenshot of your changed Inbound Security Group rules.  
![Inbound Rules for Lab 12](relative/path/to/image)
MDimages/Screenshot(4990).png
MDimages/Screenshot(4991).png
> Why should HTTP allow any IP, while SSH has restrictions?
HTTP helps serve websites and accessible to the publice, while SSH provides some security in the
managing servers from unauthorized attacks.
> Describe how you validated or can validate if your rules are working with the restrictions given.
I would have to use my ssh -i command to open my instance from another device.
## Part 5 - It's Alive!  Maybe...

1. For the given server IP, describe purpose and what types of requests it does / doesn't respond to:
    - `8.8.8.8`
        - Purpose: Google's public DNS servers to resolve domain names to IP addresses.
        - Responds to: nslookup google.com
                    ping 8.8.8.8
        - Does not respond to: curl http://8.8.8.8
    - `5.9.243.187` -> `wttr.in` -> `https://wttr.in`
        - Purpose: Provides a display of recent weather information
        - Responds to: https command request(s) for weather information
        ping 5.9.243.187
        - Does not respond to: 
            telnet wttr.in 23
            ssh wttr.in
    - Your AWS instance public IP
        - Purpose: Giving SSH access or hosting services
        - Responds to:  https command request(s) and SSH
        - Does not respond to: Blocked ports
    - `34.117.59.81` -> `ipinfo.io` -> `https://ipinfo.io`
        - Purpose: Show IP location
        - Responds to: requests involving to retrieve IP data
        - Does not respond to: Non - HTTP commands or invalid paths
2. Does `ping` tell you if a server is "working"? 
No, only tests connections
3. What protocol does `ping` use?  What does this mean about the server's firewalls?
ICMP, ping wouldn't work if server was still running
4. Why won't `ping` work if you specify `https://` before the domain name?
`https://` is part of the HTTP protocol so it won't be recognized by ping
5. Does an IP lookup always result in finding the correct domain name / URL to access the resource, and vice versa?
Not always, due to countless number of daily IP addresses shared, and reverse DNS lookups may not reach to the intended domain
6. What happens at when an `http` request is made to a server with `https` enabled?
Request redirection from http to https

Citations:
- https://www.one2oneinc.com/news/ping-tests/#:~:text=Ping%20test%20don't%20tell,so%20it's%20not%20100%25%20reliable.
- 

## Extra Credit - Tattle Tale

### IPv4 Source Report

| Rank  | IPv4 Address | # of Attempts |
| ----- | ------------ | ------------- |
| 1     |              |     |
| 2     |              |     |
| 3     |              |     |
| 4     |              |     |
| 5     |              |     |

Commands to parse `csv` for report:

### Username Used Report

| Rank  | Username     | # of Attempts |
| ----- | ------------ | ------------- |
| 1     |              |     |
| 2     |              |     |
| 3     |              |     |
| 4     |              |     |
| 5     |              |     |

Commands to parse `csv` for report:
