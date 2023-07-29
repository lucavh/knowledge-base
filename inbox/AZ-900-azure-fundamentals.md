# AZ-900 - Azure Fundamentals

## 1. Cloud Concepts

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

## 2. Azure Services

### Architectural Components in Azure

- __Region__ - 1+ data centers connected with low-latency network. Some services are available only in certain regions.
- __Availability Zones__ - 3+ zones connected to protect from data center failures
- __Region Pair__ - each region is paired with another region with at least 300 miles distance so data residency is maintained for disaster recovery
- __Geographies__ - are fault tolerant to protect from region wide failures, each region belongs to one Geography
- __Resource__ - object used to manage services, saved as JSON definition
- __Resource Groups__ - grouping of resources
- __Resource Manager__ - management layer for all resources and resource groups, unified language
- __Management Groups__ - designed to apply standards across deployments in multiple Azure subscriptions.

### Core Products in Azure

#### Virtualization

- Azure __Virtual Machines__ (VMs) - custom software, custom requirements, very specialized, high degree of control (IaaS)
- __VM Scale Sets__ - auto-scaled workloads for VMs (IaaS)
- Azure __Container Instances__ - simple container hosting, easy to start (PaaS)
- Azure __Kubernetes Service__ - highly scalable and customizable container hosting platform (PaaS)
- Azure __App Service__ - designed as enterprise grade web application service
- Azure __Functions__ - micro/nano-services for executing scripts (PaaS/FaaS)
- Azure __Virtual Desktop__: remote desktop service

#### Networking

- Connect cloud and on-premises
- Azure __Virtual Network__ - logically isolated networking components
  - Segmented into one or more subnets
  - Enable communication of resources with eachother, internet and on-prem
  - Scoped to a single region
  - __VNet__ peering allows cross-region communication
- Azure __Traffic Manager__ - designed to distribute TCP/UDP traffic globally (multiregional environments)
- Azure __Load Balancer__ - event traffic distribution for TCP/UDP traffic (in a single Azure region)
- Azure __Front Door__ - optimise global routing of HTTP(s) traffic (multiregional environments)
- Azure __Application Gateway__ - HTTP(s) traffic distribution (in a single Azure region)
- Azure __VPN Gateway__ - specific type of virtual network gateway for on-premises to Azure traffic over the public internet.

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
- Azure __SQL Managed Instance__ - fully fledged SQL Server managed by cloud provider
- Azure __SQL on VM__ - fully fledged SQL server on IaaS
- Azure __SQL DW (Synapse)__ - massively Parallel Processing (MPP) version of SQL server

### Solutions in Azure

#### IoT

- Azure __IoT Central__ - SaaS application for management of IoT devices
- Azure __IoT Hub__ - managed service for bi-directional communication
- Azure __IoT Edge__ - analyze data locally on IoT devices, speed event response and reduce data sent to the cloud (extension of IoT Hub)
- Azure __Sphere__ - secure end-2-end IoT Solutions

#### Big Data

- Azure __Synapse Analytics__ - big data analytics platform (PaaS)
- Azure __HDInsight__ - flexible multi-purpose big data platform (PaaS)
- Azure __Databricks__ - big data collaboration platform (PaaS)

#### Artificial Intelligence

- Azure __Machine Learning__ - cloud-based platform for creating, managing and publishing machine learning models
  - Machine Learning __Workspace__ - top level resource
  - Machine Learning __Studio__ - drag-and-drop web portal
- Azure __Cognitive Service__ - designed for apps that can interact with users using spoken and written language
- Azure __Language Understanding__ (LUIS) - develop an AI app that accepts requests through chat, applies NLP and can be hosted on Azure
- Azure __Bot Service__ - Comunniative AI (chatbots)

#### Serverless

- Azure __Functions__ - serverless coding platform (PaaS/FaaS)
- Azure __Logic Apps__ - serverless enterprise integration service (PaaS)
- Azure __Event Grid__ - fully managed serverless event routing service

#### DevOps

- Azure __DevOps__ - collection of services for building solutions using DevOps practices
- Azure __DevTest Labs__ - service for creation of sandbox environments for developers/testers (PaaS)

#### Monitoring

- Azure __Monitor__ - end-to-end logging solution, the tool to get telemetry from your Azure resources or on-premise environments
- Azure __Application Insights__ - monitor customer-facing web apps for performance anomalies (feature of Azure Monitor)
- Azure __Log Analytics__ - query log data collected by Azure Monitor Logs
- Azure __Time Series Insights__ - analyse time series data in Azure with Azure Time Series Insights (e.g. performance anomalies on IoT devices)

#### Management Tools on Azure

- Azure __Portal__ - self-service web portal
- Azure __PowerShell__ - PowerShell module designed for automation
- Azure __CLI__ - command line interface for Azure
- Azure __Cloud Shell__ - cloud-based scripting environment
- Azure __Advisor__ - personalized consultant service, designed to provide recommendations and best practices for cost, security, reliability, performance and operational excellence.
- Azure __Service Health__ - alerts about outages & planned maintenance

## 3. Security, Privacy, Compliance, and Trust

### Securing network connectivity in Azure

- __Network Security Groups__ (NSG) - designed to filter traffic to (inbound) and from (outbound) Azure resources located in Azure Virtual Network
- __Applocation Security Groups__ (ASG) - feature that allows grouping of virtual machines located in Azure Virtual Network
- Azure __Firewall__ - managed, cloud-based firewall service (PaaS)
- Azure __DDoS Protection__ - designed to detect malicious traffic and block it and prevent additional costs for auto-scaling environments.
- __Defende in depth__ - layering of defensive mechanism (data > app > compute > network > perimiter > identity & access > physcical security)

### Azure Identity services

- __Authentication__ -  process of assertion of identity
- __Authorization__ - process of ensuring that ony authenticated identities get access to the resources for which they have been granted access
- __Access Management__ - process of controlling, verifying, tracking and managing access to authorized users and applications
- Azure __Active Directory__ (AD) - identity and Access Management service in Azure
  - __Identities__ - users, groups, allocations
  - __Access management__ - subscriptions, resource groups, roles, role assignments, authentication and authorization settings, etc.
  - Azure AD __Identity Protection__ - risk based policies to protect Azure identities from external threats (e.g. logging in from anonymous IP, etc.)
  - Azure AD __Conditional Access__ - add policies to allow access only from trusted and compliant devices

### Security tools and features of Azure

- Azure __Security Center__ - centralized and unified infrastructure and platform security management service.
  - Integrated with Azure Advisor
  - Two tiers
    - __Free__ - Azure Defender OFF, continuous assessments, security score, and actionable security recommendations.
    - __Paid__ - Azure Defender ON, hybrid security, threat protection alerts, vulnerability scanning, just in time (JIT) VM access, etc.
- Azure __Key Vault__ - managed service for securing sensitive information (PaaS)
- Azure __Defender for Cloud Apps__ - designed to discover Shadow IT (non-sanctioned apps)
- Azure __Defender for Identity__ - designed to protect on-premises identities from external threats
- Azure __Information Protection (AIP)__ - cloud-based solution that enables organisations to discover, classify, and protect documents and emails by applying labels to content

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
- Azure __Blueprints__ - centralized storage for organizationally approved design patterns, a package of various Azure components (artifacts), such as resource groups, ARM templates, policy assignments and role assignments
- Azure __Automation__ - automate and centrally manage various processes both in Azure and on-premises.

### Privacy and compliance resources in Azure

#### Resources

- __Microsoft Privacy Statement__ - collection, purpose and usage of personal data
- __Online Services Terms (OST)__ - licensing terms, what can be done and what is forbidden
- __Data Protection Addendum__ - appending to OST describing obligations by both parties with regards to processing of customer and personal data
- __Trust Center__ - web portal for everything related to security, compliance, privacy, policies, best practices, etc.
- __Azure Compliance Documentation__ - web portal focusing on compliance offerings in Azure, similar to the Trust Center but narrowed down

#### Azure Sovereign Regions

- Provide Azure services in markets with very strict regulatory requirements
- Azure __Government__ -designed for the US government
- Azure __China__ - designed for the Chinese market, available to legal entities in China
- Azure __Germany__ - available to eligible customers and partners globally doing business in the EU/EFTA

## 4. Azure Cost Management and SLA's

### Planning and managing costs in Azure

- Azure __Reservations__ - purchase Azure services for 1-3 years in advance with significant discounts
- Azure __Spot VMs__ - purchase unused VM capacity for significant discount
- __Hybrid Use Benefit__ - use existing licenses in the cloud
- Azure __Pricing Calculator__ - estimate the cost of Azure services
- Azure __Total Cost of Ownership (TCO) calculator__ - estimate and compare the cost of running workloads on-premise versus in Azure
- Azure __Cost Management__ - centralized service to analyze past cloud usage and expenses, and predict future expenses
- __Minimizing costs__ in Azure
  - Use Azure Pricing Calculator to choose the low-cost region
  - Utilise Hybrid Use Benefit and Azure Reservations
  - Utilise Azure Cost Management for monitoring, budgets, alerts and recommendations
  - Understand service lifecycle and automate environments
  - Use autoscaling features to your advantage
  - Utilise __Azure Monitor__ to find and scale down underutilized resources
  - Use tags and policies for effective governance

### __SLA's__

- Guarantees about uptime and connectivity, varies by service.
- Free services usually don't have an SLA. All free Azure services have a minimum uptime of 99.9% (three 9's).
- Minimal SLA in Azure is 99.9%
- Adding __dependency__ (Azure website with SQL DB backend) - `Availability(s1) * Availability(s2)`
- Adding __redundancy__ (two redundanct web apps behind a load balancer) - `(100 - (Unavailability(web1) * Unavailability(web2)))`
