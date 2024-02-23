# Overview

This section shows all the connection settings in our onPrem environment.
Diagrams and configurations are stored as well.

##On-prem server specs
* HP Microserver 
* 32GB RAM
* Hard drive 2TB

##Public entry point. IP Address (Router Public IP)
92.220.49.188

##On-prem server IP
NIC 1: 192.168.0.11
NIC 2: 192.168.0.12
Part of router local network

##Virtual WAN network
Address range: 10.1.0.0/16
WAN DG: 10.1.0.1
WAN DHCP: 10.1.0.1
WAN DNS: 10.1.0.1 ; 10.1.0.2 (obtained via DHCP). 

Incoming traffic to on-prem NIC1 and NIC2 is translated to WAN DG.

Machines:
* pfSense WAN NIC IP: 10.1.0.8

##Virtual LAN network
Address range: 10.0.0.0/24


##NAT rules on Router IP 92.220.49.188
Entire NAT chain for inbound traffic on Router:
* port 2222 --> 192.168.0.11:2222 --> 10.1.0.8:2222 --> 10.0.0.10:22
  * SSH access to CP
* port 6443 --> 192.168.0.11:6443 --> 10.1.0.8:6443 --> 10.0.0.10:6443
  * HTTPS access to K8S api server.
* port 80 --> 192.168.0.11:8880 --> 10.1.0.8:8880 --> 10.0.0.11:32050
  * HTTP access to K8S Ingress Controller.
* port 443 --> 192.168.0.11:8883 --> 10.1.0.8:8883 --> 10.0.0.11:32248
  * HTTPS access to K8S Ingress Controller.
* port 500 --> 192.168.0.11:500 --> 10.1.0.8:500
  * IPSEC access to pfSense VPN Server.
* port 4500 --> 192.168.0.11:4500 --> 10.1.0.8:4500
  * IPSEC access to pfSense VPN Server.














