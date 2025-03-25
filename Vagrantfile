Vagrant.configure("2") do |config|
  config.vm.box = "generic/macos"
  
  # Specify the provider
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "4096"
    vb.cpus = 2  
    vb.customize ["modifyvm", :id, "--cpus", "2"]
    vb.customize ["modifyvm", :id, "--memory", "4096"]
    vb.customize ["modifyvm", :id, "--vram", "128"]
  end

  # Use the ISO file for installation
  config.vm.provision "shell", inline: <<-SHELL
    echo "Starting macOS installation..."
    hdiutil attach ~/Desktop/Sequoia.iso
  SHELL

  # Set the boot command to start from the ISO
  config.vm.boot_command = [
    '<Esc>',
    'boot',
    'enter'
  ]

  # Set the ISO as the boot disk
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["storageattach", :id, "--storagectl", "IDE Controller", "--port", "0", "--device", "0", "--type", "dvddrive", "--medium", "~/Desktop/Sequoia.iso"]
  end
end
