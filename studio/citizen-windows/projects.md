# Проекты

## Публикация проекта

Опубликовать готовый проект можно двумя способами:
* напрямую из Студии;
* в Оркестраторе.

### Публикация из Студии

Перейдите на вкладку меню **Оркестратор** и нажмите кнопку **Опубликовать**. В результате появится окно со списком проектов Оркестратора:

![alt](../../resources/Projects_ListToPublishInOrch.png)

В окне доступны действия:

* **Обновить** - обновляет список проектов, которые уже добавлены в Оркестратор.
* **Создать проект** - для загрузки нового проекта в Оркестратор.
* **Добавить версию** - помогает добавить новую версию проекта (обновить его). Перед нажатием кнопки выберите из списка проект, который желаете обновить.

При создании проекта отобразится окно конфигурации:

![alt](../../resources/Projects_PublishProject.png)

Данное окно аналогично окну добавления проекта в Оркестраторе.


### Публикация в Оркестраторе

Для того, чтобы опубликовать проект, сначала его нужно выгрузить в архив, а затем опубликовать через UI Оркестратора.

Для этого:

1. Перейдите в раздел **Файл > Экспорт > Упаковать проект**.
2. В диалоговом окне укажите имя будущего архива. Заархивируется вся папка проекта.
3. Добавьте архив через [интерфейс Оркестратора](https://docs.primo-rpa.ru/ru/orchestrator-new/orchestrator-user/add-rpa-project).

При этом необходимо следить за кодировкой файлов в архиве, особенно при использовании имен файлов на кириллице. 
Использовать кириллицу не рекомендуется, но при невозможности отказаться от нее, предпочтительнее применять кодировки `utf-8` и `cp866`.  

