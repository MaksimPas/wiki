# Overview

This section shows all the connection settings in our onPrem environment as well as configuration of physical and virtual machines.
Diagrams and configurations are stored as well.

##On-prem server specs
* HP Microserver 
* 32GB RAM
* Hard drive 2TB
* OS: Ubuntu 22.04.3

##Virtualization
VirtualBox 7.0 

##Public entry point. IP Address (Router Public IP)
92.220.49.188

##On-prem server
NIC 1: 192.168.0.11
NIC 2: 192.168.0.12
Part of router local network
Access via RDP

##Virtual WAN network
Purpose: separating internal workloads from the "outside world", providing security layer with a Firewall in this network.
Address range: 10.1.0.0/16
WAN DHCP: 10.1.0.1
WAN DG: 10.1.0.1 (obtained via DHCP). 
WAN DNS: 10.1.0.1 and 10.1.0.2 (obtained via DHCP). 

Incoming traffic to on-prem NIC1 and NIC2 is translated to WAN DG.

Machines:
* pfSense. WAN NIC IP: 10.1.0.8 (via DHCP)

##DMZ Network
No DMZ

##Virtual LAN network
Purpose: network containing K8S nodes.
Address range: 10.0.0.0/24
No DHCP. DNS and DG configured manually on each NIC.

NICs plugged into this network have following configuration:
* DG: 10.0.0.1
* DNS: 10.0.0.1

Machines: 
* pfSense. LAN NIC IP: 10.0.0.1
* CP. IP: 10.0.0.10
* worker1. IP 10.0.0.11
* worker2. IP 10.0.0.12
* worker3. IP 10.0.0.13

##NAT rules on Router IP 92.220.49.188
Entire NAT chain for inbound traffic on Router:
* port 2222 --> 192.168.0.11:2222 --> 10.1.0.8:2222 --> 10.0.0.10:22
  * SSH access to CP
* port 6443 --> 192.168.0.11:6443 --> 10.1.0.8:6443 --> 10.0.0.10:6443
  * HTTPS access to K8S api server.
* port 80 --> 192.168.0.11:8880 --> 10.1.0.8:8880
  * LB http front end port (not used, use HTTPS instead).
* port 443 --> 192.168.0.11:8883 --> 10.1.0.8:8883
  * LB front end port
* port 500 --> 192.168.0.11:500 --> 10.1.0.8:500
  * IPSEC access to pfSense VPN Server.
* port 4500 --> 192.168.0.11:4500 --> 10.1.0.8:4500
  * IPSEC access to pfSense VPN Server.
* port 3389 --> 192.168.0.11:3389 
  * RDP access to on-prem machine.

<IMG  src="https://dev.azure.com/accelerate-no/492853ab-23f1-4382-ab9d-8bff43b578f7/_apis/git/repositories/d0813bc2-10c7-466a-972b-bf8af1df545d/Items?path=/.attachments/image-e3801e46-3b8d-41b4-80bd-822746e6cc85.png&amp;download=false&amp;resolveLfs=true&amp;%24format=octetStream&amp;api-version=5.0-preview.1&amp;sanitize=true&amp;versionDescriptor.version=wikiMaster"/>














