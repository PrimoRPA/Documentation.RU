# Установка и обновление

Primo RPA Orchestrator (далее в тексте - Orchestrator, Оркестратор) может быть установлен на операционных системах семейств Windows (Windows 2019 Server, Windows 2016 Server) и Linux (Astra Linux 1.7, Cent OS 8, РЕДОС).


## Установка на Linux

Процедура установки Оркестратора на операционной системе Linux (на примере Ubuntu Server 22.04) описана в статье [**Установка Primo RPA Orchestrator на Ubuntu Server 22.04**](../../orchestrator-new/install/linux/install-on-ubuntu.md).

В общем виде, развертывание Оркестратора предполагает выполнение следующих шагов в указанном порядке:

1. Установка **PostgreSQL** - Скачайте и установите соответствующую вашей операционной системе версию, используя [инструкцию](https://www.postgresql.org/download/). Затем выполните шаги по подключению по сети и созданию пользователей согласно статье [**Установка PostgreSQL под CentOS 8**](../../../orchestrator-new/install/linux/centos/postgres-centos.md).

2. Установка **RabbitMQ** - Скачайте и установите нужную версию, используя инструкции для [Debian, Ubuntu и основанных на них дистрибутивах](https://www.rabbitmq.com/docs/install-debian), либо инструкции для [RPM дистрибутивов](https://www.rabbitmq.com/docs/install-rpm).  
Далее следуйте инструкции, описанной в статье [Установка RabbitMQ под CentOS 8](../../../orchestrator-new/install/linux/centos/rabbitmq-centos.md).

4. Установка **nginx** - установите nginx из репозиториев. Подробно установка nginx описана в документе [Установка Nginx под CentOS 8](../../../orchestrator-new/install/linux/centos/nginx-centos.md).

4. Установка **UI** - общий порядок установки UI (на примере CentOS 8) описан в документе [Установка UI под CentOS 8](../../../orchestrator-new/install/linux/centos/ui-centos.md).

5. Установка **WebApi** - описание процесса установки (на примере Cеnt OS 8) находится в документе [Руководство по установке WebApi](../../../rchestrator-new/install/linux/centos/webapi-centos.md)

> **Дальнейшие пункты (6-10) могут выполняться в произвольном порядке.**

6. Установка **RDP2** - информацию об установке RDP2 на машине с ОС Astra Linux 1.7 и CentOS 8 можно найти в соответствующих документах: [Руководство по установке RDP2 под Astra Linux 1.7](../../../orchestrator-new/install/linux/astra/RDP2-astra.md) и [Руководство по установке RDP2 под CentOS 8](orchestrator-new/install/linux/centos/rdp2-centos.md).

7. Установка **States** - выполните установку службы согласно [инструкции по установке](../../../orchestrator-new/install/linux/centos/states-centos.md).

8. Установка **RobotLogs** - процесс установки данной службы описан в статье [Установка RobotLogs под CentOS 8](../../../orchestrator-new/install/linux/centos/robotlogs-centos.md).

9. Установка **Notifications** - установите службу, следуя [инструкции](../../../orchestrator-new/install/linux/centos/notifications-centos.md).

10. Установка **MachineInfo** - порядок установки MachineInfo описан в [данной статье](../../../orchestrator-new/install/linux/centos/machineinfo-centos.md)



## Установка на Windows

В общем виде, процедура установки Оркестратора на операционной системе Windows аналогична процедуре для ОС Linux и предполагает выполнение перечисленных указанных ниже шагов.

Существует два варианта установки Оркестратора на ОС Windows: с использованием nginx и с использованием IIS. 
Кроме того, возможно использование как PostgreSQL, так и MSSQL.

Порядок установки:

1. Установка **PostgreSQL** либо **MSSQL**. 
    * Для PostgreSQL: Скачайте и установите соответствующую вашей операционной системе версию, используя [инструкцию](https://www.postgresql.org/download/). Затем выполните шаги по подключению по сети и созданию пользователей согласно статье [**Установка PostgreSQL под Windows 2016 Server**](../../orchestrator-new/install/windows/postgres-windows.md).
    * Для MSSQL: Установите версию, соответствующую имеющейся у вашей компании лицензии. Выполните специфические настройки, описанные в [статье](../../orchestrator-new/install/windows/mssql-windows.md)

2. Установка **RabbitMQ** - Скачайте и установите нужную версию, используя инструкции для [установки под Windows](https://www.rabbitmq.com/docs/install-windows).  
Далее следуйте инструкции, описанной в статье [Установка RabbitMQ под Windows 2016 Server](../../orchestrator-new/install/windows/rabbitmq-windows.md).

3. Установка **UI** и **WebApi** для **nginx** или **IIS**.
    * Для nginx: [Скачайте](https://nginx.org/ru/download.html) и установите nginx. Также ознакомьтесь с информацией на [сайте продукта](https://nginx.org/ru/docs/windows.html).
    После установки выполните действия, [описанные в инструкции](../../orchestrator-new/install/windows/nginx-windows.md).   
    Для установки UI используйте статью [Установка UI на nginx](../../orchestrator-new/install/windows/ui-nginx-windows.md).  
    Порядок установки WebApi описан в статье [Установка WebApi](../../orchestrator-new/install/windows/webapi-windows.md).  
    * Для IIS: Используйте инструкцию [Установка WebApi и UI на IIS под Windows 2016 Server](../../orchestrator-new/install/windows/webapi-ui-iis-windows.md).
4. 


НАХОДИТСЯ В РАБОТЕ

## Видео-инструкции к пошаговой установке Оркестратора

Видео по установке Оркестратора на Windows Server 2019 с WebApi (IIS) можно просмотреть [здесь](https://rutube.ru/video/9bb248ccced157536cbf8af50b038012/).


Nginx: [Установка Оркестратора на веб-сервер Nginx](https://rutube.ru/video/53ac25d2c3128bdd6cea7d055e88255b/)