Vagrant.configure("2") do |config|
  # Use a specified box
  #config.vm.box = "generic/ubuntu2204" # Option 1 - visit Vagrant cloud 
  config.vm.box = "geerlingguy/ubuntu2004" # Option 2 - visit Vagrant cloud
  
  # Set the hostname for the VM
  config.vm.hostname = "test-cloud-set-vm"
  
  # Configure the VirtualBox provider
  config.vm.provider "virtualbox" do |vb|
    # Set the name of the VM in VirtualBox
    vb.name = "Vagrant_Virtual"
  end
  
  # Do not insert a new SSH key
  config.ssh.insert_key = false
  
  # Forward port 80 on the VM to port 8080 on the host
  config.vm.network "forwarded_port", guest: 80, host: 8080
  
  # Forward port 22 for SSH access
  config.vm.network :forwarded_port, guest: 22, host: 2222, id: "ssh", auto_correct: true
  
  # Use SSH for communication
  config.vm.communicator = "ssh"
  
  # Provisioning with Ansible
  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "playbook.yml"
    #ansible.inventory_path = "/home/osama/work/inventory.ini" # or i can make ansible group directly here where i can specify the hosts 
    }
  end
  
   # Update /etc/hosts on the VM to ensure the hostname resolves correctly
  config.vm.provision "shell", inline: <<-SHELL
    echo "127.0.0.1 auto" >> /etc/hosts
  SHELL
end
  
  


 
 
 
 

