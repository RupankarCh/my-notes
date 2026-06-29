# Introduction to Cloud Computing
What is Cloud Computing?
Cloud computing is the **on-demand delivery of IT resources and applications over the internet with pay-as-you-go pricing**. Instead of owning and maintaining your own physical data centers and servers, you can access computing power, storage, and databases from a cloud provider like Amazon Web Services (AWS), Microsoft Azure, or Google Cloud Platform (GCP). This model offers several benefits, including:

**Features/Benifits of Cloud Computing:**
- **On-Demand IT Delivery:** Instant access to compute, storage and database resources via internet.
- **Cost-Effectiveness**: You only pay for what you use, eliminating the need for large capital expenditures on hardware.
- **Scalability**: **Ability to accommodate a greater load** by making the hardware stronger or by adding nodes. You can easily scale resources up or down to meet changing demands without major hardware upgrades.
- **Elasticity**: The ability to automatically adjust computing capacity to meet a sudden surge or drop in traffic.
- **Global Reach**: Cloud providers have data centers worldwide, allowing you to deploy applications closer to your users.
- **The Shared Responsibility Model:** Provider manages physical security and hardware customers remain responsible for the data and applications they place in the cloud.
- **High Availability:** Running your application/system in at least 2 availability zones. The main goal is to servive a data center loss. example services **Auto Scaling Group multi AZ**

**Types of Scalability:**
- **Vertical Scalability:** Increase in the **power of current infrastructure**.
- **Horizontal Scalability:** Increase in the **number of current infrastructure**. example service-**Auto Scaling Group, Load Balancer**

# Cloud Deployment Models
Cloud services are delivered in different ways to suit various business needs.
- **Public Cloud**: This is the most common model. **Cloud services are owned and operated by a third-party provider and delivered over the public internet**. All hardware, software, and other supporting infrastructure are managed by the provider. Examples include AWS, Azure, and GCP.
- **Private Cloud**: A **cloud environment dedicated to a single organization**. It can be physically located on the company's premises or hosted by a third-party provider. This model offers greater control and security but comes with higher costs.
- **Hybrid Cloud**: A **mix of public and private cloud environments**.A common use case is running mission-critical applications on a private cloud while using the public cloud for less sensitive tasks like web development or big data analytics.
- **Cloud Bursting**: is a strategy where an oraganization uses its **private cloud for normal workloads but "bursts" into the public cloud to handle temporary spikes in traffic**.
- **Strategic Workload Placement**: Use the **private cloud for sensitive**, mission-critical data while leveraging the **public cloud for high-scale web applications**.

# Every CSP provides the Followings services
- **Infrastructure as a Service (IaaS):** You get access to fundamental computing resources like virtual machines, storage, and networking. You manage the operating system and applications. Example Providers Amazon Web Services EC2, Microsoft Azure VM.
- **Platform as a Service (PaaS):** You get a platform to build, run, and manage applications without the complexity of managing the underlying infrastructure. Example providers: Heroku, Google App Engine, Microsoft Azure App service.
- **Software as a Service (SaaS):** You get a ready-to-use software application delivered over the internet. Example services: Google Docs, Microsoft 365, Dropbox.

# Overview of AWS, Azure & GCP service ecosystems
## CSPs (Cloud Service Providers)
The cloud is not a single technology; it's a vast ecosystem of services. The three market leaders AWS, Azure, and GCP each have a unique philosophy but offer similar core functionalities.

- **AWS (Amazon Web Services):** As the pioneer, AWS has the **most mature and extensive service catalog**. It has a reputation for offering a deep and broad range of services, from basic compute and storage to advanced machine learning, robotics, and quantum computing. It's often seen as a **developer-centric platform**, giving users a high degree of granular control.
- **Azure (Microsoft Azure):** With its strong background in enterprise software, Azure is a **powerful choice for businesses already invested in Microsoft's ecosystem**. It integrates seamlessly with Windows Server, Active Directory, and Visual Studio. Azure has focused on providing a comprehensive PaaS (Platform as a Service) offering and has made significant strides in hybrid cloud capabilities.
- **GCP (Google Cloud Platform):** Leveraging Google's own internal infrastructure, GCP is a leader in big data, machine learning, and containerization. Its services for **data analytics**, such as **BigQuery and Cloud AI Platform, are top-tier**. GCP is often favored by tech startups and **companies with a strong focus on data-driven innovation**.

## Services:
### Compute: Services for running applications
- **Virtual Machines (EC2, Azure VMs, Compute Engine)** users rent virtualized hardware where they have full control over the OS and software stack.
- **Serverless Functions** (Lambda, Azure Functions, Cloud Functions) A "Function-as-a-Service"(FaaS) model, where developers upload code and the provider handles all server management, scaling, and execution.
  - **a cloud-native model where developers deploy code without managing servers**, as the cloud provider automatically provisions, scales, and manages the infrastructure.
- **Containerization: (EKS- AKS, GKE)** All three provider managed services for Kubernetes, allowing developers to package applications with their dependencies for consistent deployment across different environments.
- **Batch Processing:** High-performance computing (HPC) services designed to run thousands of parallel jobs for complex simulations or data processing tasks.
- **Edge Computing**:(AWS Wavelength, Azure Stack Edge) Extending compute power closer to the user or IoT devices to reduce latency for real-time applications.

### Storage and Content Delivery:
- **Object storage:(AWS S3, Azure Blob and GCP Cloud Storage)** **scalable, internet-accessible storage for large files and unstructured data  like photos, videos, and backups.**, Unlike traditional file systems that organize data in a hierarchy of folders, **object storage manages data as objects in a flat structure**, which makes it ideal for handling massive amounts ofunsttuctured data. While the terminology differs—**S3 uses "Buckets," Azure uses"Containers," and GCS uses "Buckets"** —the concept is the same, a top-level logical unit used to organize objects and apply security policies.
  - **Amazon S3:** Automatically **replicating data across multiple physical facilities within a region**, ensuring that data loss is statistically near-impossible.
  - **Azure Blob Storage:** Optimized for "Binary Large Objects," this service excels at **serving contentdirectly to browsers and streaming media.**
  - **Google Cloud Storage (GCS):** **automatically transition data to lower-cost tiers basedon its "age" or frequency of use**, optimizing the storage lifecycle.
- **Block Storage: (AWS EBS, Azure ManagedDisks)** Acts like a **virtual hard drive attached to a VM**. It provides high-speed, low-latency performance required for running databases and enterprise applications.
- **File Storage:(NAS)** Managed **network-attached storage** that allows multiple virtual machines to share a single file system, supporting standard protocols like NFS and SMB.
- **Cold Storage (Archiving):(Amazon S3 Glacier)** Extremely low-cost tiers (like  designed fordata that is rarely accessed but must be kept for long-term compliance or backup.
- **Content Delivery Networks (CDN): (CloudFront, AzureCDN)** A global network of "Edge Locations" that **caches content closer to users to speed up the delivery** of web pages and video streams.

### Databases
- **Relational Databases (SQL):(AWS RDS, Azure SQL Cloud SQL)** **Managed instances of popular engines like MySQL, PostgreSQL,and SQL Server**. These services automate patching, backups, and scaling of structured data.
  - Transactional Integrity: perfect for financial systems and application requiring complex table relationships.
  - Point-in-Time Recovery: restore data from any precise moment to recover from human error or corruption.
  - Multi-AZ Failover: Automatic switching to a stadby instance during a data center outage.
- **NoSQL Databases:** **Designed for high-speed, non-relational data at massive scale.** Examples include **DynamoDB (Key-Value), Cosmos DB (Multi-model), and Bigtable (Wide-column).**
  - Schema Flexibility: Store data as JSON-like documents or key-value pairs without pre-defining tables.
  - Global Reach: Replicate data across the globe with millisecond latency for international users.
  - Serverless Operations: Platforms like DynamoDB handle all scaling and maintenance automatically.
  - High Velocity: Built to handle millions of requests per second for IoT, gaming,and social media.
- **Data Warehousing:(Amazon Redshift, Azure Synapse, Google BigQuery)** Specialized **databases built for complex analytical queries across petabytes of data**.
- **In-Memory Caching:(ElastiCache or Redis)** **Services that store frequently accessed data in RAM** to provide sub-millisecond response times for applications.
- **Graph and Ledger Databases**: Niche **databases for managing highly connected data** (socialnetworks) or providing an immutable, cryptographically verifiable record of transactions.

**Key Use Cases: SQL vs NoSQL**
- Use SQL for: Accounting systems, inventory management, and structured reporting.
- Use NoSQL for: User profiles, real-time analytics, content management, and mobile app syncing.
- Hybrid Approaches: Many modern architectures use both— **SQL for the core "truth" and NoSQL for fast-access "caching."**
- Data Integrity: SQL ensures your data is never "partial" or "wrong" through strict schema enforcement.

**Data lifecycle management:**
How data is handled from creation to eventual deletion.
**Lifecycle Strategy**: A **structured approach to managing data from its initial creation and active use to its eventual archiving and permanent deletion**.

**Lifecycle Policies:**
You can **automate the movement of data between these tiers** using lifecycle policies. These are **rule-based policies that automatically transfer or delete objects based on a set of criteria**. For example, you can set a rule to move a file from a hot tier to a cool tier after 30 days and then to an archive tier after 90 days. This automation ensures that you are always using the most cost-effective storage class for your data, without any manual intervention. Effective data lifecycle management is critical for **cost optimization**, as it prevents you from paying for expensive, high-performance storage for data that is rarely used.

##### Data Classification and Tiering:
Not all data is equally valuable or accessed with the same frequency. Cloud providers offer **different storage tiers to match your data's access patterns with the right cost**. Storage cost decreases and retieval cost increases for less frequently accessed data. 

- **Hot Tier**: For **frequently accessed data** that requires low latency. It has the highest storage cost but the lowest access cost.
- **Cool/Infrequent Access Tier**: For data that is **accessed infrequently but must be available quickly**. It has a lower storage cost than the hot tier but a higher retrieval cost.
- **Archive Tier**: For data that is **rarely accessed and can tolerate a retrieval delay of hours**. This tier has the lowest storage cost, making it **ideal for long-term backups and regulatory archives**.

**Automated Transition Policies**
- **Rule-Based Migration:** **Create "If-Then" logic to move data automatically between tiers** based on the age of the file or the last date it was accessed.
- **Phased Movement:** A **common policy** might move data from Hot to Cool after 30 days,then to Archive after 90 days of inactivity.
- **Intelligent Tiering:** Some cloud providers offer **AI-driven classes that monitor access patterns and move data between tiers in real-time** without user-defined rules.
- **Prefix and Tag Filtering:** **Policies can be applied globally to a bucket or targeted to specific folders and file types using metadata tags.**

**Expiration and Retention Rules**
- **Automated Deletion: Defines a specific "end-of-life" for data**, automatically purging files once they are no longer required for business or legal reasons.
- **Version Control Cleanup: Manages "non-current" versions of files**, automatically deletingolder iterations after a set timeframe to save space.
- **Regulatory Compliance: Helps organizations meet strict data privacy laws (like GDPR)** by ensuring personal data is not retained longer than necessary.
- **Incomplete Upload Cleanup: Automatically identifies and removes "multipart upload" fragments from failed transfers** that would otherwise incur hidden costs.
- **Legal Holds: Capability to override deletion rules temporarily during legal proceedings** to ensure critical evidence is preserved.

**Advanced Managed Features**
- Read Replicas: Distribute your data globally to ensure fast reads for users everywhere.
- AI-Powered Tuning: Automatic performance optimization and bottleneck identification.
- Security Guardrails: Private networking ensures your database is never exposed directly to the internet.
- Storage Hyperscale: Move from gigabytes to petabytes without ever migrating your database engine.

### Networking
Cloud networking **transitions physical hardware into a Software-Defined Network (SDN)**. This allows for the creation of complex, multi-tier architectures that are highly isolated yet globally accessible.

**Networking and Security:**
- **Virtual Private Clouds (VPC/VNet):** A logically isolated section of the cloud where you define your own IP address range, subnets, and routing tables, acting as your private data center in the sky.
- **Load Balancing:** **Automatically distributes incoming application traffic across multiple targets(VMs or containers)** to ensure high availability and fault tolerance.
- **DNS and Traffic Management:(Route 53 or Google Cloud DNS)** **These services translate human-readable domain names into IP addresses** and can route users based on their geographic location.
- **Firewalls and Security Groups:** Virtual firewalls that control inbound and outbound traffic at the instance or subnet level to protect resources from unauthorized access.
- **Private Connectivity:(AWS Direct Connect, Azure ExpressRoute)** Dedicated network links that bypass the public internet to provide a secure, high-bandwidth connection between on-premise offices and the cloud

<img width="360" height="372" alt="image" src="https://github.com/user-attachments/assets/a5c95478-2242-4da2-b81d-91993d7717d7" />

**VPC (Virtual Private Cloud, Regional):** 
A VPC (or VNet in Azure)  is a **logically isolated virtual network** that you define within the public cloud. It's your private network inside the cloud. It provides you with complete control over your network environment, including your **own IP address range, subnets, route tables, and network gateways**. A VPC is a foundational component that gives you the security and isolation you need to run your applications. It's like having your own private data center in the cloud.
- **Network Isolation:** No traffic can enter or leave the VPC unless you specifically configure a gateway.
- **Custom IP Addressing:** You define your own private IP range (e.g., 10.0.0.0/16) using CIDR blocks.
- **Routing Control:** You manage Route Tables that act as the GPS for your data, directing traffic between subnets, the internet, or on-premise networks.

Connecting to the World
To make the VPC functional, various gateways and connections are utilized:
- **Internet Gateway (IGW):** The bridge between your VPC and the public internet.
- **Virtual Private Gateway**: Used to **establish a secure VPN tunnel between your corporate office and your cloud VPC**.
- **VPC Peering**: Allows you to **connect two different VPCs together** so resources can communicate using private IP addresses as if they were on the same network.
- **Direct Connect / ExpressRoute**: A dedicated, **physical fiber connection from your datacenter to the cloud provider**, bypassing the public internet for higher speed and security.

**Subnets (Zonal):**
A subnet is a **logical subdivision of a VPC's IP address range**. You create subnets to organize your resources and **apply different security rules to them**. A VPC can have both **public subnets (where resources can be accessed from the internet) and private subnets (where resources are isolated from the internet)** For **example**, you would place your public-facing web servers in a public subnet and your private databases in a private subnet.

**Availability Zone Distribution**: To ensure high availability, subnets are often distributed across different physical data centers (AZs) so that a failure in one location doesn't takedown the entire network.

**Types of Subnet**
- Private Subnet - No direct internet access, To download updates, resources here typically use a NAT Gateway to reach out without allowing the internet to "reach in." e.g., resources Stateless application, Database, Backend services.
- Public Subnet - These are connected to an Internet Gateway. Resources here have public IP addresses and are accessible to the outside world, e.g., of resources are Stateful Application,  web servers, Load balancers. Its route table has a route to an Internet Gateway (IGW)
Example: 0.0.0.0/0 -> igw-xxxx
[Subnetting in seconds](https://cidr.xyz/)

**CIDR:** A method to define IP address ranges.

**Internet Gateway:**
Allows VPC to connect to internet
EC2> Subnet> Route Table> IGW> Internet

**NAT Gateway:**
allows private subnet to access internet (Outbound Traffic Only)
EC2> NAT Gateway> Internet

| Feature                           | Internet Gateway (IGW)                 | NAT Gateway                                                     |
| --------------------------------- | -------------------------------------- | --------------------------------------------------------------- |
| Purpose                           | Connect VPC directly to internet       | Allow private subnet instances to access internet outbound only |
| Public IP needed?                 | Yes (instance usually needs public IP) | NAT Gateway has public IP, private instances don’t              |
| Inbound internet traffic allowed? | Yes (if security rules allow)          | No                                                              |
| Used by                           | Public subnets                         | Private subnets                                                 |

NAT gateway> Internet Gateway> Internet

**Security Groups & Firewalls:** 
These are the primary mechanisms for controlling traffic to your cloud resources.
  - A **security group** **acts as a virtual firewall** for your virtual machines. It is a **stateful firewall, meaning** that if you allow inbound traffic, the corresponding outbound response is automatically allowed. You define rules that allow or deny traffic based on protocol (e.g., TCP UDP). port number (e.g.: 80 for HTTP. 443 for HTTPS). and source IP address. Security Group Diagram: Internet> Security Group> EC2 Instance

features of security group
- **Stateful Filtering**: If you **allow a "request" in on Port 80, the "response" is automatically allowed back out**. The firewall "remembers" the connection state.
- **Whitelist Only: By default, all inbound traffic is blocked**. You must create "Allow" rules specifying the protocol (TCP/UDP), Port (e.g., 22 for SSH), and the specific Source (an IPaddress or another Security Group).
- **Granular Control**: You can assign different security groups to different tiers; for example, a"Web-SG" might allow Port 443 from the whole world, while a "DB-SG" only allowstraffic from the "Web-SG." 
  
  - A **firewall rule** (e.g., in Google Cloud) or a Network Access Control List (NACL) (in AWS) is an additional layer of security that **controls traffic at the subnet level**. These are **stateless firewalls, so** you must explicitly allow both inbound and outbound traffc.

**Types of Cloud Firewall**
- **AWS Networking Firewall** (Advanced Protection)
- **NACL (Subnet Level)** NACLs are stateless; **stateless so allow and deny traffic must be explicitly defined**. Maximum 100 rules for inbound and outbound each. It allow you to explicitly "Deny" specific IP addresses (e.g., blocking a known malicious bot). It sits at the subnet level, they filter traffic before it even reaches the instance-level security groups.
- **Security Groups (Instance Level)** stateful **supporting only allow rules, automatically permitting return traffic**.

<img width="640" height="170" alt="image" src="https://github.com/user-attachments/assets/c1122e8d-ee9a-41e0-b6c9-4af8fbee1ee3" />


#### Practical
**Creating VPC** 
Create VPC> VPC only> Name tag> IPv4 CIDR manual input(You decide the CIDR)/IPAM allocated IPv4 CIDR block(AWS IP Address Manager (IPAM) automatically allocates a CIDR block from a predefined IP pool.)> No IPv6 CIDR  block(resources inside that VPC cannot receive private/public IPv6 addresses from that VPC subnetting model.)>  Create VPC.

**Creating Subnet**
Create Subnet> Select VPC> Subnet Name> Select Availability Zone> Selct IPv4 Subnet CIDR block> Create Subnet

**Creating and Connecting Internet Gateway with VPC**
Creating Internet Gateway> Name Tag> Create Internet Gateway
Internet Gateways> Select the IGW> Actions> Attach to VPC> Select the VPC> Attach Internet Gateway


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

