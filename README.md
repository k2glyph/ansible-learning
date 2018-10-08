# ansible-learning
Learning ansible with Windows and Control machine as linux server with the help of Virtual box and Vagrant.

Setting up Window Client:
net start WinRM

Set-Item -Path WSMan:\localhost\Client\TrustedHosts -Value *
winrm set winrm/config/client/auth '@{Basic="true"}'
winrm set winrm/config/service/auth '@{Basic="true"}'
Get-NetConnectionProfile | Set-NetConnectionProfile -NetworkCategory Private
winrm set winrm/config/service '@{AllowUnencrypted="true"}'

Testing Ping Pong:
ansible web -i inventory.yml -m win_ping
