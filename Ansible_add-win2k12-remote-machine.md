<h1>Ansible windows 2012 deployement</h1>


<h4>On Ansible Management node execute the following cmd line</h4>

    $ pip install "pywinrm>=0.1.1"
    $ yum -y install python-devel krb5-devel krb5-libs krb5-workstation
    $ pip install kerberos requests_kerberos

<h4>On the remote machine windows 2012 Execute the below powershell command line</h4>

    $ Set-ExecutionPolicy Unrestricted

<h4>Download the powershell script file  and execute it on the windows remote machine</h4> 
[https://github.com/stylersnico/ansible/blob/115aaeb17c4e13d6ef8420acd7143fddbf33ea5f/examples/scripts/ConfigureRemotingForAnsible.ps1](https://github.com/stylersnico/ansible/blob/115aaeb17c4e13d6ef8420acd7143fddbf33ea5f/examples/scripts/ConfigureRemotingForAnsible.ps1)

<h4>On Ansible Mgmt Node add the remote machine IP on /etc/ansible/hosts</h4>

<h4>check the winrm connection via  « win_ping » </h4> 

    $ ansible AWSTest -i /etc/ansible/win2k12 -m win_ping --ask-vault-pass

 


