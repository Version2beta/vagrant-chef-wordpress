# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  # Uncomment the next line if you like to watch.
  # config.vm.boot_mode = :gui

  # Port 8000 on the host will go to port 80 on the Vagrant box
  config.vm.forward_port 80, 8000, { :auto => true }

  # Here's a folder for passing stuff back and forth
  config.vm.share_folder "v-data", "/home/vagrant/host_shared", "./shared"

  config.vm.provision :chef_solo do |chef|
    chef.json = {
      :mysql => {
        :server_root_password   => "open sesame ha ha ha",
        :server_repl_password   => "open sesame ha ha ha",
        :server_debian_password => "open sesame ha ha ha"
      }
    }
    chef.cookbooks_path = "cookbooks"
    chef.data_bags_path = "data_bags"
    chef.add_recipe "apt"
    chef.add_recipe "ohai"
    chef.add_recipe "configure"
  end
end
