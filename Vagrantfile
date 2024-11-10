

Vagrant.configure("2") do |config|
    # Selecciona la caja base. Puedes usar Ubuntu como ejemplo
    config.vm.box = "ubuntu/jammy64" # Ubuntu 18.04 LTS, puedes elegir otra versión si prefieres
  
    # Asigna recursos
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"          # RAM
      vb.cpus = 2                # Núcleos de CPU
    end
  
    
    config.vm.network "forwarded_port", guest: 80, host:8080

    config.vm.synced_folder "./html", "/var/www/html", owner:"www-data", group: "www-data"

    # Instala Apache y configura el servidor
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y apache2
      sudo systemctl enable apache2
      sudo systemctl start apache2
    SHELL
  end
  