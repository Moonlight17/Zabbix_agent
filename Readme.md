# Установка zabbix-agent 4.0.12
1. На сервер скачиваем архив zabbix-agent 4.0.12
2. Разархивируем его, далее выполняем:

	* ./configure zabbix-agent
	* Make
	* cd ./zabbix-4.0.12/src/zabbix_agent/

3. Создаем директорию в (sudo mkdir /etc/zabbix/)
4. Помещаем конфигурационный файл в /etc/zabbix/zabbix.conf
5. Из дистрибутива версии 2.2 берем файл /contents/etc/zabbix –agent и помещаем в /etc/init.d/zabbix-agent/ раздела системы
6. Создаем пользователя
	
    * su -
	* addgroup --system --quiet zabbix
	* adduser --quiet --system --disabled-login --ingroup zabbix --home /var/lib/zabbix --no-create-home zabbix
	
7. Папке /run/zabbix/ и /var/lov/zabbix/ настраиваем права для созданного пользователя командами:

	* chown zabbix /run/zabbix/
	* chown zabbix /var/log/zabbix/

8. Добавим демона zabbix-agent в автозагрузку и следующей командой запустим его:

	* sudo update-rc.d zabbix-agent defaults
	* sudo service zabbix-agent start

