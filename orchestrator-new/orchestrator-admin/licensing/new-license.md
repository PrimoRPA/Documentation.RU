# Получение лицензии

Лицензия приобретается у вендора на основе запроса через интерфейс Оркестратора. 
Запрос лицензии создается на вкладке **Настройки ➝ Лицензии** с помощью кнопки **Запрос на лицензию**.

![](../../../../orchestrator-new/resources/orchestrator-admin/licensing/orch-license-request.png)

В результате откроется форма запроса лицензии.

![](../../../../orchestrator-new/resources/orchestrator-admin/licensing/orch-license-request-form.png)

В поле **Продукт** выберите подходящий [ЗАМЕНИТЬ ССЫЛКУ тип лицензий](https://docs.primo-rpa.ru/primo-rpa/orchestrator/settings/licensing) на решение Primo RPA.

Сохраните сформированный запрос в текстовый файл (например, `robot.txt`) и отправьте вендору. 
В ответ вендор пришлет файл лицензии с расширением \*.license (например, `robot.license`).

## Добавление лицензии в Оркестратор

Загрузите в Оркестратор полученный файл лицензии по кнопке **Добавить лицензию** (раздел **Настройки ➝ Лицензии**).

![](../../../../orchestrator-new/resources/orchestrator-admin/licensing/orch-license-add.png)

Убедитесь в валидности лицензии, а также в том, что ее срок не истек. 
Соответствующая информация отображается при проверке добавленной лицензии:

![](../../../../orchestrator-new/resources/orchestrator-admin/licensing/orch-license-validity.png)

Валидная непросроченная лицензия добавится в Оркестратор и отобразится в общем списке.

![](../../../../orchestrator-new/resources/orchestrator-admin/licensing/orch-license-list.png)

## Выдача лицензии на тенант

Внесенная в Оркестратор лицензия по умолчанию считается выданной на дефолтный тенант. 
Если лицензию нужно выдать на другой тенант, выделите ее и нажмите кнопку **Выдать на тенант**.

:bangbang: ***Лицензии между тенантами не делятся. У каждого тенанта свои лицензии.***

## Замена лицензии

Дата истечения лицензии подсвечивается индикатором процента истечения. Красный индикатор (100%) свидетельствует об истечении срока лицензии.

Если впоследствии произошла смена оборудования БД лицензий (ltoolslicense) Заказчиком, то лицензии, добавленные в Оркестратор, становятся невалидными. 
В этом случае лицензии требуется заменить, подробнее процесс замены описан [ЗАМЕНИТЬ ССЫЛКУ здесь](https://docs.primo-rpa.ru/primo-rpa/orchestrator/settings/licensing/change-license).
