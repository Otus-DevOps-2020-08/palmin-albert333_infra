# palmin-albert333_infra\n
palmin-albert333 Infra repository\n
#Домашняя работа к лекции №5\n
#адреса хостов\n
bastion_IP=178.154.246.168\n
someinternalhost_IP=10.130.0.22\n
#сквозное подключение\n
ssh -i ~/.ssh/id_rsa -At albert@178.154.246.168 ssh albert@10.130.0.22\n
#алиас\n
alias someinternalhost='ssh -i ~/.ssh/id_rsa -At albert@178.154.246.168 ssh albert@10.130.0.22'\n
