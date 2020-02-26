$script = <<SCRIPT
echo "Installing Golang"
sudo apt-get install wget -y 
VERSION=1.14
OS=linux
ARCH=amd64
wget -q https://dl.google.com/go/go$VERSION.$OS-$ARCH.tar.gz
sudo tar -C /usr/local -xzf go$VERSION.$OS-$ARCH.tar.gz
VAR="export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin"
echo "$VAR" >> ~/.profile
SET_GOPATH="GOPATH=$HOME/go" 
echo "$SET_GOPATH" >> ~/.profile
SET_GOBIN="GOBIN=$HOME/go/bin"
echo "$SET_GOBIN" >> ~/.profile
echo "install finish."
rm -rf go$VERSION.$OS-$ARCH.tar.gz

SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp/bionic64"
  config.vm.hostname = "go"
  config.vm.provision "shell", inline: $script, privileged: false

  # Increase memory for Parallels Desktop
  config.vm.provider "parallels" do |p, o|
    p.memory = "1024"
  end

  # Increase memory for Virtualbox
  config.vm.provider "virtualbox" do |vb|
        vb.memory = "1024"
  end

end
