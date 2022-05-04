Vagrant.require_version ">= 2.0.0"

boxes = [
    {
        :name => "master",
        :eth1 => "192.168.205.100",
        :mem => "2048",
        :cpu => "1"
    },
    {
        :name => "worker1",
        :eth1 => "192.168.205.101",
        :mem => "2048",
        :cpu => "1"
    },
    {
        :name => "worker2",
        :eth1 => "192.168.205.102",
        :mem => "2048",
        :cpu => "1"
    }

]

Vagrant.configure(2) do |config|
  config.vm.box = "generic/ubuntu2004"

  boxes.each do |opts|
      config.vm.define opts[:name] do |config|
        config.vm.hostname = opts[:name]
        config.vm.provider "virtualbox" do |v|
          v.customize ["modifyvm", :id, "--memory", opts[:mem]]
          v.customize ["modifyvm", :id, "--cpus", opts[:cpu]]
        end
        config.vm.network :private_network, ip: opts[:eth1]
      end
  end
end
