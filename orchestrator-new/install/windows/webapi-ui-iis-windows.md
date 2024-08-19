# Установка WebApi и UI на IIS под Windows 2016 Server

:small_orange_diamond: Перед началом работы установите все последние обновления Windows.

### 1. Включение компьютера в AD 
(не требуется, если используется DHCP)

Перед установкой IIS настройте статический IP адрес и DNS. В DNS пропишите IP контроллера AD. Это нужно для включения компьютера в AD.

Правой кнопкой мыши щелкните по иконке «Network» в правом нижнем углу:

![](../../../orchestrator-new/resources/install/windows/iis-1-networkicon.PNG)

Во всплывающем меню выберите «Open Network and Sharing Center»:

![](../../../orchestrator-new/resources/install/windows/iis-2-popupwindow.PNG)

В открывшемся окне «Network and Sharing Center» в левом меню выберите «Change adapter settings»:

![](../../../orchestrator-new/resources/install/windows/iis-3-changeadapter.PNG)

В открывшемся окне «Network Connections» выберите сетевой адаптер и щелкните по нему правой кнопкой мыши:

![](../../../orchestrator-new/resources/install/windows/iis-4-networkconnections.PNG)

Во всплывающем меню выберите «Properties»:

![](../../../orchestrator-new/resources/install/windows/iis-5-properties.PNG)

В открывшемся окне «Ethernet Properties» щелкните по «Internet Protocol Version 4 (NCP/IPv4)»:

![](../../../orchestrator-new/resources/install/windows/iis-6-ethernetproperties.PNG)

В открывшемся окне «Internet Protocol Version 4 (NCP/IPv4) Properties» (рисунок 7) настройте параметры:

![](../../../orchestrator-new/resources/install/windows/iis-7-ipvproperties.PNG)

Выберите «Use the following IP address» и пропишите значения полей «IP address», «Subnet mask» и «Default gateway». 
> Для VM значения этих полей можно узнать командой ipconfig

Выберите «Use the following DNS server addresses» и пропишите в поле «Preferred DNS server» IP контроллера домена.

Для удобства дальнейших настроек поменяйте имя компьютера, например, на «IIS». В главном меню Windows выберите пункт «Settings»:

![](../../../orchestrator-new/resources/install/windows/iis-8-winsettings.PNG)

В открывшемся окне «Settings» выберите пункт меню «System»:

![](../../../orchestrator-new/resources/install/windows/iis-9-settingssystem.PNG)

И потом «About»:

![](../../../orchestrator-new/resources/install/windows/iis-10-settingssystemabout.PNG)

При помощи кнопки «Rename PC» переименуйте компьютер, дождитесь перезагрузки.

Здесь же присоедините компьютер к AD:

![](../../../orchestrator-new/resources/install/windows/iis-11-joindomain.PNG)

Нажмите кнопку «Join a domain» и выберите имя AD:

![](../../../orchestrator-new/resources/install/windows/iis-12-domainname.PNG)

Нажмите кнопку «Next» и введите логин/пароль доменной учетной записи:

![](../../../orchestrator-new/resources/install/windows/iis-13-domainloginpw.PNG)

Добавьте информацию о доменной учетной записи на компьютер, выбрав «Account type» = «Administrator»:

![](../../../orchestrator-new/resources/install/windows/iis-14-domainaddacc.PNG)

Перезагрузите компьютер:

![](../../../orchestrator-new/resources/install/windows/iis-15-domainrestartpc.PNG)

После перезагрузки компьютера появится возможность входа в AD с доменной учетной записью:

![](../../../orchestrator-new/resources/install/windows/iis-16-primosignin.PNG)

## 2. Установка IIS

Войдите в систему с локальной учетной записью Administrator:

![](../../../orchestrator-new/resources/install/windows/iis-17-iisadmin.PNG)

В «Server Manager» (откроется автоматически после входа в систему, также его можно запустить из главного меню), выберите «Add Roles and Features»:

![](../../../orchestrator-new/resources/install/windows/iis-18-addroles.PNG)

В «Before you begin» нажмите кнопку «Next»:

![](../../../orchestrator-new/resources/install/windows/iis-19-addrolesbegin.PNG)

В «Installation Type» оставьте выбор по умолчанию:

![](../../../orchestrator-new/resources/install/windows/iis-20-addrolesinstalltype.PNG)

В «Server Selection» оставьте по умолчанию:

![](../../../orchestrator-new/resources/install/windows/iis-21-addrolesserversel.PNG)

В «Server Roles» выберите «Web Server (IIS)»:

![](../../../orchestrator-new/resources/install/windows/iis-22-addroles-roles.PNG)

В «Features» оставьте выбор по умолчанию:

![](../../../orchestrator-new/resources/install/windows/iis-23-addroles-features.PNG)

В «Web Server Role (IIS)» нажмите кнопку «Next»:

![](../../../orchestrator-new/resources/install/windows/iis-24-addroles-webserver.PNG)

В «Role Services» выберите «HTTP Redirection» и «Windows Authentication»:

![](../../../orchestrator-new/resources/install/windows/iis-25-addroles-roleservices.PNG)

:small_orange_diamond: «WebDAV Publishing» выбирать нельзя. Если он выбран ранее – требуется его отключить, сняв галку.

В «Confirmation» нажмите кнопку «Install» и дождитесь завершения установки:

![](../../../orchestrator-new/resources/install/windows/iis-26-addroles-confirm.PNG)

### 3. Разворачивание узлов веб-приложения

Откройте оснастку для управления IIS:

![](../../../orchestrator-new/resources/install/windows/iis-27-iismngmnt.PNG)

Создайте системную переменную окружения ASPNETCORE_ENVIRONMENT= ProdWin. Для этого в PoweShell выполните команду:
```
[System.Environment]::SetEnvironmentVariable('ASPNETCORE_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
```
Для узла WebApi создайте отдельный неуправляемый Application Pool с наименованием Primo.WebApi, 
**Start Mode = AlwaysRunning и Regular Time Interval (minutes) = 0** (чтобы пулл приложений не выгружался, так как при выгрузке сломается работа фоновых служб приложения).

Добавление Application Pool:

![](../../../orchestrator-new/resources/install/windows/iis-28-apppool.PNG)

Параметры Application Pool:

![](../../../orchestrator-new/resources/install/windows/iis-29-apppool-param1.PNG)

![](../../../orchestrator-new/resources/install/windows/iis-29-apppool-param2.PNG)

Добавлен Application Pool с наименованием Primo.WebApi:

![](../../../orchestrator-new/resources/install/windows/iis-30-apppool-primo.PNG)




