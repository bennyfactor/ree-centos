# -*- mode: ruby -*-
# vi: set ft=ruby :

$packages = <<PACKAGES

yum install -y rpmdevtools readline-devel ncurses-devel gdbm-devel db4-devel ruby
yum groupinstall -y 'Development Tools'

PACKAGES

$script = <<SCRIPT

rpmdev-setuptree

ln -s /vagrant/spec/ruby-enterprise.spec ~/rpmbuild/SPECS/ruby-enterprise.spec
for i in `ls /vagrant/patches/`; do ln -s /vagrant/patches/$1 ~/rpmbuild/SOURCES/$1; done

cd /tmp
wget "https://storage.googleapis.com/google-code-archive-downloads/v2/code.google.com/rubyenterpriseedition/ruby-enterprise-1.8.7-2012.02.tar.gz#ecf4a6d4c96b547b3bf4b6be14e082ddaa781e83ad7f69437cd3169fb7576e42"
cp ruby-enterprise-1.8.7-2012.02.tar.gz ~/rpmbuild/SOURCES/

SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "generic/centos7"
  config.vm.provision "shell", inline: $packages
  config.vm.provision "shell", inline: $script, privileged: false
end
