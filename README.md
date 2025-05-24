# Домашнее задание к занятию "`Система мониторинга Zabbix`" - `Киямов Максим`


---

### Задание 1

`Задание 1
Установите Zabbix Server с веб-интерфейсом.

Процесс выполнения
Выполняя ДЗ, сверяйтесь с процессом отражённым в записи лекции.
Установите PostgreSQL. Для установки достаточна та версия, что есть в системном репозитороии Debian 11.
Пользуясь конфигуратором команд с официального сайта, составьте набор команд для установки последней версии Zabbix с поддержкой PostgreSQL и Apache.
Выполните все необходимые команды для установки Zabbix Server и Zabbix Web Server.
Требования к результатам
Прикрепите в файл README.md скриншот авторизации в админке.
Приложите в файл README.md текст использованных команд в GitHub.`

Решение:

sudo apt install postgresql

sudo apt install wget -y

sudo wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_latest_6.0+debian11_all.deb

sudo dpkg -i zabbix-release_latest_6.0+debian11_all.deb

sudo apt update

apt install zabbix-server-pgsql zabbix-frontend-php php8.3-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent

sudo -u postgres createuser --pwprompt zabbix

sudo -u postgres createdb -O zabbix zabbix

sudo zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix

Отредактир файл /etc/zabbix/zabbix_server.conf

DBPassword=my_password

sudo systemctl restart zabbix-server apache2

sudo systemctl enable zabbix-server apache2

![Запущенный Zabbix](https://github.com/Fizic666/sys-pattern-homework/blob/main/8.3-1.jpg)


---

### Задание 2

Задание 2
Установите Zabbix Agent на два хоста.

Процесс выполнения
Выполняя ДЗ, сверяйтесь с процессом отражённым в записи лекции.
Установите Zabbix Agent на 2 вирт.машины, одной из них может быть ваш Zabbix Server.
Добавьте Zabbix Server в список разрешенных серверов ваших Zabbix Agentов.
Добавьте Zabbix Agentов в раздел Configuration > Hosts вашего Zabbix Servera.
Проверьте, что в разделе Latest Data начали появляться данные с добавленных агентов.
Требования к результатам
Приложите в файл README.md скриншот раздела Configuration > Hosts, где видно, что агенты подключены к серверу
Приложите в файл README.md скриншот лога zabbix agent, где видно, что он работает с сервером
Приложите в файл README.md скриншот раздела Monitoring > Latest data для обоих хостов, где видны поступающие от агентов данные.
Приложите в файл README.md текст использованных команд в GitHub

Решение

sudo -s

wget https://repo.zabbix.com/zabbix/6.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest_6.0+ubuntu24.04_all.deb

dpkg -i zabbix-release_latest_6.0+ubuntu24.04_all.deb

apt update.

apt install zabbix-agent

systemctl restart zabbix-agent

systemctl enable zabbix-agent


![](https://github.com/Fizic666/sys-pattern-homework/blob/main/8.3-2.jpg)`

![](https://github.com/Fizic666/sys-pattern-homework/blob/main/8.3-3.jpg)`

![](https://github.com/Fizic666/sys-pattern-homework/blob/main/8.3-4.jpg)`


