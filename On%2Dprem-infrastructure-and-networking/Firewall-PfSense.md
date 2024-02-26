PfSense has been installed on a virtual machine. pfSense acts as a firewall blocking unwanted traffic from WAN to LAN network and vise verca. 

pfSense has been configured with 2 NICs:
* WAN NIC. IP 10.1.0.8
* LAN NIC. IP 10.0.0.1

For machines in LAN network, pfSense is used as Default Gateway, DNS resolver/forwarder, Load Balancer and VPN server. 

##Access GUI
Access pfSense GUI on http://10.0.0.1:80

##Load balancing
Package HAProxy was used as Loan Balancer on pfSense machine. Load Balancing at this stage happens on layer 4 (TCP). HAProxy has following configuration:
1) Frontend listening on WAN port 8883 using TCP load balancing. No SSL offload. Forwards traffic to the Backend Pool.
2) Backend pool. Consists of 3 worker nodes. Each  node is exposed on port 32248 which is where Ingress Controller NodePort service is running.

Under such architecture the incoming HTTPS traffic is load balanced on layer 4 at pfSense and sent further to a worker node on port 32248 where it is picked up by Ingress Nginx Controller which does a layer 7 load balancing with SSL offload forwarding traffic further to correct pods. 

Remember that a Firewall rule on pfSense WAN interface must allow traffic from Internet to FrontEnd WAN port. 

HAProxy has a nice GUI (GUI local port must be enabled in settings):
![image.png](/.attachments/image-e0aa07c3-7ecb-4d46-83ef-ce80a12b51d2.png)

##VPN Server
IPSEC tunnel connecting LAN network 10.0.0.0/24 with Azure network 10.11.0.0/16

![image.png](/.attachments/image-1d5e1c76-1d18-4733-a5a7-b78b9aff936d.png)

##DNS server
DNS server is set up listening on port 53 on LAN NIC and localhost. Private domains for Azure services like Database and Key Vault are overridden - DNS lookup for these domain is forwarded to Private DNS Resolver in Azure via VPN tunnel.
![image.png](/.attachments/image-11f4d1b3-2b97-40e4-bf1b-7b81827fc2ca.png)
Important: to make pfSense send traffic to Azure Private DNS via VPN, a static route "dest={Azure_VNET} NextHop=Lan_IP" must be added - this way pfSense sends traffic (destined to Azure VNET) to its LAN interface where traffic is intercepted by IPSEC tunnel and encapsulated.


