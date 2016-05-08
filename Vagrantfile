# Vagrant configuration file
# ==========================
# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version.

Vagrant.configure(2) do |config|

# Three vagrant machines are defined below: lba, web1 and web2. All 3
# boxes used are of minimal configuration where "lba" is Ubuntu distro,
# boxes "web1" and "web2" are CentOS distributions.
	# Hostnames, IP addresses and forwarded port mappings are also
	# specified. Private network connection is used which allows
	# host-only access to the machine using specific IP address.
	#
config.vm.define "lba" do |lba|
        lba.vm.box = "ubuntu/precise32"
        lba.vm.hostname = "loadbalancer"
        lba.vm.network "private_network", ip: "192.168.0.80"
        lba.vm.network "forwarded_port", guest: 80, host: 8080
        end

config.vm.define "web1" do |web1|
        web1.vm.box = "stevewinwood/Centos7"
        web1.vm.hostname = "webserver1"
        web1.vm.network "private_network", ip: "192.168.0.81"
        web1.vm.network "forwarded_port", guest: 80, host: 8081
	end

config.vm.define "web2" do |web2|
        web2.vm.box = "stevewinwood/Centos7"
        web2.vm.hostname = "webserver2"
        web2.vm.network "private_network", ip: "192.168.0.82"
        web2.vm.network "forwarded_port", guest: 80, host: 8082
	end

# Disable automatic box update checking. Boxes will only be checked for 
# updates when the user runs `vagrant box outdated`.
#
config.vm.box_check_update = false

# Privison Vagrant Host by Ansible playbook.
#
config.vm.provision "ansible" do |ansible|
	ansible.playbook = "projectPlayBook.yml"
	ansible.inventory_path = "hosts"
	end

end
