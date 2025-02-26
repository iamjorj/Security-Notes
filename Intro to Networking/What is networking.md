
Networks allow two computers to communicate with each other. It's important for security professionals to understand this because network errors are often silent, causing us to miss things easily. 

building a secure network requires a deep understanding of how networking works. 


# Basic information

- Entire internet is built upon subdivided networks (e.g, your home network and company networks)
- networking is the delivery of packages across these networks 
- if we want to go to a company's website, the website address/URL that we enter into our browser is also known as a FQDN (fully qualified domain name)
	- the difference is the fqdn is just the address, the url specifies extra parameters. e.g. google.com vs https://google.com/search?client=firefox&q=hi
- when we send a packet to this server, the packet is forwarded through the router to the ISP, who then checks what ip google.com is, and sends the packet to that IP, then the website sends us data back

# Extra points
![net overview][https://academy.hackthebox.com/storage/modules/34/redesigned/net_overview.png]

1. Web server should be in a DMZ (Demilitarized zone), since it's prone to attacks. clients on the internet can interact with it, and initiate communications, so putting it in a DMZ lets admins put protections on it separate from other devices
2. Workstations should be on their own network, and if it's on the same network as a server, spoofing and man in the middle attacks are a bigger issue
3. switch and router should be on an admin network, this prevents workstations from seeing communication between the two devices
4. ip phones should be on their own network, prevents computers from eavesdropping, also allows less latency
5. printers should be on their own network, if authentication is required to print, can lead to passwords being stolen. have lots of information sent to them
