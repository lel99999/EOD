Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |v|
    v.memory = "1024"
    v.cpus = 2
    v.customize ["modifyvm", :id, "--cpuexecutioncap", "70"]
  end
  config.vm.define "winEOD01" do |winEOD01|
    winEOD01.vm.box = "https://app.vagrantup.com/mwrock/boxes/Windows2012R2"
    winEOD01.vm.box = "mwrock/Windows2012R2"
    winEOD01.vm.hostname = "winEOD01"
    winEOD01.vm.network "private_network", ip: "192.168.60.170"
  end

  config.vm.define "eodrh7" do |eodrh7|
    eodrh7.vm.box = "clouddood/RH7.5_baserepo"
    #eodrh7.vm.box = "iamseth/rhel-7.3"
    #eodrh7.vm.box = "javier-lopez/rhel-7.4"
    #eodrh7.vm.box = "xianlin/rhel-7.4"
    eodrh7.vm.hostname = "eodrh7"
    eodrh7.vm.network "private_network", ip: "192.168.60.172"
    eodrh7.vm.provision "shell", :inline => "sudo echo '192.168.60.172 eodrh7.local eodrh7' >> /etc/hosts"
    eodrh7.vm.provision "shell", :inline => "sudo echo '192.168.60.173 eodapp7.local eodapp7' >> /etc/hosts"

    eodrh7.vm.provision "ansible" do |ansible|
      ansible.playbook = "deploy_eod.yml"
      ansible.inventory_path = "vagrant_hosts"
      #ansible.tags = ansible_tags
      #ansible.verbose = ansible_verbosity
      #ansible.extra_vars = ansible_extra_vars
      #ansible.limit = ansible_limit
    end
  end

  config.vm.define "eodapp7" do |eodapp7|
    eodapp7.vm.box = "iamseth/rhel-7.3"
    #eodrh7.vm.box = "javier-lopez/rhel-7.4"
    #eodrh7.vm.box = "xianlin/rhel-7.4"
    eodapp7.vm.hostname = "eodapp7"
    eodapp7.vm.network "private_network", ip: "192.168.60.173"
    eodapp7.vm.provision "shell", :inline => "sudo echo '192.168.60.172 eodrh7.local eodrh7' >> /etc/hosts"
    eodapp7.vm.provision "shell", :inline => "sudo echo '192.168.60.173 eodapp7.local eodapp7' >> /etc/hosts"

    eodapp7.vm.provision "ansible" do |ansible|
      ansible.playbook = "deploy_eod.yml"
      ansible.inventory_path = "vagrant_hosts"
      #ansible.tags = ansible_tags
      #ansible.verbose = ansible_verbosity
      #ansible.extra_vars = ansible_extra_vars
      #ansible.limit = ansible_limit
    end
  end
### Research EOD server - CentOS6.7
#  config.vm.define :research_eod do |server|
#    server.vm.box = "bento/centos-6.7"
#    server.vm.host_name = "research-eod.test.dev"
#
#    server.ssh.forward_agent = true
#
#    server.vm.provision "ansible" do |ansible|
#      ansible.playbook = "deploy_research_environment.yml"
#      ansible.inventory_path = "vagrant_hosts"
#      ansible.tags = ansible_tags
#      ansible.verbose = ansible_verbosity
#      ansible.extra_vars = ansible_extra_vars
#      ansible.limit = ansible_limit
#    end

#    server.vm.network :private_network, ip: "10.0.1.19"
#  end

end
