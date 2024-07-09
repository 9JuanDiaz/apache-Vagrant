# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  
  # Definir la primera máquina virtual
  config.vm.define "web1" do |web1|
    web1.vm.box = "ubuntu/bionic64"
    web1.vm.network "private_network", ip: "192.168.33.10"
    web1.vm.synced_folder "./html", "/var/www/html"

    # Aumentar el tiempo de espera de arranque
    web1.vm.boot_timeout = 600  # 10 minutos
    web1.ssh.forward_agent = false

    web1.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y apache2
      systemctl enable apache2
      systemctl start apache2
    SHELL
  end

  # Definir la segunda máquina virtual
  config.vm.define "web2" do |web2|
    web2.vm.box = "ubuntu/bionic64"
    web2.vm.network "private_network", ip: "192.168.33.11"
    web2.vm.synced_folder "./html", "/var/www/html"

    # Aumentar el tiempo de espera de arranque
    web2.vm.boot_timeout = 600  # 10 minutos
    web2.ssh.forward_agent = false

    web2.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y apache2
      systemctl enable apache2
      systemctl start apache2
    SHELL
  end

end



