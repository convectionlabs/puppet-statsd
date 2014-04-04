# -*- mode: ruby -*-
# vi: set ft=ruby :

#fail "You must set PUPPET_HOME to proceed" if ENV['PUPPET_HOME'] == nil
PUPPET_HOME= ENV['PUPPET_HOME']

Vagrant.configure("2") do |config|
  config.vm.hostname = 'puppet-statsd'
  config.vm.synced_folder "modules", "/tmp/puppet-modules"
  config.vm.synced_folder ".", "/tmp/puppet-modules/statsd"

  config.vm.define "centos" do |centos|
    centos.vm.box     = 'centos64'
    centos.vm.box_url = 'http://puppet-vagrant-boxes.puppetlabs.com/centos-64-x64-vbox4210.box'
    centos.vm.provision :puppet do |puppet|
      puppet.manifests_path = "tests"
      puppet.manifest_file  = "vagrant.pp"
      puppet.options        = ["--modulepath", "/tmp/puppet-modules"]
    end
  end

  config.vm.define "ubuntu" do |ubuntu|
    ubuntu.vm.box     = 'ubuntu64'
    ubuntu.vm.box_url = 'http://puppet-vagrant-boxes.puppetlabs.com/ubuntu-server-12042-x64-vbox4210.box'
    ubuntu.vm.provision :puppet do |puppet|
      puppet.manifests_path = "tests"
      puppet.manifest_file  = "vagrant.pp"
      puppet.options        = ["--modulepath", "/tmp/puppet-modules"]
    end
  end
end