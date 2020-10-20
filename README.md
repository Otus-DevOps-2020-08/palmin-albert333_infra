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

## Домашнее задание к лекции №6

### Адрес и порт для подключения:

testapp_IP = 84.201.172.30
testapp_port = 9292

## Домашнее задание к лекции №7

### Выполненные действия

- Создана ветка **packer-base** в репозитории;

- Скрипты с прошлого ДЗ перенесены в папку **config-scripts**;

- Установлен **Packer**;

- Создан сервисный аккаунт **packeruser**, делегированы права, создан и экспортирован **account-key**;

- Создан шаблон **ubuntu16.json** для **packer**;

- Созданы скрипты для **provision** образа;

- Выполнена проверка шаблона и запущена сборка;

- Исправлена ошибка, из-за которой сборка образа завершалась на:


```
Build 'yandex' errored: Failed to find instance ip address: instance has no one IPv4 external address.
```

- Создана ВМ на основе собранного образа;

- Установлено и проверено приложение **reddit**;

- Переменные
`service_account_key_file`, `folder_id` и `source_image_family`
вынесены в отдельный файл **variables.json**;

- Добавлены дополнительные опции:
`zone`, `preemptible`;

Создан **bake** образ, с установленным приложением **reddit**;

Создан скрипт `create-reddit-vm.sh` для создания машины с помощью Yandex.Cloud CLI
