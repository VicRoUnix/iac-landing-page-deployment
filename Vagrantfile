# Archivo Vagrantfile para configurar una máquina virtual con Ubuntu 24.04
Vagrant.configure("2") do |config|
  # Use una caja base oficial de Ubuntu 24.04
  config.vm.box = "bento/ubuntu-24.04"

  # Configuración de la red
  # La hemos configurado para usar una red privada (NAT)
  config.vm.network "private_network", ip: "192.168.56.150"  # Cambia esta IP según tu red local
  
  #Configuración del proveedor VirtualBox
  config.vm.provider "virtualbox" do |vb|
    vb.name = "LandingPage"  # Nombre de la máquina virtual
    vb.memory = "2048"  # Asignar 2GB de RAM
    vb.cpus = 2  # Asignar 2 CPUs
  end
  
  #Configuracion para lanzar el playbook de ansible
  config.vm.provision "Ansible", do |ansible|
     ansible.playbook = "playbook.yml"
     ansible.inventory_path = "inventory/vagrant/hosts.ini"
     ansible.verbose = "v"
   end
  
end
