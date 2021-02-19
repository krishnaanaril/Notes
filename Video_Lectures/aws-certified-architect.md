# [AWS Certified Solutions Architect - Associate 2020](https://www.youtube.com/watch?v=Ia-UEYYR44s)

## VPC Follow Along

### NAT

* NAT Gateway is a highly available **AWS managed service** that makes it easy to connect to the Internet from instances within a private subnet in an Amazon Virtual Private Cloud (Amazon VPC). Previously, you needed to launch a NAT instance to enable NAT for instances in a private subnet.
* Instances in the private subnet are back-end servers that don't need to accept incoming traffic from the Internet and therefore **do not have public IP addresses**; however, they can send requests to the Internet using the NAT gateway.
* NAT is expensive. 

### VPC Endpoints

* A VPC endpoint enables you to create a private connection between your VPC and another AWS service without requiring access over the Internet, through a NAT device, a VPN connection, or AWS Direct Connect. Endpoints are virtual devices.
* Elastic IP is a permanent IP for your instance. Refer this SO answer for info: [What is Elastic IP in AWS and why it is useful?](https://stackoverflow.com/a/50306357/1520750)

### VPC Flowlogs

* VPC Flow Logs is a feature that enables you to capture information about the IP traffic going to and from network interfaces in your VPC. Flow log data can be published to Amazon CloudWatch Logs or Amazon S3. 

### VPC Cleanup

* Deleting a VPC also delete these objects associated with this VPC in this region
    * Subnets
    * Security Groups
    * Network ACLs
    * Internet Gateway
    * Egress Only Internet Gateway
    * Route tables
    * Network interface
    * Peering Connections
    * Endpoints

## IAM

* IAM allows management of access of users and resources.
* **Users**: End users who log into the console.
* **Groups**: A group of users with shareable permissions.
* **Roles**: Associate permissions to role and assign this to users or groups.
* **Policies**: Json documents which grant permission to users, groups or roles.
* **Inline policy**: A policy attached directly to a user.
* **Managed policies** are policies managed by AWS and cannot be edited. They are labeled with an orange box.

### Access Keys
* Access keys allow users to interact with aws services **programmatically** via aws cli or aws sdk. You are allowed **two access keys per user**.

### MFA
* The user has to turn on MFA for themselves. Administrator cannot enforce it on users.

## Cognito

* Cognito is a decentralized and managed authentication system.
* SAML - Single Assertion Markup Language for SSO.
* User Pools are user directories used to manage the actions for web and mobile apps such as:
    * Sign up
    * Sign in
    * Account recovery
    * Account confirmation
* Cognito Sync - Sync user data and preferences across devices with one line of code.

## AWS CLI & SDK

* AWS SDK is a set of API libraries that let you integrate AWS services into your applications.
* Credentials get stored in a plain text file (whenever possible use roles instead of AWS credentials)

## Domain Name System

* IPV4 address space is 32 bits, while address space of 128 bits.\
* Domain registrars are authorities who have the ability to assign domain names under one or more top level domains.
* Domains get registered through InterNIC, which is a service provided by the ICANN, and enforces the uniqueness of domain names all over the internet.

### Start of Authority (SOA)

* Every domain must have an SOA record. The SOA is a way for the Domain Admins to provide information about the domain eg: how often it is updated, what is the admin's email address and etc.

* Time to live (TTL) is the length of time that a DNS record gets cached on the resolving server or the users own local machine.

## Route53

* Route53 is a DNS, think GoDaddy or NameCheap but with more synergies with AWS Services.

* Route53 - TrafficFlow: A visual editor lets you create sophisticated routing configurations for your resources using existing routing types.

## EC2

* EC2 is a highly configurable server. Anything and everything on AWS uses EC2 instance underneath.
* EC2 instance types and usages
    * General Purpose
    * Compute Optimized
    * Memory Optimized
    * Accelerated Optimized
    * Storage Optimized
* EC2 Placement groups
    * Cluster
    * Partition
    * Spread
* You can provide an EC2 with UserData which is a script that will be automatically run when launching an EC2 instance.
* EC2 Pricing Model
    * On Demand
    * Spot
    * Reserved
    * Dedicated
* AMIs have an AMI ID. AMIs are region specific. Will have different AMI ID per region.
* Elastic Load Balancer (ELB) is the AWS solution for load balancing traffic, and there are 3 types available:
    1. Application Load Balancer - Http/Https
    2. Network Load Balancer - TCP/UDP
    3. Classic Load Balancer - CLB (Not recommended for use)
* The **X-Forwarded-For (XFF)** header is a command method for identifying the origination IP address of a client connecting to a web server through an HTTP proxy or a load balancer.

## Elastic File System

* It is a scalable, elastic, cloud-native NFS file system

## Elastic Block Store

* It is a virtual hard drive in the cloud.
* IOPS - Input/Output per second.
* SSSD - Solid State Drive
* EBS - Volume Types
    - General Purpose (SSD)
    - Provisioned IOPS (SSD)
    - Throughput Optimized HDD
    - Cold HDD
    - EBS Magnetic

## Cloudfront

* Cloudfront is a content distribution network. It creates cached copies of your website at various edge locations around the world.
* Cloudfront core components
    - Origin
    - Edge Location
    - Distribution
* We use Lambda@Edge functions to override the request and responses.
* The 4 available Lambda@Edge functions
    - Viewer request
    - Origin request
    - Origin response
    - Viewer response

## Relational Database Service (RDS)

* A managed relational database service. Support multiple SQL engines, easy to scale, backup and secure.
* Encryption is handled using the AWS key management service (KMS)

## Aurora

* It's a fully managed Postgres or MySQL compatible database designed by default to scale and fine-tuned to be really fast.

## Redshift

* It's a fully managed Petabyte-size Data Warehouse.
* **Columnar Storage** for database tables is an important factor in optimizing analytic query performance because it drastically reduces the overall disk I/O requirements and reduces the amount of data you need to load from disk.
* Redshift Node Types 
    - Dense Compute (dc)
    - Dense Storage (ds)
* Redshift always attempts to maintain at least 3 copies of your data.
    - Original Copy
    - Replica on the compute nodes
    - Backup copy in S3
* Redshift if Single-AZ

## DynamoDB

* DynamoDB is a NoSQL key/value and document database for internet-scale applications.

## CloudFormation

* A templating language that define AWS resources to be provisioned. Automating the creation of resources via code.
* Cloudformation can be written in two different formats: Json and Yaml.
* **AWS Quick Starts** are a collection of pre-built CloudFormation templates.

## CloudWatch

* It is a collection of monitoring services for logging, reacting and visualizing log data. The monitoring tools are as follows:
    - CloudWatch Logs
    - CloudWatch Metrics
    - CloudWatch Events
    - CloudWatch Alarms
    - CloudWatch Dashboards

## CloudTrail

* It logs API calls between AWS services. Helpful when you need to know **who to blame**.
* Easily identify which users and accounts made the call to AWS eg:
    - **Where** Source IP Address
    - **When** EventTime
    - **Who** User, UserAgent
    - **What** Region, Resource, Action
- Managed Events - Tracks management operations. Turned on by default. Can't be turned off.
- Data Events. Tracks specific operations for specific AWS services. Data Events are high volume logging and will result in additional charges. **Turned off by default**.