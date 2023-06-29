This is the main documentation of "Bestos United" project

## TEAM:


| NAME                  | OFFICE            |
|-----------------------|-------------------|
| Henrik André Tellevik | Bergen Office     |
| MUHAMMAD YASIR ABBASI | Sandefjord Office |
| Asahi Cantu           | Stavanger         |
| Pasichnyk, Maksym     | Oslo Office       |
| Oppheim, Sølve        | Trondheim Office  |

## PROJECT STATUS:

### First Quarter Goals
| Goal                                    | Status           | Description                                                           |
|-----------------------------------------|------------------|-----------------------------------------------------------------------|
| On premises system set up and tested​    | Done             | Could be accessed via browser or ssh https://92.220.49.188/ui/#/login |
| Cloud environment ready for development​ | Done             | Required resources are created in resource group [BESTOS-RG](https://portal.azure.com/#@accelerate-no.com/resource/subscriptions/264a89f0-56e0-40ba-8d89-034174fddaab/resourceGroups/BESTOS-RG/overview)                                 
| Simple solution deployed| Done        |[Frontend](https://bestos-core-app.azurewebsites.net/) - [Backend](https://bestos-backend-api.azurewebsites.net/#/Home) - [Swagger](https://bestos-backend-api.azurewebsites.net/swagger/index.html)
| Documentation in place​| Done      | [Project Wiki](https://dev.azure.com/accelerate-no/A23-BESTOS-UNITED/_wiki/wikis)
| DevOps environment and runners available| Done| [Backend and Frontend Pipelines](https://dev.azure.com/accelerate-no/A23-BESTOS-UNITED/_build)
| All members of the teams have access to the on premises system (VPN)​| Yes | OpenVPN is configured in pfsense


### Second Quarter Goals
| Goal                                    | Status           | Description                                                           |
|-----------------------------------------|------------------|-----------------------------------------------------------------------|
| Start enrolling resources into infrastructure as code (Terraform, Arm)​    | Done             | [Terraform Repo](https://dev.azure.com/accelerate-no/A23-BESTOS-UNITED/_git/terraform) |
| Integrate IaC into DevOps pipelines | Done             | Required resources are created in resource group [bestos-t-rg](https://portal.azure.com/#@accelerate-no.com/resource/subscriptions/264a89f0-56e0-40ba-8d89-034174fddaab/resourceGroups/bestos-t-rg/overview)                                 
| Dockerize application| Done        |  [Todo-api](https://bestos-core-app-t.azurewebsites.net/#/Home)
| Focus on idempotency of tasks and operations​| Done      | 
| Secure your applications| Partially Done | IaC, onPrem With with Keyvault, usage of service principal and PAT
| Initial Roadmap and Architecture/Design of Services Required| Done | [Architecture](https://dev.azure.com/accelerate-no/A23-BESTOS-UNITED/_wiki/wikis/A23-BESTOS-UNITED.wiki/84/Initial-design-and-roadmap-for-services-that-will-be-needed)




### Extras
| Goal                                    | Status           | Description                                                           |
|-----------------------------------------|------------------|-----------------------------------------------------------------------|
| Domain Controller| Done | Windows Server VM
| Users| Done| Windows Active Directory

##Important Information
### Repositories

#### [A23-BESTOS-UNITED](https://dev.azure.com/accelerate-no/A23-BESTOS-UNITED/_wiki/wikis)

This is the wiki repository and can be cloned to be edited out of the Azure devOps main branch 

#### [Frontend](https://dev.azure.com/accelerate-no/_git/A23-BESTOS-UNITED)
This is the repository for frontend code and pipeline

#### [Backend](https://dev.azure.com/accelerate-no/A23-BESTOS-UNITED/_git/backend-api)

This is the main repository for backend code and pipelines 

### Diagrams

* Complex Diagrams are developed using DrawIO. Keep all complex diagrams in a single file
* Simple or Mermaid Diagrams can be stored as a part of any markdown 

___
>**As a rule of thumb diagrams should be added to drawio and then exported to .png files, which will be later displayed in its corresponding markdown reference**