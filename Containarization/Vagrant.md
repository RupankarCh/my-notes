# Vagrant:
Vagrant is a tool/application that sits between the user and the virtual machine, making it easier to create, configure, and manage reproducible development environments using virtual machines.

Vagrant Boxes: **Pre-built, packaged base images** used by HashiCorp Vagrant to create identical, portable virtual machine environments.

Vagrantfile: A **configuration file** that defines how the Vagrant environment and virtual machine should be set up. 
[Browse VagrantBoxes](https://portal.cloud.hashicorp.com/vagrant/discover)
```
35 Contains config.vm.network "private network". ip: "192.168.33.10"  It is the private IP of the VM
40 Contains config.vm.network "public_network" It is the bridged network
46 Contains config.vm.synced_folder "../data", "/vagrant_data" the sync directory of the two systems our host system and the VM (reload after changing the sync folder)
52-58 Contains memory configuration
Provisioning: The process of automatically installing software and configuring the VM after it is created.
```



## Commands: 
```
vagrant init <geerlingguy/centos7> (To initializes the current directory as a Vagrant environment and creates a configuration file called a Vagrantfile.) 
vagrant up (To download, create, configure, and power on a virtual machine (VM) based on the settings specified in the Vagrantfile) 
vagrant ssh (To login the VM using the Vagrant user created automatically)
vagrant reload (To update new settings)
vagrant destroy (deletes the Vagrant virtual machine and all its associated resources but not the Vagrantfile itself)
```

## Multi-Machine Vagrantfile:
Here web and db are two VMs controlled by a single Vagrantfile here we dont need to do vagrant init only write the Vagrantfile from scratch.
```
Vagrant.configure("2") do |config|
  config.vm.provision "shell", inline: "echo Hello"

  config.vm.define "web" do |web|
    web.vm.box = "apache"
  end

  config.vm.define "db" do |db|
    db.vm.box = "mysql"
  end
end
```
