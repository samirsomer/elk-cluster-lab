Vagrant.configure("2") do |config|
    servers = [
        {
            :hostname => "master01",
            :box => "centos/7",
            :ip => "192.168.10.12",
            :memory => 3096,
            :ssh_port => '2200'
        },
        {
            :hostname => "data01",
            :box => "centos/7",
            :ip => "192.168.10.13",
            :memory => 2048,
            :ssh_port => '2201'
        },
        {
            :hostname => "data02",
            :box => "centos/7",
            :ip => "192.168.10.14",
            :memory => 2048,
            :ssh_port => '2202'
        }
    ]
    servers.each do |machine|
        config.vm.define machine[:hostname] do |node|
            node.vm.box = machine[:box]
            node.vm.hostname = machine[:hostname]
            node.vm.network :private_network, ip: machine[:ip]
            node.vm.network "forwarded_port", guest: 22, host: machine[:ssh_port], id: "ssh"
            node.vm.provider :virtualbox do |vb|
                vb.customize ["modifyvm", :id, "--memory", machine[:memory]]
                vb.customize ["modifyvm", :id, "--cpus", 1]
            end
        end
    end
end

# ------
