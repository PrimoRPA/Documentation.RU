# Установка RobotLogs как службы под Windows 2016 Server

## 1. Базовая установка

Базовая установка – это установка на той же машине, где развернута служба WebApi.

Сначала требуется установить [RabbitMQ](../../orchestrator-new/install/windows/rabbitmq-windows.md).

Разархивируйте C:\Install\RobotLogs.zip в C:\Primo\RobotLogs. Можно при помощи PowerShell:
```
$InstallPath = "C:\Install"
Expand-Archive -LiteralPath "$InstallPath\RobotLogs.zip" -DestinationPath "C:\Primo\RobotLogs " -Force
```
Создайте системную переменную окружения (если не создана ранее). Для этого в PoweShell выполните команду:
```
[System.Environment]::SetEnvironmentVariable('ASPNETCORE_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
```
Настройте конфигурационный файл:
Настройте строки подключения в БД:

