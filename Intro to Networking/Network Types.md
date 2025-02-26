# WAN (Wide Area Network)

- the internet
- a bunch of lans joined together
- you know what this is 
- some large companies actually have their own internal WAN 
- we identify if a network is a wan by using wan specific routing protocol e.g. BGP, checking if IP schema is not within RFC 1918

# LAN/WLAN (Local Area Network)

- the w part of wlan is wireless local area network, they're functionally the same except wlan you can connect to wirelessly
- will assign IP addresses for local use

# VPN (Virtual Private Network)

- make you feel like you're connected to a different network

## Site to Site VPN
- both the client and the server are network devices (routers/firewalls)
- share network ranges
- typically used to join company networks over the internet, letting multiple locations communicate over the internet as if it were the same network
## Remote Access VPN
- TAP (network tap) operates in the data link layer [[Network Traffic Analysis Primer#TCP/IP Stack and OSI Model|(Layer 2)]], and simulates an ethernet connection, letting you bridge networks together
- TUN (network TUNnel) operates in the network layer[[Network Traffic Analysis Primer#TCP/IP Stack and OSI Model | (Layer 3)]] 
	- doesn't bridge networks
	- communicates directly via IP 
	- simulates network layer device
	- less overhead because no need to wrap ip packets in ethernet frames
- HTB uses OpenVPN which uses a TUN Adapter to access labs
- creates routes for specific networks, therefore it's a Split Tunnel VPN
- not great for companies because makes malware harder to detect since network traffic goes out of the internet
## SSL VPN
- vpn in browser
- able to stream entire desktop sessions to browser

# Extra stuff

## GAN (Global Area Network)
- worldwide network
- internet is an example
- some very large companies have networks that could qualify as a gan
- uses the glass fibre infrastructure of WANs and connect them with undersea cables or satellite transmission
## MAN (Metropolitan Area Network)
- connects LANs in close proximity
- telecommunications network
- connections and routers are based off glass fibres increasing data throughput
## PAN/WPAN (Personal Area Network)
- WPAN is basically bluetooth or hotspot
- PAN is connecting your phone to computer with cable
- WPANs don't extend very far, should not be relied upon for businesses (obviously)
- for IOT devices, WPANs can be used to monitor/control devices with low data rates, used for smart home/automation stuff
