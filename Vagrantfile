Vagrant.configure("2") do |config|
    config.ssh.insert_key = false
    config.env.enable # Enable vagrant-env(.env)
  
    # VM Master
    config.vm.define "rke2-control-plane", primary: true do |master|
      master.vm.provider :libvirt do |libvirt|
        libvirt.cpus = 2
        libvirt.memory = 4096
        # libvirt.machine_virtual_size = 20
      end
      master.vm.box = ENV['BOX_IMAGE']
      master.vm.network :private_network, ip: "192.168.50.10", netmask: "255.255.255.0"
      master.vm.hostname = "rke2-control-plane"
      master.vm.provision "ansible" do |ansible|
        ansible.verbose = "v"
        ansible.playbook = "rke2/playbook-control-plane.yaml"
        ansible.extra_vars = {
            NAME: "rke2",
            MASTER_IP: "192.168.50.10",
            USER_PATH: ENV['USER_PATH']
        }
      end
    end
  
    # VMs Workers
    (1..ENV['WORKER_NODES_COUNT'].to_i).each do |i|
      config.vm.define "rke2-worker-#{i}" do |node|
        node.vm.provider :libvirt do |libvirt|
          libvirt.cpus = 2
          libvirt.memory = 4096
          # libvirt.machine_virtual_size = 20
        end
        node.vm.box = ENV['BOX_IMAGE']
        node.vm.network :private_network, ip: "192.168.50.#{i + 10}", netmask: "255.255.255.0"
        node.vm.hostname = "rke2-worker-#{i}"
        node.vm.provision "ansible" do |ansible|
          ansible.verbose = "v"
          ansible.playbook = "rke2/playbook-worker.yaml"
          ansible.extra_vars = {
            MASTER_IP: "192.168.50.10"
          }
        end
      end
    end
  end