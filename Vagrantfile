# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"
  config.vm.network "forwarded_port", guest: 80, host: 80
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y apache2
    cp -v /vagrant/apache2.conf /etc/apache2
    cp -v /vagrant/app.127.0.0.1.nip.io.config /etc/apache2/sites-available
    mkdir -p /var/www/app.127.0.0.1.nip.io/html
    a2ensite app.127.0.0.1.nip.io.config
    systemctl restart apache2
  SHELL
end
