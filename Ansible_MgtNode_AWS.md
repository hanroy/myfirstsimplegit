<h1>Ansible on AWS</h1>
--------------

<h4>Infra</h4>

>VM AWS Centos7 
Ansible2
Foreman

<h4>install ansible</h4>

    $ yum -y install git telnet openssl httpd  gcc g++ make automake autoconf curl-devel openssl-devel zlib-devel httpd-devel apr-devel apr-util-devel sqlite-devel rubygems
    $ rpm -iUvh http://dl.fedoraproject.org/pub/epel/7/x86_64/e/epel-release-7-8.noarch.rpm
    $ yum -y install python-pip
    $ pip install --upgrade pip
    $ yum -y update && yum -y install ansible

<h4>check version ansible</h4>

    $ ansible --version

<h4>modif /etc/hosts</h4> 

    $ cat /etc/hosts
    127.0.0.1 localhost
    127.0.0.1 ansible.mydomain.com ansible

<h4> create route 53</h4>

<h4>install foreman</h4>

    $ rpm -ivh http://yum.puppetlabs.com/puppetlabs-release-el-7.noarch.rpm
    $ yum -y install epel-release https://yum.theforeman.org/releases/latest/el7/x86_64/foreman-release.rpm
    $ yum install foreman
    $ foreman-installer
    
    Installing             Done                                               [100%] [..........................................................................................................]
      Success!
      * Foreman is running at https://ansible.mydomain.com
          Initial credentials are xxxx / xxxxxxxxxxxxxxxxxx
      * Foreman Proxy is running at https://ansible.mydomain.com:8443
      * Puppetmaster is running at port 8140
      The full log is at /var/log/foreman-installer/foreman.log



<h4>edit /etc/ansible/hosts and add remote machines</h4>

<h4>create ssh key</h4>

    $ ssh-keygen
    
    pass phrase : xxxxxxxx

<h4>send key to the remote machine</h4>

    $ ssh-copy-id -i ~/.ssh/id_rsa.pub root@1.1.1.1

<h4>check the connection to the remote machine</h4>

    $ ansible all -m ping -u root

 

<h4>make sure that from this host, ansible is able to login as root to all the other machines you are managing. To test this: </h4>

    $ ansible all -m shell -a id


