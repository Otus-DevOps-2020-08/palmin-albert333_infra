## Домашнее задание к лекции №5

### Адреса для подключения:
```
bastion_IP = 178.154.246.168
someinternalhost_IP = 10.130.0.22
```
### Проверено сквозное подключение с помощью SSH Agent Forwarding (опция -A):

**localworksation** -> **bastion** -> **someinternalhost**
```
$ ssh-add ~/.ssh/id_rsa
$ ssh -i ~/.ssh/id_rsa -A albert@178.154.246.168
albert@bastion:~$ ssh 10.132.0.22
```

### Самостоятельная проверка подключения от bastion к someinternalhost в одну команду:

#### Использование ключа -t (Force pseudo-terminal allocation)
```ssh -i ~/.ssh/id_rsa -At albert@178.154.246.168 ssh albert@10.130.0.22```

#### Добавление алиаса
```alias someinternalhost='ssh -i ~/.ssh/id_rsa -At albert@178.154.246.168 ssh albert@10.130.0.22'```

#### После правки конфига, вход осуществляется командой:
```ssh someinternalhost```
