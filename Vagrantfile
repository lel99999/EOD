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
  config.vm.define "rhel7" do |rhel7|
    rhel7.vm.box = "iamseth/rhel-7.3"
    #rhel7.vm.box = "javier-lopez/rhel-7.4"
    #rhel7.vm.box = "xianlin/rhel-7.4"
    rhel7.vm.hostname = "rhel7"
    rhel7.vm.network "private_network", ip: "192.168.60.172"
  end
end
