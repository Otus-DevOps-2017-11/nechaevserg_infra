# nechaevserg_infra
Хост bastion, IP: 35.195.149.39, внутр. IP: 10.132.0.2.
Хост: someinternalhost, внутр. IP: 10.132.0.3

Подключение одной стройкой к internalhost
ssh -tt appuser@35.195.149.39 ssh -tt appuser@10.132.0.3


Доп задание, openSSH версии 7,3 
в файле /root/.ssh/config на локальной пк прописываем

Host  bastion
        Hostname  35.195.149.39
        User appuser
        IdentityFile /root/.ssh/appuser
        Port 22

Host internalhost
        Hostname 10.132.0.3
        User appuser
        IdentityFile /root/.ssh/appuser
        Port 22
        ProxyCommand ssh -W %h:%p bastion
