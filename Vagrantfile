# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure('2') do |config|
  config.vm.provider 'virtualbox' do |vb|
    vb.memory = 2048
    vb.cpus = 2
  end

  config.vm.define 'katarina-master' do |master|
    master.vm.box = 'bento/ubuntu-24.04'
    master.vm.hostname = 'katarina-master'
    master.vm.network 'private_network', ip: '10.0.0.10'
  end

  %w[worker1 worker2].each_with_index do |name, i|
    config.vm.define "katarina-#{name}" do |worker|
      worker.vm.box = 'bento/ubuntu-24.04'
      worker.vm.hostname = "katarina-#{name}"
      worker.vm.network 'private_network', ip: "10.0.0.#{i + 11}"
    end
  end
end
