Please note that ingress-controller and todo-api pods run in the same k8s cluster and may run on the same node. 
The diagram shows one of the possible load balancing scenarios, but please note that Ingress Controller service does Layer 4 load balancing between all available ingress-controller pods, and todo-api servce does Layer4 load balancing between all available todo-api pods.


![image.png](/.attachments/image-f1de53e7-a329-468e-94da-d6f8d82b2a94.png)