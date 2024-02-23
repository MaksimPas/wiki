PfSense has been installed on a virtual machine. pfSense acts as a firewall blocking unwanted traffic from WAN to LAN network and vise verca. 

pfSense has been configured with 2 NICs:
* WAN NIC. IP 10.1.0.8
* LAN NIC. IP 10.0.0.1

For machines in LAN network, pfSense is used as Default Gateway, DNS resolver/forwarder and VPN server. 

##Access GUI
Access pfSense GUI on http://10.0.0.1

##VPN Server
IPSEC tunnel connecting LAN network 10.0.0.0/24 with Azure network 10.11.0.0/16

![image.png](/.attachments/image-1d5e1c76-1d18-4733-a5a7-b78b9aff936d.png)

##DNS server
DNS server is set up listening on port 53 on LAN NIC and localhost. Private domains for Azure services like Database and Key Vault are overridden - DNS lookup for these domain is forwarded to Private DNS Resolver in Azure via VPN tunnel.
![image.png](/.attachments/image-11f4d1b3-2b97-40e4-bf1b-7b81827fc2ca.png)
Important: to make pfSense send traffic to Azure Private DNS via VPN, a static route "dest={Azure_VNET} NextHop=Lan_IP" must be added - this way pfSense sends traffic (destined to Azure VNET) to its LAN interface where traffic is intercepted by IPSEC tunnel and encapsulated.


