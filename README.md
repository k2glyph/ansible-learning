# Ansible-Learning
---
##### Learning ansible with Windows and Control machine as linux server with the help of Virtual box and Vagrant.
## Installing Ansible on Control Machine.
1. sudo apt install python-pip
2. sudo apt install markupsafe
3. sudo apt install xmltodict
4. sudo apt install pywinrm
5. sudo apt install ansible
## Testing ansible version:
`ansible --version`
```
ansible 2.7.0
config file = /home/vagrant/pluralsight/ansible.cfg
configured module search path = [u'/home/vagrant/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
ansible python module location = /usr/local/lib/python2.7/dist-packages/ansible
executable location = /usr/local/bin/ansible
python version = 2.7.6 (default, Nov 23 2017, 15:49:48) [GCC 4.8.4]
```
## Setting up Window Client:
```
net start WinRM
Set-Item -Path WSMan:\localhost\Client\TrustedHosts -Value *
winrm set winrm/config/client/auth '@{Basic="true"}'
winrm set winrm/config/service/auth '@{Basic="true"}'
Get-NetConnectionProfile | Set-NetConnectionProfile -NetworkCategory Private
winrm set winrm/config/service '@{AllowUnencrypted="true"}'
```
## Testing Ping Pong:
`ansible web -i inventory.yml -m win_ping`
#### Response:
```
192.168.56.3 | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
```
