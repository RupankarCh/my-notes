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
- e.g., rackspace


## Public Cloud:
- Cloud resources **owned and operated by a third-party cloud service provider** delivered over the Intemet. Multi-tenant: Shared physical hardware.
- e.g., GCP, AWS, Azure

## Hybrid:
- Keep some servers on premises and extend some capabilities to the Cloud.
- Control over sensitive assets in your private infrastructure
- Flexibility and cost-effectiveness of the public cloud.

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


# EC2 (Elastic Compute Cloud/Infrastructure as a Service)
It mainly consists in the capability of :
• Renting virtual machines (EC2)
• Storing data on virtual drives (EBS)
• Distributing load across machines (ELB)
• Scaling the services using an auto-scaling group (ASG)

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
