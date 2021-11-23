# AZ-900 - Summary

## 1. Cloud Concepts (20-25%)

### Benefits of cloud computing (SHE-D-AF)
- __Scalability__
- __High Availability__: operational uptime
- __Elasticity__: scale dynamically
- __Disaster Recovery__
- __Agility__: scale quickly
- __Fault tolerance__

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
- __Public__, __Private__ and __Hybrid__ Cloud
## 2. Azure Services (15-20%)

### Architectural Components in Azure
- __Region__ - 1+ data centers connected with low-latency network. Some services are available only in certain regions.
- __Availability Zones__ - 3+ zones connected to protect from data center failures
- __Region Pair__ - each region is paired with another region with at least 300 miles distance so data residency is maintained for disaster recovery
- __Geographies__ - are fault tolerant to protect from region wide failures, each region belongs to one Geography
- __Resource__ - object used to manage services, saved as JSON definition
- __Resource Groups__ - grouping of resources
- __Resource Manager__ - management layer for all resources and resource groups, unified language

### Core Products in Azure

#### Virtualization
- Azure __Virtual Machines__ (VMs) - custom software, custom requirements, very specialized, high degree of control (IaaS)
- __VM Scale Sets__ - auto-scaled workloads for VMs (IaaS)
- Azure __Container Instances__ - simple container hosting, easy to start (PaaS)
- Azure __Kubernetes Service__ - highly scalable and customizable container hosting platform (PaaS)
- Azure __App Service__ - designed as enterprise grade web application service
- Azure __Functions__ - micro/nano-services for executing scripts (PaaS/FaaS)
#### Networking
- Connect cloud and on-premises
- Azure __Virtual Network__ - logically isolated networking components
    - Segmented into one or more subnets
    - Enable communication of resources with eachother, internet and on-prem
    - Scoped to a single region
    - __VNet__ peering allows cross-region communication
- Azure __Load Balancer__ - event traffic distribution for TCP/UDP traffic
- __Application Gateway__ - HTTP(s) traffic distribution
- __VPN Gateway__ - specific type of virtual network gateway for on-premises to Azure traffic over the public internet.

#### Storage
- Azure __Blob Storage__ - storage of files of any kind
- Azure __Queue Storage__ - storage for small pieces of data (messages)
- Azure __Table Storage__ - storage for semi-structured data (NoSQL)
- Azure __File Storage__ - shared drive
- Azure __Disk Storage__ - persistent storage for VMs
- __Cosmos DB__ - globally distributed NoSQL database service
- Azure __SQL Database__ - reliable relational database based on SQL server
- Azure __Database for MySQL__ - Azure SQL version for MySQL database engine
- Azure __Database for PostgreSQL__ - Azure SQL version for PostfgreSQL database enginge
- Azure __SQL Managed Instance__ - Fully fledged SQL Server managed by cloud provider
- Azure __SQL on VM__ - Fully fledged SQL server on IaaS
- Azure __SQL DW (Synapse)__ - Massively Parallel Processing (MPP) version of SQL server

### Solutions in Azure

#### IoT
- Azure __IoT Hub__ - managed service for bi-directional communication
- Azure __IoT Central__ - SaaS application for management of IoT devices
- Azure __Sphere__ - secure end-2-end IoT Solutions

#### Big Data
- Azure __Synapse Analytics__ - big data analytics platform (PaaS)
- Azure __HDInsight__ - flexible multi-purpose big data platform (PaaS)
- Azure __Databricks__ - big data collaboration platform (PaaS)

#### Artificial Intelligence
- Azure __Machine Learning__ - cloud-based platform for creating, managing and publishing machine learning models
    - Machine Learning __Workspace__ - top level resource
    - Machine Learning __Studio__ - drag-and-drop web portal

#### Serverless
- Azure __Functions__ - serverless coding platform (PaaS/FaaS)
- Azure __Logic Apps__ - serverless enterprise integration service (PaaS)
- Azure __Event Grid__ - fully managed serverless event routing service

#### DevOps
- Azure __DevOps__ - collection of services for building solutions using DevOps practices
- Azure __DevTest Labs__ - service for creation of sandbox environments for developers/testers (PaaS)

#### Management Tools on Azure
- Azure __Portal__ - self-service web portal
- Azure __PowerShell__ - PowerShell module designed for automation
- Azure __CLI__ - command line interface for Azure
- Azure __Cloud Shell__ - cloud-based scripting environment
- Azure __Advisor__ - personalized consultant service, designed to provide recommendations and best practices for cost, security, reliability, performance and operational excellence.

## 3. Security, Privacy, Compliance, and Trust (25-35%)

### Securing network connectivity in Azure
- __Network Security Groups__ (NSG) - designed to filter traffic to (inbound) and from (outbound) Azure resources located in Azure Virtual Network
- __Applocation Security Groups__ (ASG) - feature that allows grouping of virtual machines located in Azure Virtual Network
- Azure __Firewall__ - managed, cloud-based firewall service (PaaS)
- Azure __DDoS Protection__ - designed to detect malicious traffic and block it and prevent additional costs for auto-scaling environments.

### Azure Identity services
- __Authentication__ -  process of assertion of identity
- __Authorization__ - process of ensuring that ony authenticated identities get access to the resources for which they have been granted access
- __Access Management__ - process of controlling, verifying, tracking and managing access to authorized users and applications
- Azure __Active Directory__ (AD) - identity and Access Management service in Azure
    - __Identities__ - users, groups, allocations
    - __Access management__ - subscriptions, resource groups, roles, role assignments, authentication and authorization settings, etc.

### Security tools and features of Azure
- Azure __Security Center__ - centralized and unified infrastructure and platform security management service.
    - Integrated with Azure Advisor
    - Two tiers
        - __Free__ - Azure Defender OFF, continuous assessments, security score, and actionable security recommendations.
        - __Paid__ - Azure Defender ON, hybrid security, threat protection alerts, vulnerability scanning, just in time (JIT) VM access, etc.
- Azure __Key Vault__ - managed service for securing sensitive information (PaaS)

### Governance features of Azure
- __Role__ - "what can be done?"
- __Security Principal__ - "who can do it?"
- __Scope__ - "Where can it be done?"
- __RBAC__ - authorization system built on Azure Resource Manager (ARM), combination of role definition, security principal and scope.
- Azure __Resource Lock__ - designed to prevent accidental deletion and/or modification (two versions: ReadOnly and CanNotDelete)
- Azure __Resource Tags__ - designed for organization of Azure resources
- Azure __Policy__ - designed to help with resource governance, security, compliance, cost management, etc. 
- Azure __Policy Initiative__ - a group of policy definitions
- Policies focus on resource properties, whereas RBAC focuses on user actions. 
- Azure __Blueprints__ - centralized storage for organizationally approved design patterns, a package of various Azure components (artifacts), such as resource groups, ARM templates, policy assignments and role assignments. 

### Privacy and compliance resources in Azure

#### Resources
- __Microsoft Privacy Statement__ - collection, purpose and usage of personal data
- __Online Services Terms (OST)__ - licensing terms, what can be done and what is forbidden
- __Data Protection Addendum__ - appending to OST describing obligations by both parties with regards to processing of customer and personal data
- __Trust Center__ - web portal for everything related to security, compliance, privacy, policies, best practices, etc.
- __Azure Compliance Documentation__ - web portal focusing on compliance offerings in Azure, similar to the Trust Center but narrowed down

#### Azure Sovereign Regions
- Provide Azure services in markets with very strict regulatory requirements
- __Azure Government__ design for the US government
- __Azure China__ designed for the Chinese market
## 4. Azure Cost Management and SLA's (10-15%)
...
### Planning and managing costs in Azure
- Azure __Reservations__ - purchase Azure services for 1-3 years in advance with significant discounts
- Azure __Spot VMs__ - purchase unused VM capacity for significant discount
- __Hybrid Use Benefit__ - use existing licenses in the cloud
- Azure __Pricing Calculator__ - estimate the cost of Azure services
- Azure __Total Cost of Ownership (TCO) calculator__ - estimate and compare the cost of running workloads on-premise versus in Azure
- Azure __Cost Management__ - centralized service for reporting usage and billing of your existing Azure environment, with self-service cost exploration capabilities
- __Minimizing costs__ in Azure
    - Use Azure Pricing Calculator to choose the low-cost region
    - Utilise Hybrid Use Benefit and Azure Reservations
    - Utilise Azure Cost Management for monitoring, budgets, alerts and recommendations
    - Understand service lifecycle and automate environments
    - Use autoscaling features to your advantage
    - Utilise Azure Monitor to find and scale down underutilized resources
    - Use tags and policies for effective governance
- __SLA's__
    - Free services usually don't have an SLA
    - Adding __dependency__ (Azure website with SQL DB backend) - `Availability(s1) * Availability(s2)`
    - Adding __redundancy__ (two redundanct web apps behind a load balancer) - `(100 - (Unavailability(web1) * Unavailability(web2)))`
