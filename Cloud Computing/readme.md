# Every CSP provides the Followings services
- **Infrastructure as a Service (IaaS):** You get access to fundamental computing resources like virtual machines, storage, and networking. You manage the operating system and applications. Example Providers Amazon Web Services EC2, Microsoft Azure VM.
- **Platform as a Service (PaaS):** You get a platform to build, run, and manage applications without the complexity of managing the underlying infrastructure. Example providers: Heroku, Google App Engine, Microsoft Azure App service.
- **Software as a Service (SaaS):** You get a ready-to-use software application delivered over the internet. Example services: Google Docs, Microsoft 365, Dropbox.


# What is Cloud Computing?
Cloud computing is the **on-demand delivery of IT resources and applications over the internet with pay-as-you-go pricing**. Instead of owning and maintaining your own physical data centers and servers, you can access computing power, storage, and databases from a cloud provider like Amazon Web Services (AWS), Microsoft Azure, or Google Cloud Platform (GCP). This model offers several benefits, including:

- **Cost-Effectiveness**: You only pay for what you use, eliminating the need for large capital expenditures on hardware.
- **Scalability**: You can easily scale resources up or down to meet changing demands without major hardware upgrades.
- **Elasticity**: The ability to automatically adjust computing capacity to meet a sudden surge or drop in traffic.
- **Global Reach**: Cloud providers have data centers worldwide, allowing you to deploy applications closer to your users.

**Features of Cloud Computing:**
- On-Demand IT Delivery: Instant access to compute, storage and database resources via internet.
- Pay-As_you-Go Economics: Only pay for the specific resources consumed.
- Scalability and Elasticity: Systems can be manually scaled for long-term growth or automatically streched (elasticity) to handle sudden spikes.
- Global Infrastructure: Cloud providers maintain massive datacenters worldwide enabling businesses to deploy applications globally in minutes.
- The Shared Responsibility Model: Provider manages physical security and hardware customers remain responsible for the data and applications they place in the cloud.


# Cloud Deployment Models
Cloud services are delivered in different ways to suit various business needs.

- **Public Cloud**: This is the most common model. **Cloud services are owned and operated by a third-party provider and delivered over the public internet**. All hardware, software, and other supporting infrastructure are managed by the provider. Examples include AWS, Azure, and GCP.
- **Private Cloud**: A **cloud environment dedicated to a single organization**. It can be physically located on the company's premises or hosted by a third-party provider. This model offers greater control and security but comes with higher costs.
- **Hybrid Cloud**: A **mix of public and private cloud environments**. It allows data and applications to be shared between them. A common use case is running mission-critical applications on a private cloud while using the public cloud for less sensitive tasks like web development or big data analytics.

# Scalability:
**Ability to accommodate a greater load** by making the hardware stronger or by adding nodes.
  
## Types of Scalability:
- Vertical Scalability: Increase in the **power of current infrastructure**.
- Horizontal Scalability: Increase in the **number of current infrastructure**. example service-**Auto Scaling Group, Load Balancer**

# High Availability: 
Running your application/system in at least 2 availability zones. The main goal is to servive a data center loss. example services **Auto Scaling Group multi AZ**

# Elasticity: 
Once a system is scalable, elasticity means that **there will be some "auto-scaling" so that the system can scale based on the load.**  

# CSP (Cloud Service Providers)
The cloud is not a single technology; it's a vast ecosystem of services. The three market leaders AWS, Azure, and GCP each have a unique philosophy but offer similar core functionalities.

AWS (Amazon Web Services): As the pioneer, AWS has the **most mature and extensive service catalog**. It has a reputation for offering a deep and broad range of services, from basic compute and storage to advanced machine learning, robotics, and quantum computing. It's often seen as a **developer-centric platform**, giving users a high degree of granular control.

Azure (Microsoft Azure): With its strong background in enterprise software, Azure is a **powerful choice for businesses already invested in Microsoft's ecosystem**. It integrates seamlessly with Windows Server, Active Directory, and Visual Studio. Azure has focused on providing a comprehensive PaaS (Platform as a Service) offering and has made significant strides in hybrid cloud capabilities.

GCP (Google Cloud Platform): Leveraging Google's own internal infrastructure, GCP is a leader in big data, machine learning, and containerization. Its services for **data analytics**, such as **BigQuery and Cloud AI Platform, are top-tier**. GCP is often favored by tech startups and **companies with a strong focus on data-driven innovation**.

# All three platforms offer services in the following fundamental categories:

- Compute: **Services for running applications**, such as virtual machines (EC2, Azure VMs, Compute Engine) and serverless functions (Lambda, Azure Functions, Cloud Functions).
- Storage: **Services for storing data**, including object storage (S3, Azure Blob Storage, Cloud Storage) and block storage.
- Databases: A wide range of **database services**, from relational databases (RDS, Azure SQL DB, Cloud SQL) to NoSQL databases (DynamoDB, Cosmos DB, Cloud Firestore).
- Networking: **Services to connect and secure resources**, such as virtual private clouds (VPC, VNet), load balancers, and DNS.

# Object Storage:
Object storage = **scalable, internet-accessible storage for large files and unstructured data**, Unlike traditional file systems that organize data in a hierarchy of folders, **object storage manages data as objects in a flat structure**, which makes it ideal for handling massive amounts o funsttuctured data.

## Why it’s used for these
- Accessible via HTTP/HTTPS (perfect for browsers)
- Virtually unlimited storage
- Cheap compared to disks
- Built-in redundancy and durability

• **Amazon S3 (Simple Storage Service):** This is incredibly durable because of **data replication across multiple devices** and facilities. An object in S3 consists of **data, a unique key (its name), and metadata**. **Data is stored in buckets, which are containers in a specific AWS region**. S3 is highly scalable, and you can store viitually unlimited data.

• **Azure Blob Storage**: "Blob" stands for **Binary Large Object**. Azure Blob has different **access tiers Hot, Cool, and Archive**, which allows you to optimtze costs based on how frequently you need to access the data, Data is stored in containers within an Azure storage account.

• **Google Cloud Storage (GCS):** It also offers **a range of storage classes**, from high-performance to long-term archiving, which **automatically move objects between tiers to optimize cost**. GCS is deeply integrated with Google's other services, making it a **powerfull solution for data analytics and machine learning pipelines.**

## Data lifecycle management:
How data is handled from creation to eventual deletion.

### Data Classification and Tiering: \
Not all data is equally valuable or accessed with the same frequency. Cloud providers offer **different storage tiers to match your data's access patterns with the right cost**. Storage cost decreases and retieval cost increases for less frequently accessed data. 

- **Hot Tier**: For **frequently accessed data** that requires low latency. It has the highest storage cost but the lowest access cost.
- **Cool/Infrequent Access Tier**: For data that is **accessed infrequently but must be available quickly**. It has a lower storage cost than the hot tier but a higher retrieval cost.
- **Archive Tier**: For data that is **rarely accessed and can tolerate a retrieval delay of hours**. This tier has the lowest storage cost, making it **ideal for long-term backups and regulatory archives**.

### Lifecycle Policies:
You can **automate the movement of data between these tiers** using lifecycle policies. These are **rule-based policies that automatically transfer or delete objects based on a set of criteria**. For example, you can set a rule to move a file from a hot tier to a cool tier after 30 days and then to an archive tier after 90 days. This automation ensures that you are always using the most cost-effective storage class for your data, without any manual intervention. Effective data lifecycle management is critical for **cost optimization**, as it prevents you from paying for expensive, high-performance storage for data that is rarely used.


# Serverless computing:
a cloud-native model where developers deploy code without managing servers, as the cloud provider automatically provisions, scales, and manages the infrastructure.

# Networking

## VPC (Virtual Private Cloud, Regional): 
A VPC is a **logically isolated virtual network** that you define within the public cloud.It's your private network inside the cloud. It provides you with complete control over your network environment, including your **own IP address range, subnets, route tables, and network gateways**. A VPC is a foundational component that gives you the security and isolation you need to run your applications. It's like having your own private data center in the cloud.

## Subnets (Zonal): 
A subnet is a **logical subdivision of a VPC's IP address range**. You create subnets to organize your resources and **apply different security rules to them**. A VPC can have both **public subnets (where resources can be accessed from the internet) and private subnets (where resources are isolated from the intemet)** For **example**, you would place your public-facing web servers in a public subnet and your private databases in a private subnet.

### Types of Subnet
- Private Subnet - No direct internet access, Stateless application, Database, Backend services.
- Public Subnet - Has route to internet, Stateful Application,  web servers, Load balancers. Its route table has a route to an Internet Gateway (IGW)
Example: 0.0.0.0/0 -> igw-xxxx
[Subnetting in seconds](https://cidr.xyz/)

## CIDR: A method to define IP address ranges.

## Internet Gateway:
Allows VPC to connect to internet
EC2> Subnet> Route Table> IGW> Internet

## NAT Gateway:
allows private subnet to access internet (Outbound Traffic Only)
EC2> NAT Gateway> Internet

| Feature                           | Internet Gateway (IGW)                 | NAT Gateway                                                     |
| --------------------------------- | -------------------------------------- | --------------------------------------------------------------- |
| Purpose                           | Connect VPC directly to internet       | Allow private subnet instances to access internet outbound only |
| Public IP needed?                 | Yes (instance usually needs public IP) | NAT Gateway has public IP, private instances don’t              |
| Inbound internet traffic allowed? | Yes (if security rules allow)          | No                                                              |
| Used by                           | Public subnets                         | Private subnets                                                 |

NAT gateway> Internet Gateway> Internet

## Practical
### Creating VPC
Create VPC> VPC only> Name tag> IPv4 CIDR manual input(You decide the CIDR)/IPAM allocated IPv4 CIDR block(AWS IP Address Manager (IPAM) automatically allocates a CIDR block from a predefined IP pool.)> No IPv6 CIDR  block(resources inside that VPC cannot receive private/public IPv6 addresses from that VPC subnetting model.)>  Create VPC.

### Creating Subnet
Create Subnet> Select VPC> Subnet Name> Select Availability Zone> Selct IPv4 Subnet CIDR block> Create Subnet

### Creating and Connecting Internet Gateway with VPC
Creating Internet Gateway> Name Tag> Create Internet Gateway
Internet Gateways> Select the IGW> Actions> Attach to VPC> Select the VPC> Attach Internet Gateway

## Security Groups & Firewalls: 
These are the primary mechanisms for controlling traffic to your cloud resources.
  - A **security group** **acts as a virtual firewall** for your virtual machines. It is a **stateful firewall, meaning** that if you allow inbound traffic, the corresponding outbound response is automatically allowed. You define rules that allow or deny traffic based on protocol (e.g., TCP UDP). port number (e.g.: 80 for HTTP. 443 for HTTPS). and source IP address. Security Group Diagram: Internet> Security Group> EC2 Instance  
  
  - A **firewall rule** (e.g., in Google Cloud) or a Network Access Control List (NACL) (in AWS) is an additional layer of security that **controls traffic at the subnet level**. These are **stateless firewalls, so** you must explicitly allow both inbound and outbound traffc.

### Types of Cloud Firewall
- AWS Networking Firewall (Advanced Protection)
- NACL (Subnet Level) NACLs are stateless; **stateless so allow and deny traffic must be explicitly defined**. Maximum 100 rules for inbound and outbound each.
- Security Groups (Instance Level) stateful **supporting only allow rules, automatically permitting return traffic**.

<img width="640" height="170" alt="image" src="https://github.com/user-attachments/assets/c1122e8d-ee9a-41e0-b6c9-4af8fbee1ee3" />

# Database
Choosing between a relational and a NoSQL database **depends on your application's specific needs**. **Relational databases** are best for applications that require **structured data and transactional integrity**. while **NoSQL databases** are ideal for flexible, scalable **applications that handle large amounts of unstructured data**.

## RDS (Relational Database Service): 
AWS RDS is a fully managed relational database setvice. Instead of installing: patching, and maintaining a database on a VM. you can simply provision an RDS instance in minutes. **RDS handles the tedious tasks of backups, patching, and scaling**. It **supports** several popular database engines: including **MySQL, PostgreSQL: Oracle, and Microsoft SQL Server**.

## Azure SQL Database: 
This is a fully managed relational database-as-a-service from Microsoft. It is built on the SQL Server engine and offers the same powerful features without the need for manual administration It's ideal for developers and enterprises already familiar with SQL Server. It also offers features like **automated backups**, built-in **high availability** and **intelligent performance tuning**.

## NoSQL Databases: 
Unlike relational databases that use a rigid, tabular structure, NoSQL databases are **schema-less and more flexible**. They are designed for **handling large volumes of unstructured data** and offer high performance for specific use cases.
- **AWS DynamoDB**: A fully managed, serverless key-value and document **NoSQL database that delivers single-digit millisecond performance at any scale**.
- **Azure Cosmos DB**: Microsoft's **globally distributed, multi-model database service**. It **supports several popular NoSQL APIs including MongoDB, Cassandra and Gremlim**.
- **Google Cloud Firestore**: A flexible, scalable **NoSQL document database for mobile, web, and server development**.

# Load Balancing:
servers that forward internet traffic to multiple servers downstream.

## Why to use
- Spread load across multiple downstream instances
- Expose a single point of access (DNS) to your application
- Seamlessly handle failures of downstream instances
- Do regular health checks to your instances
- Provide SSL termination (HTTPS) for your website
- High availability across zones

