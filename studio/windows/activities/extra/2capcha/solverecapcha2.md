# Решить ReCapcha v2

![](../../../resources/activities/extra/2capcha/image-832.png)

Элемент, решающий капчу формата ReCapcha v2

| Свойство   | Тип    | Описание                |
| ---------- | ------ | ----------------------- |
| Ключ API   | String | Ключ API                |
| URL API    | String | URL API                 |
| URL        | String | URL сайта капчи         |
| Ключ сайта | String | Ключ капчи reCapcha     |
| Невидимая  |        | Призак невидимой капчи  |
| Тайм-аут   | Int32  | Тайм-аут                |
| Результат  | String | Результат разбора капчи |



**reCaptcha V2**

reCAPTCHA V2, также известная как "Я не робот" reCAPTCHA, очень популяна и выглядит вот так:

![](../../../resources/activities/extra/2capcha/image-604.png)



Решить reCAPTCHA V2 с помощью нашего нового метода очень легко, это не требует эмуляции браузера:

1. Посмотрите исходный код элемента на странице, где вы встретили reCAPTCHA.

![](../../../resources/activities/extra/2capcha/image-486.png)

1. Найдите ссылку, которая начинается с _www.google.com/recaptcha/api2/anchor_ или найдите параметр _data-sitekey_.
2. Скопируйте значение параметра _k_ из ссылки или значение _data-sitekey_.

![](../../../resources/activities/extra/2capcha/image-587.png)

3\.  Найдите элемент с id _g-recaptcha-response_ и сделайте его видимым, удалив параметр _display:none_.

![](../../../resources/activities/extra/2capcha/image-500.png)

**Внимание:** иногда содержимое страницы генерируется динамически и вы можете не найти данный элемент.\
В таком случае вам нужно изучить скрипты, отвечающие за генерацию содержимого страницы. Опция "Inspect" в Google Chrome может помочь в этом.

4\.  На странице отобразится текстовое поле. Всё что вам остается сделать — вставить полученный токен в это поле и отправить форму.

![](../../../resources/activities/extra/2capcha/image-475.png)

5\.  Поздравляем, вы решили reCAPTCHA!
