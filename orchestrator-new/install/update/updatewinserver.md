# Обновление Оркестратора под Windows Server 2016

Для обновления Оркестратора необходимо произвести следующие действия:

1.	Остановить службы WebApi (для Nginx), States, Notifications, MachineInfo, RobotLogs, RDP2.

2.	Переименовать папки в `C:\Primo`: 
* WebApi-old, States-old, Notifications-old, MachineInfo-old, RobotLogs-old, UI-old (для IIS); 
* nginx-1.21.1/html_old (для Nginx).

3.	Распаковать архивы WebApi.zip (для IIS: WebApi-IIS.zip), States.zip, Notifications.zip, MachineInfo.zip, RobotLogs.zip, RDP2.zip, UI.zip в папку `C:\Primo`.

4.	Только для IIS – скопировать файл в новую версию: `C:\Primo\UI\web.config`. 

5.	Перенести значения из старых файлов конфигурации в новые, не копируя сами файлы. Например, из `C:\Primo\WebApi-old\appsettings.ProdWin.json` скопировать значения ConnectionStrings, OrchBaseUrl, RabbitMQ, License в `C:\Primo\WebApi\appsettings.ProdWin.json`.

6.	Повторить пункт 5 со службами States, Notifications, MachineInfo, RobotLogs и RDP2.

7.	Удалить содержимое `C:\Primo\WebApi\Logs`. 

8.	Запустить от имени администратора скрипт для удаления очередей:

```
@ECHO OFF
set SBIN="C:\Program Files\RabbitMQ Server\rabbitmq_server-3.8.11\sbin"
cd /d %SBIN%
call rabbitmqctl.bat set_policy delque ".*" "{""expires"":1}" --apply-to queues
call rabbitmqctl.bat clear_policy delque
```
 
В случае ошибок выполнить две команды в PowerShell от имени администратора:
```
Copy-Item C:\Windows\System32\config\systemprofile\.erlang.cookie -Destination $env:USERPROFILE
Restart-Service -Name RabbitMQ 
```

9.	Запустить все службы: службы WebApi, States, Notifications, MachineInfo, RobotLogs, RDP2.
В случае, если служба WebApi не запускается, причина, скорее всего, будет в лог-файле `C:\Primo\WebApi\Logs`.

10.	В веб-интерфейсе Оркестратора перейти в **Настройки> Дистрибутив роботов** и загрузить из последнего дистрибутива:
* файлы для роботов на Windows: Primo.Robot.x64.zip, Primo.Robot.x86.zip; 
* а также файл Primo.Robot.x64-linux.zip для роботов на платформе Linux.

11.	Выделить загруженные дистрибутивы и в веб-интерфейсе назначить их основными, щелкнув на кнопку «Сделать основным».

12.	На машине Агента остановить службу Primo.Orchestrator.Agent.

13.	Переименовать папку `C:\Primo\Agent_old`.

14.	Разархивировать Agent.zip из скачанного дистрибутива.

15.	Перенести значения из старого файла конфигурации в новый, не копируя сам файл. Например, из `C:\Primo\Agent-old\appsettings.ProdWin.json`  копируем значения OrchBaseUrl в `C:\Primo\ Agent\appsettings.ProdWin.json`.

16. Запустить службу Primo.Orchestrator.Agent


