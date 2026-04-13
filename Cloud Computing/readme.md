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

# Cloud Deployment Models
Cloud services are delivered in different ways to suit various business needs.

- **Public Cloud**: This is the most common model. **Cloud services are owned and operated by a third-party provider and delivered over the public internet**. All hardware, software, and other supporting infrastructure are managed by the provider. Examples include AWS, Azure, and GCP.
- **Private Cloud**: A **cloud environment dedicated to a single organization**. It can be physically located on the company's premises or hosted by a third-party provider. This model offers greater control and security but comes with higher costs.
- **Hybrid Cloud**: A **mix of public and private cloud environments**. It allows data and applications to be shared between them. A common use case is running mission-critical applications on a private cloud while using the public cloud for less sensitive tasks like web development or big data analytics.


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


# Serverless computing:
a cloud-native model where developers deploy code without managing servers, as the cloud provider automatically provisions, scales, and manages the infrastructure.

