# Интеграция с внешними системами 

## Интеграция через Webhooks

Для интеграции с внешними системами имеется возможность использовать Webhooks на события Оркестратора:

![](../../orchestrator-new/resources/deploy/integration-webhooks1.PNG)

Для этого требуется:

* Развернуть службу LogEventsWebhook\*, настроить её на получение событий из RabbitMQ и обращение к WebApi внешней системы. Внешних систем может быть несколько (на рисунке показано две). Для каждой из них используется своя очередь RabbitMQ через обменник (тип fanout) с именем eventswebhook и отдельный экземпляр службы LogEventsWebhook.
* Разработать и развернуть WebApi (интеграционный шлюз) с 2-мя end-point для приема событий от Webhooks: для авторизации (не обязательный) и для приема событий от Webhooks (обязательный). Этот WebApi заказчик разрабатывает самостоятельно в соответствии со спецификацией\**. 
* Разрешить Webhooks на события Оркестратора в конфигурационном файле Оркестратора. Разрешение настраивается в секции `Integration: EventWebhook:Enabled`:

```json
"Integration": {
    "EventWebhook": {
      "Enabled": true
    }
```

Любое событие Оркестратора распараллеливается по очередям через обменник eventswebhook.

После настройки интеграции проверить её работу можно, сопоставляя записи журнала Оркестратора с записями в хранилище, в котором сохраняются события от Webhooks во внешней системе, или её логам.
В качестве примера внешней системы, с которой происходит интеграция посредством LogEventsWebhook, поставляется служба ArcSight, которая конвертирует события в формат ArcSight и сохраняет их в виде текстовых файлов в папке обмена

> \* См. статьи [Установка LogEventsWebhook как службы под Windows 2016 Server](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/windows/additional-components-win/logeventswebhook-win) или [Установка LogEventsWebhook под CentOS](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/linux/additional-components-linux/logeventswebhook-linux-centos).\
> \*\* См. статью [Спецификация WebApi на прием событий Оркестратора](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/admin/webapi-spec/webapi-orc-events). 

## Аналитическая БД

Предагрегированная аналитическая информация о событиях содержится в аналитической БД.
