# palmin-albert333_infra
palmin-albert333 Infra repository
#Домашняя работа к лекции №5
#адреса хостов
bastion_IP=178.154.246.168
someinternalhost_IP=10.130.0.22
#сквозное подключение
ssh -i ~/.ssh/id_rsa -At albert@178.154.246.168 ssh albert@10.130.0.22
#алиас
alias someinternalhost='ssh -i ~/.ssh/id_rsa -At albert@178.154.246.168 ssh albert@10.130.0.22'
