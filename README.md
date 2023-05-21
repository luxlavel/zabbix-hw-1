# Домашнее задание к занятию "`Zabbix part 1`" - `Lobakin Pavel`

---

### Задание 1

`Установите Zabbix Server с веб-интерфейсом.`

1. `# wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4+debian11_all.deb`
2. `# sudo dpkg -i zabbix-release_6.0-4+debian11_all.deb`
3. `# apt update`
4. `# apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-apache-conf zabbix-sql-scripts`
5. `# sudo -u postgres createdb -O zabbix zabbix`
6. `# zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix`
7. `Отредактируйте файл /etc/zabbix/zabbix_server.conf в поле DBPassword= ваш пароль`
8. `# systemctl restart zabbix-server apache2`
9. `# systemctl enable zabbix-server apache2`

![Домашняя страница Zabbix](https://github.com/luxlavel/zabbix-hw-1/blob/main/zabbix%20hw%201.png)

---

### Задание 2

`Установите Zabbix Agent на два хоста.`

1. `# wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4+debian11_all.deb`
2. `# sudo dpkg -i zabbix-release_6.0-4+debian11_all.deb`
3. `# apt update`
4. `# apt install zabbix-agent`
5. `# systemctl restart zabbix-agent apache2`
6. `# systemctl enable zabbix-agent apache2`
7. `Чтобы агент начал работать с нашим сервером, необходимо изменить настройки в файле zabbix_agentd.conf`
8. `sudo nano /etc/zabbix/zabbix_agentd.conf - В раздел Server добавьте адрес сервера или просто замените имеющийся`
9. `# systemctl restart zabbix-server apache2`

![скриншот раздела Configuration > Hosts, агенты подключены к серверу](https://github.com/luxlavel/zabbix-hw-1/blob/main/zabbix%20hw%201-2.png)
![скриншот лога zabbix agent](https://github.com/luxlavel/zabbix-hw-1/blob/main/zabbix%20hw%201-3.png)
![скриншот раздела Monitoring > Latest data](https://github.com/luxlavel/zabbix-hw-1/blob/main/zabbix%20hw%201-4.png)

---
