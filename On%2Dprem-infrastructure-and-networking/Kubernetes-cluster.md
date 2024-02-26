We have deployed a Kubernetes Cluster consisting of 1 Control Plane (CP) node and 3 worker nodes.

##Node OS & RAM
OS: Ubuntu 22.04.3
RAM: 2 GB
Disk: 40 GB SSD

Container runtime: containerd.
CNI:  Calico. 

kubectl v 1.29.1
kubeadm v 1.29.1
kubelet v 1.29.1
containerd v 1.6.27

Node CIDR: 10.0.0.0/24
POD CIDR: 192.168.0./16
Service Cluster CIDR: 10.96.0.0/12

Installed packages:
* ingress-nginx
  * Layer 7 load balancing to app service. SSL offload.
* external-secrets
  * Managing secrets in Azure Key Vault and injecting those in K8S native secrets. 
* cert-manager
  * Provisioning Cluster with SSL certificates from Let's Encrypt. 
* kube-cost 
  * Cluster cost overview + optimization. 
* prometheus-stack
  * Prometheus + Grafana. Node metrics. 

##Main app
Resources deployed in the cluster can be found in main repo in "k8s" folder. 




##Future stuff: 
* kubeshark. Like Wireshark, only for Kubernetes cluster. 
* Elastick + Kibana for pod logs. 
* HPA (horizointal pod autoscaler).
