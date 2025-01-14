# Компоненты системы

На схеме ниже приведены компоненты Оркестратора и их связи между собой, со Студией, роботами и внешними сервисами\*. 

> \* *Распределение по машинам серверной части может отличаться в зависимости от комплекта поставки и/или принятых в организации решений по развертыванию Системы. Некоторые сервисы не показаны на рисунке.*

![](../orchestrator-new/resources/Orch-components.PNG)

Оркестратор содержит следующие компоненты (подсистемы):

1.	**Серверы БД** (PostgreSQL 13 или MS SQL SERVER 2016+):
    * Основная БД с настройками Оркестратора – Main DB (ltools - здесь и далее физическое название БД, которое используется в конфигурационных файлах).
    * БД с пользователями и правами – Identity DB (ltoolsidentity).
    * БД с лицензиями – License DB (ltoolslicense).
    * БД с логом событий – Logs DB (ltoolslogs).
    * БД NuGet-сервера – NuGet DB (ltoolsnuget).
    * БД репозитория Ltw-файлов – LtwRepo DB (ltoolsltwrepo).
    * Аналитическая БД – Analytic DB (ltoolsanalytic)
2. **Серверы приложений**:
    * WebApi – REST веб-API.
    * NuGet-сервер.
    * RDP2 – служба для поддержки активных RDP-сессий для Windows-роботов. Также может использоваться для трансляции активных RDP-сессий в UI.
    * MachineInfo – служба определения параметров оборудования для работы с лицензиями.
    * Front – веб-сервер для отдачи статического контента (UI администрирования в браузере, SPA) и реверс-прокси для WebApi, RobotLogs, NuGet и RDP2 (Nginx или IIS).
    * States – служба вычисления системных состояний.
    * Notification – служба для рассылки уведомлений на email.
    * Analytic - служба сбора аналитики по событиям Оркестратора. Для автономной настройки запущенного сервиса Analytic может использоваться консольная утилита AnalyticConsole.
    * RobotLogs – служба приема логов от Роботов и от Оркестратора. Для автономной настройки запущенного сервиса RobotLogs может использоваться консольная утилита RobotLogsConsole.
    * LogEventsWebhook – служба интеграции логов посредством веб-хуков\*.
    * RabbitMQ – брокер очередей сообщений.
3. **Агент Оркестратора**. Agent устанавливается на машине Робота как служба и используется для управления Роботом\*\* и машиной Робота (логически является автономным продолжением Оркестратора на машине Робота). 
Если одна машина Робота делится между несколькими тенантами, то для каждого тенанта устанавливается отдельный Агент на своем порту (5002, 5003, 5004, ...).
Для автономной настройки запущенного сервиса Agent может использоваться консольная утилита AgentConsole. Для автоматического обновления агента используется утилита AgentUpdater.
4. **Программа для шифрования паролей в конфигурационных файлах**.

>  \* - Заказчик самостоятельно в соответствии со спецификацией разрабатывает интеграционный шлюз.  
>  \*\* - Не входит в комплект поставки, скачивается отдельно по предоставляемому вендором адресу.  

:bangbang: **Системное время всех серверов должно быть синхронизировано**


## Дополнительно

#### Grafana

В [комплект поставки](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/kit) также включена внешняя аналитическая система Grafana, 
которая технически не является компонентом Оркестратора. Ее стоит рассматривать как стороннее средство для получения/визуализации аналитики 
по работе Оркестратора. Может быть заменена на любое аналогичное средство. Инструкция по установке Grafana приведена в статьях [**Установка и настройка Grafana под Windows 2016 Server**](../../orchestrator-new/install/windows/additional-components-win/grafana-win.md) и 
[**Установка и настройка Grafana под CentOS 8**](../../orchestrator-new/install/linux/additional-components-linux/grafana-linux-centos.md).

#### SMTP-сервер

Оркестратор может выполнять почтовую рассылку о событиях. Для этого он должен быть настроен для подключения к SMTP-серверу организации.

#### POP3/IMAP-сервер

Оркестратор может выполнять чтение писем для срабатывания триггеров заданий. Для этого он должен быть настроен для подключения к POP3/IMAP-серверам организации или MS Exchange Server.


