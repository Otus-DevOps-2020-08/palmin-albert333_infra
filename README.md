# palmin-albert333_infra

palmin-albert333 Infra repository

## Домашнее задание к лекции №5

### Адреса для подключения:

bastion_IP = 178.154.246.168

someinternalhost_IP = 10.130.0.22

### Проверено сквозное подключение с помощью SSH Agent Forwarding (опция -A):

**localworksation** -> **bastion** -> **someinternalhost**
```
$ ssh-add ~/.ssh/id_rsa
$ ssh -i ~/.ssh/id_rsa -A albert@178.154.246.168
appuser@bastion:~$ ssh 10.132.0.22
```

### Проверка способа подключения от bastion к someinternalhost в одну команду:

#### 1) Использование ключа -t (Force pseudo-terminal allocation)
```ssh -i ~/.ssh/id_rsa -At albert@178.154.246.168 ssh albert@10.130.0.22```

#### 2). Настройкой в ~/.ssh/config на локальной машине:
```
Host bastion
    HostName 178.154.246.168
    User albert
    IdentityFile ~/.ssh/id_rsa

Host someinternalhost
    HostName 10.130.0.22
    User albert
    IdentityFile ~/.ssh/id_rsa
    ForwardAgent yes
    ProxyJump bastion
```
#### После правки конфига, вход осуществляется командой:
```ssh someinternalhost```
