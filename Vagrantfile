Vagrant.configure("2") do |config|
  config.vm.box = "generic/bullseye64"
  config.vm.hostname = "alrigu.fjeclot.net"
  config.vm.provider "virtualbox" do |v|
    # v.gui = true
    v.name = "pj9f4a7.2_alrigu"
    v.memory = 2048
    v.cpus = 2
    v.customize ['modifyvm', :id, '--clipboard', 'bidirectional'] 
    config.vm.synced_folder "../codi" "/var/www/html"  
  end

  config.vm.network "public_network" #config treballar amb adaptador pont
  config.vm.network "forwarded_port", guest: 80, host: 8000
  config.vm.network "forwarded_port", guest: 433, host: 8443
  
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update -y
    sudo apt-get install -y net-tools
    sudo apt-get install -y apache2 apache2-doc
    sudo apt-get install -y libapache2-mod-php
    sudo apt-get install -y php7.4
    sudo apt-get install -y mariadb-server 
    sudo apt-get install -y mariadb-client
    sudo apt-get install -y php7.4-mysql
    sudo apt-get install -y composer
  SHELL

end
