# Получить сообщения

![](../../../../resources/activities/extra/messengers/telegram/image-43.png)

Элемент, получающий сообщения из чата Telegram.

| Свойство              | Тип                                                   | Сообщение                                     |
| --------------------- | ----------------------------------------------------- | --------------------------------------------- |
| Соединение с Telegram | Primo.Messaging.TelegramMsg. TelegramSvc              | Соединение с Telegram                         |
| Начиная с             | DateTime?                                             | Получит сообщения начиная с заданного времени |
| Буфер\*               | int                                                   | Размер буфера сообщений                       |
| Сообщения             | List\<Primo.Messaging.TelegramMsg. Model.ChatMessage> | Массив полученных сообщений                   |
| ID чата\*             | String                                                | ID чата                                       |
