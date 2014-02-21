VAGRANTFILE_API_VERSION = "2"

$script = <<SCRIPT
sudo apt-get update
sudo apt-get install -y python-pip python-dev
cd app/
sudo pip install -r requirements.txt
SCRIPT

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "precise64"

  config.vm.network :forwarded_port, guest: 5000, host: 5000
  config.vm.network :forwarded_port, guest: 10843, host: 10843
  # config.vm.network :private_network, ip: "192.168.100.100"

  config.vm.synced_folder "app", "/home/vagrant/app"

  config.vm.provision "shell", inline: $script

end
