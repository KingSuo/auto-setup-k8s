$change_sshd_config = <<-SCRIPT
echo change sshd_config to allow public key authentication and relaod sshd...
sed -i 's/\#PermitRootLogin yes/PermitRootLogin yes/' /etc/ssh/sshd_config
sed -i 's/\#PubkeyAuthentication yes/PubkeyAuthentication yes/' /etc/ssh/sshd_config
sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/' /etc/ssh/sshd_config
systemctl reload sshd
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.provision "shell", inline: "echo Hello"
  config.vm.network "public_network", bridge: "en0: Wi-Fi (Wireless)"

  config.vm.define "k8s-master-01" do |master_01|
    master_01.vm.box = "centos/7"
    master_01.vm.hostname = "k8s-master-01"
    master_01.vm.network "private_network", ip: "10.110.111.111"
    master_01.vm.provision "shell", inline: $change_sshd_config
    master_01.vm.provider "virtualbox" do |v|
      v.memory = 2048
      v.cpus = 2
    end
  end

  config.vm.define "k8s-worker-01" do |worker_01|
    worker_01.vm.box = "centos/7"
    worker_01.vm.hostname = "k8s-worker-01"
    worker_01.vm.network "private_network", ip: "10.110.111.112"
    worker_01.vm.provision "shell", inline: $change_sshd_config
    worker_01.vm.provider "virtualbox" do |v|
      v.memory = 2048
      v.cpus = 2
    end
  end

  config.vm.define "k8s-worker-02" do |worker_02|
    worker_02.vm.box = "centos/7"
    worker_02.vm.hostname = "k8s-worker-02"
    worker_02.vm.network "private_network", ip: "10.110.111.113"
    worker_02.vm.provision "shell", inline: $change_sshd_config
    worker_02.vm.provider "virtualbox" do |v|
      v.memory = 2048
      v.cpus = 2
    end
  end

  config.vm.define "k8s-docker-register" do |docker|
    docker.vm.box = "centos/7"
    docker.vm.hostname = "k8s-docker-register"
    docker.vm.network "private_network", ip: "10.110.111.120"
    docker.vm.provision "shell", inline: $change_sshd_config
    docker.vm.provider "virtualbox" do |v|
      v.memory = 1024
      v.cpus = 2
    end
  end
end