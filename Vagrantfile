Vagrant.configure(2) do |config|
  config.vm.box = "CentOS6.5"
  config.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.5.3/centos65-x86_64-20140116.box"
  config.vm.hostname = "vb.local"
  config.vm.network "private_network", ip: "33.33.33.10"
  config.vm.provision :shell, :inline => <<-EOT
    # yum
    rpm -Uvh http://ftp.iij.ad.jp/pub/linux/fedora/epel/6/x86_64/epel-release-6-8.noarch.rpm
    rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-6.rpm
    rpm -Uvh http://dev.mysql.com/get/mysql-community-release-el6-5.noarch.rpm
    yum -y update
    # iptables off
    service iptables stop
    chkconfig iptables off
    # localtime
    rm -rf /etc/localtime
    ln -s /usr/share/zoneinfo/Asia/Tokyo /etc/localtime
    # ntp
    yum -y install ntp
    service ntpd start
    chkconfig ntpd on
    # mysql
    yum -y install mysql-community-server
    service mysqld start
    chkconfig mysqld on
    mysql -u root -e "SET PASSWORD FOR root@localhost=PASSWORD('pass');"
    # phpmyadmin
    yum -y --enablerepo=remi,remi-php56 install phpMyAdmin
    cp /vagrant/provision/phpMyAdmin.conf /etc/httpd/conf.d/phpMyAdmin.conf
    # php
    yum -y --enablerepo=remi-php56 install php php-mcrypt php-mbstring php-pdo php-mysqlnd php-gd php-pecl-xdebug
    cp /vagrant/provision/php.ini /etc/php.ini
    cp /vagrant/provision/15-xdebug.ini /etc/php.d/15-xdebug.ini
    # apache
    yum -y install httpd
    chkconfig httpd on
    cp /vagrant/provision/httpd.conf /etc/httpd/conf/httpd.conf
    service httpd start
    # composer
    curl -sS https://getcomposer.org/installer | php
    mv composer.phar /usr/local/bin/composer
  EOT
end
