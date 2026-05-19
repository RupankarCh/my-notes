# Architecture
```
User
  ↓
Internet
  ↓
AWS VPC
 ├── Public Subnet
 │     └── EC2 (Web Application)
 │
 └── Private Subnet
       └── RDS MySQL Database
```


## Phase 1: Create AWS Networking
### Step 1: Create VPC

Create: VPC CIDR
```
10.0.0.0/16
```
This becomes your private cloud network.

### Step 2: Create Subnets

1. Public Subnet
```
10.0.1.0/24
```
Purpose: EC2 application server

2. Private Subnet
```
10.0.2.0/24
```
Purpose: Database server

### Step 3: Create Internet Gateway

Attach it to the VPC.
This allows internet access.

### Step 4: Configure Route Tables
1. Public Route Table
Add:
```
0.0.0.0/0 → Internet Gateway
```
**Associate: Public subnet**

2. Private Route Table
No internet route.
**Associate: Private subnet**

## Phase 2 — Launch Application Server
### Step 5: Create Security Group for EC2

Allow Inbound Rules:

| Type  | Port |
| ----- | ---- |
| SSH   | 22   |
| HTTP  | 80   |
| HTTPS | 443  |

Restrict SSH to your IP if possible.

### Step 6: Launch EC2 Instance

Use:
Ubuntu Server
t2.micro (free tier)

Place it in Public subnet

Attach: EC2 security group

### Step 7: Install Application Stack

Example for Node.js:
```
sudo apt update
sudo apt install nodejs npm -y
sudo nano app.js
```
paste and save
```
const http = require('http');

// We use port 80 because your security group is open to HTTP (Port 80)
const port = 80;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/html');
  res.end(`
    <h1>🚀 Hello from your AWS Application Server!</h1>
    <p>Your public route table, subnet, and security group configurations are working perfectly.</p>
  `);
});

server.listen(port, () => {
  console.log(`Server running on port ${port}`);
});
```

Run:
```
node app.js
```

## Phase 3 — Create Cloud Database
### Step 8: Create RDS MySQL

Create 2 Subnet Groups first
Create Database:
MySQL
Free tier
Private subnet only 
Disable: Public access

### Step 9: Edit previously created Database Security Group
Allow MySQL access from EC2 app instance:

Inbound add and select MySQL/Aurora	port 3306 and Source as EC2 security group ONLY.
Outbound leave default.

## Phase 4 — Connect App to Database
### Step 10: Get RDS Endpoint
- In the left-hand navigation sidebar, click on Databases.
- You will see a list of your database instances. Click directly on the DB identifier (the name you gave your database) of your MySQL instance.
- Scroll down slightly to the Connectivity & security tab (this tab is usually open by default).
- Under the Endpoint & port section, you will see your endpoint. It looks like a long string of text, for example: project-database.c123456789.us-east-1.rds.amazonaws.com

create a .env file and enter these credentials 
Example:
```
DB_HOST=mydb.xxxxxx.ap-south-1.rds.amazonaws.com
DB_USER=admin
DB_PASSWORD=password
DB_NAME=bookstore
```

## Phase 5 — Deploy Application
### Step 12: Run Application

Example:
```
node app.js
```
Access: http://EC2-PUBLIC-IP
















