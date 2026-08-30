# Vagrant:
A tool used to create and manage reproducible development environments using virtual machines.

Vagrant Boxes: **Pre-built, packaged base images** used by HashiCorp Vagrant to create identical, portable virtual machine environments.

Vagrantfile: A **configuration file** that defines how the Vagrant environment and virtual machine should be set up.
```
35 Contains config.vm.network "private network". ip: "192.168.33.10"  It is the private IP of the VM
40 Contains config.vm.network "public_network" It is the bridged network
52-58 Contains memory configuration
Provisioning: The process of automatically installing software and configuring the VM after it is created.




## Commands: 
```
vagrant init (To initializes the current directory as a Vagrant environment and creates a configuration file called a Vagrantfile.) 
vagrant up (To create, configure, and power on a virtual machine (VM) based on the settings specified in the Vagrantfile) 
vagrant ssh (To login the VM using the Vagrant user created automatically)
vagrant reload (To update new settings)
```
