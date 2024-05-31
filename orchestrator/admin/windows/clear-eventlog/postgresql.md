# Настройка автоматической очистки событий Оркестратора для PostgreSQL 

Инструкция предполагает работу с СУБД PostgreSQL, установленной на Windows 2016 Server. Настройка выполняется с помощью Stack Builder - утилиты для установки дополнительных инструментов и драйверов для PostgreSQL.

**Для настройки автоматической очистки событий выполните следующие шаги:**

1. Найдите на машине Application Stack Builder:

![](../../../resources/admin/windows/clear-eventlog/postgre.-очистка-логов.-application-stack-builder.png)

2. Выберите сервер установки и нажмите **Следующий**:

![](../../../resources/admin/windows/clear-eventlog/postgre.-очистка-логов.-выбор-сервера.png)

3. Выберите компонент **Категории** ➝ **Add-ons, tools and utilities** ➝ **pgAgent**:

![](../../../resources/admin/windows/clear-eventlog/postgre.-очистка-логов.-выбор-компонента.png)

4. Выберите каталог загрузки для установки пакета и нажмите **Следующий**.\
   В новом окне также нажмите **Следующий**: 

![](../../../resources/admin/windows/clear-eventlog/postgre.-очистка-логов.-выбор-каталога-загрузки.png)

5. В появившемся окне Setup pgAgent нажмите **Next**, в окне Upgrade Mode тоже нажмите **Next**:

![](../../../resources/admin/windows/clear-eventlog/postgre.-очистка-логов.-окно-setup.png)

6. Укажите детали подключения к серверу и нажмите **Next**:

![](../../../resources/admin/windows/clear-eventlog/postgre.-очистка-логов.-детали-подключения-к-серверу.png)

7. Укажите учетные данные службы pgAgent, нажмите **Next**:

![](../../../resources/admin/windows/clear-eventlog/postgre.-очистка-логов.-учетка-pgagent.png)

8. В результате появится сообщение о том, что схема pgagent создана.
9. Добавьте метод trust в файл `<Posgresql_folder>\data\pg_hba.conf` для `host   all             all             ::1/128`:

![](../../../resources/admin/windows/clear-eventlog/postgre.-очистка-логов.-метод-trust.png)

10. Запустите программу pgAdmin и подключитесь к серверу Postgresql.
11.	Создайте pgAgent Job:

![](../../../resources/admin/windows/clear-eventlog/postgre.-очистка-логов.-pgagent-job.png)

12.	Задайте название job и перейдите на вкладку Steps.
13.	Создайте шаг job. Укажите название **TruncLogs**. Нажмите **Edit**, выберите базу **ltoolslogs**.

![](../../../resources/admin/windows/clear-eventlog/postgre.-очистка-логов.-шаг-job.png)

14.	Перейдите на вкладку Code, укажите команду вызова процедуры:
```
CALL public.truncate_logs(30,524288000);
```
![](../../../resources/admin/windows/clear-eventlog/postgre.-очистка-логов.-вкладка-code.png)

15. Перейдите на вкладку Schedules, добавьте расписание. Укажите название **RunEvery30mins**. В поле Start укажите текущую дату и время.
16.	Перейдите на вкладку Repeat. В поле Hours выберите значение **\<Select All\>**. В поле Minutes выберите **00** и **30**:

![](../../../resources/admin/windows/clear-eventlog/postgre.-очистка-логов.-вкладка-repeat.png)

17. В завершение нажмите кнопку **Save**.


 
