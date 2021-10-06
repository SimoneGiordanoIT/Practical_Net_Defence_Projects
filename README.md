# Practical_Net_Defence_Projects
A compilation of the four projects assigned to be able to partecipate to the Practical Network Defence exam at Cybersecurity faculty

# Network topology

![alt text](https://github.com/SimoneGiordanoIT/Practical_Net_Defence_Projects/blob/main/Topology.PNG?raw=true)

# First assignment
- Enable IPv6 on the Main Firewall-Router and enable the prefix redistribution in
  DMZ network, so that the services exposed to the outside are IPv6-ready. Moreover, you have to properly
  configure the other sub-networks, according to your network design.
- All the internal hosts have to be able to access the internal DNS in the Server network. For this purpose you
  CAN configure the DNS service in the Domain Controller (dc) machine (100.100.1.2) using zentyal, but
  alternative DNS services can be considered, since zentyal DOES NOT WORK with IPv6

Security policy of ACME co.
- All the host have to use as DNS resolver the internal DNS.
- Only the webserver service provided in the DMZ has to be accessible from the Internet.
- The proxy service provided in the DMZ has to be accessible only from the hosts of the Acme network.
  However, the proxy needs internet access (see below, section Services of the ACME co.)
- All the services provided by hosts in the Internal server network have to be accessible only by Client
  network and DMZ hosts.
- Anything that is not specifically allowed has to be denied.
- All the hosts (but the Client network hosts) have to use the syslog service on the Log server (syslog).
- All the host of the network have to be managed via ssh only from hosts within the Client network. 
- All the Client network hosts have to only access external web services (http/https).

Services of the ACME co.
- A web service in the standard port (in Web Server host)
- A DNS in the standard port (in Domain Controller host)
- A syslog server in the UDP standard port (in Log Server host)
- A proxy server that can be used by the hosts of the ACME network to request connections via HTTP or
  HTTPS to external hosts.
  
# Second assignment
- Properly setup the proxy server to act as the VPN gateway, namely a gateway for the road
  warriors of ACME co. You have to create the following users:Becca, Huck and Jim
  The users connected to the VPN have to be able to access the internal server network and the client
  network. This means that, if needed, the firewall rules of both Main Firewall-Router and Internal Firewall
  router have to be properly adjusted. You have to decide the security level, the authentication mechanism
  and the implementation software.
- Main-Internal VPN tunnel
  You have to properly setup a VPN tunnel between the two routers, since the actual connection is running
  on an insecure medium: any packet running between the two routers should go through the VPN tunnel,
  namely, should be encrypted
  
# Third assignment
- SQUID as Forward Proxy
  In the DMZ, you have to setup the squid software of the proxyserver host to accept, forward, cache and
  possibly log the responses of all the HTTP requests coming from the hosts of the ACME co. clients network.
  HTTPS traffic should go straight to Internet (no TLS bump expected). Clients should not be allowed to
  navigate in HTTP/HTTPS without using the proxy. Moreover, before accepting their requests, all the clients
  have to be authenticated using the authentication mechanism you find more suitable.
- Apache as Reverse Proxy
  In the DMZ, you have to configure the webserver apache to act as a reverse proxy to give access to the
  manufacturer of the ACME’s coffee machine (fantasticcoffee), in the External Services network.
  Fantasticcoffee machine ONLY uses HTTP and is, very likely, prone to security breaches ( it has → it has
  vulnerabilities, 100% guarantee!). Then, you have to secure the coffee machine. For this purpose, a reverse
  proxy is needed to provide HTTPS support and to limit the access only to the hosts coming from ACME
  client network.
  You have to setup ACME webserver so that it will handle the requests for fantasticcoffee. Use the apache
  mod_proxy module with TLS settings. Moreover, configure modsecurity2 in your webserver so that you can
  filter the requests to be forwarded to the coffee machine: you should only allow requests with proper
  parameters.

# Fourth assignment
- Logging
  In the Internal Server network, you have to set up a logging service that collects the relevant logs from the
  hosts of ACME co’s networks. You can opt for any software solution, for example, the rsyslog already
  installed, the zentyal’s logging facility, another logging software you can get from the repositories. You can
  also consider installing a web interface to better visualize the logs.

# Authors
Emanuele Santo Iaia [<img src="https://cdn4.iconfinder.com/data/icons/social-messaging-ui-color-shapes-2-free/128/social-linkedin-circle-512.png" width="20" height="20">](https://www.linkedin.com/in/emanuele-santo-iaia-4315411a2/)
[<img src="https://upload.wikimedia.org/wikipedia/commons/9/91/Octicons-mark-github.svg" width="20" height="20">](https://github.com/Lelito-IAIA)

Simone Giordano [<img src="https://cdn4.iconfinder.com/data/icons/social-messaging-ui-color-shapes-2-free/128/social-linkedin-circle-512.png" width="20" height="20">](https://www.linkedin.com/in/simone-giordano-itengineer/)
[<img src="https://upload.wikimedia.org/wikipedia/commons/9/91/Octicons-mark-github.svg" width="20" height="20">](https://github.com/SimoneGiordanoIT)
