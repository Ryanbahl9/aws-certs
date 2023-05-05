
AWS Certified Cloud Practitioner


## Job Roles in the Cloud


- Cloud Architect
  - Builds blueprints for 
- System Administrator
- Security Administrator
- DevOps Administrator

## Map On-Premises Job Roles to Job Roles in the Cloud
| On-Site | AWS |
| --------- | ---------|
| IT Solutions Architect | AWS Cloud Architect |
| Sys Admin & Net Admin & Security Admin & Desktop Admin | AWS Sys Ops and AWS Security Admin |
| Database Admin & Application Dev Admin | AWS DevOps Admin |



# AWS Cloud Practitioner Essentials

## Module 1 introduction

Client Server Model

Key Value: Only pay for what you use

one click could bring more or fewer servers online.

Cloud computing is the on-demand delivery of IT resources over the internet with pay-as-you-go pricing


## Module 2: Compute in the cloud

### Amazon Elastic Compute Cloud
- amazon EC2 for short
- you use EC2 to gain access to virtual servers 
- Multitenancy: Sharing underlying hardware between machines
- You control the networking aspect of EC2
- CaaS - Compute as a service

---
---
| EC2 instance type | Description |
| ---------------------- | ----------- |
| General Purpose |  Good balance of compute, memory and network. Diverse workloads like web servers and code depositories |
| Compute Optimized | Compute intensive tasks like Gaming servers, High performance computing, or scientific modeling. Good for batch Processes |
| Memory Optimized | Memory intensive tasks |
| Accelerated Computing | anything that uses hardware acceleration, like Floating point number calc., Graphics processing, data pattern matching (ML?) |
| Storage Optimized | Databases and stuff |

---
---

| Amazon EC2 pricing | Description |
| ----------------- | ----------- |
| On Demand | You pay for the duration the instance runs for (Per hour or Per Second) |
| Amazon EC2 Savings Plan | Low pricing in exchange for a commitment for a consistent amount of usage measured in dollars per hour ( 1 or 3 year terms )|
| Reserved Instances | Steady state workloads or predictable usage. ( 1 or 3 year term) |
| Spot Instances | ideal for workloads with flexible start and end times, or that can withstand interruptions. They give a 2 minute warning to finish up work and save state |
| Dedicated hosts | Usual for security requirements |

---
---

- Scaling Amazon EC2
  - Scaling up means adding more power to an instance. 
  - Scaling out means adding more instances 
- EC2 auto scaling (You set these 3 settings)
  - Minimum capacity (launch immediately after creation)
  - desired capacity ( defaults to minimum if not set)
  - maximum capacity
- Directing Traffic with elastic Load Balancing
  - Many Load Balancers you can work with and install AWS
  - But AWS has their own called "Elastic Load Balancing"
- Elastic Load Balancing
  - A load balancer acts as a single point of contact for all incoming web traffic to your Auto Scaling group
  - Works with auto scaling groups
  - its a regional construct
  - because it runs at a region level, it is always highly available 
  - automatically scales with however many instances you create.
- Tightly coupled architecture
  - if a single component fails it affects other applications
- Loosely coupled architecture
  - a single failure doesn't affect other applications
- Amazon offers:
  - Amazon Simple Queue Service: SQS
    - Send store and receive messages between software components AT ANY VOLUME
    - Scale automatically
  - Amazon Simple Notification Service: SNS
    - similar to SQS but to send msgs to users
    - pub sub model
    - these subscribers can also be software nodes
  - AWS Lambda Function
    - Serverless option
    - all you do is upload your code, create a trigger
    - when the trigger happens, your code is run and AWS handles the environment 
    - Lambda is best for code that takes less then 15 minutes 
  - Amazon Elastic Container Service
    - Amazon ECS
    - can run on top of EC2
  - Amazon Elastic Kubernetes Service
    - Amazon EKS
    - can run on top of EC2
  - AWS Fargate 
    - Serverless option to run ECS or EKS
  - 
  
## Module 3: Global Infrastructure and reliability 

- AWS Global Infrastructure 
  - High availability and fault tolerance 
- AWS Regions
  -  No data you own goes in or out of any specific region with out you specifically requesting / allowing for that data to be moved
    - E.G. data in the Frankfort region will never leave Frankfort
  - If you don't have requirements, you should choose one close to you
  - not all regions have all features 
  - different regions have different regions
- 4 things to consider when choosing a region
  - Compliance with legal and government requirements
  - Proximity to customers 
  - Available services within a region
  - Pricing
- Availability Zones
  - One Availability Zone is not one data center, but multiple per zone
  - Best practice is to run your EC2 containers in at least 2 AZs, which means deploying them twice
  - Data centers in a zone can be 10s of miles away from each other and still have single digit millisecond latency 
  - Elastic load balancing runs at a Availability zone level
- Amazon Cloudfront 
  - Amazons name for their CDN (Content Delivery Network)
  - Cloudfront uses Edge Locations
- Edge Locations
  - Caches data in far away locations
  - separate from Availability zones
  - you can push data and services from a AZ to an Edge location
  - Also runs amazon's Route 53
- Route 53
  - Amazons DNS and hostname service
  - Route customers to the correct web locations with low latency 
  - Tell data where to go
- AWS Outposts
  - Use aws services in their own buildings 
  - ASW will basically install a mini region in your building
  - is completely owed and operated by aws
  - but isolated within their own building

- Regions contain Availability zones

- How to Provision AWS Resources
  - Simple answer, everything is an API call
  - AWS Management Console
  - AWS CLI
  - AWS Software Dev Kits (SDKs)
  - Various other tools like Cloud Formation
- AWS Management console
  - Is a web portal
  - View bills
  - build test environments 
  - View Monitoring
- CLI is for command line and SDK is for programming languages 
- AWS Elastic Beanstalk
  - Helps you make EC2 environments 
  - Just upload code and configs and Beanstalk and builds out your env for you
  - you can save env configs
- AWS Cloud formation
  - Infrastructure as code
  - you can define a wide variety of AWS resources in a declarative way using JSON or YAML text-based documents called CloudFormation templates.
  - 
  
  
## Module 4: Networking 

- Amazon Virtual Private Cloud
  - Amazon VPC 
  - Allows you to isolate sections of the AWS cloud
  - Deploy resources in a virtual network
  - they can be public facing (access to internet) or private
  - the private and public section are subnet rages in your VPC
  - basically your own private network in aws
- Internet Gateway
  - an internet gateway to the public part of your vpc
- Virtual private gateway 
  - an internet gateway that only allows specific networks to access
  - Allows a vpn gateway from another data center (on-site of in the cloud) to your vpc
- AWS Direct Connect
  - a private fiber connection to your aws vpc
- Network Access control list (Network ACL)
  - Checks packets entering and leaving subnets in VPC
  - Like passport control 
  - Stateless - Has no memory
  - by default allows all in and outbound traffic
- Security Groups
  - Every EC2 instance automatically comes with a security group
  - no packets in or out by default
  - Stateful - They remember packets and allow in returning packets
  - by default allows all outbound traffic and denies all inbound traffic unless its a response from a remembered packet


  
## Module 5: Databases and Storage
- Instance Store volumes
  - a type of block storage that is attached to the host the EC2 is running on. 
  - all volume written to this is erased when an instance is restarted or stopped
  
- Amazon Elastic Block Store (EBS)
  - a place to store files
  - files that exist in blocks on a hard drive 
  - it updates just the pieces that change
  - good for databases, enterprise software, and files systems 
- EBS Volumes
  - virtual hard drives that you can attach to EC2 instances 
  - It will persist between restarts 
  - it supports snapshots of the EBS stores
  - snapshots only records blocks of data that has changed
  - stores data in one availability zone
  
- Amazon Simple Storage service (amazon S3)
  - Data stored as objects 
  - Objects stored in buckets 
  - max object size is 15 tb
  - version objects - always retain previous version of this object
  - supports permissions 
  - you can tier data for how much you're gonna access it
- S3 standard 
  - %99.9999999999 chance that data will remain instant over a year
  - data is in at least 3 different locations / data centers
  - Static website hosting - a collection of static html pages
- S3 standard - infrequent access (S3 Standard - IA)
  - for data that is access less frequently but needs fast access times when needed
- S3 Glacier 
  - for data that is needed to be kept for several years
  - you can implement vault locks
  - can implement Write once / read many (WORM) in a vault lock police
  - 3 options of retrieval 
  - Amazon S3 Glacier Flexible Retrieval
    - can be retrieved with in a few hours
  - Amazon S3 Glacier Deep Archive
    - can be retrieved with in 12 hours
- Amazon S3 life cycle management
  - moves data automatically between tiers
- Amazon Elastic File System
  - A managed file system 
  - Could be shared between multiple users
  - Automatically scales
  - stored across multiple Availability zones
- Amazon relational database service (RDS)
  - Uses SQL
  - 6 available engines
    - Amazon Aurora
    - PostgreSQL
    - MySQL
    - MariaDB
    - Oracle Database
    - Microsoft SQL Server
- Amazon Aurora
  - the most managed db
  -  6 replicates copies across 3 Availability Zones AZ
  - Continuous backup to amazon S3
  - point in time recovery 
  - 1/10 the cost of commercial grade databases
  - 2 available engines
    - PostgreSQL
    - MySQL
- Amazon Dynamo DB
  - A serverless database
  - Nonrelational database
  - Organized into tables with items and attributes 
  - Automatically scales
- Amazon Redshift
  - Datawarehouse service
  - can handel exabytes of data
  - good for business intelligence or analytics 
- Amazon Database Migration Service
  - transferring data from an existing
- Amazon Neptune 
  - Graph database
- Amazon managed blockchain
  - a blockchain solution
- Amazon Quantum Ledger Database (Amazon QLDB)
  - an immutable record system where any record cannot be changed
- Amazon elasticache
  - managed cashing layers
  - redis or memcache D
- Amazon DynamoDB Accelerator (DAX)
  - native caching layer for nonrelational data

  
  
## Module 6: Security
- Shared responsibility model
  - amazon controls security of the cloud and customers control security in the cloud 

- AWS Security responsibilities
  - SOFTWARE
  - COMPUTE
  - REGIONS
  - STORAGE
  - DATABASE
  - HARDWARE/AWS GLOBAL INFRASTRUCTURE
  - AVAILABILITY ZONES
  - NETWORKING
  - EDGE LOCATIONS
- Customer Security responsibilities 
  - CUSTOMER DATA
  - PLATFORM
  - APPLICATIONS
  - IDENTITY AND ACCESS MANAGEMENT OPERATING SYSTEMS
  - NETWORK AND FIREWALL CONFIGURATION
  - NETWORKING TRAFFIC
  - SERVER-SIDE ENCRYPTION
  - PROTECTION

- User Permissions and access
  - Root account is the own of the aws account
  - Should always turn on MFA (multi factor authentication)
  - AWS Identity and Access Management (IAM)
    - new users created are not allowed to access anything by default
    - least privileged principle 
  - AWS 
    - Root user
      - owner and full permissions
    - Users 
      - nothing allowed by default
    - Groups
      - you can set permissions for groups then add users to permissions
    - policies
      - Yaml files that describe permissions that you can then attach to users of groups
    - Rolls
      - have associated permissions
      - Assumed for temporary amounts of time
      - when a user get a roll, it abandons all previous permissions 
      - you can map corporate identities to rolls
- AWS Organizations
  - a central location tyo manages multiple aws accounts
  - supports Organizational units
  - Organizational units
    - Group accounts into organizational units (OUs) to make it easier to manage accounts with similar business or security requirements
  - it has centralized management for all aws accounts
  - consolidated billing
  - Bulk discounts
  - Hierarchical groupings of accounts
  - AWS service and API action access control
  - Service control policies (SCPs)
    - can place restrictions on what aws services can use
    -  can be used on Individual accounts and Organizational units
- Compliance
  - AWS Artifact allows you to access compliance reports done by 3rd parties
    - AWS Artifact agreements
      - For if you need to sign an agreement with aws
      - AWS Artifact Agreements, you can review, accept, and manage agreements for an individual account and for all your accounts in AWS Organizations
    - AWS Artifact report
      - AWS Artifact Reports provide compliance reports from third-party auditors
  - Customer Compliance Center
    - The Customer Compliance Center contains resources to help you learn more about AWS compliance. 
  - aws risk and compliance white paper allows documentation for compliance reports

- Denial-of-service attacks
  - the point of a DDOS attack is to overwhelm the service
  - AWS Shield
    - Automatically protects costumers at no added cost
    - detect malicious traffic in real time and automatically mitigates it
  - AWS Shield with AWS WAF (Web Application Firewall)
    - blocks known bad actors
    - will recognize new attacks as they evolve with machine learning
    - writing custom rules to mitigate complex DDoS attacks.

- Additional security services
  - encryption at rest
    - encryption when data is not being accessed 
  - encryption in transit 
  - AWS Key Management Service(AWS KMS)
    - for managing the encryption keys that can access your data
  - Amazon inspector
    - helps to improve security be running automated test against your infrastructure
    - it helps to check on deviances from best practices 
    - consists of 3 pieces
      - Network Configuration reachability 
      - an amazon agent that can be installed in EC2 instances
      - Security assessment service
  - Amazon Guard Duty
    - threat detection
    - analyzes continuous streams of metadata from stuff like network traffic
    
    
## Module 7: Monitoring and Analytics

- 

