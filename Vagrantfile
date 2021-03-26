servers=[
  {
    :hostname => "master",
    :ip1 => "192.167.100.11",
    :box => "generic/ubuntu1604",
    :ram => 1024,
    :cpu => 1
  },
  {
    :hostname => "container",
    :ip1 => "192.167.100.12",
    :box => "generic/ubuntu1604",
    :ram => 1024,
    :cpu => 1
  },
  {
    :hostname => "backup",
    :ip1 => "192.167.100.13",
    :box => "generic/ubuntu1604",
    :ram => 1024,
    :cpu => 1
  }
]

Vagrant.configure(2) do |config|
  servers.each do |machine|

    config.ssh.insert_key = false
    config.ssh.private_key_path = File.expand_path('~/.vagrant.d/insecure_private_key')

    config.vm.define machine[:hostname] do |node|
      node.vm.box = machine[:box]
      node.vm.network "private_network", ip: machine[:ip1]
      node.vm.hostname = machine[:hostname]
      node.vm.provider "virtualbox" do |vb|
        vb.customize ["modifyvm", :id, "--memory", machine[:ram]]
      end
    end
  end
end
