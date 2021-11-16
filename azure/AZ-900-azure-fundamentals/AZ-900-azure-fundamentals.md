# AZ-900 Microsoft Azure Fundamentals

## Cloud Basics
- Benefits of cloud computing:
    1. Cost effective
    2. Scalable
    3. Elastic
    4. Current
    5. Reliable
    6. Global
    7. Secure
- Cloud deployment models
    1. Public cloud
    2. Private cloud (on-premise)
    3. Hybrid cloud
- Serverless computing: run application code without infrastructure hassle

## IaaS, PaaS, SaaS
- __IaaS__: instant computing infrastructure, e.g. VMs, storage and OS.
- __PaaS__: provides environment for building, testing and deploying software applications, e.g. web app, Azure SQL Databases
- __SaaS__: software that is cerntally hosted and managed for the end customer, e.g. Office 365, Skype

## Cloud Compliance
- __CJIS__: Criminal Justice Information Services
- __CSA STAR Certification__: independent third-party assessment of cloud provider's security posture
- __GDPR__: General Data Protection Regulation
- __EU Model clauses__: guarantuees around transfers of personal data outside of the EU
- __HIPAA__: Health Insurance Portability and Accountability Act, US Federal lab that regulats patient Protected Health Information (PHI)
- __ISO/IEC 27018__: International Org. for Standardization (ISO) and International Electrotechnical Commission (ICE) 27018 covers the processing of personal information by clous service providers
- __MTCS Singapore__: Multi-Tier cloud security Singapore
- __SOC 1, 2 & 3__: service organization controls, audits that cover controls for data security
- __NIST CSF__: National Institute of Standards and Technology (NIST) cybersecurity framework (CSF)
- __UK Government G-Cloud__: cloud computing certification for services used by government agencies in the UK

## Scaling
- __Dynamic scalability architecture__: architectural model based on a system of predefined scaling conditions that trigger the dynamic allocation of IT resources from resource pools. 
- __Vertical__ scaling (up/down) vs __horizontal__ scaling (in/out)

## Virtualization
- Azure uses __virtualization__, an abstraction layer, called a hypervisor, which separates tight coupling between hardware (CPU, RAM, GPU, ..) and it's OS. 

## Purchasing options
1. Azure website -> monthly billing
2. Microsoft representative -> monthly billing
3. Microsoft partner (CSP = Cloud Solution Provider) -> partner manages billing

## Licensing options
1. Free-trial
2. Pay-as-you-go
3. Azure in open licensing: buy from a third-party reseller using a 12-month upfront commitment
4. Enterprise Agreement (EA): for big enterprises

## Azure Subscription
- A subscription is a logical container used to provision resources in Azure, when you create an Azure resource like a VM, you identify the subscription it belongs to. Each subscription is a separate entity that can't be merged.
- You can create multiple subscriptions to separate 
    1. __Environments__: can be useful because resource access control happens at the subscription level. 
    2. __Organizational structures__: allows you to manage and control access to reasources that users provision within each subscription
    3. __Billing__
    4. __Subscription limits__

## Billing structure
- Billing Account > Billing Profile > Invoice Section > Azure Subscription

## Support
- __Free__
    - Basic support
    - Community support
- __Paid__
    - __Azure Support Plans__
        - __Developer__: 1-business day response
        - __Standard__: 1-hour response
        - __Professional Direct__: 1-hour response + priority tracking, access to a pool of technical experts
    - __Azure Premier Support__

## Data Centers
Geography > Region (Region Pairs) > Availability Zone > Data Center

- __Geographies__:
    - Defined by geopolitical boundaries or country borders
    - __Fault-tolerant__ (ability to detect and correct all types of problems in environment) to withstand complete region failure 
- __Regions__: 
    - Provide better scalability, redundancy and preserve data residency
    - __Special regions__: for compliance or legal purposes, e.g. Azure Government, a physical and logical network-isolated instances of Azure for US government agencies and partners. 
    - __Region pairs__: pairs are in the same geography, and are at least 300 miles away. 
- __Availability zones__:
    - Physically separate data centers within an Azure region.

