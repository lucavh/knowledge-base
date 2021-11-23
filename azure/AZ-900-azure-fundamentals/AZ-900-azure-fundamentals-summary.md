# AZ-900 - Summary

## 1. Cloud Concepts (20-25%)

### Benefits of cloud computing (SHE-D-AF)
- Scalability
- High Availability: operational uptime
- Elasticity: scale dynamically
- Disaster Recovery
- Agility: scale quickly
- Fault tolerance

### Consumption-based model
- No associated upfront cost
- No wasted resources
- Pay for what you need
- Stop paying when you don't

### Service Models responsibilities
- S - Application
- S - Data
- P - Runtime
- P - Middleware
- P - Operating System
- I - Virtualization
- I - Servers
- I - Networking
- I - Storage

### Cloud Deployment Model
- Public, Private and Hybrid Cloud
## 2. Azure Services (15-20%)

### Architectural Components in Azure
#### Region (1+ data centers)
- Data centers connected with low-latency network
- Some serbices are available only in certain regions
- Special government regions (US DoD Central, US Gov Virginia, etc)
- Special partnered regions (China East, China North)

#### Availability Zones (3+ zones)
- Designed to protect from data center failures

#### Region Pair
- Each region is paired with another region with at least 300 miles distance
- Data residency maintained for disaster recovery

#### Geographies (2+ regions)
- Fault tolerant to protect from region wide failures
- Each region belongs to one Geography.

#### Azure Resource
- Object used to manage services
- Saved as JSON definition

#### Resource Groups
- Grouping of resources

#### Resource Manager (-> ARM templates)
- Management layer for all resources and resource groups
- Unified language

### Core Products in Azure

#### Virtualization
- Azure Virtual Machines (VMs) - custom software, custom requirements, very specialized, high degree of control (IaaS)
- VM Scale Sets - auto-scaled workloads for VMs (IaaS)
- Azure Container Instances - simple container hosting, easy to start (PaaS)
- Azure Kubernetes Service - highly scalable and customizable container hosting platform (PaaS)
- Azure App Service - designed as enterprise grade web application service
- Azure Functions (PaaS/FaaS) - micro/nano-services for executing scripts
#### Networking
- Connect cloud and on-premises
- Azure Virtual Network - logically isolated networking components
    - Segmented into one or more subnets
    - Enable communication of resources with eachother, internet and on-prem
    - Scoped to a single region
    - VNet peering allows cross-region communication
- Azure Load Balancer - event traffic distribution for TCP/UDP traffic
- Application Gateway - HTTP(s) traffic distribution
- VPN Gateway - pecific type of virtual network gateway for on-premises to Azure traffic over the public internet.

#### Storage
- Azure Blob Storage - storage of files of any kind
- Azure Queue Storage - storage for small pieces of data (messages)
- Azure Table Storage - storage for semi-structured data (NoSQL)
- Azure File Storage - shared drive
- Azure Disk Storage - persistent storage for VMs
- Cosmos DB - globally distributed NoSQL database service
- Azure SQL Database - reliable relational database based on SQL server
- Azure Database for MySQL - Azure SQL version for MySQL database engine
- Azure Database for PostgreSQL - Azure SQL version for PostfgreSQL database enginge
- Azure SQL Managed Instance - Fully fledged SQL Server managed by cloud provider
- Azure AQL on VM - Fully fledged SQL server on IaaS
- Azure SQL DW (Synapse) - Massively Parallel Processing (MPP) version of SQL server

### Solutions in Azure

#### IoT
- Azure IoT Hub - managed service for bi-directional communication
- Azure IoT Central- SaaS application for management of IoT devices
- Azure Sphere - secure end-2-end IoT Solutions

#### Big Data
- Azure Synapse Analytics - big data analytics platform (PaaS)
- Azure HDInsight - flexible multi-purpose big data platform (PaaS)
- Azure Databricks - big data collaboration platform (PaaS)

#### Artificial Intelligence
- Azure Machine Learning - cloud-based platform for creating, managing and publishing machine learning models
    - Machine Learning Workspace - top level resource
    - Machine Learning Studio - drag-and-drop web portal

#### Serverless
- Azure Functions - serverless coding platform (PaaS/FaaS)
- Azure Logic Apps - serverless enterprise integration service (PaaS)
- Azure Event Grid - fully managed serverless event routing service

#### DevOps
- Azure DevOps - collection of services for building solutions using DevOps practices
- Azure DevTest Labs - service for creation of sandbox environments for developers/testers (PaaS)

#### Management Tools on Azure
- Azure Portal - self-service web portal
- Azure PowerShell - PowerShell module designed for automation
- Azure CLI - command line interface for Azure
- Azure Cloud Shell - cloud-based scripting environment
- Azure Advisor - personalized consultant service, designed to provide recommendations and best practices for cost, security, reliability, performance and operational excellence.

## 3. Security, Privacy, Compliance, and Trust (25-35%)

### Securing network connectivity in Azure
- Network Security Grousp (NSG) - designed to filter traffic to (inbound) and from (outbound) Azure resources located in Azure Virtual Network
- Applocation Security Groups (ASG) - feature that allows grouping of virtual machines located in Azure Virtual Network
- Azure Firewall - managed, cloud-based firewall service (PaaS)
- Azure DDoS Protection - designed to detect malicious traffic and block it and prefent additional costs for auto-scaling environments.

### Azure Identity services
- Authentication: -  process of assertion of identity
- Authorization - process of ensuring that ony authenticated identities get access to the resources for which they have been granted access
- Access Management - process of controlling, verifying, tracking and managing access to authorized users and applications
- Azure Active Directory (AD) - identity and Access Management service in Azure
    - Identities - users, groups, allocations
    - Access management - subscriptions, resource groups, roles, role assignments, authentication and authorization settings, etc.

### Security tools and features of Azure
- Azure Security Center - centralized and unified infrastructure and platform security management service.
    - Integrated with Azure Advisor
    - Two tiers
        - Free - Azure Defender OFF, continuous assessments, security score, and actionable security recommendations.
        - Paid - Azure Defender ON, hybrid security, threat protection alerts, vulnerability scanning, just in time (JIT) VM access, etc.
- Azure Key Vault - managed service for securing sensitive information (PaaS)

### Governance features of Azure
- Role - "what can be done?"
- Security Principal - "who can do it?"
- Scope - "Where can it be done?"
- RBAC - authorization system built on Azure Resource Manager (ARM), combination of role definition, security principal and scope.
- Azure Resource Lock - designed to prevent accidental deletion and/or modification (two versions: ReadOnly and CanNotDelete)
- Azure Resource Tags - designed for organization of Azure resources
- Azure Policy - designed to help with resource governance, security, compliance, cost management, etc. 
- Azure Pilicy Initiative - a group of policy definitions
- Policies focus on resource propoerties, whereas RBAC focuses on user actions. 
- Azure Blueprints - centralized storage for organizationally approved design patterns, a package of various Azure components (artifacts), such as resource groups, ARM templates, policy assignments and role assignments. 

### Privacy and compliance resources in Azure

#### Resources
- Microsoft Privacy Statement - collection, purpose and usage of personal data
- Online Services Terms (OST) - licensing terms, what can be done and what is forbidden
- Data Protection Addendum - appending to OST describing obligations by both parties with regards to processing of customer and personal data
- Trust Center - web portal for everything related to security, compliance, privacy, policies, best practices, etc.
- Azure Compliance Documentation - web portal focusing on compliance offerings in Azure, similar to the Trust Center but narrowed down

#### Azure Sovereign Regions
- Provide Azure services in markets with very strict regulatory requirements
- Azure Government design for the US government
- Azure China designed for the Chinese market
## 4. Azure Cost Management and SLA's (10-15%)
...

