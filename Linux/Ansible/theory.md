Ansible Automation Platform - Containerized

# Features:
1. Agentless
2. IaC(Infrastructure as Code)
3. Moduler
4. Push Based Model
5. Idempotent - If a task is already done, It won't run again.

winrm for windows remote usage.

1. Adhoc Command
2. Playbook (extension .yml and .yaml)

Term:
- Play: It contains task.
- Playbook: Collection of play.
- Task: Action, performed by module.

Return Codes:
0 - Successful

Inventory File Types:
1. Static (Specify hosts, it is a text file)
2. Dynamic (Fetching cloud instance IP address, It populates the inventory file)

Types of Group:
1. All
2. Ungrouped

Playbook:
1. Starts and ends with 3 dashes ---
2. Stop level components name, hosts, tasks

