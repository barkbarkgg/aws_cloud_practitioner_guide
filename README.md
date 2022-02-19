Approved for Public Release; Distribution Unlimited. Public Release Case Number 21-4011

©2022 The MITRE Corporation. ALL RIGHTS RESERVED.

The author's affiliation with The MITRE Corporation is provided for identification purposes only, and is not intended to convey or imply MITRE's concurrence with, or support for, the positions, opinions, or viewpoints expressed by the author.

This guide is based on material from [Free Code Camp's Cloud Practitioner Guide] https://www.youtube.com/watch?v=3hLmDS179YE. Big thanks to Free Code Camp!

# Amazon Web Services Cloud Practitioner Cheat Sheet

- Date: December 2021
- Purpose: To help you pass the AWS Cloud Practitioner Exam! This document is a *supplement* to other materials to prepare for the Cloud Practitioner Exam; it is *not* the only material you should look at. The intended use of this document is to look over the day of and leading up to taking the exam, just as a recap of what you have learned. 

## About the exam
- AWS foundational knowledge (i.e. can poke around the AWS console)
- exam focuses on business-centric concepts
- not important for developers, but is important stepping stone towards Solutions Architect Associate
- Pro tip: take the exam in-person, not online
- Numbers:
    - $100 USD
    - 90 minutes
    - 65 questions
    - passing is at least 70%
    - valid for 3 years

| Content      | Percentage |
| ----------- | ----------- |
| Cloud Concepts      | 28       |
| Security   | 24        |
| Technology   | 36        |
| Billing/Pricing   | 12        |

## What is cloud computing?

Cloud computing is the technology of using a network of remote servers to store/manage/process data, instead of a local server or PC.

| On-premises      | Cloud provider |
| ----------- | ----------- |
| You own the servers      | Provider owns the servers       |
| You hire IT staff   | Provider hires IT staff        |
| You pay rent   | Provider pays rent        |
| You take the risk   | Risk is shared        |

### 6 Advantages/Benefits of Cloud Computing

| On-premises      | Cloud provider |
| ----------- | ----------- |
| Trade capital for variable expenses       | No upfront cost <br> Pay-as-you-go       |
| Benefit from enemies of scale   | Sharing cost with over 100,000 other customers        |
| Stop guessing capacity   | Don't have to pay for idle servers        |
| Increase in speed/agility   | Implement your own solution in minutes        |
| No money spent on maintaining servers | AWS manages physical servers <br> Deploy in multiple regions across the globe |

### Types of Cloud Computing

- Software-as-a-service (SaaS) - for customers
  - Office 365, Salesforce, Gmail 
  - product run/managed by service provider
  - don't have to worry about maintenance; just use the product
- Platform-as-a-service (SaaS) - for developers
  - Ansible, Netlify, Heroku
  - don't manage underlying infrastructure; just manage your applications
  - don't worry about operating system or hardware
- Infrastructure-as-a-service (IaaS) - for administrators
  - AWS, GCP, Azure
  - basics of cloud with access to networking/compute/storage
  - don't worry about IT staff/servers

### Cloud Computing Deployment Models
- Cloud - fully on the cloud
  - Dropbox, Squarespace
  - Startups/SaaS
- Hybrid - cloud + on-premises
  - Banks/FinTech/Healthcare
  - Professional Services/Governments/Legacy enterprise
- On-prem - fully on-prem *(private cloud)*
  - Governments/Legacy enterprise
  - Sensitive data
  - Heavily regulated industries

### Common Acronyms (Initialisms)
| Acronym | Service |
|--|--|
|IAM|Identity & Access Management|
|S3|Simple Storage Service
|SWF | Simple Workflow Service
|SNS | Simple Notification Service
|SQS | Simple Queue Service
|SES | Simple Email Service
|SSM | Simple Systems Manager
|RDS | Relational Database Service
|VPC | Virtual Private Cloud
|CFN | CloudFormation
|WAF | Web Application Firewall
|MQ | Amazon Active MQ
|ASG | Auto Scaling Group
| TAM | Technical Account Manager
| ELB | Elastic Load Balancer
| ALB | Application Load Balancer
| NLB | Network Load Balancer
| EC2 | Elastic Cloud Compute
| ECS | Elastic Container Service
| ECR | Elastic Container Repository
| EBS | Elastic Block Storage
| EFS | Elastic File Storage
| EMR | Elastic MapReduce
| EB | Elastic Beanstalk
| ES | ElasticSearch
| EKS | Elastic Kubernetes Service
| MKS | Managed Kafka Service
| IoT | Internet of Things
| RI | Reserved Instances

## AWS Global Infrastructure 
- 22 Regions, 69 Availability Zones (AZs), many Edge locations
### Regions 
- physical location with at least 2 AZs
- compute resources do not span across regions
- physically isolated from each other
- `us-east`
  -  largest AWS region
  -  new services debut here
  -  `us-east-1` - region to view billing info
-  services can vary by region
### Availability Zones (AZs)
- AWS-owned datacenter
- `us-east-1a` - "`a`" suffix indicates which AZ
- multi-AZ cloud deployments allow for failover configurations, increasing resiliency
- less than 10 milliseconds between AZs
### Edge locations 
- datacenter owned by AWS partner with direct connection to AWS
- serve requests for Cloudfront/Route 53 services
- S3 transfer acceleration/API gateway
- low-latency traffic
### GovCloud *(USA only)*
- capable of hosting Controlled Unclassified Information (CUI)
- operated by US Citizens on US soil
- only accessible to US entities
- root account holders must pass screening
- comply w/ FedRAMP, CJIS, EAR, ITAR, DoD Cloud Computing Security Requirements Guide

## Basic AWS Services
- Elastic Compute Cloud (EC2) 
  - rent a more powerful computer (called an *instance*) to run your code on
- Simple Storage Service (S3)
  - each S3 instance is called a *bucket*
  - database for storing files
  - capable of hosting a static website
- CloudFront
  - custom Content Delivery Network (CDN) to Edge locations
- Relational Database Service (RDS)
- Lambda 
  - serverless compute; rather than running code on an instance, code can just sit in the cloud
  - can be event-triggered to run based on events in other AWS services
- Marketplace
  - curated digital catalog with thousands of software products from independent vendors
  - examples include AMIs/CloudFormation Templates/Web ACL/WAF rules *(more on all of these later)*
- Trusted Advisor
  - automated checklist of AWS best practices
  - advises on security, savifs, performance, service limits, and fault tolerance
  - | Objective      | Relation to AWS Services |
    | ----------- | ----------- |
    | Cost Optimization      | Idle load balancers <br> Unassociated Elastic IP addresses       |
    | Performance | High-utilization EC2 instance        |
    | Security  | Multi-factor authentication on root AWS account <br> Identity and Access Management (IAM) Access Key Rotation       |
    | Fault Tolerance   | Amazon RDS Backups        |
    | Service Limits   | Virtual Private Cloud (VPC)        |
- Quick Starts
  - prebuilt templates to deploy popular stacks on AWS in less than a minute
  - reduces many manual steps into just one automatic step
  1. Reference deployment architecture
  2. CloudFormation templates to automate/configure deployment
  3. Deployment Guide

## Organizations

### Organizations & Accounts
- AWS Organizations centrally manage billing, control access, compliance, security, and share resources across AWS accounts within the organization
- root account user - single sign-in account with complete access to AWS services
- organization units - group of AWS accounts within an Organization that can contain Organizations themselves
- service control policies - central control over allowed permissions for all Organization accounts

### AWS Landing Zone
- helps enterprises quickly set up multiple secure accounts in AWS
- Account Vending Machine (AVM) 
  -  provision/configure new AWS accounts via the Service Catalog Template
  -  uses Single Sign-On (SSO) for managing/addressing accounts
-  environments are customizable, allowing customers to implement their own account baselines through Landing Zone configurations/update pipeline

### Resource Groups & Tagging 
- tags - words/phrases as metadata for AWS resources
- resource groups - collection of resources with common tags, can be based on alarm/metrics/configs

## Billing

### Consolidated Billing

- use Cost Explorer service to visualize billing data
- one master account can pay charges incurred by member accounts

### Consolidated Billing Volume Discounts
- *Note: These are hyptothetical numbers, and are not reflective of AWS's actual charge for storage.*
- Suppose Odo has 4 terabytes (4 TB) and Dax has 8 TB.
- | Data Limit      | Cost ($/GB) |
    | ----------- | ----------- |
    | 0-10 TB      | $0.17/GB       |
    | 11-50 TB      | $0.13/GB       |
- Odo: $(4*1024)*0.17 = \$696.32$
- Dax: $(8*1024)*0.17 = \$1392.64$
- Unconsolidated: $696.32+1392.64 = \$2088.96$
- Consolidated: $((10*1024)*0.17)+((2*1024)*0.13) = \$2007.04$

### AWS Budgets

- Cost/Usage/Reservation Budgets
- first two budgets are free, then each budget is $0.02/day with limit of twenty thousand budgets
- track monthly/quarterly/yearly
- EC2/RDS/Redshift/ElastiCache reservation alerts

### Total Ownership
- calculator to estimate cost of moving from on-prem to AWS

### Free Services
- IAM, VPC, Orgs & Consolidated BIlling/Cost Explorer
- Auto Scaling/CloudFormation/Elastic Beanstalk/OpsWorks/Amplify/AppSync/CodeStar
  - free services, but may provision other non-free services in order to function

### AWS Support Plans
| Basic                              | Developer                           | Business                                 | Enterprise                               |
|------------------------------------|-------------------------------------|------------------------------------------|------------------------------------------|
| Email support for accounts/billing | Tech support via email in <24 hours | Tech support via email in <24 hours      | Tech support via email in <24 hours      |
|                                    | No 3rd party support                | Tech support via chat/phone in <24 hours | Tech support via chat/phone in <24 hours |
|                                    | General guidance in <24 hours       | General guidance in <24 hours            | General guidance in <24 hours            |
|                                    | System impaired in <12 hours        | System impaired in <12 hours             | System impaired in <12 hours             |
|                                    |                                     | Production impaired in <4 hours          | Production impaired in <4 hours          |
|                                    |                                     | Emergency outage in <1 hour              | Emergency outage in <1 hour              |
|                                    |                                     |                                          | Personal Concierge                       |
|                                    |                                     |                                          | Technical Account Manager (TAM)          |
| 7 Trusted Advisor Checks           | 7 Trusted Advisor Checks            | All Trusted Advisor Checks               | All Trusted Advisor Checks               |
| Free                               | $20/month                           | $100/month                               | $15000/month                             |

## Elastic Cloud Compute (EC2)
- Sessions Manager - lets you manage your EC2 instances, on-premises instances, and virtual machines (VMs) through an interactive one-click browser-based shell or through the AWS CLI
- Amazon Machine Image (AMI) - template to make an EC2 instance with

### EC2 Pricing Models
| Instance Type      | Notes |
| ----------- | ----------- |
| On-demand      | least commitment <br> pay per hour <br> short/spiky/unpredicatable workloads <br> can't be interrupted <br> suitable for first time apps       |
| Spot      | ≤ 90% off (most savings) <br> request spare capacity in AWS's servers <br> flexible start/end times <br> can be terminated by AWS, but you're not charged <br> if you terminate it early, *you* will be charged <br> suitable for non-critical background news      |
| Reserved Instances (RI)      | best long-term <br> Term × Class Offering × Payment Option <br> - Term - 1 or 3 years <br> - Class Offering <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - Standard - 75% decrease in price, fixed RI attributes <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - Convertible - 54% decrease in pricing, RI can stay or increase in attributes <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; - Scheduled - varied savings; reserved for specific time periods <br> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;     |
| Dedicated Host Instances      | <ul><li>most expensive</li><li>for regulated/server-bound licensing</li><li>multi-tenant and single-tenant per instance</li><li>offered within on-demand/reserved instances</li><li>for enterprises/large organizations</li></ul> |

## Technology Overview
### AWS Networking
- recall Regions, AZ's, and Edge locations
- Virtual Private Cloud (VPC) - logically isolated section of AWS
- Internet gateway - connects AWS to rest of internet
- Route Tables - determine where traffic from subnets is directed towards
- NACLs - subnet-level firewall
- Security Groups - instance-level firewall
- subnets - logical partition of IP network into multiple, smaller network segments
### Database Services
- DynamoDB - NoSQL key/value database, guaranteed read/write rates
- DocumentDB - NoSQL Document database, Mongo compatible
- Relational Database Service (RDS) - "regular" table database, with support for MySQL, PostGres, Maria, Oracle, etc
  - Aurora - fully managed, MySQL (5 times faster), PSQL (3 times faster)
  - Aurora Serverless - fewer features, but only runs when needed
- Neptune - managed graph database
- Redshift - columnar database, petabyte capable
- ElastiCache - caching database (Redis/MemCache)
### Provisioning Services
- provisioning - allocate/create resources/hardware
- Elastic Beanstalk - manages/deploys/scales web apps
- OpsWorks - configuration management using Chef/Puppet
- CloudFormation - infrastructure-as-code (JSON/YAML)
- Quickstart - pre-made packages to launch/configure AWS services
- Marketplace - digital catalog of thousands of independent software products

### Computing
- Elastic Cloud Compute (EC2) - highly configurable server
- Elastic Container Service (ECS) - basically Docker-as-a-service, allows you to use containers as your instance
- Fargate - microservices, pay per task
- Elastic Kubernetes Service (EKS) - deploy containerized apps using Kubernetes
- Lambda - serverless functions, pay for compute time
- Elastic Beanstalk - orchestrates AWS services together
- AWS Batch - plans/schedules/executes batch compute workloads

### Storage
- Simple Storage Service (S3) - file/object storage
- S3 Glacier - low-cost storage for archiving/backup
- Storage Gateway - hybrid cloud storage with local cache
- Elastic Block Storage (EBS) - hard drive in AWS attached to an EC2 instance
- Elastic File Storage (EFS) - file storage for multiple EC2 instances
- Snowball - physically migrate huge amounts of data using a physical  server (50-80 TB)
  - Edge - Snowball, but for 100 TB
  - Snowmobile - shipping container to migrate data from on-prem to AWS (100 PB)

### Business-Centric Services
- Amazon Connect - call center software
- Workspaces - virtual remote desktop in Windows/Linux
- WorkDocs - AWS's version of Sharepoint; just host document
- Chime - platform videoconferencing/online meetings (basically Slack)
- WorkMail - business email/contacts/calendar service
- Pinpoint - targeted marketing campaign system
- Simple Email Service (SES) - cloud-based email delivery
- Quicksight - business intelligence with just a few clicks

### Enterprise Integration
- Direct Connect - gigabit connection from on-prem to AWS
- Virtual Private Network (VPN) - secure connection to AWS
  - site-to-site - on-prem to AWS
  - client - client (laptop) to AWS
- Storage Gateway - hybrid storage service
    - on-prem storage can use AWS cloud storage
    - good for backup/archiving/disaster recover/migration
  - Active Directory - directory-aware workloads/resources can use Active Directory based on Microsoft Active Directory

### Logging Services
- CloudTrail - all API calls between AWS services
  - detect misconfigurations, malicious actors, etc
  - automate responses to cloud events
- CloudWatch - collection of services
  - Logs 
    - performance data about AWS services
    - App and Lambda logs
  - Metrics - time-series of log data
  - Events - trigger events based on condition
    - Ex - take snapshot of EC2 instance per hour
  - Alarms - notifications based on metrics
  - Dashboard - visualize metrics with graphs

## Security
### Shared Responsibility Model
|Entity|Responsibility|
|--|---|
|You *(in the cloud)*|data<br>config<br>in the cloud|
|AWS *(of the cloud)*|Hardware<br>Operation of services<br>Global infrastructure|

|Entity|Responsibilities|
|--|--|
|Customer|Customer/User data<br>Platforms/Apps/IAM<br>OS/Network/Firewall configuration<br>Client-side data encryption and data integrity authentication<br>Server-side encryption<br>Networking traffic protection|
|AWS|AWS Services Software<br>Hardware/AWS Global Infrastructure<br>Region/AZs/Edge locations|

### AWS Compliance Programs
- compliance programs - set of internal policies/procedures to comply with laws/rules/regulations or to uphold business reputation
- HIPAA is 1 example

### AWS Artifact
- free portal for access to AWS's compliance reports
- reports based on global compliance frameworks

### Amazon Inspector
- How we prove EC2 instance is hardened?
- Hardening - eliminating as many security risks as possible
- Inspector runs a security benchmark against an EC2 instance
- Network & Host Assessments can be performed
- Ex - Center for Internet Security's automated assessment has 699 checks 

### Web Application Firewall (WAF)
- protect your web app from common exploits
- can make your own allow/deny rules or use a ruleset from Marketplace
- can be attached to CloudFront/Application Load Balancer

### OWASP Top 10
1. Injection
2. Broken authentication
3. Sensitive data exposure
4. XML external entities
5. Broken access control
6. Security Misconfigs
7. Cross-site scripting
8. Insecure deserialization
9. Using components with known vulnerabilities
10. Insufficient logging/monitoring

### AWS Shield
- AWS Shield - managed Distributed Denial of Service (DDoS) protection service that safeguards applications running on AWS
- DDoS attack - malicious attempt to disrupt normal traffic by flooding a website with traffic
- All customers get AWS Shield Standard
- If using Route53 or CloudFront, you are using Shield Standard
- Protects against Layer 3 (Network)/4 (Transport)/7 (Application) attacks
- Shield Advanced - $3K/year
  - additional protection against larger/sophisticated attacks
  - visibility into attacks
  - 24/7 access to DDoS experts
  - available on: Route53, Cloudfront, ELB, AWS Global Accelerator, Elastic IP

### Penetration Testing
- Penetration testing (PenTesting) - authorized simulated cyberattack on a computer, performed to evaluate system's security

| Permitted Services to PenTest | Prohibited Activities              |   |   |   |
|-------------------------------|------------------------------------|---|---|---|
| EC2, NAT Gateways, ELB        | DNS zone walking via Route53       |   |   |   |
| RDS                           | DDoS                               |   |   |   |
| Cloudfront                    | Port/Protocol/API Request Flooding |   |   |   |
| Aurora                        |                                    |   |   |   |
| API Gateways                  |                                    |   |   |   |
| AWS Lambda                    |                                    |   |   |   |
| Elastic Beanstalk             |                                    |   |   |   |

- Other simulated events require approval from AWS, for which a response can take up to 7 days.

### GuardDuty
- GuardDuty - threat detection service that uses machine learning to continuously monitor for malicious/suspicious activity & unauthorized behavior
- tracks CloudTrail/VPC Flow/DNS logs
- can alert you of findings which can automate incident response via CloudWatch Events or with 3rd-party services

### Key Management Service (KMS)
- multi-tenant Hardware Security Module (HSM)
- many AWS services are integrated to use KMS to encrypt your data with just a checkbox
- Envelope encryption - KMS Master Key encrypts Data Key encrypts data

### Amazon Macie
- Macie - monitors continuously for S3 data access activity
- uses machine learning to analyze CloudTrail logs

### Security Groups via NACLs
| Security Groups             | NACLs                            |   |   |   |
|-----------------------------|----------------------------------|---|---|---|
| firewall and instance level | acts as firewall at subnet level |   |   |   |
| implicitly denies traffic   | 'Allow'/'Deny' rules             |   |   |   |
| creates 'Allow' Rules       

### Virtual Private Network
- lets you establish secure/private tunnel from network/device to AWS
- site-to-site - connect on-premises to AWS VPC
- client - connect users to AWS or on-premises networks

## AWS Well-Architected Framework
From AWS's Well-Architected [documentation][1]:
> The AWS Well-Architected Framework documents a set of foundational questions that allow you to understand if a specific architecture aligns well with cloud best practices.

### Pillars of the Well-Architected Framework
|Name|Description|
|-|-|
|Operational Excellence|The ability to support development and run workloads effectively, gain insight into their operations, and to continuously improve supporting processes and procedures to deliver business value.|
|Security|The security pillar describes how to take advantage of cloud technologies to protect data, systems, and assets in a way that can improve your security posture.|
|Reliability|The reliability pillar encompasses the ability of a workload to perform its intended function correctly and consistently when it’s expected to. This includes the ability to operate and test the workload through its total lifecycle. This paper provides in-depth, best practice guidance for implementing reliable workloads on AWS.|
|Performance Efficiency|The ability to use computing resources efficiently to meet system requirements, and to maintain that efficiency as demand changes and technologies evolve.|
|Cost Optimization|The ability to run systems to deliver business value at the lowest price point.|
|Sustainability|The ability to continually improve sustainability impacts by reducing energy consumption and increasing efficiency across all components of a workload by maximizing the benefits from the provisioned resources and minimizing the total resources required.|

### Terms
|Term|Definition|
|-|-|
|Component|the code, configuration, and AWS Resources that together deliver against a requirement <br> often the unit of technical ownership, and is decoupled from other components|
|Workload|a set of components that together deliver business value <br> usually the technology level at which business and technology leaders communicate|
|Architecture|how components work together in a workload<br>architecture diagrams often focus on how components communicate and interact|
|Milestones|key changes in your architecture as it evolves through the product lifestyle|
|Technology portfolio|collection of workloads that are required for the business to operate|x

### General Design Principles
|Principle|Description|
|-|-|
|Stop guessing your capacity needs.|If you make a poor capacity decision when deploying a workload, you might end up sitting on expensive idle resources or dealing with the performance implications of limited capacity. With cloud computing, these problems can go away. You can use as much or as little capacity as you need, and scale up and down automatically.|
|Test systems at production scale.|In the cloud, you can create a production-scale test environment on demand, complete your testing, and then decommission the resources. Because you only pay for the test environment when it's running, you can simulate your live environment for a fraction of the cost of testing on premises.|
|Automate to make architectural experimentation easier.|Automation allows you to create and replicate your workloads at low cost and avoid the expense of manual effort. You can track changes to your automation, audit the impact, and revert to previous parameters when necessary.|
|Allow for evolutionary architectures.|In a traditional environment, architectural decisions are often implemented as static, onetime events, with a few major versions of a system during its lifetime. As a business and its context continue to evolve, these initial decisions might hinder the system's ability to deliver changing business requirements. In the cloud, the capability to automate and test on demand lowers the risk of impact from design changes. This allows systems to evolve over time so that businesses can take advantage of innovations as a standard practice.|
|Drive architectures using data.|In the cloud, you can collect data on how your architectural choices affect the behavior of your workload. This lets you make fact-based decisions on how to improve your workload. Your cloud infrastructure is code, so you can use that data to inform your architecture choices and improvements over time.|
|Improve through game days.|Test how your architecture and processes perform by regularly scheduling game days to simulate events in production. This will help you understand where improvements can be made and can help develop organizational experience in dealing with events.|

[1]: https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html
