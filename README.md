# DevOps Intro
## Life before DevOps 
### Why DevOps 
#### Key Pillars of DevOps
##### Monolith Architecture 

- **Devops Introduction**
- Devops is a culture that bridges the gap between Development and Operation
-

- **Life before DevOps**
- Waterfall - V-Model 
- Transition to Agile and Scrum - Scrum is a framework that works under the Agile Methodology 

### Create `Vagrantfile` in the current location

```
Vagrant.configure("2") do |config|


# creating a virtual machine ubuntu
config.vm.box = "ubuntu/xenial64"

# assign private ip to our VM
config.vm.network "private_network", ip: "192.168.10.100"

# alias for private ip
# ensure to install hostsupdater before rerunning vagrant
config.hostsupdater.aliases = ["development.local"]

# Sync folder from OS to Vm
config.vm.synced_folder ".", "/home/vagrant/app"


# automate execution of provision.sh
config.vm.provision "shell", path: "./Vagrant/provision.sh", run: 'always'



end
```

### Create `provision.sh` 

```
#!/bin/bash
# update systen
sudo apt-get update -y

# upgrade the packages
sudo apt-get upgrade -y

# install NGINX
sudo apt-get install nginx -y

```

### Vagrant Comamands

```
Common commands:
     autocomplete    manages autocomplete installation on host
     box             manages boxes: installation, removal, etc.
     cloud           manages everything related to Vagrant Cloud        
     destroy         stops and deletes all traces of the vagrant machine
     global-status   outputs status Vagrant environments for this user
     halt            stops the vagrant machine
     help            shows the help for a subcommand
     hostsupdater
     init            initializes a new Vagrant environment by creating a Vagrantfile
     login
     package         packages a running vagrant environment into a box
     plugin          manages plugins: install, uninstall, update, etc.
     port            displays information about guest port mappings
     powershell      connects to machine via powershell remoting
     provision       provisions the vagrant machine
     push            deploys code in this environment to a configured destination
     rdp             connects to machine via RDP
     reload          restarts vagrant machine, loads new Vagrantfile configuration
     resume          resume a suspended vagrant machine
     snapshot        manages snapshots: saving, restoring, etc.
     ssh             connects to machine via SSH
     ssh-config      outputs OpenSSH valid configuration to connect to the machine
     status          outputs status of the vagrant machine
     suspend         suspends the machine
     up              starts and provisions the vagrant environment
     upload          upload to machine via communicator
     validate        validates the Vagrantfile
     version         prints current and latest Vagrant version
     winrm           executes commands on a machine via WinRM
     winrm-config    outputs WinRM configuration to connect to the machine

Additional subcommands are available, but are either more advanced
or not commonly used. To see all subcommands, run the command
`vagrant list-commands`.
        --[no-]color                 Enable or disable color output
        --machine-readable           Enable machine readable output
    -v, --version                    Display Vagrant version
        --debug                      Enable debug output
        --timestamp                  Enable timestamps on log output
        --debug-timestamp            Enable debug output with timestamps
        --no-tty                     Enable non-interactive output

```
 