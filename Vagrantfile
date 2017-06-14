Vagrant.configure("2") do |config|
  config.vm.define "local" do |local|
    local.vm.box = 'ubuntu/xenial64'
    local.vm.network "private_network", type: "dhcp"
  end

  config.vm.synced_folder '.', '/vagrant', disabled: true

  config.vm.provision "chef_solo" do |chef|
    chef.add_recipe "ghost-blog"
    chef.json = {
      "ghost-blog" => {
        "install_dir" => "/srv/www/ghost",
        "nginx" => {
          "server_name" => "ghost.local",
          "ssl" => false
        }
      }
    }
  end
end
