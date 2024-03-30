# Домашнее задание к занятию "`Zabbix часть 1`" - `Латыпов Данияр`


### Задание 1

   Установите Zabbix Server с веб-интерфейсом.
   Процесс выполнения
      1. Выполняя ДЗ, сверяйтесь с процессом отражённым в записи лекции.
      2. Установите PostgreSQL. Для установки достаточна та версия, что есть в системном репозитороии Debian 11.
      3. Пользуясь конфигуратором команд с официального сайта, составьте набор команд для установки последней версии Zabbix с поддержкой PostgreSQL и Apache.
      4. Выполните все необходимые команды для установки Zabbix Server и Zabbix Web Server.
   
   
### Решение 1

Использованные команды:
   apt install postgresql

   wget https://repo.zabbix.com/zabbix/6.4/debian/pool/main/z/zabbix-release/zabbix-release_6.4-1+debian12_all.deb

   dpkg -i zabbix-release_6.4-1+debian12_all.deb

   apt update

   apt install zabbix-server-pgsql zabbix-frontend-php php8.2-pgsql zabbix-apache-conf zabbix-sql-scripts

   sudo -u postgres createuser --pwprompt zabbix

   sudo -u postgres createdb -O zabbix zabbix

   sed -i 's/# DBPassword=/DBPassword=123456789/g' /etc/zabbix/zabbix_server.conf

   systemctl restart zabbix-server zabbix-agent apache2

   systemctl enable zabbix-server zabbix-agent apache2

   ![admin panel](https://github.com/ka3-14bara/8-03-hw/blob/main/img/log-on-admin-panel.png)

---

### Задание 2

Установите Zabbix Agent на два хоста.

Процесс выполнения:
   1. Выполняя ДЗ, сверяйтесь с процессом отражённым в записи лекции.
   2. Установите Zabbix Agent на 2 вирт.машины, одной из них может быть ваш Zabbix Server.
   3. Добавьте Zabbix Server в список разрешенных серверов ваших Zabbix Agentов.
   4. Добавьте Zabbix Agentов в раздел Configuration > Hosts вашего Zabbix Servera.
   5. Проверьте, что в разделе Latest Data начали появляться данные с добавленных агентов.


---

### Решение 2

![hosts](https://github.com/ka3-14bara/8-03-hw/blob/main/img/hosts.png)

![log files on agent machines](https://github.com/ka3-14bara/8-03-hw/blob/main/img/log-files.png)

![latest data zabbix](https://github.com/ka3-14bara/8-03-hw/blob/main/img/latest_data.png)

![dashboard example](https://github.com/ka3-14bara/8-03-hw/blob/main/img/dashboard.png)

---
