# Список чатов

![](../../../../resources/activities/extra/messengers/autofaq/image-238.png)

Элемент, получающий список чатов AutoFAQ.

| Свойство             | Тип                                                    | Описание             |
| -------------------- | ------------------------------------------------------ | -------------------- |
| Соединение с AutoFAQ | Primo.Messaging.AutoFaq.AutoFaqSvc                     | Соединение с AutoFAQ |
| Страница             | int                                                    | Индекс страницы      |
| Размер               | int                                                    | Размер страницы      |
| ID оператора         | String                                                 | ID оператора         |
| Дата с               | DateTime                                               | Дата начала          |
| Дата по              | DateTime                                               | Дата окончания       |
| Статусы              | List\<String>                                          | Статусы чатов        |
| Чаты                 | List\<Primo.Messaging.AutoFAQ.Model. ConversationItem> | Список чатов         |

