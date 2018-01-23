# Vagrant configuration file
# ==========================
# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version.

Vagrant.configure(2) do |config|

# Hostnames, IP addresses and forwarded port mappings are also
# specified. Private network connection is used which allows
# host-only access to the machine using specific IP address.
#
config.vm.define "master" do |master|
    master.vm.box = "centos/7"
    master.vm.hostname = "master"
    master.vm.network "private_network", ip: "192.168.121.10"
    end

config.vm.define "minion-1" do |minion1|
    minion1.vm.box = "centos/7"
    minion1.vm.hostname = "minion-1"
    minion1.vm.network "private_network", ip: "192.168.121.21"
	  end

config.vm.define "minion-2" do |minion2|
    minion2.vm.box = "centos/7"
    minion2.vm.hostname = "minion-2"
    minion2.vm.network "private_network", ip: "192.168.121.22"
    end

# Disable automatic box update checking. Boxes will only be checked for
# updates when the user runs `vagrant box outdated`.
#
config.vm.box_check_update = false

# Privison Vagrant Host by Ansible playbook.
#
config.vm.provision "ansible" do |ansible|
    ansible.playbook = "kubernetes.yml"
    ansible.inventory_path = "hosts"
    end

end
