# Обновление Оркестратора под CentOS 8

Для обновления Оркестратора необходимо произвести следующие действия:

1.	Остановить службы WebApi, States, Notifications, MachineInfo, RobotLogs, RDP2.

2.	Переименовать папки в `/opt/Primo`: WebApi-old, States-old, Notifications-old, MachineInfo-old, RobotLogs-old, RDP2-old.

3.	Разархивировать WebApi-linux.zip, States-linux.zip, Notifications-linux.zip, MachineInfo-linux.zip, RobotLogs-linux.zip, RDP2-CentOS.zip, UI.zip в `/opt/Primo`.

4.	Перенести значения из старых файлов конфигурации в новые, не копируя сами файлы. Например, из `/opt/Primo/WebApi-old/appsettings.ProdLinux.json` копируем значения ConnectionStrings, OrchBaseUrl, RabbitMQ, License в `/opt/Primo/WebApi/appsettings.ProdLinux.json`.

5.	Повторить пункт 4 со службами MachineInfo, States, RDP2.

6.	Удаляем содержимое `/opt/Primo/WebApi/Logs`.

7.	Запустить от имени администратора скрипт для удаления очередей: 

```
#!/bin/bash

rabbitmqctl set_policy delque ".*" '{"expires": 1}' --apply-to queues
rabbitmqctl set_policy delex ".*" '{"expires": 1}' --apply-to exchanges
rabbitmqctl clear_policy delque
rabbitmqctl clear_policy delex
```

8.	Запускаем все службы: службы WebApi, Notifications, States, MachineInfo, States.

9.	В случае если служба WebApi не запускается, причина, как правило, будет в лог файле `/opt/Primo/WebApi/Logs`.

10.	В веб-интерфейсе Оркестратора переходим в **Настройки > Дистрибутив роботов** и загружаем из последнего дистрибутива оба файла для роботов на платформе Windows: Primo.Robot.x64.zip, Primo.Robot.x86.zip. А также файл Primo.Robot.x64-linux.zip для роботов на платформе Linux.

11.	Выделяем загруженные дистрибутивы и в веб-интерфейсе назначаем их основными, щелкнув на «Сделать основным».
