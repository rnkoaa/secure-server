# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  name = 'cfssl-machine'
  config.vm.provider 'virtualbox' do |v|
    v.memory = 512
  end

  config.vm.box = "debian/stretch64"
  # `vagrant box outdated`. This is not recommended.
  config.vm.box_check_update = false

  config.vm.hostname = "#{name}.alpha.consul"
  config.vm.network 'private_network', ip: "192.168.33.10"
  # config.vm.synced_folder "workspace/", "/home/vagrant/workspace"
  # else
    # do nothing for now
    # end
    config.vm.provision 'shell', inline: <<-SHELL
      echo "==> Shell Provisioning"
      sudo apt-get update -y && sudo apt-get upgrade -y \
        && sudo apt-get -y install vim wget git zip unzip tree curl build-essential git zsh
      
      wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh || true
    
      file="/home/vagrant/.vimrc"
      if [ -f "$file" ]
      then
          echo ".vimrc exists, will not download again."
      else
        wget -q -O /home/vagrant/.vimrc https://raw.githubusercontent.com/amix/vimrc/master/vimrcs/basic.vim
        # curl -s -L -o /home/vagrant/.vimrc https://raw.githubusercontent.com/amix/vimrc/master/vimrcs/basic.vim
      fi
      
      mkdir downloads && cd downloads && wget -q https://dl.google.com/go/go1.10.2.linux-amd64.tar.gz
      tar -xvf go1.10.2.linux-amd64.tar.gz && sudo mv go /usr/local
      
      # setup zsh for easy access
      echo 'export PATH=$PATH:/usr/local/go/bin' >> /home/vagrant/.zsh_profile
      echo 'export PATH=$PATH:/home/vagrant/go/bin' >> /home/vagrant/.zsh_profile
      echo 'source /home/vagrant/.zsh_profile' >> /home/vagrant/.zshrc
      sudo chown vagrant:vagrant /home/vagrant/.zsh_profile
      # change the default shell to be zsh
      sudo chsh -s /bin/zsh vagrant
  SHELL

  config.vm.provision 'shell', privileged: false, inline: <<-SHELL
    wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh || true
     # setup zsh for easy access
     echo 'export PATH=$PATH:/usr/local/go/bin' >> /home/vagrant/.zsh_profile
     echo 'export PATH=$PATH:/home/vagrant/go/bin' >> /home/vagrant/.zsh_profile
     echo 'source /home/vagrant/.zsh_profile' >> /home/vagrant/.zshrc
     sudo chown vagrant:vagrant /home/vagrant/.zsh_profile
     # change the default shell to be zsh
     sudo chsh -s /bin/zsh vagrant

  SHELL
end
