# Оркестратор 23.7

Примечания к выпуску Оркестратора 23.7 описывают изменения для версии приложения, выпущенной в июле 2023 года.

### Новые функции
1. Добавлена [видеотрансляция](https://docs.primo-rpa.ru/primo-rpa/orchestrator/settings/register-rdp-users#translyaciya-rdp-sessii) активной RDP-сесии машины робота. Трансляция помогает быстрее понять, запустился ли робот, и отследить его действия в реальном времени. Функция не подразумевает перехват управления RDP-сессией и никоим образом не мешает ее работе. Запись видео не ведется. Чтобы трансляция была доступна в UI Оркестратора, у службы RDP2 должны быть установлены соответствующие настройки конфигурации. Просмотреть трансляцию можно:
   * в разделе **Настройки > Машины роботов > Все RDP-пользователи** выбранной машины. Окно трансляции вызывается из столбца **RDP-сессия активна** по кнопке **Консоль**.
   * в разделе **Все роботы** по нажатию кнопки **Консоль**. Опция доступна только, если робот и RDP-сесия активны.
3. Оптимизирована работа экземпляров Оркестратора при развертывании в одном кластере. Теперь в момент запуска им будет назначаться свой диапазон уникальных идентификаторов сущностей из базы данных. В результате мониторинг роботов, машин роботов и RDP-сессий со стороны Оркестратора будет выполняться быстрее.
4. Оптимизирована работа с RPA-проектами: больше не проверяется наличие файлов проекта на диске, поскольку их хранение перенесено в БД.
5. В БД ltools стала фиксироваться приостановка машин роботов: период, когда к серверу Оркестратора не подключена ни одна учетная запись робота.

### Исправленные ошибки
1. Пользователям с авторизацией через Active Directory были доступны неполные возможности UI Оркестратора, в отличие от внутренних пользователей. Данная ошибка исправлена, тип авторизации более не влияет на набор прав.
1. Для заданий с запуском по расписанию исправлен вывод значения в колонке **Следующая дата по расписанию**. Теперь оно отображается сразу после создания задания. Ранее - только после первого запуска.
1. При загрузке новой версии RPA-проекта не сохранялось состояние параметра **Закрыть RDP-сессию**. Ошибка исправлена - значение, установленное в момент загрузки, будет сохраняться. В том числе при назначении этой версии активной.
1. Исправлена ошибка, из-за которой при запуске WebApi брокер сообщений RabbitMQ не создавал в нем каналы.
1. В целях безопасности парольная фраза от сертификата PKCS12, для работы с RabbitMQ, стала шифроваться посредством утилиты PasswordEncryptor.zip (входит в комплект поставки). 
1. При различии временных зон Оркестратора и БД не происходило своевременного снятия блокировок триггеров. Ошибка исправлена.
1. Исправлен неправильный HTTP-статус ответа, который возвращается при ошибке «Попытка изменить статус элемента другим роботом». 

### Где скачать
Скачать комплект поставки Оркестратора 23.7 можно по этой [ссылке](http://disk3.primo-rpa.ru/index.php/s/t9BHBjR6PP06Yax?path=%2FArchive%2FOrchestrator). Он имеет название **Primo RPA Orchestrator 23.7.zip**.

Обращаем внимание, что робот Enterprise, который используется в Оркестраторе, [скачивается](http://disk3.primo-rpa.ru/index.php/s/t9BHBjR6PP06Yax?path=%2FArchive%2FRobot) отдельно от комплекта поставки. Архив с роботом имеет название **Primo RPA Robot Orchestrator <архитектура> 23.7.zip**.
