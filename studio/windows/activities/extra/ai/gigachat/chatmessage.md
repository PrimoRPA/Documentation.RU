# Вопрос в чат

Элемент позволяет отправить вопрос в сервис GigaChat.

![](../../../../resources/activities/extra/ai/gigachat/сбер-токен.png)

Элемент становится доступным после установки библиотеки **Primo.AI**. Найти его можно в группе элементов GigaChat на соответствующей панели:

![](../../../../resources/activities/extra/ai/gigachat/gigachat-on-panel.png)

В переменной вывода вернется ответ от нейросетевой модели.


## Предварительные условия

Для успешной отправки вопроса сначала следует [получить токен](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai/gigachat/el_gettoken). Токен действует в течение 30-ти минут, после чего его потребуется обновить.


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**GigaChat**:

1. **Творчество\*** *[Double]* — творческая составляющая ответа. В значении укажите число от 0 до 1. Чем выше значение, тем более непредсказуемым будет результат выполнения запроса. По умолчанию `0.5`.
1. **Тайм-аут\*** *[Int32]* — максимальное время ожидания выполнения запроса. Указывается в миллисекундах, по умолчанию `20000`.

**Запрос**:

1. **Токен\*** *[String]* — токен запроса. Указывается в виде переменной или константы.
1. **Вопрос\*** *[String]* — текст вопроса.
1. **Роль\*** *[String]* — имя роли в чате. По умолчанию `"user"`.

**Вывод**:
* **Ответ** *[String]* — переменная для хранения ответа GigaChat. 

Пример заполнения свойств:

![](../../../../resources/activities/extra/ai/gigachat/сбер-свойства-вопрос.png)

## Просмотр ответа

Чтобы просмотреть ответ GigaChat, установите [точку останова](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/debug#tochka-ostanova) и запустите [отладку](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/debug) процесса. На панели [**Вывод**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/debug#panel-vyvod) откройте текущее значение переменной:

![](../../../../resources/activities/extra/ai/gigachat/сбер-переменная-ответа.png)

Пример отладки процесса с записью ответа в консоль:

![](../../../../resources/activities/extra/ai/gigachat/сбер-отладка.png)

## Полезные материалы

* [Как формулировать запросы к GigaChat](https://developers.sber.ru/help/gigachat/prompt-guide);
* [Примеры удачных запросов](https://developers.sber.ru/help/gigachat/prompt-examples);
* [Ответы на общие вопросы о GigaChat](https://developers.sber.ru/help/gigachat/faq).



