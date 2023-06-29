**Bestos Resource group**
![BESTOS-RG.png](/.attachments/BESTOS-RG-6ea624d4-df26-4ca2-8864-e83824cf7dd8.png)

**Initial design and roadmap for services that will be needed**


![init_model.png](/.attachments/init_model-8578359b-4a1b-4420-90a7-cfc71aa25b37.png)


**Description of the model**

At the moment we have created the basic for developing and publishing a simple containerized web application with front end, back end, database, security, logging etc.

The future plan is to extend this web application to more functionality both in front end and back end, including endpoints for consuming externally, crud operations to database, using azure key vault for securing data\keys, load balancing for making an stable solution with minimum of delay.

At the moment we are using docker images, and are planning to use kubernetes as the orchestration tool.

The content is not decided yet, so that will come!

The plan is to use the external lookup service to integrate to public services and use this service from our bestos application service.

The admin web\service\database is still under planning.