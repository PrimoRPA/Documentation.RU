# Установка MS SQL Server 2019 и MS SQL Management Studio

Раздел содержит инструкцию по установке MS SQL Server 2019 и MS SQL Management Studio (далее - MS SQL MS) под Windows 2016 Server. 

**Для установки выполните шаги:**

1. Запустите установку MSSQL SERVER из `C:\Install\MSSQL.zip\SQL2019-SSEI-Dev.exe`.
2. Установите MS SQL MS из `C:\Install\MSSQL.zip\SSMS-Setup-RUS.exe`.
3. Установите PowerShell из `C:\Install\PowerShell-7.1.3-win-x64.msi`.
4. Включите учетную запись суперпользователя **sa** базы данных. Для этого запустите MS SQL Management Studio:

![](../../resources/admin/windows/install-mssql-start.png)

5\. В разделе Security выберите параметр для **Аутентификации сервера** в соответствии с рисунком ниже:

![](../../resources/admin/windows/install-mssql-2.png)

6\. Не перезагружаясь, в свойствах суперпользователя **sa** введите пароль 2 раза:

![](../../resources/admin/windows/install-mssql-3.png)

7\. В этом же окне в разделе Status включите **Login**. Перезагрузите сервер:

![](../../resources/admin/windows/install-mssql-4.png)

8\.	При подключении к базе данных в MS SQL Management Studio выберите нужную **аутентификацию**, введите **логин** и **пароль**, как показано на рисунке:

![](../../resources/admin/windows/install-mssql-5.png)

9\. Последовательно выполните команды  из файла `C:\Install\MSSQL.zip\get_cpu_hdd_host.txt` - они требуются для определения параметров оборудования. Если для этого используется сервис MachineInfo, то выполнять команды не нужно.

![](../../resources/admin/windows/install-mssql-6.png)

![](../../resources/admin/windows/install-mssql-7.png)

![](../../resources/admin/windows/install-mssql-8.png)

![](../../resources/admin/windows/install-mssql-9.png)

![](../../resources/admin/windows/install-mssql-10.png)

![](../../resources/admin/windows/install-mssql-11.png)

![](../../resources/admin/windows/install-mssql-12.png)

:red_circle: **При создании процедуры get_cpu_hdd_host нужно следить, чтобы случайно не внести изменения в текст скрипта. Недопустимо вносить даже не значимые с точки зрения кода скрипта пробелы, пустые строки и менять регистр!**

10\.	Разрешите удаленное подключение к серверу БД:

![](../../resources/admin/windows/install-mssql-13.png)

11\. При помощи утилиты `C:\Windows\System32\SQLServerManager15.msc` включите TCP/IP для сервера БД. Название и расположение файла зависит от версии и установки MS SQL SERVER:

![](../../resources/admin/windows/install-mssql-14.png)

12\. Перезапустите службу:

![](../../resources/admin/windows/install-mssql-15.png)
