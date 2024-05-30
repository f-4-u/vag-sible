Vagrant.configure("2") do |config|
    config.vm.box = "archlinux/archlinux"

    config.vm.provider "virtualbox" do |vb|
        vb.memory = "1024"
        vb.cpus = 2
    end

    config.vm.hostname = "EXAMPLE"
    config.vm.network "private_network", type: "dhcp"

    # Provision to install Python
    config.vm.provision "shell", path: "install_python.sh"


    config.vm.provider "virtualbox" do |vb|
        vb.name = "EXAMPLE"
        vb.gui = false  # Ensure GUI is enabled for clipboard and drag-and-drop
        vb.customize ["modifyvm", :id, "--clipboard", "bidirectional"]  # Enable bidirectional clipboard
        vb.customize ["modifyvm", :id, "--draganddrop", "bidirectional"]  # Enable drag-and-drop
    end

    # Ansible provisioners
    config.vm.provision "ansible" do |ansible|
        ansible.compatibility_mode = "2.0"
        ansible.playbook = "ansible/inital.yml"
    end

    config.vm.provision "ansible" do |ansible|
        ansible.compatibility_mode = "2.0"
        ansible.playbook = "ansible/create_user.yml"
    end

    config.vm.provision "ansible" do |ansible|
        ansible.compatibility_mode = "2.0"
        ansible.playbook = "ansible/install.yml"
    end

    config.vm.provision "ansible" do |ansible|
        ansible.compatibility_mode = "2.0"
        ansible.playbook = "ansible/security.yml"
    end

    config.vm.provision "ansible" do |ansible|
        ansible.compatibility_mode = "2.0"
        ansible.playbook = "ansible/ssh_config.yml"
    end


    config.vm.provision "ansible" do |ansible|
        ansible.compatibility_mode = "2.0"
        ansible.playbook = "ansible/audit.yml"
    end
end
