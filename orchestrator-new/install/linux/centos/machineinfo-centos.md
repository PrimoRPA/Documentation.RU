# Установка MachineInfo под CentOS 8

Подключаемся к серверу по SSH с пользователем с правами root. 
Создаем папку `/opt/Primo/MachineInfo`:

`sudo mkdir /opt/Primo/MachineInfo`

Разархивируем MachineInfo-linux.zip в `/opt/Primo/MachineInfo`:

`sudo unzip /srv/samba/shared/install/MachineInfo-linux.zip -d /opt/Primo/MachineInfo`
	
Создаем службу:

Переходим в каталог `/opt/Primo/MachineInfo`

`cd /opt/Primo/MachineInfo`

Копируем файл службы (идет с комплектом поставки) в `/etc/systemd/system`:
```
sudo cp Primo.Orchestrator.MachineInfo.service /etc/systemd/system/Primo.Orchestrator.MachineInfo.service
sudo systemctl daemon-reload
```
Помещаем службу в автозапуск:
	
`sudo systemctl enable /etc/systemd/system/Primo.Orchestrator.MachineInfo.service`
	
Даем права на запуск:

`sudo chmod -R 777 /opt/Primo/MachineInfo/Primo.Orchestrator.MachineInfo`

Проверяем выполнение команды

`sudo lsblk --nodeps -no serial /dev/sda`

Если она выполнится с ошибкой, находим вместо `/dev/sda` какое-то другое блочное устройство (диск) и прописываем его в конфигурационном файле:

![](../../../resources/install/linux/centos/install-linux-centos-machineinfo.PNG)

Стартуем службу:

`sudo systemctl start Primo.Orchestrator.MachineInfo`

Проверяем состояние службы:

`sudo systemctl status Primo.Orchestrator.MachineInfo`

Открываем порт на файерволе:
``
sudo firewall-cmd --zone=public --add-port=5051/tcp --permanent
sudo firewall-cmd --reload
``

Если используется один сервер с MachineInfo, в конфигурационном файле службы WebApi прописывается ссылка на него:

![](../../../resources/install/linux/centos/install-linux-centos-machineinfo2.PNG)

Timeout (по умолчанию 4 сек) – время ответа, после которого сервис считается не доступным.
Если используется кластер MachineInfo, или MachineInfo используется в гео-кластере, в конфигурационном файле службы WebApi прописываются ссылки на все узлы кластера:

![](../../../resources/install/linux/centos/install-linux-centos-machineinfo3.PNG)

Порядок узлов имеет значение. В момент генерации запроса на лицензию должны быть доступны все узлы. 

**Важно**: Узлы нельзя скрывать за лоадбалансером!

