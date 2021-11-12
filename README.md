Monday 8th November 2021

# DevOps Introuction 

Devops is a culture that bridges the gap between Development and Operation.

The word DevOps iteself stands for development and operations. DevOps is a culture that allows the development and operations teams to work together in a more collaborative way in order to deliver a software product faster and more efficiently with a minimual failure rate.

DevOps engineers should have knowledge of the development of software hence, they should be able to understand the code written.

## Life before DevOps 

Before DevOps, there were separate teams: software development team, quality assurance team and system engineering team. 

The testing and deployment were isolated activities and so a large amount of time was spent in testing, deployment and designing instead of building the project.

The reason for the emergence of DevOps was because in the past, there was a barrier between the development and operations team as there was no collaboration between them. Therefore, DevOps was introduced in order to solve this issues.

## Why DevOps 

There are both technical and business benefits in DevOps:

Technical:
- You can detect faults in the product from early which leads to faster corrections of the defect
- Having microservices in places means that you isolate faults and detect vulnerabilities in code early as well without it affecting the entire project. 
- There is continuous software delivery - so you don't have the wait till the entire project is finished to deliver. Having microservices means you can deliver each seperately.

Business:
- There is a faster delivery of features
- Improved communication and collaboration between teams 
- Reduces costs - a devops role means making sure that the technology being used is as efficent as possible

#### Key Pillars of DevOps

1. Customer-Centric Action - the customer is taken into consideration in all actions that are taken
2. End-To-End Responsibility - DevOps team provides product support until the product or service comes to its end of life. This enhances the quality of the product produced.
3. Continuous Improvement 
4. Automation everything
5. Work as one team
6. Monitor and test everything

## Monolith Architecture 
Ideal for small applications. 

 
# Vagrant Introduction

Vagrant is installed on our localhost (e.g in this case my windows machine) just like VirtualBox, Ruby, Bash, Git and SSH is.

Any instructions that you need to implement and give to VirtualBox would need to be added onto the `Vagrantfile`.

Vagrant creates a log file that it creates automaticatically. It also creates a .vagrant/ (holds all the dependencies required) and a .git/ folder. 

## Create a `Vagrantfile` in the current location

Inside the Vagrantfile, set up the configuration which includes the set of instructions.
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

- The IP that we have allocated is stored on your localhost under the etc folder and it adds the link in there also - works without the IP
- In your home folder: in /etc folder - we have a host file - this is where all the entries on localhost are saved 

**Adding the hotsupdater plugin**
Once line of code is added, run the commands:
- `vagrant plugin install vagrant-hostsupdater`
- `vagrant plugin update vagrant-hostsupdater`

**Set of commands to run vagrant:**
- `vagrant up` - this command should be run in the location where `Vagrant file` exists as it looks for this file and reads the information and set of instructions 
- `vagrant status` - checks whether vagrant is running or not 
- `vagrant ssh` 
- `sudo apt-get update` - this will not run if you do not have a internet connection 
- `sudo apt-get upgrade -y`
- `sudo apt-get install nginx` - nginx is a web sever that we use for reverse proxy
- `systemctl status nginx` - check if its running and active 
- `sudo systemctl start nginx`

## To destroy Vagrant 

- `vagrant destroy` - no more communication from our OS to VM
- To confirm do `vagrant status` 
- Remove .vagrant by entering the command `rm -rf .vagrant/`

If you now look on VirtualBox, the machine we created should have disappeared.

### More Vagrant Comamands

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
 