# Решить hCapcha

![](../../../resources/activities/extra/2capcha/image-505.png)

Элемент, решающий капчу формата hCapcha

| Свойство   | Тип    | Описание                |
| ---------- | ------ | ----------------------- |
| Ключ API   | String | Ключ API                |
| URL API    | String | URL API                 |
| URL        | String | URL сайта с капчой      |
| Ключ сайта | String | Ключ hCapcha            |
| Тайм-аут   | Int32  | Тайм-аут                |
| Результат  | String | Результат разбора капчи |



**hCaptcha**

hCaptcha - это относительно новый вид капчи, который очень похож на reCAPTCHA

![](../../../resources/activities/extra/2capcha/image-801.png)

Принцип решения капчи довольно прост:

1. Найдите в исходном коде страницы значение параметра _data-sitekey_.
2. Поместите его в свойство Ключ сайта
3. Поместите полученный токен в скрытые элементы _h-captcha-response_ и _g-recaptcha-response_ и отправьте форму.

