https://github.com/karanpratapsingh/system-design
### IP
- version
	- IPv4 - 32 bit 2^32  -> 4 million IPs
		- _Example: `102.22.192.181`_
	- IPv6 - 128bits, 340e+36 IPs
		- _Example: `2001:0db8:85a3:0000:0000:8a2e:0370:7334

- ISP - Internet service provider
- DHCP - dynamic host configuration Protocol

### TCP & UDP
- TCP - connection oriented (high latency)
	- support retransmission of lost packet
	- File transfer
	- email
	- database sync (cross datacenter, replication, DR)
- UDP - connectionless (low latency)
	- We should use UDP over TCP when we need the lowest latency and late data is worse than the loss of data.
		- online gaming
		- livestreaming
		- zoom call / whatapp

### DNS
#### How DNS works
![[dns.png]]

DNS lookup involves the following eight steps:
1. A client types example.com into a web browser, the query travels to the internet and is received by a DNS resolver (receive the DNS query).
2. The resolver then recursively queries a DNS root name server.
3. The root server responds to the resolver with the address of a Top-Level Domain (TLD) -> based on the extension of the domain (e.g., .com, .net, .org).
4. The resolver then makes a request to the .com TLD.
5. The TLD server then responds with the IP address of the domain's name server, example.com.
6. Lastly, the recursive resolver sends a query to the domain's name server.
7. The IP address for example.com is then returned to the resolver from the name server.
8. The DNS resolver then responds to the web browser with the IP address of the domain requested initially.

##### Record Type
- **CNAME (Canonical Name record)** - domain alias, forward one domain/subdomain to another domain, does not provide IP
- **A (Address record)**: This is the record that holds the IP address of a domain. IPV4
- **AAAA**: IPV6 

### Load Balancing
- no single server is overworked, which could degrade performance. 
- If a single server goes down, the load balancer redirects traffic to the remaining online servers. 
- When a new server is added to the server group, the load balancer automatically starts sending requests to it.
- load balance server can be multiple - incase one LB server (active) goes down, the passive LB server can take over, makes more fault-tolenrant
##### Distribution method
- host based
- path based
- content based, based on content such as the value of a parameter. (only application layer)
##### Load balancer types
- Software (Nginx / **HAProxy** - high-performance TCP/HTTP load balancer)
	- nginx installed in vm and forwards requests to multiple BE servers
	- routing method - least connections, to prevent server overload
	- add health check - prevent send request to failure servers
- Hardware
	- balances traffic between several high-performance application servers behind the corporate firewall
	- physical device, cost a lot
- DNS
	- **Issues**
		- never check health status, if one server goes down, possible still returns the failed IP
		- dns cache can be stale
		- possible choose a server not near, add latency
	- **To resolve issue**
		- Not at DNS layer, will be solve in application layer, network layer after DNS lookup, actual load distribution happens in L4/L7
			1. DNS points to a load balancer, not a server
			2. The load balancer handles routing, e.g., health check, geo routing
		- Layer 4 Load Balancer
		  Great when performance is critical, and the logic doesn’t depend on request content.
			- Routes based on IP and TCP/UDP ports
			- Fast and lightweighted
			- commonly for non-HTTP traffics as cannot inspect http headers/urls
				- e.g., game servers, databases -> TCP protocol
		- Layer 7 Load Balancer
		  Useful for web apps, APIs, or microservices where smarter routing is needed.
			- route based on **URL path, headers, cookies, etc**
			- WebSocket support, Content-based routing, **ssl termination** (load balancer decrypts HTTPS traffic before passing it to backend services.This offloads the SSL workload (CPU-heavy) from your app servers or pods.)
			- e.g., ALB, nginx, traefik
##### Sticky Session
Once a user connects to a specific server (or pod), **all their future requests go to the same server** during that session.
For example, login, shopping cart
If a user request goes to a different sever (because of load balancing), the state can be lost/inconsistent
###### How to implement
- load balancer set a cookie, and route all the future requests with this cookie to the same BE
- use user's source IP to assign traffics
- route base on header e.g., `X-Session-Id`
###### Potential issues
- pod restart/crash, session gone unless use Redis store the session
- some pods may have more traffics (long living sessions)
	-  can use JWT, token bases auth, then don't need sticky sessions.
		- stateless, any BE pod can validate and process the request
### Clustering
- A computer cluster is a group of two or more computers, or nodes, that run in parallel to achieve a common goal.
- at least one node is designated as the leader node and acts as the entry point to the cluster.
- a cluster should be designed to minimize latency and prevent bottlenecks in node-to-node communication.
- servers in one cluster are aware of each others and work together for common purpose
#### High Availability Cluster
- active-active
	- at least two nodes are actively running the same kind of services simultaneously![[active_active.png]]
	- main purpose, load balancing, distributed traffic to all the nodes to prevent overload and single node failover
- active-passive
	- at least two nodes, not all the nodes are active (e.g. two nodes structure, if the first node already active, the second node must be passive or on standby)![[active_passive.png]]
#### kubernetes
- master node
	- main server to control pod will run on which server, monitor pod running status
	- etcd, main database, store cluster status
- worker nodes
	- server that run the pods, monitor the lifecycle of the pods
	- load balancing (kube-proxy
	
![[kubernetes.png]]
