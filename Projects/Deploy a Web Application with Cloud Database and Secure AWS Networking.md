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





