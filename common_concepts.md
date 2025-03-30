#### IP
- version
	- IPv4 - 32 bit 2^32  -> 4 million IPs
		- _Example: `102.22.192.181`_
	- IPv6 - 128bits, 340e+36 IPs
		- _Example: `2001:0db8:85a3:0000:0000:8a2e:0370:7334

- ISP - Internet service provider
- DHCP - dynamic host configuration Protocol

#### TCP & UDP
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

#### DNS
##### How DNS works