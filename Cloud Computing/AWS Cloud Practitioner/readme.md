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
### to allow it on IAM users:
Billing and Cost Management> Account> IAM user and role access to Billing information (Edit)> Activate IAM Access Update.

### Charges By Service:
Billing and Cost Management> Bills> Charges By Service

### See forecast wether you are going to pass the free tire:
Billing and Cost Management> Free Tire

### Budget: (Billing and Cost Management> Budget)
It is set to get alert whenever you reach threashold budget.


Terms AWS Regions: A region is a **cluster of Datacenters.**

#Scinario Based Questions:
How to Choose Best Region for your task?
Based on Factors: 1.Compliance of the Country. 2.Proximity(Latency): if most users will be Indian then region my be India. 3.Available Service based on Regions(Not all regions have all services). 4.Pricing varies in each region.
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
## Users and Groups:
- Root account created by default, shouldn't be used or shared
- Users are people within your organization, and can be grouped
- Groups only contain users, not other groups
- Users don't have to belong to a group, and user can belong to multiple groups

## IAM Permissions:
- Users and Groups can be assigned a JSON documents called policies
- These policies define the permissions of the users
- In AWS you apply the least privilege principle: don't give more permissions than a user needs

## Multi-Session Support
It is used to **login to different accounts simultaniously on same window** of a browser.

## IAM Policies
- Inline Policies: Policies for a Single user.
- Group Policies: Policies for users of a perticular group

<img width="1233" height="593" alt="Screenshot 2026-03-23 225741" src="https://github.com/user-attachments/assets/494f9eab-47e6-4a89-88c7-c4f77c187e3f" />

## IAM Password Policy (IAM>Account Settings>Edit Password Policy)
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

## Multi Factor Authentication MFA (IAM>Security Credentials)
- Users who have root access to your account and can possibly change configurations or delete resources in your AWS account.To be safe you want to protect your Root Accounts and IAM users, Use MFA = password you know + security device you own. Main benefit of MFA: if a password is stolen or hacked. the account is not compromised
- MFA Device Options in AWS: Virtual MFA Device(Authy,Google Authenticator), Universal 2nd Factor (U2F) Security Key, Hardware Key Fob MFA Device.

### How can users access AWS ?
- To access AWS, you have three options:
  - AWS Management Console (protected by password + MFA)
  - AWS Command Line Interface (CLI): protected by access keys
  - AWS Software Developer Kit (SDK) - for code: protected by access keys

## Access Key Generation
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
 


## Create Access Keys:
  IAM>Users>username>Create Access Key
  
## Configuration of AWS CLI:
[Install AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
  on CMD type 'aws configure'
  enter credentials

## Commands AWS CLI
```
aws --version     #To see the version of AWS CLI
aws configure     #To configure AWS CLI
aws iam list-users    #To list all users
```

**AWS CloudShell** is a browser based terminal provided by AWS to manage AWS console

## IAM Roles and Services: 
- Some AWS service will need to perform actions on your behalf
- To do so, we will assign permissions to AWS services with IAM Roles
Common roles:
- EC2 Instance Roles
- Lambda Function Roles
- Roles for CloudFormation

## Creating a Role
IAM> Roles> Create Role>AWS Service> Select Service> Next> Attach Policy> Next> Name Role> Create Role

## Attaching a Role to a Instance
Select the instance Actions> Security> Modify> Select the Role and Update IAM role

## IAM Security Tools
- IAM Credentials Report (account-level)
    - a report that lists all your account's users and the status of their various credentials

- IAM Access Advisor (user-level)
    - Access advisor shows the service permissions granted to a user and when those services were last accessed.
    - You can use this information to revise your policies.

## Creating a Credential Report

IAM> Credential Report> Download Credential Report>


## Creating IAM Access Advisor

IAM> users> username> Access Advisor

# Scaling
- Vertical Scaling: Upgrading the resources, the process of increasing the capacity of an existing resource, such as a virtual machine (VM) or database, by adding more power to it.
- Horizontal Scaling: the process of adding more machines or instances to your infrastructure to handle increased traffic or workloads.

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
| Use Case    | Cache, temp data | OS, databases |

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
| 🌐 Use Case    | OS, databases                             | Shared files, web apps                    |
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

# Networking
## VPC 
### Creating VPC
VPC> Create VPC> VPC only> Name tag> IPv4 CIDR manual input> 
Create Subnet> 
Create EC2 instance with the VPC and Subnet created

### AWS Internet Access Flow for a VPC
Create internet gateway> Name tag> create > attach to VPC> Auto assign public IP> Name the security group>

# Network Security
- AWS-Security Groups
- Azure-NSG
- GCP-Firewall Rules


# Database
Database is a place where data is stored, organized and accessed. 

## Types of Database based on storage
- SQL data is stored in a structure. Features Tables(rows, columns), Fixed Schema, Relationships. e.g., MySQL, PostgreSQL
- NoSQL data is stored in the form of Objects without an structure. Represented in JSON format. e.g., MongoDB, DynamoDB (for Flexible Large Scale Data)


### SQL Databases Across Cloud (Features-Automated Backups, Scaling, No Server Management)
- AWS-RDS
- Azure-Azure SQL Database
- GCP-Cloud SQL

### NoSQL Databases Across Cloud (Features- Flexible Schema, High Scalability, Used in real-time apps)
- AWS-DynamoDB
- Azure-Cosmos DB
- GCP-Firestore/Bigtable

## Data Access Flow
App>Firewall/Security Group> Database

## AWS RDS: 
Managed Database service in AWS.(Features Multi-AZ, Server setup, Automated Backups, Scaling, Security patches, Monitoring) 

### Supported Engines by AWS:
MySQL, PostgreSQL, MariaDB, Oracle, SQL Server

## Types of Database Instance
- Master Database Instance: Read, Write Permission
- Slave Database Instance: Read Permission

## How to create a Database 
RDS> Create Database, Full Configuration, 

## Engine use case based on needs
| Use Case                 | Good Choice         |
| ------------------------ | ------------------- |
| Simple web app           | MySQL               |
| Complex analytics app    | PostgreSQL          |
| Enterprise legacy app    | Oracle / SQL Server |
| High-scale cloud app     | Aurora              |
| Serverless key-value app | DynamoDB            |

## Object Storage S3:

### Terms: 
- Cross_Origin Resource sharing: Sharing Resource between multiple buckets.

### configuring access permissions
Product bucket> Bucket Policy> enter a bucket policy from aws given example

### Static Website Hosting on S3:
1. Create a bucket with default settngs
2. Add the HTML file, and any media folder if there is any in the static website and Upload
3. Click on that HTML file you will see Object URL where you can access the file
4. Bucket> Bucket_name> Properties> **Static Website Hosting**> Edit> Enable> Name the Index Document> Save Changes.
5. Bucket> Permissions> **Uncheck block all public access**> Save Changes
6. Bucket> Permissions> **Object Ownership**> Edit> **ACLs enabled**>
7. Select all the objects> **Actions> Make Public using ACL> Make Public**
or after step 5 enter the add the bucket policy under permissions
```
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



# AWS Lambda

- **ECR (Elastic Container Registry)** is a private repository that **stores and manages Docker container images**.
- **ECS(Elastic Container Service)** is the **orchestration service** that deploys, runs, and scales those containers. 
