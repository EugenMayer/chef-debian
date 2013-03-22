Vagrant.configure('2') do |config|
  if ENV['WHEEZY']
    config.vm.box     = 'debian-7.0'
    config.vm.box_url = 'https://reaktor-vm.s3.amazonaws.com/vagrant/debian-7.0-rc1_chef-11.4.0.box'
  else
    config.vm.box     = 'debian-6.0'
    config.vm.box_url = 'https://reaktor-vm.s3.amazonaws.com/vagrant/debian-6.0.7_chef-11.4.0.box'
  end

  config.vm.provision :chef_solo do |chef|
    chef.log_level = :debug if ENV['DEBUG']

    recipes = ENV['RECIPES'] || 'default'
    recipes.split.each do |recipe|
      chef.add_recipe "debian::#{recipe}"
    end
  end
end
