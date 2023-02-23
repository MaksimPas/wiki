## HP Microserver

* 32GB RAM
* Hard drive 2TB



### IP Address

92.220.49.188


1. Navigate to the following portal https://92.220.49.188
![image.png](/.attachments/image-b08df911-0280-4437-a4bc-5abbe62352a4.png)
2. Retrieve User and password from its corresponding KeyVault (**No User nor passwords will be documented here**)

## Steps to enable remote access to vmhost via https

1- Added DMZ host as shown in the picture which is WAN IP address in my tplink router
![altibox-config.jpg](/.attachments/altibox-config-155441c0-f065-4b2e-9c5c-e9561bd5ef69.jpg)

2- From Tplink router, i added forwarding to the ip address of the VMWare host which is in LAN network of router as shown in the image below
![router config.jpg](/.attachments/router%20config-430295c8-d233-409e-b31b-41554d3b7185.jpg)

## Architecture Diagram

![image.png](/.attachments/image-75282c87-d864-41f8-890d-28c7f18c0e23.png)

## Domain server and active directory installation

Followed steps mentioned in this article
https://computingforgeeks.com/install-active-directory-domain-services-in-windows-server/?utm_content=cmp-true