
# What is Network Traffic Analysis (NTA)

- examining network traffic
- characterizes common ports and protocols used
- establish a baseline for environment  
- monitor and respond to threats
- grants deep insight into network
- helps determine anomalies, such as threats, and is able to early and effectively pinpoint these
- attackers update their tactics frequently to avoid detection, and they often leverage legitimate credentials with tools companies allow in their network causing detection and response to be difficult

# NTA uses

- **Collecting** real time traffic in the network
- **Setting** a baseline for normal communication
- **Identifying** traffic from suspicious hosts/non standard ports, and detecting issues with networking protocols (http errors), problems with TCP, and other networking misconfigurations
- **Detecting** malware on the wire, such as ransomware, exploits, and non-standard interactions
- investigating past incidents and threat hunting

If a threat wants to infiltrate our network, they will eventually have to interact with the network itself. We utilize our knowledge of network traffic to disrupt this.

If we detect many `SYN` packets on ports we normally don't use, someone's probably doing a port scan and determining what ports are open on the host


# Required skills

general skills that we will acquire over time
applies to all parts of cybersec

## TCP/IP Stack and OSI Model

![tcp/ip osi][https://academy.hackthebox.com/storage/modules/81/net_models4.png]

an understanding of all the layers ensures we are able to grasp concepts, and how networking traffic and the host applications interact
## Basic Networking concepts
understanding what traffic we will see at each level includes an understanding of the layers that make up the TCP/IP stack and the OSI model, as well as the concepts of switching and routing. tapping a network on a backbone link shows much more traffic than tapping an office switch
## Common Ports and Protocols
Identifying standard ports and protocols quickly and having a functional understanding of how they communicate ensures that we identify potentially malicious traffic
## Concept of IP Packet and Sublayers
Foundational knowledge of how TCP and UDP communicate will ensure we know what we're searching for, and that we know what we're seeing. 
## Protocol Transport Encapsulation
Being able to read/dissect when the encapsulation changes helps us move to data quicker

# Berkeley Packet Filter (BPF) Syntax

primary syntax for network packets
makes it easy to filter and decode

[documentation][https://www.ibm.com/docs/en/qsip/7.4?topic=queries-berkeley-packet-filters]

# Performing NTA

To listen passively, we must be connected to the network segment we wish to listen on. If we wish to capture traffic from a specific VLAN we must be connected to it.

## General workflow

Problem-->ingest traffic-->reduce noise by filtering-->analyze and explore-->detect and alert-->ingest traffic

1. ingest traffic
	- once we know our placement, capture traffic
	- use capture filters if we know what we're looking for
2. reduce noise by filtering
	- filter stuff 
3. analyze and explore
	- is the traffic encrypted or not?
	- are users attempting to access resources that they should not have access to?
	- are hosts talking to each other when they normally don't
4. detect and alert
	- are we seeing errors
	- analyze to see if malicious

fix and monitor
- if we make a change or fix an issue, monitor it for a while to see if the issue has been fully resolved

