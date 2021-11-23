# AZ-900 - Practice
## Concepts
---
### Cloud advantages
- Paying only for the capacity when needed, is an example of elasticity.
- A financial analysis of migration of on-premises files to Azure Storage showed that storing data in Azure would be less expensive than hosting it on-premises. The report also showed unit cost in Azure would decrease even further as the data archive grows. This is an example of economies of scale.
---
### Cloud models & expenditures
- Company X is planning to move to Azure, but currently hosts business applications in a shared virtualisation infrastructure on-premises, utilising Hyper-V. This is an example of Private Cloud.
- ⚠️ You need to provide additional capacity than what is currently available on-prem. The solution must minimise capital expense (CapEx) and operational expense (OpEx). Then, a hybrid cloud is recommended.
- Azure SQL Database and an on-premise SQL cluster represent an Operational expense and a Capital expense, respectively.
- Migrating existing on-premises SQL VMs to Azure, implements the Operational Expenditure model.
---
### SaaS, PaaS, IaaS
- Examples of SaaS: Office 365,
- Examples of PaaS: Event Grid, Azure App Service, Azure (My)SQL Database, Cosmos DB
- Examples of IaaS: Azure VMs
- With SaaS you are responsible for configuring the solution features. Not for maintaining infra, not for deploying updates, not for availability and scalability. 
---
### Azure Region
- Each Azure Region features datacenters deployed within a latency-defined perimeter. They're connected through a dedicated regional low-latency network. 
- Azure China 
	- ⚠️ Available to legal entities in China. Not any organisation globally, doing business in China. 
	- Workloads deployed on Azure China can be accessed anywhere globally.
- Azure Germany
	- ⚠️ Available to eligible customers and partners globally doing business in the EU/EFTA. Not to anyone who wants data residency in Germany.
- Use Azure Site Recovery for service recovery in the event of site outage at on-premises datacenter. 
### Azure Availability Sets
- ⚠️ Azure Availability Sets protects against server rack-level failures.
### Azure Availability Zones
- ⚠️ Azure Availability Zones protects against datacenter-level failures. 
- By utilising availability zones, the service will remain available if a single Azure datacenter fails.
---
### Service Previews
- Standard lifecycle for Azure services released by Microsoft:
	1. Private Preview
	2. Public Preview
	3. General Availability
- Azure services in Public Preview 
	- are available to all costumers.
	- are NOT available in all Azure regions.
	- do NOT include an SLA
---
### SLA's
- Guarantees about uptime and connectivity, varies by service.
- All free Azure services have a minimum SLA of 99.9% (three 9's).
---
### Resources
- Use resource locks (read-only) to prevent (additional) resources from being created/deleted in an Azure resource group (including administrators).
### Resource Groups
- There are no additional costs when using additional resource groups.
- Resources do not inherit the taks assigned to the parent resource group.
- A resource group can have resources deployed in multiple regions. 
### Security Groups
- ⚠️ Group users for assignment of permissions (Office 365). Less suitable: Resource Groups.
### Management Groups
- ⚠️ Apply standards across deployments in multiple Azure subscriptions.
### Subscriptions
- Multiple subscriptions can be associated to the same Azure AD.
- ⚠️ Open a support request when you've reached the limits in your Azure subscription.
---
### Azure Tags
- ⚠️ Simplify cost reporting per business unit. 
---
### Accounts & identity management
- Use Azure Free account to try some Azure services (max. 12 months).
- Authentication: user authentication is the process of validating that a user is who they claim to be.
- Authorization: RBAC is an example of authorization.
- ⚠️ For SSO, Password Hash Synchronisation and Pass-through authentication are available. You cannot support SSO and multi-factor authentication without synchronising on-premises identities to Azure.
- RBAC are inherited: management groups > subscriptions > resource groups > resources.
---
---
## Tools
---
### Compliance & Regulations
#### Microsoft Trust Center
- Determine if the Azure platform meets particular regulatory standard.
---
### Pricing / Cost Management
#### Azure Price Calculator vs Azure TCO Calculator
- The Azure Calculator is meant to get pricing when you know exactly what you need in Azure, or want to look up pricing for the resources you know about. TCO Calculator is meant when you want to estimate how much it would cost to move your resources from on-premises to Azure, by inputting what you are currently using, and letting it convert that into Azure equivalence.
#### Azure Pricing Calculator
- Prior to migration, costs can be estimated using the Azure Pricing Calculator.
- Calculate estimated cost before deploying. 
#### Azure Reservations
- Pricing option (commitment of X years) to reduce hosting costs if planning to run services for an extended period (years) and make predicting future spending easier.
#### Azure Cost Management
- Analyze past cloud usage and expenses, and predict future expenses.
- Do not use for:
	- Identify recommendations on how to reduce the cost of running VMs (Azure Advisor)
---
### Best practices & Recommendations
#### Azure Advisor
- ⚠️ Identify recommendations on how to reduce the cost of running VMs.
- Get best practice recommendations for high availability of your existing VM resources. 
- Do not use for:
	- Identifing deviations from Microsoft security best practices in your Azure cloud infrastructure (Azure Security Center).
#### The Trust Center
- ⚠️ Verify that Azure complies with regulatory obligations. 
---
### Compute
#### Azure Container Instances
- Enable elastic bursting for Azure Kubernetes Service.
- ⚠️ Do NOT provide feature parity for Linux and Windows containers.
- ⚠️ Do NOT enable running containers without servers to manage.
#### Azure VMs
- Azure doesn't charge for the VM core hours while it is Stopped (Deallocated). However, you continue to accrue charges for the Azure storage needed for the VM’s OS disk and any attached data disks. 
### Serverless computing
#### Azure Functions
- Execute code
- Automate a task using a script with minimum cost and maintenance effort.
#### Azure Logic Apps
- Execute (business) workflows based on triggers. 
- Automate business processes in a low-code environment with a visual interface.
---
### Security
#### Azure Security Center vs Azure Sentinel
- Azure Security Center is a tool for security posture management and threat protection, it protects workloads running in Azure, on-premises, and in other clouds. Azure Security Center is one of many sources of threat information fed into Azure Sentinel to create a view of the entire enterprise.
#### Azure Security Center
- ⚠️ Identify deviations from Microsoft security best practices in your Azure cloud infrastructure.
- Verify whether your Azure environment meets regulatory requirements.
- Find recommendations for security best practices and security configuration for Azure Kubernetes Service (AKS).
#### Azure Key Vault
- Store, manage and access SSL/TLS certificates.
#### Defender for Cloud Apps
- Use Defender for Cloud Apps (formerly Microsoft Cloud App Security) to discover Shadow IT (non-sanctioned apps).
#### Defender for Identity
- Use Microsoft Defender for Identity (formerly Azure Advanced Threat Protection - ATP) to protect on-premises identities from external threats.
#### Azure DDoS
- Azure DDoS, which protects your Azure resources against distributed denial of services attacks, includes both Basic and Standard tiers.
#### Azure Information Protection (AIP)
- Cloud-based solution that enables organisations to discover, classify, and protect documents and emails by applying labels to content.
#### Azure AD Identity Protection
- Set up risk-based policies in Azure AD.
- ⚠️ Set up policies for logging in from anonymous IP or unusual location. Less suitable: Azure AD Conditional Access.
- Protect your Azure identities from external threats. 
---
### Networking
#### Connecting on-premise <=> Azure
1. Point-to-site connectivity with Virtual Network (manually connect)
2. Site-to-site connectivity with Virtual Network (keep communication up all the time) 
3. Private site-to-site connectivity with ExpressRoute (private connections)
- In a Site-to-Site VPN, the Azure Virtual Network Gateway is the cross-premises gateway that connects your Azure Virtual Network with your on-premises VPN appliances. 
- ⚠️ Use Site-to-Site VPN to connect on-premises datacenter to Azure with minimal expense during low-scale pilot deployment.
- Use Azure ExpressRoute to connect on-premises application resources, minimise latency and maximise security. 
#### Azure Firewall
- Deploy an Azure Firewall to securely limit inbound traffic and protect VMs from unwanted inbound requests. 
#### Virtual Networks
- Azure VMs in different subnets in the same virtual network can communicate by default.
- ⚠️ Azure routes traffic between all subnets within a virtual network, by default. Create a user defined route to override Azure's default routing. 
- Azure VMs in different virtual networks can not communicate by default.
#### Azure Traffic Manager vs Azure Load Balancer
- Azure Traffic Manager is been designed to distribute traffic globally (multiregional environments). 
- Azure Load Balancer can only route traffic inside an Azure region, as it only works with Virtual Machines in the same region.
#### Azure Traffic Manager
- Non-HTTP(s) load balancing option with minimal latency globally. 
#### Application Security Group (ASG)
- ⚠️ Restrict communication for current and future resources with a minimum of administrative effort.
#### Network Security Group (NSG)
- ⚠️ Add a security rule to the Network Security Group (NSG) to allow inbound traffic and provide access to an application over the internet via HTTP/S.
- Do not use for:
	- Restricting communication for current and future resources (Application Security Group (ASG)).
#### Azure Front Door
- Optimise global routing of web traffic and optimise end-user performance and reliability through quick global failover.
#### Azure Application Gateway
- Load balancing HTTPS traffic in a single Azure region. 
---
### Automation
#### Azure Resource Manager (ARM) templates
- Ensure deployments of Azure resources are the same for every deployment.
- Do not use for:
	- Identifing and enforcing standards across new and existing Azure deployments (Azure Policy)
#### Azure DevOps
- ⚠️ Automate version updates of PaaS application hosted in Azure. 
#### Azure Automation
- Automate and centrally manage various processes in VMs hosted both in Azure and on-premises.
- Do not use for:
	- Automation of version updates of PaaS application hosted in Azure (Azure DevOps)
#### Azure Blueprints
- ⚠️ Enable delivery of templates for repeatable deployment and configuration of new subscriptions and environments.
---
### Policies
#### Azure Policiy vs Azure Initiative
- Azure Policy is a service in Azure which allows you create polices which enforce and control the properties of a resource. When these policies are used they enforce different rules and effects over your resources, so those resources stay compliant with your IT governance standards.
- An Azure initiative is a collection of Azure policy definitions that are grouped together towards a specific goal or purpose in mind. Azure initiatives simplify management of your policies by grouping a set of policies together as one single item.
#### Azure Policy
-  Identify and enforce standards across new and existing Azure deployments.
- Make sure that resources are only created in approved regions. 
#### Azure Access Policies
- Apply authorization standards across deployments in multiple Azure subscriptions. 
#### Azure Initiatives
- Define a group of Azure policies that define and enforce corporate standards. 
- Do not use for:
	- Delivery of templates for repeatable deployment and configuration of new subscriptions and environments (Azure Blueprints)
---
### Monitoring
#### Azure Monitor
- Comprehensive solution for collecting, analysing and acting on telemetry from your cloud and on-premises environments. 
- Monitor health and performance of microservices running on Azure Kubernetes Service (AKS).
- Alert on service failures in you Azure services, such as web app instances hosted in App Service, and Azure VMs that stop running for any reason. 
- ⚠️ Aggregate events from a large number of resources hosted in Azure for correlation, alerting and reporting.
#### Azure Application Insights
- Monitor customer-facing web apps for performance anomalies. 
- Azure Application Insights, a feature of Azure Monitor, can be used to monitor your live applications. It will automatically detect performance anomalies, and includes powerful analytics tools to help you diagnose issues.
- Do not use for:
	- Analysing telemetry data in Azure when the goal is to identify performance anomalies on IoT devices and opportunities to improve device operation (Azure Application Insights).
#### Azure Time Series Insights
- ⚠️ Analyse telemetry data in Azure with Azure Time Series Insights (when the goal is to identify performance anomalies on IoT devices and opportunities to improve device operation). 
#### Azure Log Analytics
- ⚠️ Correlate events from multiple Azure resources in a central repository.
---
### Storage
#### Disk Storage
- Storage for Azure VMs is hosted in Disk storage.
#### Azure File(s)
- Use for a line-of-business application that requires access to a file share with minimum cost and administration effort.
- Migrate a legacy application to Azure that requires a file share accessible on a UNC path and provides an SMB file share and secure access. 
#### Azure Blob Storage
- Object store used for storing vast amounts unstructured data, while Azure File Storage is a fully managed distributed file system based on the SMB protocol and looks like a typical hard drive once mounted.
#### Azure Cosmos DB
- Store custom data in JSON format with high global availability.
- Data stored in MongoDB (document-like storage) is best migrated to Azure Cosmos DB. 
- Data stored in NoSQL database is best migrated to Azure Cosmos DB.
#### Azure SQL Database
- Relational databases are best migrated to Azure SQL Database.
#### Azure Event Grid
- ⚠️ Relay messages from a variety of sources (Azure services) to an application. Azure Event Grid is a fully-managed event routing service.
#### Azure Event Hub
- Big Data streaming platform and event ingestion service that can receive and process millions of events per second.
- Do not use for:
	- Correlation of events from multiple Azure resources in a central repository (Azure Log Analytics).
	- Relay messages from a variety of sources (Azure services) to an application (Azure Event Grid).
	- Aggregate events from a large number of resources hosted in Azure for correlation, alerting and reporting (Azure Monitor).
---
### Data Science
#### Azure Machine Learning Studio
- No-code tool to build and test machine learning models. 
#### Azure HDInsight
- Deploy an Apache Hadoop cluster in Azure.
#### Azure Cognitive Service
- Use for apps that can interact with users using spoken and written language.
#### Azure Databricks
- ⚠️ Host big data service, which can serve as data source for machine learning algorithms. 
#### Azure Language Understanding (LUIS)
- ⚠️ Develop an AI app that accepts requests through chat, applies NlP and can be hosted on Azure.
---
### IoT
#### Azure IoT Edge
- Analyze data locally on IoT devices, speed event response and reduce data sent to the cloud. 
#### Azure IoT Central
- Manage IoT devices with minimal need for custom development (SaaS).
#### Azure IoT Hub
- Central message hub for bi-directional communication between your IoT app and the devices it manages. Azure IoT central is an IoT application that simplifies the creation of IoT solutions. 
---

