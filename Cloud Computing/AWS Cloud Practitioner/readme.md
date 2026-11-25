
<img width="394" height="568" alt="image" src="https://github.com/user-attachments/assets/bd77e3b5-3aa5-4510-aa7b-6abe2044e48e" />

**Availability Zone:** two or more data centers.
**Edge Location:** Point of Presence (PoP) in the AWS global network located close to end users—typically in major cities worldwide—that caches content, terminates connections, and runs lightweight edge logic to reduce latency.

**Right sizing Concept:** the process of optimizing cloud resources by ensuring that instance types and sizes match workload performance and capacity requirements at the lowest possible cost. e.g., tolls CloudWatch, Cost Explorer(Explore right sizing recommendation)

**Value Proposition:**
- Trading Fixed Expenses for Variable Expenses: Pay for only what you use, On demand pricing.
- Massive Economies of Scale: AWS can buy hardware and run data centers much more cheaply per unit that a single mid-sized company could never negotiate.
- Eliminating Capacity Guesswork: Dynamically scale resources based on actual demand.
- Increasing Speed and Agility: Instant resource provisioning, Rapid experimentation, Scalability and flexibility, Reduced time-to-market.
- Reducing Data Center Costs
- Global Reach in Minutes: Extensive global infrastructure, Rapid deployment, Low latency, Scalability and flexibility.

Advantages of High Availability:
- Fault tolerance and reliability
- Minimal downtime and business continuity
- Scalability and performance optimization
- Data protection and security
- Cost efficiency
- Data protection and security

Advantages of Elasticity:
- Automatic scaling
- Cost optimization
- Improved performance
- Operational efficiency
- Business agility

**Advantages of Agility:**
- Faster time-to-market
- Flexibility and innovation
- Scalability and adaptability
- Cost efficiency
- Competitive advantage

**AMS Well-Architected Six Pillars:**
Operational Excellence Design Principles:
- Organize teams around business outcomes
- Implement observability for actionable insights
- Safely automate where possible
- Make frequent, smalt, reversible changes
- Refine operations procedures frequently
- Anticipate failure
- Learn from all operational events and metrics
- Use managed services

**Fixed Costs at AWS:**
- Reserved instances
- Dedicated hosting
- Enterprise support plans
- Licensing fees
- Storage commitments

**Variable Costs at AWS**
- On-demand instances
- Data transfer costs
- Storage usage
- Serverless computing
- Auto Scaling Resources

## Cloud Adoption Framework
**Cloud Adoption Resources**
- AWS Professional Services: A global team of AWS experts assist customers.
- AWS Well-Architected Framework: Helps organizations understand pros and cons of cloud adoption
- AWS Prescriptive Guidance: recommendation and best practices
- AWS Migration Acceleration Program (MAP): provides tools, best practices, and financial incentives to help customers migrate to AWS efficiently.
- AWS Training and Certification: offers courses and certifications to help individuals and teams build cloud expertise.
- AWS Cloud Adoption Framework (AWS CAF): boost business outcome through use of AWS. CAF groups capabilities in six perspectives: Business. People, Governance, Platform, security, and Operations. 

**CAF four phases:**
- Envision: Identify and prioritize transformation opportunities in line with your strategic objectives.
- Align: Identify capability gaps and cross organizational dependencies
- Launch: Deliver pilots in production and demonstrate incremental business value.
- Scale: expand pilots and business value to desired scale

Cloud Adoption Strategies
- Catalyze organizational change
- Accelerate value realization
- Mitigate transformation risks
- Enhance workforce capabilities
- Align cloud initiatives with business objectives
- Cultivate a culture of continuous improvement

## Cloud Migration
Best Cloud Migration Strategies (7Rs):
- Retire: Decommissioning application that are no longer needed
- Retain: Keep the applications that are not ready for migration.
- Rehost: moving applications to aws with minimal changes.
- Relocate: moving workloads to AWS without making significant modifications, typically at the hypervisor level.
- Repurchase: replaces existing applications with cloud native alternatives like SAAS
- Replatform: Optimizing applications while migrating to aws
- Refactor or Re-Architect: redesigning applications to fully leverage cloud native capabilities.

Common Data Migration Strategies at AWS:
- Database Migration Service (DMS), which enables continuous replication and supports heterogeneous database migrations

**AWS Migration Services for Licensing Optimization**
- AWS Migration Hub: Centralizes tracking and management of migration projects.
- AWS License Manager: Helps enforce licensing rules and track compliance during migration.
- AWS Snowball DataSync: Assist in migrating large-scale workloads efficiently while maintaining data integrity.

# Server:
A server consists of Compute, Memory, Storage, Database, Network. 

Problems with traditional IT approach
- Pay for the rent for the data center
- Pay for power supply, cooling, maintenance
- Adding and replacing hardware takes time
- Scaling is limited
- Hire 24/7 team to monitor the infrastructure
- How to deal with disasters? (earthquake, power shutdown, fire.. .)

# Cloud Computing:
What is Cloud Computing?
- **Cloud computing is the on-demand delivery of compute power, database storage, applications, and other IT resources.** Through a cloud services platform with pay-as-you-go pricing
- You can provision exactly the right type and size of computing resources you need
- You can access as many resources as you need, almost instantly
- Simple way to access servers, storage, databases and a set of application services
- CSP owns and maintains the network-connected hardware required for these application services, while you provision and use what you need via a web application.

## Private Cloud:
- Cloud services used by a single organization, not exposed to the public. **Single-tenant: Dedicated physical hardware.**
- Complete control
- Security for sensitive applications
- Meet specific business needs
- e.g., rackspace, bank system


## Public Cloud:
- Cloud resources **owned and operated by a third-party cloud service provider** delivered over the Intemet. Multi-tenant: Shared physical hardware.
- e.g., GCP, AWS, Azure

## Hybrid:
- Public + Private + On Premises
- Keep some servers on premises and extend some capabilities to the Cloud.
- Control over sensitive assets in your private infrastructure
- Flexibility and cost-effectiveness of the public cloud.

<img width="1136" height="334" alt="image" src="https://github.com/user-attachments/assets/86ac24fd-c8e9-4f96-9353-99106206cda1" />


**AWS Services to maintain Hybrid Cloud Architecture:**
- AWS Outpost: Delivers fully managed physical AWS hardware racks or servers directly into your on-premises data center so you can run native AWS services locally with consistent APIs and ultra-low latency.
- VMware Cloud on AWS: Allows you to seamlessly migrate, extend, and manage existing on-premises VMware vSphere workloads directly on dedicated AWS cloud infrastructure using the same VMware tools
- AWS Local Zones: Places core AWS compute, storage, and database infrastructure in major metro areas close to end users to deliver single-digit millisecond latency without needing your own physical data center
- AWS Snow Family: Provides rugged, portable physical devices for offline bulk data migration and local edge computing in remote or disconnected environments with limited network connectivity

### Types of Cloud Computing:

**Infrastructure as a Service (IaaS)**
- Provide Building Blocks for cloud IT
- **Provides networking, computers, data storage space**
- Highest level of flexibility
- Easy parallel with traditional on-premises IT and easily adaptable from a on premise to cloud

**Platform as a Service (PaaS)**
- **Removes the need for your organization to manage the underlying infrastructure**
- Focus on the deployment and management of your applications

**Software as a Service (SaaS)**
- Completed product that is run and managed by the service provider
<img width="1653" height="1026" alt="Screenshot 2026-03-20 214919" src="https://github.com/user-attachments/assets/08f2873c-13fc-426e-8e5c-3c10985c8faa" />

<img width="1115" height="279" alt="image" src="https://github.com/user-attachments/assets/7d1da321-70ab-40c2-9718-a5a1f9902364" />
<img width="947" height="610" alt="image" src="https://github.com/user-attachments/assets/65d11996-122b-438d-be90-d1fed7229845" />


## Pricing
- Compute: Pay for compute time
- Storage: Pay for data stored in the Cloud
- Data transfer OUT of the Cloud: is charged, Data transfer IN is free

## Billing and Cost Management:
AWS savings plans offer up to 72% savings compared to on-demand pricing.

**Practicals:**
**Allow Billing and Cost Management for IAM user:**
Billing and Cost Management> Account> IAM user and role access to Billing information (Edit)> Activate IAM Access Update.

**Charges By Service:**
Billing and Cost Management> Bills> Charges By Service

**See forecast wether you are going to pass the free tire:**
Billing and Cost Management> Free Tire

**Budget:** (Billing and Cost Management> Budget)
It is set to get alert whenever you reach threashold budget.


Terms AWS Regions: A region is a **cluster of Datacenters.**

# Scinario Based Questions:

How to Choose Best Region for your task?
Based on Factors: 
1.Compliance of the Country. 
2.Proximity(Latency): if most users will be Indian then region my be India. 
3.Available Service based on Regions(Not all regions have all services). 
4.Pricing varies in each region.
or you can check [Regional Service Table](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/)

Terms Availability zone: Each availability zone (AZ) is **one or more discrete data centers with redundant power,networking, and connectivity.** (each region has minimum 3 and maximum 6 AZ). They're separate from each other, so that they're isolated from disasters.

<img width="1746" height="813" alt="Screenshot 2026-03-20 212330" src="https://github.com/user-attachments/assets/9e2f0c6e-1e57-4d12-a79e-a27b066327f9" />

# Classic Ports to know
- 22 = SSH (Secure Shell) - log into a Linux instance
- 21 = FTP (File Transfer Protocol) — upload files into a file share
- 22 = SFTP (Secure File Transfer Protocol) — upload files using SSH
- 80 = HTTP — access unsecured websites
- 443 = HTTPS — access secured websites
- 3389 = RDP (Remote Desktop Protocol) — log into a Windows instance

# Errors
- If your application is not accessible (time out), then it's a security group issue
- If your application gives a "connection refused" error, then it's an application error or it's not launched

# IAM 
Identity and Access Management, Global service

## IAM Guidelines & Best Practices
- Don't use the root account except for AWS account setup
- One physical user = One AWS user
- Assign users to groups and assign permissions to groups
- Create a strong password policy
- Use and enforce the use of Multi Factor Authentication (MFA)
- Create and use Roles for giving permissions to AWS services
- Use Access Keys for Programmatic Access (CLI / SDK)
- Audit permissions of your account using IAM Credentials Report & IAM Access Advisor
- Never Share IAM users and Access Advisors

## Shared Responsibility Model for IAM
AWS Responsible for:
- Infrastructure (global network security)
- Configuration and vulnerability analysis
- Compliance validation
User Responsible for:
- Users, Groups, Roles, Policies management and monitoring
- Enable MFA on all accounts
- Rotate all your keys often Use IAM tools to apply appropriate permissions
- Analyze access patterns & review ermissions
- Data protection
- Application security
- Identity & access management (IAM)
- Configuration management
- Patch management
- Monitoring & logging

**Best Use:**
**Users and Groups:**
- Root account created by default, shouldn't be used or shared
- Users are people within your organization, and can be grouped
- Groups only contain users, not other groups
- Users don't have to belong to a group, and user can belong to multiple group

# IAM 
**IAM Permissions:**
- Users and Groups can be assigned a JSON documents called policies
- These policies define the permissions of the users
- In AWS you apply the least privilege principle: don't give more permissions than a user needs
**Principal = "Who is allowed to access/use this function?"**

**Multi-Session Support**
It is used to **login to different accounts simultaniously on same window** of a browser.

**IAM Policies**
- Inline Policies: Policies for a Single user.
- Group Policies: Policies for users of a perticular group

<img width="1233" height="593" alt="Screenshot 2026-03-23 225741" src="https://github.com/user-attachments/assets/494f9eab-47e6-4a89-88c7-c4f77c187e3f" />

**IAM Password Policy** (IAM>Account Settings>Edit Password Policy)
- Strong passwords = higher security for your account
- In AWS, you can setup a password policy:
    - Set a minimum password length
    - Require specific character types:
      - including uppercase letters
      - lowercase letters
      - numbers
      - non-alphanumeric characters
    - Allow all IAM users to change their own passwords
    - Require users to change their password after some time (password expiration)
    - Prevent password re-use

**Multi Factor Authentication MFA** (IAM>Security Credentials)
- Users who have root access to your account and can possibly change configurations or delete resources in your AWS account.To be safe you want to protect your Root Accounts and IAM users, Use MFA = password you know + security device you own. Main benefit of MFA: if a password is stolen or hacked. the account is not compromised
- MFA Device Options in AWS: Virtual MFA Device(Authy,Google Authenticator), Universal 2nd Factor (U2F) Security Key, Hardware Key Fob MFA Device.

**How can users access AWS?**
- To access AWS, you have three options:
  - AWS Management Console (protected by password + MFA)
  - AWS Command Line Interface (CLI): protected by access keys
  - AWS Software Developer Kit (SDK) - for code: protected by access keys

**Access Key Generation**
- Access Key ID = username
- Secret Access Key = password

**AWS CLI** A tool that enables you to interact with AWS services using commands in your command-line shell
- Direct access to the public APIs of AWS services
- You can develop scripts to manage your resources
- [AWS CLI](https://github.com/aws/aws-cli)

**AWS SDK** AWS Software Development Kit (AWS SDK)
- Language-specific APIs (set of libraries)
- Enables you to access and manage AWS services programmatically
- Embedded within your application
- AWS CLI is built on AWS SDK for Python
- It Supports
  - JavaScript, Python, PHP, .NET, Ruby, Java, Go, Node.js, C++
  - Mobile SDK (Android, iOS, ...)
  - IoT Device SDK (Embeded C, Arduino, ...)
 


**Create Access Keys:**
  IAM>Users>username>Create Access Key
  
**Configuration of AWS CLI:**
[Install AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
  on CMD type 'aws configure'
  enter credentials

**Commands AWS CLI**
```
aws --version     #To see the version of AWS CLI
aws configure     #To configure AWS CLI
aws iam list-users    #To list all users
```

**AWS CloudShell** is a browser based terminal provided by AWS to manage AWS console

**IAM Roles and Services:**
- Some AWS service will need to perform actions on your behalf
- To do so, we will assign permissions to AWS services with IAM Roles
Common roles:
- EC2 Instance Roles
- Lambda Function Roles
- Roles for CloudFormation

**Creating a Role**
IAM> Roles> Create Role>AWS Service> Select Service> Next> Attach Policy> Next> Name Role> Create Role

**Attaching a Role to a Instance**
Select the instance Actions> Security> Modify> Select the Role and Update IAM role

**IAM Security Tools**
- IAM Credentials Report (account-level)
    - a report that lists all your account's users and the status of their various credentials

- IAM Access Advisor (user-level)
    - Access advisor shows the service permissions granted to a user and when those services were last accessed.
    - You can use this information to revise your policies.

**Creating a Credential Report**

IAM> Credential Report> Download Credential Report>


**Creating IAM Access Advisor**

IAM> users> username> Access Advisor

Summary chart for **AWS IAM**:

| Aspect / Feature | What It Means / Does | Key Detail or Rule |
| --- | --- | --- |
| **Service Scope** | Global identity & access control | Enforces authentication & authorization + **Least Privilege** |
| **Root User** | Account owner identity | Lock down, enable MFA, avoid daily use |
| **IAM Users & Groups** | Users = people/apps; Groups = collections of users | Groups **cannot** be nested inside other groups |
| **IAM Roles** | Temporary credentials for services/apps/federation | No static password/keys; used by EC2, Lambda, CloudFormation |
| **Principal** | Entity making a request or allowed access | User, role, service, or federated identity |
| **Policies (JSON)** | Define `Effect`, `Principal`, `Action`, `Resource`, `Condition` | **Explicit `Deny` always overrides `Allow**` |
| **Policy Types** | **Managed** (AWS/Customer reusable) vs. **Inline** (1-to-1 with identity) | Inline policies are deleted with the user/group/role |
| **Multi-Session Support** | Sign in to multiple AWS identities/accounts at once | Works within the **same browser window** |
| **Password Policy** | Rules for IAM user passwords | Length, character types, expiry, reuse block, self-change |
| **MFA** | Password + 2nd factor | Virtual app (Google Authenticator/Authy), U2F key, or hardware fob |
| **Access Methods** | **Console** (pass + MFA), **CLI** (access keys/STS), **SDK** (code/Boto3), **CloudShell** (browser CLI) | CLI is built on the Python SDK; CloudShell runs in-browser |
| **CLI Setup & Check** | `aws --version` → `aws configure` → `aws iam list-users` | Access Key ID = username; Secret Access Key = password |
| **Role Attachment** | Create role (`IAM` → `Roles`) & attach (`EC2` → `Actions` → `Security` → `Modify IAM role`) | Needs `iam:PassRole` when passing roles to services |
| **Credentials Report** | **Account-level** audit of users & credential status | Shows passwords, MFA status, access key age/rotation |
| **Access Advisor** | **Principal-level** view of granted vs. last-used services | Helps remove unused permissions over time |

# EC2 (Elastic Compute Cloud/Infrastructure as a Service)
This is the **core compute service** on AWS. When you launch an EC2 instance, you follow a specific process:

- Choose an AMI (Amazon Machine Image): This is a **pre-configured template** for your instance, including the **operating system** (e.g., Linux, Windows) and any **pre-installed software**.
- Select an Instance Type: This determines the virtual hardware of your instance, such as the number of vCPUs and the amount of RAM. AWS has a wide variety of instance types optimized for different workloads (e.g., general purpose, compute-optimized, memory-optimized).
- Configure Security and Networking: You must configure a **security group**, which acts as a virtual firewall, defining which inbound and outbound network traffic is allowed. You also manage a key pair for secure SSH access to your Linux instances.

It mainly consists in the capability of :
- Renting virtual machines (EC2)
- Storing data on virtual drives (EBS)
- Distributing load across machines (ELB)
- Scaling the services using an auto-scaling group (ASG)
- you have stopped your EC2 instance and then started it again today. When you do so, **the public IP of your EC2 instance will change**. Therefore, in your command, or Putty configuration, please make sure to edit and save the new public IP.

## EC2 User Data
- It is possible to bootstrap our instances using an EC2 User data script.
- **bootstrapping means launching commands when a machine starts**
- That script is only run once at the instance first start
- EC2 user data is used to automate boot tasks such as:
 - Installing updates
 - Installing software
 - Downloading common files from the internet
 - Anything you can think of The EC2 User Data Script runs with the root user

### User Data
Advanced Detail> User Data (When Creating a new instance)

A Simple Bash Script to run a website on AWS's instance's public IP a static website using User Data
```
#!/bin/bash
# Use this for your user data (script from top to bottom)
# install httpd (Linux 2 version)
yum update -y
yum install -y httpd
systemctl start httpd
systemctl enable httpd
echo "<h1>Hello World from $(hostname -f)</h1>" > /var/www/html/index.html
```
[**EC2 Instance Types**](https://aws.amazon.com/ec2/instance-types/)

[**EC2 Instances Info**](https://instances.vantage.sh/)

**EC2 Naming Conventions**: m5.2xlarge
m: Instance Class
5: Generation (AWS improves them over time)
2xlarge: size within the instance class

- General Purpose-Web Servers/Code Repositories
- Compute Optimized-Compute Intensive Tasks (Starting with C mainly)
- Memory Optimized-Fast Performance to handle Large Data Sets
- Storage Optimized-Storage intensive tasks that require high, sequencial read write access to large data sets on local storage.

## Security Groups: 
EC2> Network Security> Secrity Groups
control how traffic is allowed into or out of our EC2 Instances.
They regulate:
- Access to Ports
- Authorised IP ranges — IPv4 and IPv6
- Control of inbound network (from other to the instance)
- Control of outbound network (from the instance to other)
- Can be attached to multiple instances

###Good to Know Security Groups:
- Locked down to a region /VPC combination
- Does live "outside" the EC2 — if traffic is blocked the EC2 instance won't see it
- It's good to maintain one separate security group for SSH access
- All inbound traffic is blocked by default
- All outbound traffic is authorised by default
- A new security group is created everytime we create a new EC2 Instance
- 0.0.0.0/0 means anywhere 

## AWS Key Management Service:
It is a managed service from Amazon Web Services used to create, store, manage, and control cryptographic keys that protect your data through encryption. KMS manages those keys safely.

## Connecting to Instance SSH (Secure Shell):

### On Linux or Mac
It allows you to control a remote machine all using the command line.

Usage:
- Make sure the instance has SSH access (port 22) enabled on Security Groups.
- Remove if there is any space in the .pem file 
- Open the Terminal on the folder/directory where the .pem file is located
- chmod 0400 <file.pem>
- ssh -i <file.pem > <hostname@Public_IPoftheInstance>

### On Windows >10 (PuTTY)

#### PuTTY Key Generation:
Open PuTTY gen load the .pem file> Save the Private Key> Save Key without Passphrase> Name It and Save.

#### PuTTY login
<hostname@Public_IPoftheInstance>
Name a Session 
SSH> Auth> Credentials> Upload the .ppk file under (Private key file for authentication)
Save the session 

### On Windows <11 
ssh -i .\file.pem <hostname@Public_IPoftheInstance>  
If any permission error then change the permission of the file on properties.

### EC2 Instance Connect:
There is no SSH key option because when we connect to it It's going to upload a temporary SSH key and establish a connection this way.

<img width="1022" height="479" alt="image" src="https://github.com/user-attachments/assets/ccb58285-b15f-4bbc-a91e-739e72dc57a8" />
<img width="1717" height="919" alt="image" src="https://github.com/user-attachments/assets/908d607a-c270-4702-999a-7b1c3be9be06" />
<img width="837" height="487" alt="image" src="https://github.com/user-attachments/assets/68d9d21b-2a50-420b-9d5d-301860c21afc" />
<img width="1581" height="816" alt="image" src="https://github.com/user-attachments/assets/f21b289a-ad6c-44cb-aaea-d58b38de3d85" />

## EBS(Elastic Block Store) Volumes
- A **network drive you can attach to your instances while they run**. **Instances> Storage**
- For a Instance By Default the root EBS volume is deleted and by default any other attached volume is not deleted after the instance is deleted they persist Data even after termination.
- They can only be **mounted to one instances at a time** except io1 and io2 volume types: this is called the EBS Multi-Attach feature. but **two EBS volumes can be attached to one instance simultaniously**. It is also possible to create a EBS Volume and keep it unattached to any instance.
- They are bound to a specific AZ (To move a volume accross zones you need to snapshot it)
- It has a **scalable** capacity

### Creating a Volume and Attach to a Instance:
EBS> Volumes> Create Volume 
Select the volume> Actions> Attach a Volume> Select The Instance> Attach Volume

### EBS Backups:
- Makes a **backup of your EBS volume** a point in time
- Not Necessery to detach volume when doing snapshot but it is recomended
- You can copy snapshots accross AZ or regeions

### EBS Snapshot Features:
- EBS snapshot archive: to store a snapshot at cheaper cost, but takes 24-72 Hours to restore those snapshots
- EBS Recycle Bin:  You can configure recycle bin to restore deleting snapshots

### Creating a Snapshot and Archiving It:
Select> Actions> Create snapshot
Select the snapshot> Actions> Archive the snapshot> 

### Retrieving a Snapshot and Creating a Volume from a snapshot:
Select the snapshot> Right Click> Copy snapshot> Select Regeion> Copy snapshot
Select the snapshot> Actions> Create volume from snapshot

### Recycle Bin Config and Recover:
Snapshots> Recycle Bin> Create Retention Rule> Name it> Select Resource Type (EBS Snapshot)> Create Retention Rule.
Select The resource> Recover Resources

## AMI (Amazon Machine Image)
Amazon Machine Images (AMIs) in Amazon EC2 are **pre-configured, customizable templates** that include the** operating system, software, and settings**. They allow users to quickly launch instances without manual installation, ensuring faster boot time and consistent environments.
- AMIs are built for a specific regeion, later it can be copied accross regions.

### Types AMI EC2 Instances:
- A Public AMI: AWS provided
- Your customized AMI: You make and maintain them yourself
- An AWS Marketplace AMI: An AMI which is made by someone else. (It can also be sold)

### AMI Setup Process(From an EC2 Instance):
1. Start an EC2 instance and customize it.
2. Stop the Instance (for data intefrity)
3. Build an AMI (this will also create EBS snapshot)
  - Right Click the on the Instance> Image and Template> Create Image
  - Name It> Create Image 
4. We can launch instances from other AMI

## EC2 Image Builder:
Automate the creation of VM or container Images.
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/59de08f0-ce15-43b0-8494-1646503a7c31" />


## EC2 Instance Store: 
A type of temporary storage that comes physically attached to the host machine running your EC2 instance.

### Use Case:
⚡ Temporary high-speed storage – For cache and short-term data
🧠 Big data processing – Fast handling of large datasets (Hadoop, Spark)
🔁 Scratch space – Working area for tasks like rendering or compiling
🚀 High I/O workloads – Applications needing very fast read/write speeds


| Feature     | Instance Store   | EBS           |
| ----------- | ---------------- | ------------- |
| Speed       | Very Fast ⚡      | Fast          |
| Persistence | ❌ Temporary      | ✅ Permanent   |
| Use Case    | Cache, temp data | OS, s |

## EFS (Elastic File System):
- It is managed NFS (Network File System) that can be mounted on 100s of EC2 instances.
- It can only be used with Linux EC2 instances and can be attached multiple instanced situated in myltiple Availability Zone.
- Highly Available, Scalable, Expensive, Pay per use, No capacity planning.

| Feature        | EBS                                       | EFS                                       |
| -------------- | ----------------------------------------- | ----------------------------------------- |
| 🧩 Type        | Block storage                             | File storage                              |
| 🔗 Attachment  | Attached to **one EC2 instance** (mostly) | Can be used by **multiple EC2 instances** |
| 📁 Access      | Like a hard disk (you format it)          | Like a shared network folder              |
| ⚡ Performance  | Very high (low latency)                   | Scales automatically                      |
| 📈 Scalability | Manual resizing                           | Auto scaling                              |
| 🌐 Use Case    | OS, s                             | Shared files, web apps                    |
| 💾 Persistence | Permanent                                 | Permanent                                 |

### EFS Infrequent Access (EFS-IA):
- Storage class that is cost optimized for files that are not accessed everyday. upto 92% lower cost compared to other EFS standard.
- If EFS-IA is enabled it will automatically move data to it based on access on last time they were accessed and Lifecycle policy.


## EC2 Shared Responsibility Model:

AWS Manages:
- Infrastructure
- Replication of data for EFS drives and EBS volumes.
- Replacing faulty hardware
- Ensureing their employees can't access your data.

You Manage:
- Setting for Backup/Snapshot procedues.
- Setting up data encryption.
- Responsibility of any data on drives.
- Understanding the risks of using EC2 Instance store.

## Amazon FSx:
Launch 3rd Party high performance file system.
Fully managed service.
Types:
FSx for Lustre (Linux + Cluster= Luster): Fully managed, high performance, scalable, low latency, fast used for High Performance Computing (HPC), used for ML, Analytics, Video Processing...
FSx for Windows file server: Fully managed, highly reliable, shared windows native shared file system, built on Windows file server.It supports all windows native protocols and Active Directory integrated.
FSx for NetApp ONTAP


## EC2 Summary:
- EBS volumes:
    - network drives attached to one EC2 instance at a time
    - Mapped to an Availability Zones
    - Can use EBS Snapshots for backups / transferring EBS volumes across AZ

- AMI: create ready-to-use EC2 instances with our customizations
- EC2 Image Builder: automatically build, test and distribute AMIS
- EC2 Instance Store:
    - High performance hardware disk attached to our EC2 instance
    - Lost if our instance is stopped / terminated

- EFS: network file system, can be attached to 100s of instances in a region
- EFS-IA: cost-optimized storage class for infrequent accessed files
- FSx for Windows: Network File System for Windows servers
- FSx for Lustre: High Performance Computing Linux file system

# Containerization and Orchastration
## ECS (Elastic Container Service)
An AWS-managed container orchestration service that lets you deploy, run, scale, and manage containerized applications without managing your own container control plane. Developers can define and run multi-container applications using Docker Compose, making it easy to transition existing workflows to AWS.

## Fargate
**Launch Docker containers** on AWS, without managing the underlying infrastructure. Serverless offering, AWS just runs containers for you based on the CPU, RAM you need.

## ECR (Elastic Container Registry)
Private Docker Registry on AWS, This is where you store your Docker images so they can be run by ECS or Fargate.
features: image lifecycle management, image vulnerability scanning, Cross Region/Cross account replication, built in encryption, access control. 

<img width="538" height="326" alt="Screenshot 2026-10-28 232457" src="https://github.com/user-attachments/assets/e48886a4-795f-471e-b3a9-5ff24278a8a4" />

## EKS (Elastic Kubernetes Service)
Allows you to **launch managed Kubernetes clusters on AWS**, Kubernetes is an **open-source system for management, deployment, and scaling of containerized apps** (Docker), EKS supports hybrid and multi-cloud deployments.

# Serverless
- Serverless is a new paradigm in which the developers don't have to manage servers anymore, They just deploy code/functions
- Initially... Serverless == FaaS (Function as a Service)
- Serverless was pioneered by AWS Lambda but now also includes anything that's managed: "databases, messaging, storage, etc."
- Serverless does not mean there are no servers. .. it means you just don't manage / provision / see them
- e.g., S3, DynamoDB, Fargate, Lambda

## Lambda
Function as a service, which executes code and respond to events. 

**Features:**
- Virtual functions — no servers to manage!
- Limited by time - short executions
- Event-Driven: functions get invoked by AWS when needed
- Scaling is automated!
- Easy Pricing:
  - Pay per request and compute time
  - Free tier of I AWS Lambda requests and 400,000 GBs of compute time
- Integrated with the whole AWS suite of services
- Integrated with many programming languages (e.g., Node.js(JavaScript), Python, Java, C# (.NET Core) / Powershell, Ruby, Custom Runtime API (community supported, example Rust or Golang))
- Easy monitoring through AWS CloudWatch
- Easy to get more resources per functions (up to 10GB of RAM!)
- Increasing RAM will also improve CPU and network!

**Use case:** 
- Building Serverless APIs
- Real time file processing/ streaming data processing 
- Automative DevOps tasks
- Data transformation in ETL pipelines
- Scheduled CRON jobs
- Mass emailing
- Event-driven notifications
- IoT backend processing

**Pricing**
<img width="762" height="291" alt="image" src="https://github.com/user-attachments/assets/84822098-e801-41e3-be73-a82f8e965124" />

**Lambda Hands on**
```
Visualization of Lambda
Lambda> Functions> go to URL write begin instead off functions> Select a language Run, Next> Next.  

Creating a function
Lambda> Functions> Create function> Use a blueprint, choose Hello world python, Name it, Create function.

Testing a function
Lambda> Functions> function_name> Test, Test.

Triggers
Lambda> Functions> function_name> Triggers, Add trigger> Select the trigger, Add.
```
Notes:
- a function needs an IAM role to write on cloudwatch.
- 

# Networking
## VPC 
### Creating VPC
VPC> Create VPC> VPC only> Name tag> IPv4 CIDR manual input> 
Create Subnet> 
Create EC2 instance with the VPC and Subnet created

### AWS Internet Access Flow for a VPC
Create internet gateway> Name tag> create > attach to VPC> Auto assign public IP> Name the security group>

## Network Security
- AWS-Security Groups
- Azure-NSG
- GCP-Firewall Rules

## NAT
| Feature                             | Custom NAT EC2 | AWS NAT Gateway     |
| ----------------------------------- | -------------- | ------------------- |
| Runs on EC2                         | ✅              | ❌                   |
| You manage OS                       | ✅              | ❌                   |
| You configure NAT                   | ✅              | ❌                   |
| CloudWatch monitoring               | ✅              | ✅                   |
| AWS manages infrastructure          | ❌              | ✅                   |
| Automatic infrastructure redundancy | ❌              | ✅                   |
| You pay EC2 + other resources       | ✅              | NAT Gateway pricing |

## What is ELASTIC IP (EIP): 
A static public IPv4 address in AWS that you can associate with an EC2 instance or other supported resources and keep even when the underlying instance is stopped or restarted.


---

# AWS Databases & Storage Notes

A **database** stores, organizes, and retrieves structured or semi-structured data efficiently.

* **Data Access Flow:** `App` → `Firewall / Security Group` → `Database`
* **Why Databases Beat Raw Storage (S3, EBS, EFS, Instance Store):**
* Structured/indexed storage for fast querying and searching.
* Defined relationships and ACID/transactional guarantees (depending on engine).
* Rapid provisioning, high availability, and vertical/horizontal scaling.
* Automated backups, restores, upgrades, and AWS-managed OS patching.



### Managed vs. Unmanaged (Self-Managed) Databases

* **Unmanaged (DB on EC2):** Full OS/root/SSH access and custom engine control, but you handle installation, OS patching, backups, clustering, and failover manually.
* **Managed (RDS, Aurora, DynamoDB, etc.):** AWS automates provisioning, OS patching, continuous backups with **Point-in-Time Recovery (PITR)**, CloudWatch/Performance Insights monitoring, Read Replicas, Multi-AZ failover, and maintenance windows. *(Trade-off: no SSH access to the underlying host.)*

---

## 1. Relational Databases (SQL / OLTP)

Data is organized into **tables (rows & columns)** with fixed schemas, primary/foreign keys, and SQL queries.

| Cloud Provider | Managed SQL Service |
| --- | --- |
| **AWS** | Amazon RDS, Amazon Aurora |
| **Azure** | Azure SQL Database |
| **GCP** | Cloud SQL, Cloud Spanner |

### Amazon RDS (Relational Database Service)

* **Supported Engines:** MySQL, PostgreSQL, MariaDB, Oracle, Microsoft SQL Server, IBM Db2, and Amazon Aurora.
* **Instance Roles:** **Primary (Master)** handles reads and writes; **Read Replicas (Standby/Slave)** handle read-only traffic.
* **Deployment Topologies:**
* **Multi-AZ (High Availability / DR):** Synchronous replication to a standby instance in another Availability Zone (1 standby for RDS, or 2 readable standbys with Multi-AZ DB Clusters). Automatic failover; no manual read scaling on standard single-standby Multi-AZ.
* **Read Replicas (Read Scalability):** Asynchronous replication (up to **15** replicas) to offload read-heavy traffic; replicas can be promoted to standalone databases.
* **Multi-Region Read Replicas:** Cross-region replication for regional disaster recovery and low-latency local global reads (writes still route to the primary region; incurs cross-region data transfer costs).



### Amazon Aurora & Aurora Serverless

* **Architecture:** AWS-proprietary, cloud-optimized relational engine compatible with **MySQL** (up to 5x faster than standard RDS MySQL) and **PostgreSQL** (up to 3x faster than standard RDS PostgreSQL).
* **Storage & Cost:** Distributed, fault-tolerant storage auto-scales in **10 GB** increments up to **256 TB** across 3 AZs (6 copies). Costs roughly ~20% more than standard RDS, often offset by higher throughput.
* **Aurora Serverless:** Automatically starts up, shuts down, and scales compute capacity per second based on demand—ideal for intermittent, unpredictable, or dev/test workloads with zero capacity planning.
* **Aurora DSQL:** Serverless, distributed SQL database (PostgreSQL-compatible) designed for virtually unlimited horizontal scale and active-active multi-region strong consistency.

### Engine Selection Cheat Sheet

| Workload / Use Case | Recommended Service / Engine |
| --- | --- |
| Simple web application | RDS MySQL / MariaDB |
| Complex queries, geospatial, or vector search (`pgvector`) | RDS PostgreSQL / Aurora PostgreSQL |
| Enterprise legacy / commercial licensing | RDS Oracle / SQL Server / IBM Db2 |
| High-scale, cloud-native relational app | Amazon Aurora |
| Globally distributed active-active SQL | Aurora DSQL |
| Serverless key-value / predictable high-scale | Amazon DynamoDB |

---

## 2. NoSQL Databases (Non-Relational)

Flexible schemas (key-value, document, wide-column, graph) built for massive horizontal scale and low-latency access. *(Cross-cloud equivalents: AWS DynamoDB, Azure Cosmos DB, GCP Firestore / Bigtable.)*

* **Amazon DynamoDB:**
* Serverless, fully managed **Key-Value & Document** database replicated across 3 AZs.
* Delivers consistent **single-digit millisecond latency** at virtually any scale (trillions of rows, millions of requests/sec).
* Secured via **IAM**; offers **Standard** and **Infrequent Access (IA)** table classes.
* **DynamoDB Accelerator (DAX):** Fully managed in-memory cache exclusively for DynamoDB, cutting read latency from milliseconds to **microseconds** (10x improvement). *(Unlike ElastiCache, DAX is tightly coupled to DynamoDB.)*
* **DynamoDB Global Tables:** Multi-region, **active-active** replication allowing local reads and writes in every participating AWS Region.


* **Amazon DocumentDB:** Managed JSON document database (**MongoDB-compatible**). Uses Aurora-style decoupled storage that auto-scales in **10 GB** increments across 3 AZs.
* **Amazon Keyspaces:** Managed, serverless **Apache Cassandra-compatible** wide-column database.
* **Amazon Neptune:** Managed **Graph** database (replicated across 3 AZs, up to 15 read replicas) optimized for highly connected relationships—social networks, fraud detection, recommendation engines, and knowledge graphs.

---

## 3. In-Memory & Caching Services

* **Amazon ElastiCache:** Managed **in-memory caching** supporting **Valkey**, **Redis OSS**, and **Memcached**. Offloads read-heavy database queries and stores ephemeral session state with sub-millisecond latency.
* **Amazon MemoryDB:** Durable, **in-memory primary database** (compatible with Valkey and Redis OSS) that uses a Multi-AZ transactional log so data persists safely across restarts while keeping microsecond read performance.

---

## 4. Analytics, Data Warehousing & Specialized Databases

* **Amazon Redshift & Redshift Serverless:**
* **OLAP** (Online Analytical Processing) petabyte-scale data warehouse using **columnar storage** and **Massively Parallel Processing (MPP)** with a PostgreSQL-based SQL interface.
* **Redshift Serverless** automatically provisions and scales compute for variable BI/reporting workloads without cluster management.


* **Amazon Athena:** Serverless interactive SQL query engine (built on Trino/Presto) that queries data directly in **Amazon S3** (CSV, JSON, ORC, Avro, **Parquet**). Priced at **$5.00 per TB scanned**—use columnar/compressed formats like Parquet and partitioning to cut scan costs.
* **Amazon EMR (Elastic MapReduce):** Managed big-data clusters running **Apache Hadoop, Spark, Hive, HBase, Presto, and Flink** on EC2 (supports Spot Instances & auto-scaling) for large-scale data processing and ML.
* **AWS Glue:** Serverless **ETL** (Extract, Transform, Load) service and central **Glue Data Catalog** used by Athena, Redshift, and EMR to discover schemas.
* **Amazon QuickSight:** Serverless, ML-powered **Business Intelligence (BI)** service for interactive dashboards (per-session pricing) integrating with S3, Athena, RDS, Aurora, and Redshift.
* **Amazon Timestream:** Serverless **time-series database** for IoT telemetry, metrics, and event logs—automatically tiers recent data in memory and historical data to magnetic storage.
* **Amazon Managed Blockchain:** Managed service to join public networks or build private consortium networks using **Hyperledger Fabric** or **Ethereum**.
* **AWS Database Migration Service (DMS):** Migrates databases to AWS with minimal downtime (source stays live during migration). Supports **homogeneous** (e.g., Oracle → Oracle) and **heterogeneous** (e.g., SQL Server → Aurora, using the AWS Schema Conversion Tool) migrations.

---

**5. Quick Reference: Database & Analytics Summary**

| Category | AWS Service(s) |
| --- | --- |
| **Relational (OLTP)** | Amazon RDS, Amazon Aurora, Aurora DSQL |
| **Key-Value & Document (NoSQL)** | Amazon DynamoDB (+ DAX), Amazon DocumentDB, Amazon Keyspaces |
| **Graph & Time-Series** | Amazon Neptune (Graph), Amazon Timestream (Time-Series) |
| **In-Memory Cache / DB** | Amazon ElastiCache (Cache), Amazon MemoryDB (Durable DB) |
| **Data Warehouse (OLAP)** | Amazon Redshift / Redshift Serverless |
| **Big Data & Serverless SQL** | Amazon EMR (Hadoop/Spark), Amazon Athena (SQL on S3) |
| **ETL, BI & Migration** | AWS Glue (ETL/Catalog), Amazon QuickSight (BI), AWS DMS (Migration) |

---

**6. Hands-On CLI / Console Quick Notes**
* **RDS Creation & Snapshots:**
* *Create:* `Aurora and RDS` → `Databases` → `Create database` → choose engine (`MySQL`), template (`Free tier`), credentials, and VPC.
* *Snapshot:* `Databases` → select DB → `Actions` → `Take snapshot` (snapshots can be shared across accounts, copied to other regions, and restored as new DB instances).


* **DynamoDB Table & Items:**
* *Create:* `DynamoDB` → `Tables` → `Create table` → set Table name + **Partition Key** (and optional Sort Key).
* *Insert:* `Tables` → select table → `Explore table items` → `Create item` → add attributes.



---

## 7. Appendix: Amazon S3 (Object Storage) Basics

Unlike hierarchical file systems, **Amazon S3** uses a **flat namespace** where objects sit inside globally uniquely named buckets.

* **Object Anatomy:** **Key** (full object path/name) + **Value/Data** (0 bytes up to **5 TB** per object) + **Metadata** (system & custom key-value tags) + optional **Version ID**.
* **Durability & Availability:** S3 Standard automatically replicates objects across **at least 3 Availability Zones** within a region (99.999999999% — 11 nines of durability).
* **Core Features:**
* **Versioning:** Preserves, retrieves, and restores every version of an object (protects against accidental deletes/overwrites).
* **Access Control:** Managed via **IAM Policies** (user/role permissions) and **S3 Bucket Policies** (resource-based JSON policies); **Block Public Access** is enabled by default.
* **CORS (Cross-Origin Resource Sharing):** Browser security mechanism allowing a web page hosted in one origin/bucket to request resources from another origin/bucket.


* **Static Website Hosting Steps:**
1. Create a bucket and upload `index.html` and static assets.
2. Open `Bucket` → `Properties` → **Static website hosting** → `Enable` → specify `index.html`.
3. Open `Bucket` → `Permissions` → edit **Block public access** and uncheck *Block all public access*.
4. Attach a public read **Bucket Policy** (recommended over legacy ACLs):
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::BUCKET_NAME/*"
    }
  ]
}

```

# AWS CloudWatch (Metrics, Alarms, Dashboards)
**CloudWatch monitors everything in real-time and enables centralized logging, automatically collects metrics from EC2, CPU, Lambda invocations, RDS connections.**

Terms:
- **Monitoring**: **Tracking known metrics (CPU usage, memory, disk space) against preset thresholds**. e.g., CPU at 75% at 10:00 AM
- **Observability**: **Proactive and investigative**. It is a system property built from collected telemetry data—specifically logs, metrics, and traces (the three pillars) e.g., **checking why the metrics went higher**.

**Metrics is measurement over time.** 
Types of Metrics:
- **Standard metrics**: AWS services send automatically (free, 5-min intervals)
- **Custom metrics**: You send application-specific data using API (e.g., user logins)

Namespace: Groups metrics by service (AWS/EC2, AWS/Lambda, AWS/RDS)

Click on a running EC2 Instance> Monitoring, Manage detailed monitoring, Enable Detailed monitoring and Confirm.

View Specific Metrics
CloudWatch> Metrics, All metrics, EC2 to check specific EC2 metrics.

**CloudWatch Alarms** (Automated Alerts)
**Alarm monitors one metric, Triggers action when threshold breached**.

1.Three states: 0K (normal), ALARM (threshold exceeded), INSUFFICIENT_DATA
2.Threshold types: Static (CPU > 80%) or Anomaly detection (Al-based)
3.Actions: Send notification (SNS), Auto-scale resources, Stop/Terminate instance
4.Evaluation: Choose how many periods must breach before alarming


# AWS Lambda
Serverless
Instead of managing servers, operating systems, scaling, or deployment infrastructure, you just upload a function and define what should trigger it.
- No server management
- Auto scaling
- Pay per execution (You don't need to pay even when nobody is using your app)

## When to Use Serverless:
- Event-driven apps
- APIs
- Automation
- File processing

## When not to use Serverless:
- Long running tasks
- Full control needed
- Constant Workloads

## CSP's Serverless Service Names
- AWS-Lambda
- Azure-Functions
- GCP-Cloud Functions

## Terms
- **ECR (Elastic Container Registry)** is a private repository that **stores and manages Docker container images**.Similar to Docker Hub, but managed by AWS.
- **ECS(Elastic Container Service)** is the **orchestration service** that deploys, runs, and scales those containers.
- **FaaS (Function as a Service)** cloud computing model where you **write and deploy small pieces of code called functions**, and the **cloud provider runs them only when triggered by an event**.
- **Ephemeral storage** in AWS Lambda is temporary local /tmp disk space used during function execution for intermediate files and processing, after process is done, temporary storage is deleted.
- **SQS Simple Queue Service** A managed message queuing service that acts as a buffer and event source for serverless functions
- **SNS Simple Notification Service**-One to many
- **EventBridge** executes at a perticular time
- GCP **Pub/Sub** Public means send message, Subscribe means receive message

## AWS Lambda Function Creation Flow (Practical)
Lambda> Create function> Name it> select runtime> Create Function> Configuration> Triggers> Add trigger> Select Trigger, Bucket Name, Event Type, click I acknowledge, Add > Permissions> Resource-based policy statements, Add permissions> Enter Statement ID> Enter Principal> Select Action> Save> Code, Write Code> Deploy> Test 

## Scenario: If you build a WhatsApp notification system, which would you choose and why?

### Why AWS Lambda
- Deep integrations (API Gateway, SQS, SNS, EventBridge)
- Highly scalable & reliable
- Strong IAM security
- Widely used in production systems

#### Architecture:
User Action> API Gateway> Lambda> SQS> Lambda> WhatsApp API

### Why Azure Functions 
- Easy to develop (especially .NET)
- Built-in bindings (less code)
- Great for enterprise/internal tools

#### Architecture:
HTTP Trigger> Function> Queue> Function> WhatsApp API

### Why Google Cloud Functions
- Fast deployment
- Cost-effective
- Strong event-driven model (Pub/Sub)

#### Architeqture:
Event> Pub/Sub> Function> WhatsApp API

GCP Generation 1 (Gen 1) and Generation 2 (Gen 2) refer to two different runtimes/architectures for serverless functions.
| Feature              | Gen 1                            | Gen 2                                     |
| -------------------- | -------------------------------- | ----------------------------------------- |
| Platform             | Original Cloud Functions runtime | Built on Cloud Run                        |
| Scaling              | Basic autoscaling                | Better autoscaling + more control         |
| Concurrency          | 1 request per instance           | Multiple concurrent requests per instance |
| Performance          | Good                             | Faster startup / better throughput        |
| Event Triggers       | Limited set                      | Broader via Eventarc                      |
| Timeout Limits       | Lower                            | Higher                                    |
| CPU / Memory Control | Basic                            | More flexible                             |
| Networking           | Simpler                          | Better VPC/network integration            |
| Traffic Handling     | Less customizable                | More production-grade                     |


# Load Balancer:
servers that forward internet traffic to multiple servers downstream.

## ELB (Elastic Load Balancer) Service
managed load balancer.

### Why ELB
- **auto upgrades, maintenance, high availability**
- **Less Configuration** but more costly compared to load balancer configuration on EC2 Instances.



<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/e56cd2f0-ccd5-42b0-b6d8-0c2f91114e66" />


### Types of load balancer in AWS
- Application Load Balancer (HTTP/HTTPS only) - Layer 7
- Network Load Balancer (TCP/UDP) - Layer 4
- Gateway Load Balancer (GENEVE protocol on IP Packets) - Layer 3
- Classic Load Balancer (retired in 2023) -Layer 4,7

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/457282ea-1a9a-4151-affc-4e9091ec1d98" />

| Load Balancer Type                  | Layer                 | Best For                               | Protocols Supported          | Key Features                                                   |
| ----------------------------------- | --------------------- | -------------------------------------- | ---------------------------- | -------------------------------------------------------------- |
| **Application Load Balancer (ALB)** | Layer 7 (Application) | Web apps, APIs, microservices          | HTTP, HTTPS, WebSocket, gRPC | Path-based routing, host-based routing, SSL termination        |
| **Network Load Balancer (NLB)**     | Layer 4 (Transport)   | High-performance apps, TCP/UDP traffic | TCP, UDP, TLS                | Ultra-low latency, static IP, handles millions of requests/sec |
| **Gateway Load Balancer (GWLB)**    | Layer 3 + 4           | Security appliances, firewalls         | IP packets (GENEVE)          | Routes traffic through virtual firewalls / IDS / IPS           |

Load Balancer Creation Practical:
Create 2 Instances with Amzon Linux> Don't select key pair because we dont need SSH capability we can use EC2 Instance Connect if we ever need to> Select existing security group, launch wizard 1(which will allows HTTP traffic and SSH traffic into our EC2 Instance> Add EC2 User Data in Advanced details
```
#!/bin/bash
# Use this for your user data (script from top to bottom)
# install httpd (Linux 2 version)
yum update -y
yum install -y httpd
systemctl start -y httpd
systemctl start httpd
systemctl enable httpd
echo "<h1>Hello World from $(hostname -f)</h1>" > /var/www/html/index.html
```
Go to Load Balancers> Create Load Balancer> Select load balancer type as Application Load Balancer, Create> Name it> Internet-facing> IPv4> Deploy in all AZ> Create a new security group to only allow HTTP traffic, Name it, Inbound Rules-Type HTTP  Source 0.0.0.0/0(anywhere), create security group> Select the security group created> Listeners and routing, protocol HTTP, Create target group, Instances, Name group, Next> Select both Instances, Include as pending below, create target> Select the target group on Listeners and routing> Create Load Balancer> View Load Balancer

Note: You can check your instance heath by going to EC2> Target groups> Specific Target Group> Health Checks.

Outcome: Now you can access the website using the DNS name of the load balancer each time you refresh the website is switched between those two different instances.

# Auto Scaling Groups (Saves Cost)
- Scale Out (Add EC2 instances) to match an increased load
- Scale in (remove EC2 instances) to match a decreased load
- Automatically register new instances to a load balancer
- Replace unhealthy instances

Types of Scaling Strategies for ASG:
- Manual Scaling
- Dynamic Scaling: Respond to changing demand (e.g., Simple/Step Scaling: when a CloudWatch alarm is triggered (example CPU>70%) then add 2 units, Target Tracking Scaling: I want the average ASG CPU to stay at around 40%, Scheduled Scaling: Anticipate a scaling based on known usage patterns)
- Predictive Scaling: Uses ML to predict future traffic ahead of time based on past records.


## Pratical
EC2> Auto Scaling Groups, Create an Auto Scaling Group> Name It, Create a Launch Template> Name It, Select Instance Configuration, Enter the User Data, Create Launch Template> Select the Launch template, Next> Select the AZ you want the instances to be, and Balanced best effort, Next> Attach to an existing load balancer if load balancer already created, select target groups, Turn on Elastic Load Balancing health checks, Next> Desired capacity 2, max capacity can be hire than desired capacity, Next> Next> Next> Create Auto Scaling Group.

EC2> Target Group> Click on the ASG> Health checks> Edit, (To change the health check timings)

EC2> Load balancer> Copy the DNS Name and open that on browser (To check if the both load balancer is working, It will only work if the User data of these instances are for web hosting)

EC2> Auto Scaling groups> ASG_name> Click on one Instance, Terminate Instance (To see if the ASG is adding the desired number of instances go to Activity of the ASG)

EC2> Auto Scaling groups> ASG_name> Details, Edit (To change the capacity of the ASG)

EC2> Auto Scaling groups, Select the ASG and Delete (To terminate the instances)

## * **Custom VPC:** A private, isolated virtual network you create in the cloud to securely host and organize your resources.
* **Public Subnet:** A designated range of IP addresses within a VPC that has a route directly to the internet.
* **Internet Gateway:** A VPC component that enables communication and traffic flow between resources inside your VPC and the internet.
* **Route Table:** A set of rules (routes) that determines where network traffic from your subnet or gateway is directed.
* **NACL (Network Access Control List):** A stateless subnet-level firewall that controls inbound and outbound traffic using allowed and denied rules.
* **Security Group:** A stateful virtual firewall at the instance or resource level that controls allowed inbound and outbound traffic.




<img width="1117" height="425" alt="image" src="https://github.com/user-attachments/assets/03f5cd9d-79e0-456e-b483-7134a1bba0c0" />

# S3
- allows people to store objects in buckets.
- Buckets are defined at the region level but it's a global service.
-  Naming
  - Shared Global Namespace - has a globally unique name (across all regions all accounts)
  - Account Regional Namespace - allows for "reuse" of the same bucket name across regions

Use Cases:
- Backup and storage
- Disaster Recovery
- Archive
- Hybrid Cloud Storage
- Application Hosting
- Media hosting
- Data lakes and big data analytics
- Software Delivery

Objects:
Every file is the key there is no concepts of directories here. Max object size is 50TB, if uploading more than 5GB must use multi-part upload.
- Objects(files) have a key
- **The key IS the full path to the object**.:
  - s3://my-bucket/my_file.txt
- The key is composed of prefix + object name
- Metadata (list of text key / value pairs — system or user metadata)
- Tags (Unicode key / value pair — up to IO) — useful for security / lifecycle
- Version ID (if versioning is enabled) 

Practical S3 Bucket Creation :
```
Create bucket>
General for Normal use case
Directory for lowlatency use cases>
Global namespace - Must be unique across all AWS accounts and Regions (Worldwide)
Account regional namespace	- Must be unique only within your AWS account and Region(Account + Region)>
Block all Public Access is recommended>
Bucket Versioning Disable
Bucket Versioning Enable (To restore previous version of the objects>
Tags - track storage costs and organize buckets>
Default encryption - Server side encryption is automatically applied to new objects stored in this bucket>
Bucket Key reduces encryption costs as it lowers calls to aws KMS(Key management system)
create>
```

S3 Security:
- User-Based
    - IAM Policies — which API calls should be allowed for a specific user from IAM
- Resource-Based
    - Bucket Policies — bucket wide rules from the S3 console - allows cross account
    - Object Access Control List (ACL) — finer grain (can be disabled)
    - Bucket Access Control List (ACL) — less common (can be disabled)
- Encryption: encrypt objects in Amazon S3 using encryption keys.
- Bucket Settings to Block all Public access.

S3 Bucket Policies:
<img width="458" height="382" alt="image" src="https://github.com/user-attachments/assets/595a9ff1-2135-4ef5-84ec-c515fbfdee90" />

- JSON based policies
    - Resources: buckets and objects
    - Effect: Allow / Deny
    - Actions: Set of API to Allow or Deny
    - Principal: The account or user to apply the policy to
- Use S3 bucket for policy to:
    - Grant public access to the bucket
    - Force objects to be encrypted at upload
    - Grant access to another account (Cross Account)
    - EC2 Instance Roles can connect to a S3 Bucket

Practical Bucket Security:
```
Bucket><Bucket_name>>Permissions> Block public access(bucket settings) Edit>
```
```
Bucket><Bucket_name>>Permissions> Bucket Policy, Edit> Write JSON or use Policy generator>
Select Type of Policy - S3 Bucket Policy
Principal - whom?
Actions - GetObject
Amazon Resource Name (ARN) - Copy and paste the ARN from the Edit bucket policy tab and add "/*" to let all the objects of the bucket to be accessed.
Paste it into your Policy and Save Changes
```

S3 - Static Website Hosting:
- S3 can host static websites and have them accessible on the Internet
- The website URL will be (depending on the region)
- You need to make your bucket public readable otherwise you will get 403 error.


Practical Static Website Hosting:
```
S3 > Buckets> <Bucket_name> > Properties > Static Website Hosting, Edit and Enable, Specify the Index document. Save Changes.
Upload the index file into the bucket.
Go to properties again to see the website URL
```

## Amazon S3 -Versioning
- You can version your files in Amazon S3
- It is enabled at the bucket level
- Same key overwrite will change the "version": l, 2, 3.
- It is best practice to version your buckets
    - Protect against unintended deletes (ability to restore a version)
    - • Easy roll back to previous version
• Notes:
- Any file that is not versioned prior to enabling versioning, will have version ID as "null"
- Suspending versioning does not delete the previous versions

Practical Versioning:
```
Buckets > <Bucket_name> > Properties, Bucket Versioning Edit > Enable (To enable versioning in a bucket

Buckets > <Bucket_Name>, Objects > Show versions (To see object versions)

Buckets > <Bucket_Name>, Objects, select the object versioned > Delete (To roll back to previous version, If bucket versioning is enabled object will provide a delete marker on it when attempted to deleted and if the marker is removed we can get back the object)
```

## S3 Replication (CRR & SRR)

- Must **enable Versioning** in source and destination buckets
- CRR Cross Region Replication
- SRR Same Region Replication
- Buckets can be in different AWS accounts
- Coping is asynchronous
- Must give proper IAM permissions to S3

**Use case**:
- CRR - compliance, lower latency access, replication across accounts
- SRR - log aggregation, live replication between production and test accounts

Practical
```
Create <origin> bucket, Name it, Select Region, Enable Versioning  > Create <target> Bucket, Name it, Select Region(Same or different), Enable Versioning (To create the two bucket)

Management, Create Replication rule > Name it, Status Enabled, Source Bucket Apply to all objects in the bucket, Choose a bucket in this account, Browse Buckets Select the <target_bucket_name>, IAM role create new role, save  (Now you can upload object to the origin bucket and it will be replicated to the target bucket, with same version ID)
```

## S3 Storage Classes
- Amazon S3 Standard-General Purpose
- Amazon S3 Standard-Infrequent Access (IA)
- Amazon S3 One Zone-Infrequent Access
- Amazon S3 Glacier Instant Retrieval
- Amazon S3 Glacier Flexible Retrieval
- Amazon S3 Glacier Deep Archive
- Amazon S3 Intelligent Tiering

Can move between classes manually or using S3 Lifecycle configurations

**Durability: How many times a object is going to be available and not lost by Amazon S3**. It's 11 9s which means (99.999999999% Durability for all storage classes)

**Availability: Measures how readily available a S3 service is**. S3 has 99.99% availability which means not available 53 minutes a year.

**Use Case of each Class:**
- **Infrequent** Access: **data that is less frequently accessed, but requires rapid access when needed**, Lower cost than S3 Standard.
 - Amazon **S3 Infrequent Access (IA)**: 99.9% Availability, Disaster Recovery, Backups etc.
 - Amazon **S3 One Zone-Infrequent Access**: High Durability in a single AZ but data lost when AZ is destroyed. 99.5% Availability
- **Glacier** Storage Classes: **Low-cost** object storage, for archiving/backup, Pay for **price for storage + object retrieval cost**, **Minimum storage duration of 90 days**
 - Amazon S3 Glacier **Instant Retrieval**: **Millisecond Retrieval**, great for **data accessed once a quarter.**
 - Amazon S3 Glacier **Flexible Retrieval**: Expedited (l to 5 minutes), Standard (3 to 5 hours), Bulk (5 to 12 hours) — free 
 - Amazon S3 Glacier **Deep Archive**: Amazon Glacier Deep Archive is the **most cost-effective option if you want to archive data and do not have a retrieval time requirement**. You can retrieve data in 12 or 48 hours.

S3 **Intelligent-Tiering**: 
- Small **monthly monitoring and auto-tiering fee**
- **Moves objects automatically between Access Tiers based on usage**
- There are **no retrieval charges** in S3 Intelligent-Tiering
- Frequent Access tier (automatic): default tier
- Infrequent Access tier (automatic): objects not accessed for 30 days
- Archive Instant Access tier (automatic): objects not accessed for 90 days
- Archive Access tier (optional): configurable from 90 days to 700+ days
- Deep Archive Access tier (optional): config. from 1 80 days to 700+ days

<img width="1165" height="565" alt="image" src="https://github.com/user-attachments/assets/accff1f8-40d0-4401-8afc-2d3362762439" />

<img width="1173" height="577" alt="image" src="https://github.com/user-attachments/assets/aa25ab05-7854-4146-9cff-6c19a352249f" />

**Practical S3 Storage Classes:**
```
Create a Bucket, Name it > Add files for upload, properties, Select the Class > Upload

Buckets > <Bucket_name> > <Object_name>, properties, Edit Storage class > Save Changes (To modify the storage class of an existing object)

Buckets > <Bucket_name>, Management > Create Life Cycle Rule > Name it, Apply to all objects in the bucket, Move current versions of objects between storage classes, Select the class transitions and days after object creation, Add transition to add more (To change storage class based on rules created by you)
```

**S3 Express One Zone Storage Class**: High performance single AZ storage class
- Objects stored in a Directory Bucket (bucket in a single AZ)
- **Handle 100,000s requests per second with single-digit millisecond latency**
- Up to **1Ox better performance than S3 Standard (50% lower costs)**
- High Durability (99.999999999%) and Availability (99.95%)
- **Co-locate your storage and compute resources in the same AZ (reduces latency)**
- Use cases: **latency-sensitive apps, data-intensive apps,Al & ML training, financial modeling, media processing, HPC**... Best integrated with SageMaker Model Training, Athena, EMR, Glue...

## S3 Encryption
- **Server Side** Encryption(Default): Each **uploaded object will be encrypted by amazon S3**
- **Client Side** Encryption: **User encrypts the file before uploading it**.

## IAM Access Analyzer for S3 
**Find resources in your account which is shared with other entities.**
- Ensures that only intended people have access to your S3 buckets
- Example: publicly accessible bucket, bucket shared with other AWS account...
- Evaluates S3 Bucket Policies, S3 ACLs, S3 Access Point Policies

## Shared Responsibility Model for S3

AWS:
- **Infrastructure** (global security, durability, availability, sustain concurrent loss of data in two facilities)
- **Configuration and vulnerability analysis**
- **Compliance validation**

User:
- **S3 Versioning**
- **S3 Bucket Policies**
- **S3 Replication Setup**
- **Logging and Monitoring**
- **S3 Storage Classes**
- **Data encryption** at rest and in transit

## AWS Snowball
AWS Snowball Edge is essentially **a physical AWS storage/compute appliance that AWS ships to your location**. You use it when moving a very large amount of data over the internet would be too slow, unreliable, or impractical.
- Highly-secure, portable devices to collect and process data at the edge, and migrate data into and out of AWS
- Helps migrate up to Petabytes of data

**Edge Computing**: 
- Edge computing means **processing data close to where the data is generated**, instead of always sending raw data to a centralized AWS Region first.
 - A truck on the road, a ship on the sea, a mining station underground... These locations may have limited intemet and no access to computing power
- We setup a Snowball Edge device to do edge computing
 -  Snowball Edge Compute Optimized (dedicated for that use case) & Storage Optimized
 -  Run EC2 Instances or Lambda functions at the edge
- **Use cases: preprocess data, machine learning, transcoding media**

**Practical Snow Family**
```
Snow family > Create new job, Name it, Choose Job type > Next, Select the Snow device, Select Bucket > Next > Next > Shipping Address > Save
```

**Pricing**:
- You **pay for device usage and data transfer out of AWS**
- **Data transfer IN to Amazon S3 is $0.00 per GB**

## S3 Storage Gateway:
**Bridge between on-premises data and clouud data** in S3. Used for **exposing cloud storage data to on-premises you have to use aws storage gateway**.

## S3 Summary
- Buckets vs Objects: Buckets have global unique name, tied to a region
- S3 security: IAM policy, S3 Bucket Policy (public access), S3 Encryption
- S3 Websites: host a static website on Amazon S3
- S3 Versioning: multiple versions for files, prevent accidental deletes
- S3 Replication: same-region or cross-region, must enable versioning
- S3 Storage Classes: Standard, IA, I Z-IA, Intelligent, Glacier (Instant, Flexible, Deep)
- Snowball: import data onto S3 through a physical device, edge computing
- Storage Gateway: hybrid solution to extend on-premises storage to S3


# AWS Governance Concepts
- Identity and access management (IAM)
- Continuous monitoring and logging
- Network and edge security
- Data security and encryption
- Auditing and compliance(AWS Artifact and AWS Config)

## AWS Compliance Services:
- Amazon GuardDuty: Continuously monitors AWS accounts, workloads, and logs for malicious activity and anomalous behavior.   
- AWS Config: Tracks, records, and evaluates AWS resource configurations and changes over time against desired settings.   
- AWS Artifact: Self-service portal for on-demand access to AWS security and compliance reports and legal agreements. 
 - AWS Artifact Reports: Provides downloadable AWS compliance and security documents.
 - AWS Artifact Agreements: Lets you review, accept, and track legal and regulatory agreements for your account or AWS organization.
- AWS Compliance Center: Hub for researching cloud-related regulatory and compliance requirements.
- AWS Security Hub: Aggregates and displays a central view of your security posture and compliance status.
- AWS Audit Manager: Helps continuously audit AWS usage to simplify compliance and risk assessments.

## AWS License Service:
- AWS License Manager: Powerful tool designed to help organizations manage their software licenses across AWS and on-premises environments. It also provide builtin dashboards.

# AWS Security – Short Notes

AWS Security focuses on protecting cloud resources, applications, data, identities, and networks from unauthorized access, attacks, and data breaches.

## 1. AWS Security Monitoring and Threat Detection

### 1.1 AWS Security Hub
**Definition:** AWS Security Hub is a centralized security service that collects security findings from multiple AWS services and provides a single view of your cloud security posture.

**Key Features:**
- Centralized security monitoring.
- Automated security and compliance checks.
- Aggregates findings from services like GuardDuty and Inspector.
- Supports automated remediation.
- Can integrate with SIEM tools like Splunk.

**Remember:** Security Hub = One dashboard for AWS security.

### 1.2 Amazon GuardDuty
**Definition:** Amazon GuardDuty is an intelligent threat detection service that continuously monitors AWS environments to identify suspicious activities and potential security threats.

**Data Sources:**
- CloudTrail logs.
- VPC Flow Logs.
- DNS logs.

**Detects:**
- Compromised credentials.
- Unauthorized cryptocurrency mining.
- Malware activity.
- Unusual login patterns.
- Suspicious network traffic.

**Remember:** GuardDuty = Detects threats and suspicious activities.

### 1.3 Amazon Inspector
**Definition:** Amazon Inspector is an automated vulnerability management service that continuously scans AWS workloads for software vulnerabilities and unintended network exposure.

**Key Features:**
- Scans EC2 instances.
- Scans container images.
- Identifies software vulnerabilities.
- Detects network exposure.

**Remember:** Inspector = Finds vulnerabilities.

### 1.4 AWS Shield
**Definition:** AWS Shield is a managed DDoS protection service that protects AWS applications and resources against Distributed Denial of Service attacks.

**Types:**

| Feature | Shield Standard | Shield Advanced |
|---|---|---|
| Cost | Free | Paid |
| Protection | Basic DDoS protection | Enhanced DDoS protection |
| Monitoring | Automatic | Advanced monitoring |
| Support | Standard AWS support | 24/7 Shield Response Team (SRT) access |
| Integration | AWS services | AWS WAF and other services |

- **Shield Standard:** Automatically protects supported AWS services against common DDoS attacks.
- **Shield Advanced:** Provides enhanced protection, attack visibility, cost protection, and access to specialized response support.

**Remember:** Shield = Protects against DDoS attacks.

---

## 2. AWS Services for Capturing Logs

| AWS Service | Easy Definition |
|---|---|
| AWS CloudTrail | Records API calls and user activities across AWS accounts. |
| Amazon CloudWatch Logs | Collects and monitors logs from AWS resources and applications. |
| AWS X-Ray | Traces requests across distributed applications to identify performance issues. |
| VPC Flow Logs | Captures information about IP traffic flowing through a VPC. |
| AWS Config | Tracks configuration changes and checks resource compliance. |
| AWS Security Hub | Collects security findings from multiple AWS services. |
| Amazon S3 Server Access Logs | Records requests made to objects stored in S3 buckets. |
| AWS Lambda Logs | Captures Lambda function execution logs, typically through CloudWatch Logs. |

**Easy memorization:**
- CloudTrail = Who did what?
- CloudWatch = What is happening?
- X-Ray = Where is the application slow?
- VPC Flow Logs = What network traffic is flowing?
- Config = What configuration changed?
- Security Hub = What security problems exist?
- S3 Logs = Who accessed my bucket?
- Lambda Logs = What happened during function execution?

---

## 3. AWS Audit and Compliance Services

### 3.1 AWS CloudTrail
**Definition:** AWS CloudTrail records user activities and API calls made through the AWS Management Console, CLI, and SDKs.

**Uses:**
- Security auditing.
- Tracking user activities.
- Monitoring API usage.
- Troubleshooting operational issues.
- Compliance monitoring.

**Remember:** CloudTrail = Audit trail of AWS activities.

### 3.2 AWS Config
**Definition:** AWS Config continuously monitors and records changes in AWS resource configurations to help maintain security and compliance.

**Key Features:**
- Configuration tracking.
- Compliance validation.
- Continuous monitoring.
- Automated remediation.
- Audit and reporting.

**Remember:** Config = Tracks configuration changes.

### 3.3 AWS Audit Manager
**Definition:** AWS Audit Manager helps organizations continuously collect and organize evidence to simplify audits and demonstrate compliance.

**Key Features:**
1. Prebuilt and custom compliance frameworks.
2. Automated evidence collection.
3. Centralized evidence management.
4. Compliance monitoring.
5. Audit-ready reports.

**Remember:** Audit Manager = Collects evidence for audits.

---

# 4. AWS Encryption and Key Management

### 4.1 AWS KMS (Key Management Service)
**Definition:** AWS KMS is a managed service that allows you to create, manage, and control cryptographic keys used for encryption and decryption.

**Uses:**
- Encrypting data.
- Managing encryption keys.
- Controlling access to keys.
- Integrating with AWS services.

**Remember:** KMS = Manages encryption keys.

### 4.2 AWS CloudHSM
**Definition:** AWS CloudHSM provides dedicated hardware security modules (HSMs) to generate and manage cryptographic keys with greater control.

**Remember:** CloudHSM = Dedicated hardware for cryptographic keys.

### 4.3 AWS Encryption SDK
**Definition:** AWS Encryption SDK is a client-side encryption library that helps developers encrypt and decrypt data within their applications.

**Remember:** Encryption SDK = Encrypt data before sending it to AWS.

### 4.4 AWS Certificate Manager (ACM)
**Definition:** AWS Certificate Manager manages(provisioning, managing, and deploying) SSL/TLS certificates to secure network communication.

**Remember:** ACM = Manages SSL/TLS certificates.

### 4.5 AWS Secrets Manager
**Definition:** AWS Secrets Manager securely stores, retrieves, and automatically rotates sensitive information such as database passwords and API keys.

**Remember:** Secrets Manager = Protects passwords and secrets.

### Encryption Services – Quick Comparison

| Service | Main Purpose |
|---|---|
| AWS KMS | Manage encryption keys. |
| AWS CloudHSM | Dedicated hardware-based key management. |
| AWS Encryption SDK | Client-side data encryption. |
| AWS Certificate Manager | Manage SSL/TLS certificates. |
| AWS Secrets Manager | Store and rotate passwords and secrets. |
| SSE-C | S3 server-side encryption using customer-provided encryption keys. |

---

# 5. AWS Identity and Access Management (IAM)

### 5.1 AWS IAM
**Definition:** AWS Identity and Access Management (IAM) controls who can access AWS resources and what actions they can perform.

**Remember:** IAM = Who can access what?

### 5.2 IAM Users
**Definition:** An IAM user is an identity created within an AWS account for a person or application that requires AWS access.

**Example:** Creating an IAM user for a developer.

### 5.3 IAM Groups
**Definition:** IAM groups allow administrators to organize users based on their roles and assign permissions to multiple users together.

**Common Groups:**

| Group | Permission |
|---|---|
| Administrator | Full AWS access. |
| Power Users | Broad AWS access, but generally no IAM administration. |
| ReadOnly/Auditor | Can view resources but cannot modify them. |

**Remember:** Groups = Manage permissions for multiple users.

### 5.4 IAM Roles
**Definition:** An IAM role is an identity with specific permissions that trusted users, applications, or AWS services can temporarily assume.

**Example:** An EC2 instance assumes an IAM role to access an S3 bucket without storing permanent access keys.

**Remember:** Role = Temporary AWS permissions.

### 5.5 IAM Policies
**Definition:** IAM policies are JSON documents that define which AWS actions are allowed or denied.

**Example:** Allowing a user to read objects from an S3 bucket but not delete them.

**Remember:** Policy = Rules of access.

### 5.6 IAM Access Analyzer
**Definition:** IAM Access Analyzer identifies unintended resource sharing and unused permissions to help maintain least-privilege access.

**Remember:** Access Analyzer = Finds unnecessary access.

### 5.7 IAM Identity Center (AWS SSO)
**Definition:** IAM Identity Center provides centralized single sign-on (SSO) access to multiple AWS accounts and business applications.

**Remember:** Identity Center = One login for multiple AWS accounts and applications.

### IAM vs IAM Identity Center

| IAM | IAM Identity Center |
|---|---|
| Manages identities and permissions within AWS accounts. | Centrally manages workforce access across multiple AWS accounts. |
| Supports IAM users, groups, and roles. | Supports centralized SSO. |
| Commonly used for AWS resource access management. | Commonly used for employee access management. |

---

# 6. AWS Authentication and Access Security

### 6.1 AWS Root Account
**Definition:** The AWS root user is the original identity created when an AWS account is registered and has complete access to that account.

**Important Root Account Activities:**
- Changing account settings.
- Selecting or changing support plans.
- Closing an AWS account.
- Modifying root user MFA.
- Restoring certain IAM permissions.
- Managing consolidated billing.
- Performing certain account-level operations.

**Security Best Practices:**
- Enable MFA.
- Never use the root account for daily activities.
- Avoid creating root access keys.
- Use IAM users or roles for regular administration.

**Remember:** Root Account = Complete control over an AWS account.

### 6.2 Password Policy
**Definition:** An IAM password policy defines rules that users must follow when creating or changing their passwords.

**Common Rules:**
- Minimum password length.
- Uppercase and lowercase letters.
- Numbers and special characters.
- Password expiration, if configured.
- Password reuse restrictions.

**Remember:** Password Policy = Rules for strong passwords.

### 6.3 Security Token Service (STS)
**Definition:** AWS Security Token Service (STS) generates temporary security credentials that allow users and applications to access AWS resources.

**Remember:** STS = Temporary security credentials.

### 6.4 AWS Access Keys
**Definition:** AWS Access Keys are credentials used to authenticate programmatic requests to AWS through the CLI, SDKs, and APIs.

**Two Components:**
1. Access Key ID – Identifies the access key.
2. Secret Access Key – Secret used to sign requests.

**Remember:** Access Keys = Credentials for programmatic AWS access.

### 6.5 AWS Multi-Factor Authentication (MFA)
**Definition:** MFA adds an additional authentication layer by requiring users to provide another verification method besides their password.

**AWS MFA Options:**

| Type | Easy Explanation |
|---|---|
| Passkeys | Passwordless authentication using biometrics or device PIN. |
| Security Keys | Physical FIDO-compatible authentication devices. |
| Virtual Authenticator Apps | Mobile apps generating temporary OTP codes. |
| Hardware Tokens | Physical devices generating OTP codes. |

**Remember:** MFA = Password + Additional verification.

### 6.6 Passkeys
**Definition:** Passkeys are passwordless authentication credentials based on FIDO standards that use biometrics or a device PIN for secure sign-in.

**Key Benefits:**
- Phishing-resistant authentication.
- No traditional password required.
- Uses fingerprint, face recognition, or device PIN.

**Remember:** Passkeys = Secure login without passwords.

---

# 7. AWS Access Management Concepts

### 7.1 Identity-Based Policies
**Definition:** Identity-based policies are attached to IAM users, groups, or roles to define what actions they can perform on AWS resources.

**Example:** Allowing an IAM user to access an S3 bucket.

### 7.2 Resource-Based Policies
**Definition:** Resource-based policies are attached directly to AWS resources and define who can access those resources and what actions they can perform.

**Example:** An S3 bucket policy allowing another AWS account to access the bucket.

**Difference:**

| Identity-Based Policy | Resource-Based Policy |
|---|---|
| Attached to IAM identities. | Attached to AWS resources. |
| Defines what an identity can do. | Defines who can access a resource. |
| Example: IAM user policy. | Example: S3 bucket policy. |

### 7.3 Cross-Account Roles
**Definition:** Cross-account roles allow users or services from one AWS account to access resources in another AWS account without creating separate IAM users in both accounts.

**Remember:** Cross-account role = Access another AWS account securely.

### 7.4 Least Privilege Principle
**Definition:** The principle of least privilege means giving users and services only the minimum permissions required to perform their tasks.

**Example:** A developer who only needs to view S3 files should not receive permission to delete buckets.

**Remember:** Least Privilege = Only the permissions you need.

### 7.5 AWS CloudFormation
**Definition:** AWS CloudFormation is an Infrastructure as Code (IaC) service that creates and manages AWS resources using using JSON or YAML templates.

**Security Benefits:**
- Defines infrastructure consistently.
- Supports controlled resource creation.
- Works with IAM permissions to restrict deployment activities.
- Helps maintain standardized security configurations.

**Remember:** CloudFormation = Create AWS infrastructure using code.

---

# 8. AWS Systems Manager and Configuration Management

### 8.1 AWS Systems Manager (SSM)
**Definition:** AWS Systems Manager is a centralized service for managing, monitoring, and automating operational tasks across AWS, on-premises, and supported multicloud resources.

**Uses:**
- Remote server management.
- Patch management.
- Automation.
- Monitoring system configurations.
- Managing EC2 instances.

**Remember:** Systems Manager = Manage servers from one place.

### 8.2 Systems Manager Parameter Store
**Definition:** Parameter Store is a centralized service for storing configuration data and secrets in a hierarchical structure.

**Features:**
- Stores configuration values.
- Supports plain-text and encrypted parameters.
- Integrates with AWS KMS.
- Supports secure retrieval of parameters.

**Remember:** Parameter Store = Stores configuration values and secrets.

### Parameter Store vs Secrets Manager

| Parameter Store | Secrets Manager |
|---|---|
| Stores configuration data and secrets. | Primarily stores sensitive secrets. |
| Supports plain-text and encrypted values. | Provides managed secret storage. |
| Does not provide built-in automatic secret rotation for all parameters. | Supports automatic secret rotation through configured integrations. |
| Offers Standard and Advanced parameter tiers. | Designed for sensitive credential lifecycle management. |

---

# 9. Important AWS Security Concepts – Last-Minute Revision

| AWS Service / Concept | One-Line Definition |
|---|---|
| Security Hub | Centralized security findings and posture management. |
| GuardDuty | Detects suspicious activities and threats. |
| Inspector | Scans for vulnerabilities. |
| Shield | Protects against DDoS attacks. |
| CloudTrail | Records API calls and user activities. |
| CloudWatch | Monitors logs and metrics. |
| X-Ray | Traces application requests. |
| VPC Flow Logs | Records network traffic information. |
| AWS Config | Tracks resource configuration changes. |
| Audit Manager | Collects evidence for compliance audits. |
| KMS | Manages encryption keys. |
| CloudHSM | Provides dedicated hardware security modules. |
| Encryption SDK | Performs client-side encryption. |
| Certificate Manager | Manages SSL/TLS certificates. |
| Secrets Manager | Stores and rotates sensitive credentials. |
| IAM | Controls access to AWS resources. |
| IAM User | Identity for a person or application. |
| IAM Group | Organizes users and permissions. |
| IAM Role | Provides temporary permissions. |
| IAM Policy | Defines access permissions. |
| Access Analyzer | Identifies unintended access. |
| Identity Center | Provides centralized SSO. |
| STS | Generates temporary credentials. |
| MFA | Adds another authentication layer. |
| Passkeys | Provides passwordless authentication. |
| Access Keys | Authenticate programmatic AWS requests. |
| Systems Manager | Manages and automates AWS operations. |
| Parameter Store | Stores configuration values and secrets. |
| CloudFormation | Creates infrastructure using code. |
| Root Account | Has complete account-level access. |

## 10. Five Important Security Principles to Remember

1. **Least Privilege:** Give only the minimum permissions required.
2. **Defense in Depth:** Use multiple layers of security instead of relying on one.
3. **Encryption at Rest:** Protect stored data using encryption.
4. **Encryption in Transit:** Protect data while travelling across networks using TLS.
5. **Continuous Monitoring:** Continuously monitor AWS resources to detect suspicious activities.

---

### Quick Memory Trick: AWS Security Services

Remember these five groups:

| Group | Services | Purpose |
|---|---|---|
| Threat Detection | GuardDuty, Inspector, Security Hub | Detect and investigate threats. |
| Protection | Shield, WAF | Protect applications and networks. |
| Monitoring & Logging | CloudTrail, CloudWatch, X-Ray, VPC Flow Logs | Record and monitor activities. |
| Identity & Access | IAM, STS, Identity Center, MFA | Control who gets access. |
| Encryption & Secrets | KMS, CloudHSM, Secrets Manager, ACM | Protect data and credentials. |

**Exam tip:** Pay special attention to the differences between:
- GuardDuty vs Inspector vs Security Hub.
- CloudTrail vs CloudWatch.
- IAM User vs IAM Role.
- IAM vs IAM Identity Center.
- Identity-Based vs Resource-Based Policies.
- KMS vs CloudHSM.
- Parameter Store vs Secrets Manager.
- Shield Standard vs Shield Advanced.

These comparisons help you understand the services rather than simply memorizing their definitions.


Here is a clean, study-ready note organizing your AWS firewall concepts along with key architectural details and distinctions.

---

## AWS Firewall & Network Security Notes

AWS uses a **defense-in-depth** model rather than a single firewall product, placing controls across network layers, subnets, instances, and web applications.

### 1. Network Access Control Lists (NACLs)

* **Scope & Layer:** Subnet-level firewall inside a VPC operating at **Layers 3/4** (IPs, ports, protocols).
* **State & Rules:** **Stateless** (return traffic must be explicitly permitted) and supports both **Allow** and **Deny** rules.
* **Evaluation Order:** Rules are evaluated in ascending numerical order (lowest rule number first), stopping at the **first match**. A `*` (catch-all) rule at the end denies unmatched traffic.
* **Association:** Each subnet maps to **one and only one** NACL, though multiple subnets can share the same NACL. Default NACLs allow all traffic; custom NACLs deny all traffic until rules are added.

### 2. Security Groups (SGs)

* **Scope & Layer:** Instance/resource-level virtual firewall operating at **Layers 3/4**, enforced at the hypervisor level on Elastic Network Interfaces (`eth0` and additional ENIs).
* **State & Rules:** **Stateful** (allowed inbound/outbound connection state is tracked automatically so return traffic is permitted) and **"Allow only"**—there are **no explicit deny rules**.
* **Evaluation Order:** All applicable rules are evaluated before deciding whether to allow traffic.
* **Key Advantage:** Can reference other **Security Group IDs** as sources/destinations (ideal for dynamic auto-scaling tiers like web → app → database) rather than static IP CIDRs.

### 3. AWS Network Firewall

* **Scope & Layer:** Managed **VPC-level** stateful network firewall and **Intrusion Detection and Prevention System (IDS/IPS)** deployed via firewall endpoints in dedicated subnets.
* **Key Capabilities:**
* Supports both **stateless** and **stateful** rule groups (including Suricata-compatible IPS rules).
* Performs **domain/FQDN/SNI filtering** and **TLS inspection** (decrypting and re-encrypting HTTPS traffic for deeper inspection).
* Useful for filtering east-west traffic between VPCs/subnets and north-south egress/ingress traffic.



### 4. AWS WAF (Web Application Firewall)

* **Scope & Layer:** Protects **Layer 7 (HTTP/HTTPS)** web traffic on resources such as **Application Load Balancers (ALBs)**, **Amazon CloudFront**, **API Gateway**, and **AWS AppSync**.
* **What It Inspects:** Deep packet/request inspection to mitigate **SQL injection (SQLi)**, **cross-site scripting (XSS)**, request smuggling/forgeries, bots, and volumetric/HTTP flood patterns (often paired with **AWS Shield** for DDoS protection).
* **Matching Conditions:** IPv4/IPv6 addresses, originating countries (geo-match), headers/cookies/query strings/body, string or regex patterns, request size constraints, and managed rule groups (including SQLi and XSS rules).

### 5. AWS Firewall Manager

* **Role:** Central policy management service built on **AWS Organizations** that enforces firewall rules consistently across multiple AWS accounts and VPCs.
* **What It Manages:** Common Security Group baselines, **AWS WAF** policies, **AWS Network Firewall** policies, **AWS Shield Advanced** protections, and VPC security controls from a delegated administrator account.

---

#### Quick Comparison

| Service | Primary Scope | Stateful / Stateless | Rule Types | Best For |
| --- | --- | --- | --- | --- |
| **NACL** | Subnet (VPC) | Stateless | Allow & Deny (numbered) | Subnet boundary blocks & explicit IP denies |
| **Security Group** | ENI / Instance | Stateful | Allow only | Fine-grained port/SG-to-SG instance access |
| **Network Firewall** | VPC (via endpoints) | Both (stateless + stateful) | Pass, Drop, Alert, Reject (Suricata / domains) | VPC IDS/IPS, domain filtering, TLS inspection |
| **AWS WAF** | HTTP/S apps (ALB, CloudFront, API GW) | HTTP request/session context | Allow, Block, Count, Captcha, Challenge | SQLi, XSS, web exploits, API & bot protection |
| **Firewall Manager** | Multi-account (AWS Organizations) | Policy orchestration layer | Central compliance policies | Enforcing standards across many accounts |

## AWS Trusted Advisor:
An automated cloud optimization tool that evaluates your AWS environment against best practices and recommends improvements. It does not modify resources directly, instead surfacing actionable insights and status indicators (such as no problem detected, recommended investigation, or recommended action).

## AWS Health Dashboard: 
Central hub for monitoring the real-time operational status of AWS services and receiving personalized alerts about your cloud resources. It is helpful during outages or maintenance events when verifying whether connectivity issues stem from an AWS service event.

## AWS Security Center: 
It is not an official AWS service, but AWS provides a comprehensive set of security tools and best practices to protect cloud environments.

## AWS re:Post: 
A cloud knowledge service designed to assist builders in overcoming technical challenges.

## AWS Knowledge Center: 
A resource hub that provides answers to frequently asked questions from AWS customers.

## AWS Security Blog:
An official AWS resource that provides insights, best practices, and technical guidance on cloud security
