# Overview

This section shows all the connection settings in our onPrem environment.
Diagrams and configurations are stored as well.

## HP Microserver

* 32GB RAM
* Hard drive 2TB

### IP Address

92.220.49.188

1. Navigate to the following portal <https://92.220.49.188>
![image.png](/.attachments/image-b08df911-0280-4437-a4bc-5abbe62352a4.png)
2. Retrieve User and password from its corresponding KeyVault (**No User nor passwords will be documented here**)

## Steps to enable remote access to vmhost via https

1- Added DMZ host as shown in the picture which is WAN IP address in my tplink router
![altibox-config.jpg](/.attachments/altibox-config-155441c0-f065-4b2e-9c5c-e9561bd5ef69.jpg)

2- From Tplink router, i added forwarding to the ip address of the VMWare host which is in LAN network of router as shown in the image below
![router config.jpg](/.attachments/router%20config-430295c8-d233-409e-b31b-41554d3b7185.jpg)

## Architecture Diagram

![image.png](/.attachments/image-75282c87-d864-41f8-890d-28c7f18c0e23.png)

![hardware diagram](./.attachments/diag-hardware.drawio.png)

## Domain server and active directory installation

Followed steps mentioned in this article
<https://computingforgeeks.com/install-active-directory-domain-services-in-windows-server/?utm_content=cmp-true>

## Available virtual machines

### Windows Server 2022

Host name: ODIN

#### Active directory

Users have been granted on-prem access to the system, login organization settings are:
Logon name  : `<user name>@bestos-united.accelerate-no-2023`
Logon name (Pre windows 2000) : BESTOS-UNITED\<user name>

![software diagram](./.attachments/diag-software.drawio.png)

### Azure Pipelines agent

An agent has been configured to work with Azure DevOps. This feature will allow the team to run pipelines under this agent fully available and azure independent.
Agent has been configured to run as a service.
![image.png](/.attachments/image-6e26cd30-0fbd-4696-b19d-fa60de8ca2ff.png)

### PFSense

![image.png](/.attachments/image-b0d77f7e-4b45-4644-8e68-67d4370a0868.png)
