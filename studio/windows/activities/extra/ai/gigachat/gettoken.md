# Получить токен

Элемент позволяет получить токен для работы с сервисом GigaChat.

![](../../../../resources/activities/extra/ai/gigachat/сбер-токен.png)

Элемент становится доступным после установки библиотеки **Primo.AI**. Найти его можно в группе элементов GigaChat на соответствующей панели:

![](../../../../resources/activities/extra/ai/gigachat/gigachat-on-panel.png)

Используйте сохраненный токен в элементе **Вопрос в чат**, чтобы вступить в диалог с нейросетевой моделью.

## Предварительные условия

Для получения токена вам потребуется указать в свойствах элемента авторизационные данные клиента. Ознакомьтесь с [инструкцией по работе с AI](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/ai#gigachat), чтобы узнать, как их получить.

![](../../../../resources/activities/extra/ai/gigachat/sber-auth-data.png)


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**GigaChat**:

1. **Секрет\*** *[String]* - название переменной с авторизационными данными клиента. 
1. **Тайм-аут\*** *[Int32]* - максимальное время ожидания выполнения запроса. Указывается в миллисекундах, по умолчанию `20000`.

**Вывод**:
* **Токен** *[String]* - название переменной для хранения полученного токена GigaChat. Токен действует в течение 30-ти минут с момента выпуска.

Пример заполнения свойств:

![](../../../../resources/activities/extra/ai/gigachat/сбер-свойства-токен.png)

