Vagrant.configure("2") do |config|


# creating a virtual machine ubuntu
 config.vm.box = "ubuntu/xenial64"

# assign private ip to our VM
 config.vm.network "private_network", ip: "192.168.10.100"

# Ensure to install hostsupdater plugin on our localhost before rerunning (reloading) the vagrant 
 config.hostsupdater.aliases = ["development.local"]

# Sync folder from OS to VM
# "." means current location into/inside our vm 
 config.vm.synced_folder ".", "/home/vagrant/app"

 # automate execution of provision.sh
 config.vm.provision "shell", path: "./Vagrant/provision.sh", run: 'always'

end
