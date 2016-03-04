Vagrant.configure(2) do |config|
  config.vm.box = "phusion/ubuntu-14.04-amd64"

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    
    # Make sure the en_US.UTF-8 locale works properly
    echo 'export LC_ALL="en_US.utf8"' >> ~/.bash_profile
    source ~/.bash_profile
    sudo locale-gen en_US.UTF-8 
    sudo dpkg-reconfigure locales
    
    # Install Git
    sudo apt-get install -y git
    
    # Install rbenv
    git clone https://github.com/rbenv/rbenv.git ~/.rbenv
    cd ~/.rbenv && src/configure && make -C src
    echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
    echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
    source ~/.bash_profile 
    cd
    
    # Install ruby-build
    git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
    
    # Install a recent version op Ruby
    sudo apt-get install -y autoconf bison build-essential libssl-dev libyaml-dev libreadline6-dev zlib1g-dev libncurses5-dev libffi-dev libgdbm3 libgdbm-dev
    rbenv install 2.3.0
    rbenv global 2.3.0
    echo 'gem: --no-document' >> ~/.gemrc
    
    # Install bundler
    gem install bundler
    
    # Install a recent version of Postgres
    echo "echo 'deb http://apt.postgresql.org/pub/repos/apt/ trusty-pgdg main' >> /etc/apt/sources.list.d/pgdg.list" | sudo sh
    wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
    sudo apt-get update
    sudo apt-get install -y postgresql-9.5 postgresql-server-dev-9.5
  SHELL
end
