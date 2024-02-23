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
192.168.0.11 and 192.168.0.12

##Virtual WAN network



##NAT rules on Router IP 92.220.49.188
Entire NAT chain for inbound traffic on Router:
* port 2222 --> 192.168.0.11:2222 --> 10.1.0.8:2222 --> 10.0.0.10:22
  * SSH access to CP
* port 6443 --> 192.168.0.11:6443
  * HTTPS access to K8S api server.
* port 80 --> 192.168.0.11:8880
  * HTTP access to K8S Ingress Controller.
* port 443 --> 192.168.0.11:8883
  * HTTPS access to K8S Ingress Controller.
* port 500 --> 192.168.0.11:500
  * IPSEC access to pfSense VPN Server.
* port 4500 --> 192.168.0.11:4500
  * IPSEC access to pfSense VPN Server.














