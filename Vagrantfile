 #-*- mode: ruby -*-
 # vi: set ft=ruby :

 # Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
 VAGRANTFILE_API_VERSION = "2"
 Vagrant.require_version ">= 1.5.0"

 Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
 # Name this how you like.  I find that naming it after the cookbook helps me
 # keep track of what I am doing.
   config.vm.hostname = "the-commons-local-1"

 # The location where you placed the machine image when installing Vagrant
 # above
   config.vm.box =
       "~/vagrant_boxies/precise-server-cloudimg-amd64-vagrant-disk1"

# You can use the IP address here along with your host file to hit a web
# application you are writing.
  config.vm.network :private_network, ip: "192.168.1.2"

# We are not going to use this setting here, but if you were to want to
# develop your web application on your laptop while view it as if running
# on this VM it would be something like:
# config.vm.synced_folder "../code/my_webapp", "/var/www/html/local"

# When Vagrant spins up a machine, it will also load your cookbook
# dependencies via Berkshelf
  config.berkshelf.enabled = true

# Set the version of Chef you want to use.  The omnibus plug in will
# ensure you get the version you want installed as Vagrant spins up
# the machine
  config.omnibus.chef_version = '11.14.2'
# Chef Zero path to chef server objects.  These are things like data bags,
# roles and environments.
  config.chef_zero.chef_repo_path = "../chefrepo/"

# Here is where you tell Vagrant how to configure the machine it is
# spinning up.  In this case we are using chef, but you could choose
# Puppet or some other provisioner.
  config.vm.provision :chef_client do |chef|
# Set the name of the node explicitly.  I prefer to have my machine
# names and node names match
  chef.node_name = config.vm.hostname
# Tell Vagrant what cookbooks to execute. Usually it is just
# the default recipe of the cookbook this Vagrantfile is in.
  chef.run_list = [
     "recipe[the_commons::default]"
  ]
  end
end
