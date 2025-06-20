## Toute commande doit-ere exécution dans le répertoire contenant le Vagrantfile
## UP / DOWN
# vagrant up : lance TOUT
# vagrant up <hostname>: lance hostname
# vagrant halt [<hostname>]: arête tout ou seulement hostname
# vagrant destroy [-f] [<hostname>] : détruit [-f sans confirmation] //
# vagrant reload [<hostname>]: halt && up
## CNX
# vagrant ssh [<hostname>]: connexion SSH sur le compte "vagrant" 
#                           via l'interface NAT (127.0.0.1 + redirection 2222 <=> 22)
# vagrant ssh-config: configuration du vagrant ssh
# vagrant global-config
# vagrant plugin (un)install <plg>
##------------------------------------------------------------------

Vagrant.configure(2) do |config|
  
  ## VARS
  subject  = "git"
  hostname = "#{subject}.lan"
  image    = "ml-registry/#{subject}"
  memory   = 1024
  cpus     = 1
  
  ## MAIN
  
  config.vm.define "#{hostname}" do |machine|
    machine.vm.provider "virtualbox" do |v|
      v.memory = "#{memory}"
      v.cpus = "#{cpus}"
      v.name = "#{hostname}"
      v.customize ["modifyvm", :id, "--ioapic", "on"]
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    end
    machine.vm.box = "#{image}"
    machine.vm.hostname = "#{hostname}"
    machine.ssh.insert_key = true
  end
end
