# Networking -DevOps

Created: November 1, 2023 9:35 PM
Class: Dev
Type: Study Group

How does computer networks work?

How does computer connect to internet?

What is an IP address and Port?

What is a DNS

---

### LAN, Switch, Router, WAN, Gateway

LAN = 

- collection of devices connected together in one physical location (e.g: Home internet)
- each devices on this network is identified by a unique IP
    - IP = (Internet protocol) 172.16.0.0
        - composed of 32 bit value (32 1s or 0s)
        - can range from 0.0.0.0 to 255.255.255.255
- Devices communicate via these IP addresses.

Switch = How devices within the LAN talk to each other? 

- Sits within the LAN
- Knows all of the IP addresses of each devices
- Facilitates the connection between all the devices within the LAN

Router = How to talk to devices or servers outside of the LAN

- Network devices that sits between LAN and outside networks (WAN)
- connects devices on LAN and WAN

![Untitled](Networking%20-DevOps%20b1895c4d31d44b4d9c8c8ccf54ae39c5/Untitled.png)

The IP address of the Router is called the **Gateway**

Mobile device connects ⇒ to the switch ⇒ Router ⇒ webpage to access e.g Facebook. 

- Allows network devices to access the internet

Subnet : 

How to know whether the other devices is inside or outside of the LAN. 

- This is decided on the IP address of the target device
- Devices in the LAN belongs to same IP address range

![Untitled](Networking%20-DevOps%20b1895c4d31d44b4d9c8c8ccf54ae39c5/Untitled%201.png)

![Untitled](Networking%20-DevOps%20b1895c4d31d44b4d9c8c8ccf54ae39c5/Untitled%202.png)

![Untitled](Networking%20-DevOps%20b1895c4d31d44b4d9c8c8ccf54ae39c5/Untitled%203.png)

Network Address Translation (NAT) 

When devices attempts to connect to an external network (internet), the Private IP address of the devices is replaced by the Router.

The router’s IP address will replace the local device’s private IP address for transmitting and receiving data. This process is regarded as NAT. 

Benefits:

- Security and Protection of devices within the LAN because the private IP addresses are not directly exposed to the Public.
- Can re-use IP addresses without conflicting each other.

Firewall: 

- a system that prevents unauthorized access from entering a private network.
- allows device IP address at port to be accessed. = Port configuration
- Using firewall rules, you can define which requests are allowed
- Which IP address in your network is accessible
- Which IP address can access your server
- You can e.g. allow any device access your server.

Port: 

- These are like doors through which guests can access to a single building
- every device has a set of ports
- you can allow specific ports (doors)
- you can allow specific ports (doors) AND specific IP address (guests)
    - different applications listen on specific ports
    - there are standard ports for many applications:
        - port 80 ⇒ web Servers
        - port 3306 ⇒ mysql DB
        - port 5432 ⇒ PostgresQL DB
    
    For every application, you need a port to access. 
    
    Every port is unique on a device
    

DNS: Doman Name Service

- Using DNS, we can give a unique name to an IP address.
- The DNS basically translates IP addresses to domain names.

![Untitled](Networking%20-DevOps%20b1895c4d31d44b4d9c8c8ccf54ae39c5/Untitled%204.png)

To prevent the long process of the system searching for the Name servers/IP addresses, the DNS entries are CACHED for speed and efficiency. 

ICANN: Internet Corporation for Assigned Names and Numbers

- Manages the TLD development and architecture of the internet domain space.
- Authorizes Domain Name Registrars, which register and assign domain names

Networking commands to troubleshoot  your network

> ifconfig: ip address, subnet masks, gateway address, etc.
> 
> 
> netstat: what active connections you have on your machine.
> 
> which applications and typically listening and through which ports 
> 
> pa aux: current running process and programs and there information including on which ports they are running, and how much computer resources they are consuming
> 
> nslookup : gets the ip address for any domain name, 
> 
> display the ip address of the dns server that the computer is currently used. 
> 
> ping: ping [google.com](http://google.com) = checks wether a service or an application is accessible or not.
>