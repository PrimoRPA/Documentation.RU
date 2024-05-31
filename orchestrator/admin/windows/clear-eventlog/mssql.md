# Настройка автоматической очистки событий Оркестратора для MSSQL

Разверните узел Агент SQL Server, откройте контекстное меню узла **Задания** и выберите **Управление расписаниями**:

![](../../../resources/admin/windows/clear-eventlog/1.-mssql-управление-расписаниями.png)

В диалоговом окне **Управление расписаниями** выберите **Создать**:

![](../../../resources/admin/windows/clear-eventlog/2.-mssql-создать.png)

В поле **Имя** введите имя нового расписания - **Каждые 30 минут**.\
Тип расписания - **Повторяющееся задание**. Задание будет выполняться ежедневно каждые 30 минут.\
Если не нужно, чтобы расписание вступило в силу немедленно после создания, снимите флажок **Включено**:

![](../../../resources/admin/windows/clear-eventlog/mssql.-очистка-событий.-свойства-расписания.png)


Создаем хранимую процедуру:

```TSQL
USE ltoolslogs;

CREATE PROC truncate_logs(
    @last_minutes INTEGER, 
    @max_database_size INTEGER)  
AS 
BEGIN
    DECLARE @database_size INTEGER;  
	SET @database_size = (SELECT total_size_mb = SUM(size)
                          FROM sys.master_files WITH(NOWAIT)
                          WHERE database_id = DB_ID() 
                          GROUP BY database_id);
    IF (@database_size > @max_database_size) BEGIN
       EXEC msdb.dbo.sp_delete_database_backuphistory @database_name = 'ltoolslogs';
       DELETE FROM OrchEvents 
       WHERE OrchTimestampUtc < DATEADD(mi, -@last_minutes, GETUTCDATE());
    END;
END;
```

Создаем задание, которое будет запускать эту хранимую процедуру по расписанию:

![](../../../resources/admin/windows/clear-eventlog/mssql.-очистка-событий.-создать-задание.png)

Вводим общие параметры задания:
* Имя - **Очистка журнала событий**; 
* Описание - **В БД ltoolslogs при достижении максимального размера БД в таблице OrchEvents удаляются старые записи - старше чем 30 минут**

![](../../../resources/admin/windows/clear-eventlog/4.-mssql-создание-задания-с-процедурой.png)

Задаем шаги задания: будет один шаг с именем шага **truncate_logs** и командой:
```
USE ltoolslogs;
EXEC truncate_logs  @last_minutes=30, @max_database_size=524288000;
```

![](../../../resources/admin/windows/clear-eventlog/6.-mssql-шаги-задания.png)

Задаем расписание. Чтобы выбрать готовое, нажимаем кнопку **Выбрать**:
  
![](../../../resources/admin/windows/clear-eventlog/7.-mssql-расписание-параметры.png)

Откроется список расписаний:
  
![](../../../resources/admin/windows/clear-eventlog/8.-mssql-выбор-расписания-для-задания.png)

Выбираем ранее созданное расписание **Каждые 30 минут**:
  
![](../../../resources/admin/windows/clear-eventlog/9.-mssql-выбор-2.png)

Нажимаем **ОК**. Задание **Очистка журнала событий** будет отображаться среди всех заданий:
  
![](../../../resources/admin/windows/clear-eventlog/10.-mssql-отображение-задания.png)

