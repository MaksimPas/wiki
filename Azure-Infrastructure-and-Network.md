We have a shared Kubernetes cluster in AKS which was mainly used for testing purposes. 

Other resources used:
- Storage account
- SQL server with Private Endpoint and privatelink domain.
- Key Vault with Private Endpoint and privatelink domain.
- DNS Private resolver with Outbound Endpoint.
- Container registry
- Container App
- Resources necessary for VPN communication: VNG, LNG, VNET, Subnet, Public IP, Connection.
- Public DNS Zone. 

##Purpose of created resources
Storage account was mainly used to store remote backend for Terraform. 

SQL server with SQL database was the database for the app. Key Vault contained app specific secrets like SQL connection string, container registry authentication info, and other secrets. Please note that both SQL Server and Key Vault have one private endpoint each to make those accessible on VNET level by the on-prem app via VPN. Both SQL server and Key Vault are registered in a respective privatelink domain which is connected to hub VNET to enable DNS resolution from the DNS private Resolver. DNS Private Resolver has 1 inbound endpoint - it does not need an outbound endpoint for external domain resolution or forwarding. 
The purpose of such architecture is to allow on-prem app resolve privatelink addresses of SQL Server and Key Vault via DNS private resolver - this communication (nslookup queries) happens via VPN. DNS server on-prem is conigured to forward lookup queries for privatelink-domains to Azure DNS Resolver.

Container registry contains container builds of the app. Container App was used to test specific container build. 