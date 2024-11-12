Vagrant.configure("2") do |config|
  # Specify the Ubuntu 22.04 box
  config.vm.box = "bento/ubuntu-22.04"

  # VM settings
  config.vm.provider "vmware_desktop" do |v|
    v.memory = 8024               # In MB
    v.cpus = 8                    # Core Number
    v.gui = true
  end

  # Network settings (DHCP)
  config.vm.network "public_network", type: "dhcp"

  # Provisioning to create user 'sunil' with password '12345'
  config.vm.provision "shell", inline: <<-SHELL
    # Create user 'user' with password 'password'
    sudo useradd -m -s /bin/bash user
    echo 'user:password' | sudo chpasswd

    # Grant 'user' sudo privileges
    sudo usermod -aG sudo user
  SHELL
end
