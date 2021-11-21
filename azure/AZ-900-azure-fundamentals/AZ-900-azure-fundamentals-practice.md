# AZ-900 - Practice

Standard lifecycle for Azure services released by Microsoft:
	1. Private Preview
	2. Public Preview
	3. General Availability

Azure services in Public Preview are/are not available in all Azure regions.

Pricing option to reduce costs and making predicting future spending easier: Azure Reservations.

!!! Use Azure Advisor to identify recommendations on how to reduce the cost of running VMs. Not Azure Cost Management.

Azure availability zones are physically separate locations within each Azure region that are tolerant to local failures. By utilising availability zones, the service will remain available if a single Azure datacenter fails.

There are no additional costs when using additional resource groups.

Prior to migration, costs can be estimated using the Azure Pricing Calculator.

Azure SLA's guarantee uptime and connectivity, varies by service.

Azure services in Public Preview are available to all costumers.

Use Azure Reservations to reduce hosting costs if planning to run services for an extended period (years).

Use Azure Pricing Calculator to calculate estimated cost before deploying. 

Azure Price Calculator vs Azure TCO Calculator:
The Azure Calculator is meant to get pricing when you know exactly what you need in Azure, or want to look up pricing for the resources you know about. TCO Calculator is meant when you want to estimate how much it would cost to move your resources from on-premises to Azure, by inputting what you are currently using, and letting it convert that into Azure equivalence.

!!! Use the Trust Center to verify that Azure complies with regulatory obligations. Not the Knowledge Center.

!!! Use Azure Security Center to identify deviations from Microsoft security best practices in your Azure cloud infrastructure. Not Azure Advisor.

Azure services in Public Preview 
- do not include an SLA

Use Azure Free account to try some Azure services (max. 12 months).

All free Azure services have a minimum SLA of 99.9% (three 9's).

Resources do not inherit the taks assigned to the parent resource group.

User authentication is the process of validating that a user is who they claim to be.

Use resource locks (read-only) to prevent additional resources from being created in an Azure resource group (including administrators).

RBAC is an example of authorization.

!!! Use Azure Policy to identify and enforce standards across new and existing Azure deployments. Not Azure Resource Manager (ARM) templates.

!!! Use Azure Tags to simplify cost reporting per business unit. Not Resource Groups or Management Groups.

Use Azure AD Identity Protection to set up risk-based policies in Azure AD.

!!! Azure China is available to legal entities in China. Not any organisation globally, doing business in China. 

!!! Use a Security Group to group users for assignment of permissions (Office 365). Not Resource Groups.

!!! For SSO, Password Hash Synchronisation and Pass-through authentication are available. You cannot support SSO and multi-factor authentication without synchronising on-premises identities to Azure.

!!! Use Azure Blueprints to enable delivery of templates for repeatable deployment and configuration of new subscriptions and environments. Not Azure Policy initiatives.

Use the Microsoft Trust Center to determine if the Azure platform meets particular regulatory standard.

Use Azure Security Center to verify whether your Azure environment meets regulatory requirements.

Use Microsoft Cloud App Security (renamed to Defender for Cloud Apps) to discover Shadow IT (non-sanctioned apps).

Can workloads deployed on Azure China be accessed anywhere globally? Yes, you can access your workloads deployed on Azure China anywhere globally.

!!! Use Azure AD Identity Protection to set up policies for logging in from anonymous IP or unusual location. Not Azure AD Conditional Access.

!!! Azure Germany is available to eligible customers and partners globally doing business in the EU/EFTA. Not to anyone who wants data residency in Germany.

Use Microsoft Defender for Identity (formerly Azure Advanced Threat Protection - ATP) to protect on-premises identities from external threats.

RBAC are inherited: management groups > subscriptions > resource groups > resources.

Use Azure Policy to make sure that resources are only created in approved regions. 

Use Azure locks to prevent accidental deletion of Azure resources.

In a Site-to-Site VPN, the Azure Virtual Network Gateway is the cross-premises gateway that connects your Azure Virtual Network with your on-premises VPN appliances. 

Use Azure Identity Protection to protect your Azure identities from external threats. 

Use Azure Initiative to define a group of Azure policies that define and enforce corporate standards. 

!!! Use Application Security Group (ASG) to restrict communication for current and future resources with a minimum of administrative effort. Not Network Security Group (NSG).

Deploy an Azure Firewall to securely limit inbound traffic and protect VMs from unwanted inbound requests. 

!!! Add a security rule to the Network Security Group (NSG) to allow inbound traffic and provide access to an application over the internet via HTTP/S

Use Azure Front Door to optimise global routing of web traffic and optimise end-user performance and reliability through quick global failover.

!!! Azure routes traffic between all subnets within a virtual network, by default. Create a user defined route to override Azure's default routing. 

Azure VMs in different virtual networks can not communicate by default.

Azure IoT hub is a central message hub for bi-directional communication between your IoT app and the devices it manages. Azure IoT central is an IoT application that simplifies the creation of IoT solutions. 

Azure Security Center => Azure Sentinel
Azure Security Center is a tool for security posture management and threat protection, it protects workloads running in Azure, on-premises, and in other clouds. Azure Security Center is one of many sources of threat information fed into Azure Sentinel to create a view of the entire enterprise.

You can find recommendations for security best practices and security configuration for Azure Kubernetes Service (AKS) with Azure Security Center.

Azure Monitor > Azure Application Insigths
Azure Monitor is a comprehensive solution for collecting, analysing and acting on telemetry from your cloud and on-premises environments. Azure Application Insights, a feature of Azure Monitor, can be used to monitor your live applications. It will automatically detect performance anomalies, and includes powerful analytics tools to help you diagnose issues.

Use Azure Monitor to alert on service failures in you Azure services, such as web app instances hosted in App Service, and Azure VMs that stop running for any reason. 

!!! Use Azure Monitor to aggregate events from a large number of resources hosted in Azure for correlation, alerting and reporting. Not Azure Event Hub.

Use Azure Automation to automate and centrally manage various processes in VMs hosted both in Azure and on-premises.

Data stored in MongoDB (document-like storage) is best migrated to Azure Cosmos DB. 

Data stored in NoSQL database is best migrated to Azure Cosmos DB.

Use Azure Application Insights to monitor customer-facing web apps for performance anomalies. 

Use Azure Machine Learning Studio as a no-code tool to build and test machine learning models. 

Use Azure Advisor to get best practice recommendations for high availability of your existing VM resources. 

Use Azure Cosmos DB to store custom data in JSON format with high global availability.

Use Azure HDInsight to deploy an Apache Hadoop cluster in Azure.

Use Azure Monitor to monitor health and performance of microservices running on Azure Kubernetes Service (AKS).

Serverless computing services are Azure Functions (execute code) and Azure Logic Apps (execute workflows based on triggers). 

Use https://portal.azure.com to access the Azure Portal.

Use Azure IoT Edge to analyze data locally on IoT devices, speed event response and reduce data sent to the cloud. 

Use Azure IoT Central to manage IoT devices with minimal need for custom development (SaaS).

!!! An Azure Availability Sets protects against server rack-level failures. While availability sets are used to protect applications from hardware failures within an Azure data center, availability zones, protect applications from complete Azure data center failures. 

Use Azure Site Recovery for service recovery in the event of site outage at on-premises datacenter. 

!!! Use Azure Traffic Manager as a non-HTTP(s) load balancing option with minimal latency globally. Not Azure Load Balancer.

!!! Analyse telemetry data in Azure with Azure Time Series Insights (when the goal is to identify performance anomalies on IoT devices and opportunities to improve device operation). Not Application Insights.

Use Azure Marketplace to find an offering to quickly deploy a WordPress website.

Each Azure region features datacenters deployed within a latency-defined perimeter. They're connected through a dedicated regional low-latency network. 

Azure Information Protection (AIP) is a cloud-based solution that enables organisations to discover, classify, and protect documents and emails by applying labels to content.

Multiple subscriptions can be associated to the same Azure AD.

Storage for Azure VMs is hosted in Disk storage.

Use Azure Files to migrate a legacy application to Azure that requires a file share accessible on a UNC path and provides an SMB file share and secure access. 

Use Azure Key Vault to store, manage and access SSL/TLS certificates.

Connecting on-premise <=> Azure:
1. Point-to-site connectivity with Virtual Network (manually connect)
2. Site-to-site connectivity with Virtual Network (keep communication up all the time) 
3. Private site-to-site connectivity with ExpressRoute (private connections)

!!! Use Site-to-Site VPN to connect on-premises datacenter to Azure with minimal expense during low-scale pilot deployment. Not Point-to-Site VPN.

Use Azure ExpressRoute to connect on-premises application resources, minimise latency and maximise security. 

!!! Use Management Groups to apply standards across deployments in multiple Azure subscriptions.

Use Access Policies to apply standards across deployments in multiple Azure subscriptions. 

Relational databases are best migrated to Azure SQL Database.

!!! Use Azure Databricks to host big data service, which can serve as data source for machine learning algorithms. Not Azure SQL.

!!! Use Azure Language Understanding (LUIS) to develop an AI app that accepts requests through chat, applies NlP and can be hosted on Azure. Not Azure Cognitive Speech Services.

!!! Open a support request when you've reached the limits in your Azure subscription.

!!! Use Azure DevOps to automate version updates of PaaS application hosted in Azure. Not Azure Automation.

Use Azure Cognitive Service for apps that can interact with users using spoken and written language.

!!! Azure Container Instances do NOT provide feature parity for Linux and Windows containers.

Use Azure Monitor to monitor the health and availability of your Azure Kubernetes Service (AKS) cluster. 

!!! Use Azure Event Grid to relay messages from a variety of sources (Azure services) to an application. Azure Event Grid is a fully-managed event routing service. Not Azure Event Hub. 

An Azure Availability Zone protects against datacenter-level failures.

!!! Use Log Analytics to correlate events from multiple Azure resources in a central repository. Not Azure Event Hub.

Use Azure Application Gateway for load balancing HTTPS traffic in a single Azure region. 

A resource group can have resources deployed in multiple regions. 

Azure doesn't charge for the VM core hours while it is Stopped (Deallocated). However, you continue to accrue charges for the Azure storage needed for the VM’s OS disk and any attached data disks. 

Use Azure Resource Manager (ARM) templates to ensure deployments of Azure resources are the same for every deployment.

Azure Blob Storage is an object store used for storing vast amounts unstructured data, while Azure File Storage is a fully managed distributed file system based on the SMB protocol and looks like a typical hard drive once mounted.

Use Azure File for a line-of-business application that requires access to a file share with minimum cost and administration effort.

Use Azure Functions to automate a task using a script with minimum cost and maintenance effort.

Use Logic Apps to automate business processes in a low-code environment with a visual interface.

A financial analysis of migration of on-premises files to Azure Storage showed that storing data in Azure would be less expensive than hosting it on-premises. The report also showed unit cost in Azure would decrease even further as the data archive grows. This is an example of economies of scale.

Migrating existing on-premises SQL VMs to Azure, implements the Operational Expenditure model.

Paying only for the capacity when needed, is an example of elasticity.

Hosting databases for customer-facing web applications in Azure MySQL Database is an example of platform as a service.

Office 365, Azure VMs and Event Grid represent, SaaS, IaaS and Paas, respectively.

!!! You need to provide additional capacity than what is currently available on-prem. The solution must minimise capital expense (CapEx) and operational expense (OpEx). Then, a hybrid cloud is recommended.

Azure App Service, Azure SQL Database, and Cosmos DB are examples of Platform as a Service.

Azure VMs are Infrastructure as a Service.

Azure SQL Database and an on-premise SQL cluster represent an Operational expense and a Capital expense, respectively.

Company X is planning to move to Azure, but currently hosts business applications in a shared virtualisation infrastructure on-premises, utilising Hyper-V. This is an example of Private Cloud.

With Software as a Service you are responsible for configuring the solution features. Not for maintaining infra, not for deploying updates, not for availability and scalability. 

Azure Container instances enable elastic bursting for Azure Kubernetes Service.

!!! Azure Container Instances do NOT enable running containers without servers to manage.

Azure DDoS, which protects your Azure resources against distributed denial of services attacks, includes both Basic and Standard tiers.

Azure VMs in different subnets in the same virtual network can communicate by default.










