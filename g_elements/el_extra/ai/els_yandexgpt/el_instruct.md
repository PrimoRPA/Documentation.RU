# Задать вопрос

Задает вопрос YandexGPT в асинхронном режиме. Используйте этот элемент, если ваш вопрос не требует срочного ответа. В асинхронном режиме генерация текста займет больше времени, но ответ будет качественнее и дешевле.

![](<../../../../.gitbook/assets1/задать вопрос.png>)


Элементы группы YandexGPT, включая **Задать вопрос**, становятся доступными после установки в Студии библиотеки **Primo.AI**:

![](<../../../../.gitbook/assets1/yandexgpt-items.png>)


## Предварительные условия

Для успешного создания чата вам потребуется знать [ID папки в Yandex Cloud и IAM-токен](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/ai#yandexgpt).


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**YandexGPT**:

1. **ID папки\*** *[String]* — идентификатор папки в Yandex Cloud. Значение в виде переменной или константы. 
1. **Токен\*** *[String]* — IAM-токен запроса, указывается в виде переменной или константы. Время жизни IAM-токена не превышает 12-ти часов, но рекомендуется запрашивать его каждый час.
1. **Творчество\*** *[Double]* — творческая составляющая ответа. В значении укажите число от 0 до 1. Чем выше значение, тем более непредсказуемым будет результат выполнения запроса. По умолчанию `0.5`.
1. **Макс. длина\*** *[Int32]* — максимальная длина пары «запрос-ответ» в символах. По умолчанию `4000`. Значение не должно превышать 4700 символов.
1. **Тайм-аут\*** *[Int32]* — максимальное время ожидания выполнения запроса. Указывается в миллисекундах, по умолчанию `20000`.

**Запрос**:

* **Вопрос\*** *[String]* — текст вашего вопроса.

**Вывод**:
* **Ответ** *[String]* — переменная для хранения ответа от бота. 

Пример заполнения свойств:

![](<../../../../.gitbook/assets1/parameters-WFInstruct-2.png>)






