PfSense has been installed on its own virtual machine running on the on-premises server.
The configuration can be done by opening a webbrowser from the windows server. The address for the pfsense is pfsense.bestos.no (Can only be reached from inside the network).
Following settings have been applied

![image.png](/.attachments/image-00e1d438-61a5-4146-b741-460876dc8d7f.png)

We have configured the use of VPN. Each user of the team has it's own user. To connect to the the windows server, each user has it's own installation file that installs the software on their computer. The configuration for each user includes their own certificate and a user/password needed to be able to connect to the vpn. The installation can be downloaded from the sabestos storage account in the azure portal. 

![image.png](/.attachments/image-cf7ed3c3-534c-4ac5-b69d-f3a67c1050e8.png)