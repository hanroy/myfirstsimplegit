# Ansible on AWS

## Infra

- VM AWS Centos7
- Ansible2
- Foreman

## install ansible

```bash
$ yum -y install git telnet openssl httpd  gcc g++ make automake autoconf curl-devel openssl-devel zlib-devel httpd-devel apr-devel apr-util-devel sqlite-devel rubygems
$ rpm -iUvh http://dl.fedoraproject.org/pub/epel/7/x86_64/e/epel-release-7-8.noarch.rpm
$ yum -y install python-pip
$ pip install --upgrade pip
$ yum -y update && yum -y install ansible
```

## check version ansible

```bash    
$ ansible --version
```

## modif /etc/hosts 

```bash
$ cat /etc/hosts
127.0.0.1 localhost
127.0.0.1 ansible.mydomain.com ansible
```
##  create route 53

## install foreman

```bash
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
```

## edit /etc/ansible/hosts and add remote machines

## create ssh key

```bash
$ ssh-keygen
    
pass phrase : xxxxxxxx
```
## send key to the remote machine

```bash
$ ssh-copy-id -i ~/.ssh/id_rsa.pub root@1.1.1.1
```

## check the connection to the remote machine

```bash
$ ansible all -m ping -u root
```
 

## make sure that from this host, ansible is able to login as root to all the other machines you are managing. To test this: 
```bash
$ ansible all -m shell -a id
```

