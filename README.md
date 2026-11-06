# zabbix-lab
zabbix setup over ansible

Действующие лица: 3 ВМ debian trixie:
1. ansible, раздаёт конфигурацию zabbix, используя community.zabbix коллекцию.
2. vm1 клиент zabbix
3. vm2 сервер zabbix

Для доступа к веб интерфейсу сервера с хост машины на ansible поднят nginx реверс прокси, 
а также настроена маршрутизация между внутренней сетью vm1, vm2 и внешним миром через bridge сеть ansible.

В инвентаре inventory/hosts.yml описаны хосты, на которых осуществляется настройка.
ansible.cfg файл конфига для ansible, в нём явно указан путь к инвентарю и ssh ключу, используемый пользователь.
group_vars/all.yml файл с переменными, используемыми в плейбуках
В playbooks/
1. deploy_key.yml настраивает доступ для ansible по ключу ssh, без него ansible нужно явно указывать
2. deploy_zabbix_agent.yml настраивает установку zabbix клиента на vm1.
3. deploy_zabbix_server.yml настраивает установку zabbix сервера, postgreSQL, nginx, PHP.




