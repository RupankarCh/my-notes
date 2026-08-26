Terraform: **Open-source IaC tool**.

# IaC: Tools allow you to **manage infrastructure with configuration files rather than through a graphical user interface**.

## Features: 
- Reusable
- Consistent(Same Configuration)
- Collaboration
- Fast as no repeatable work

<img width="653" height="360" alt="image" src="https://github.com/user-attachments/assets/2cb2c60a-576b-447b-b143-95a2d04fb163" />

## Commands: 
**terraform init** (initializes a working directory by **downloading necessary provider plugins, setting up the backend for storing state, and downloading any required modules**.)

**terraform validate** (checks the configuration files in a directory to ensure they are syntactically valid and internally consistent**.)

**terraform fmt** (automatically formats your HCL configuration files into a standard, canonical format and style.)

**terraform plan** (compares your configuration code against the current real-world state and creates an execution plan showing the exact changes Terraform will make to your infrastructure.)

**terraform apply** (executes the changes proposed in your plan to create, update, or destroy real-world infrastructure to match your configuration files.)
