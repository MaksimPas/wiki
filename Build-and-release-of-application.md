# Pipelines

ADO pipelines with Cloud agents are used to build and deploy the solution. CI/CD pipelines were created. 

# Repository
Azure DevOps repos were used. 

#Build pipeline (CI) 
A CI Build pipeline builds the Docker image from the application and pushes the image to the container registry. Pipeline repo path: 
https://dev.azure.com/accelerate-no/A23-BESTOS-UNITED/_git/backend-api2?path=/pipelines/backend-api-build.yml

---
<DIV style="color: #000000;background-color: #fffffe;font-family: Consolas, 'Courier New', monospace;font-weight: normal;font-size: 12px;line-height: 16px;white-space: pre"><DIV><SPAN style="color: #000000">-&#160;</SPAN><SPAN style="color: #008080">task</SPAN><SPAN style="color: #000000">:&#160;</SPAN><SPAN style="color: #0451a5">Docker@2</SPAN></DIV><DIV><SPAN style="color: #000000">&#160;&#160;</SPAN><SPAN style="color: #008080">inputs</SPAN><SPAN style="color: #000000">:</SPAN></DIV><DIV><SPAN style="color: #000000">&#160;&#160;&#160;&#160;</SPAN><SPAN style="color: #008080">containerRegistry</SPAN><SPAN style="color: #000000">:&#160;</SPAN><SPAN style="color: #0451a5">'$(dockerRegistryServiceConnrection)'</SPAN></DIV><DIV><SPAN style="color: #000000">&#160;&#160;&#160;&#160;</SPAN><SPAN style="color: #008080">repository</SPAN><SPAN style="color: #000000">:&#160;</SPAN><SPAN style="color: #0451a5">'$(imageRepository)'</SPAN></DIV><DIV><SPAN style="color: #000000">&#160;&#160;&#160;&#160;</SPAN><SPAN style="color: #008080">command</SPAN><SPAN style="color: #000000">:&#160;</SPAN><SPAN style="color: #0451a5">'buildAndPush'</SPAN></DIV><DIV><SPAN style="color: #000000">&#160;&#160;&#160;&#160;</SPAN><SPAN style="color: #008080">Dockerfile</SPAN><SPAN style="color: #000000">:&#160;</SPAN><SPAN style="color: #0451a5">'$(dockerfilePath)'</SPAN></DIV><DIV><SPAN style="color: #000000">&#160;&#160;&#160;&#160;</SPAN><SPAN style="color: #008080">tags</SPAN><SPAN style="color: #000000">:&#160;</SPAN><SPAN style="color: #0451a5">'latest'</SPAN></DIV></DIV>

---

#CD Pipelines
CD pipelines were created pushing image to Azure K8S cluster and on-prem cluster. These pipelines authenticate into the cluster and apply k8s yaml configuration. 

AKS pipeline:
https://dev.azure.com/accelerate-no/A23-BESTOS-UNITED/_git/backend-api2?path=/pipelines/pipeline-deploy-to-k8s-Azure.yml

On-prem Cluster pipeline:
https://dev.azure.com/accelerate-no/A23-BESTOS-UNITED/_git/backend-api2?path=/pipelines/pipeline-deploy-to-k8s-onprem.yaml

---
<DIV style="color: #000000;background-color: #fffffe;font-family: Consolas, 'Courier New', monospace;font-weight: normal;font-size: 12px;line-height: 16px;white-space: pre"><DIV><SPAN style="color: #000000">-&#160;</SPAN><SPAN style="color: #008080">task</SPAN><SPAN style="color: #000000">:&#160;</SPAN><SPAN style="color: #0451a5">Kubernetes@1</SPAN></DIV><DIV><SPAN style="color: #000000">&#160;&#160;</SPAN><SPAN style="color: #008080">inputs</SPAN><SPAN style="color: #000000">:</SPAN></DIV><DIV><SPAN style="color: #000000">&#160;&#160;&#160;&#160;</SPAN><SPAN style="color: #008080">connectionType</SPAN><SPAN style="color: #000000">:&#160;</SPAN><SPAN style="color: #0451a5">'Kubernetes&#160;Service&#160;Connection'</SPAN></DIV><DIV><SPAN style="color: #000000">&#160;&#160;&#160;&#160;</SPAN><SPAN style="color: #008080">kubernetesServiceEndpoint</SPAN><SPAN style="color: #000000">:&#160;</SPAN><SPAN style="color: #0451a5">'A23-k8s-cluster-on-prem-ns-default'</SPAN></DIV><DIV><SPAN style="color: #000000">&#160;&#160;&#160;&#160;</SPAN><SPAN style="color: #008080">namespace</SPAN><SPAN style="color: #000000">:&#160;</SPAN><SPAN style="color: #0451a5">'default'</SPAN></DIV><DIV><SPAN style="color: #000000">&#160;&#160;&#160;&#160;</SPAN><SPAN style="color: #008080">command</SPAN><SPAN style="color: #000000">:&#160;</SPAN><SPAN style="color: #0451a5">'apply'</SPAN></DIV><DIV><SPAN style="color: #000000">&#160;&#160;&#160;&#160;</SPAN><SPAN style="color: #008080">useConfigurationFile</SPAN><SPAN style="color: #000000">:&#160;</SPAN><SPAN style="color: #0000ff">true</SPAN></DIV><DIV><SPAN style="color: #000000">&#160;&#160;&#160;&#160;</SPAN><SPAN style="color: #008080">configuration</SPAN><SPAN style="color: #000000">:&#160;</SPAN><SPAN style="color: #0451a5">'k8s/deploy-to-do-api-onprem.yaml'</SPAN></DIV><DIV><SPAN style="color: #000000">&#160;&#160;&#160;&#160;</SPAN><SPAN style="color: #008080">secretType</SPAN><SPAN style="color: #000000">:&#160;</SPAN><SPAN style="color: #0451a5">'dockerRegistry'</SPAN></DIV><DIV><SPAN style="color: #000000">&#160;&#160;&#160;&#160;</SPAN><SPAN style="color: #008080">containerRegistryType</SPAN><SPAN style="color: #000000">:&#160;</SPAN><SPAN style="color: #0451a5">'Container&#160;Registry'</SPAN></DIV><DIV><SPAN style="color: #000000">&#160;&#160;&#160;&#160;</SPAN><SPAN style="color: #008080">dockerRegistryEndpoint</SPAN><SPAN style="color: #000000">:&#160;</SPAN><SPAN style="color: #0451a5">'bestos-container-registry'</SPAN></DIV></DIV>

---



#IaC pipelines
IaC pipeline for each environment (dev, qa and prod) has been set up. 

