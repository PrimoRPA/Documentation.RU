## Системные требования для работы Primo Studio Linux на операционной системе Линукс

Для установки и эксплуатации Primo Studio Linux компьютер пользователя должен соответствовать требованиям из таблицы.

:small_orange_diamond: ***Требования указаны без расчета учетных записей. Каждая учетная запись требует дополнительно 10 Гб свободного пространства на жестком диске.***

|                         |     Минимальные     |      Рекомендуемые    |
| ----------------------- | ------------------- | ----------------------|
| CPU                     |        2 ядра       |         4 ядра        |
| Оперативная память      | 4 Гб (возможно существенное замедление работы) |  8 Гб и выше |   
| Свободное место на HDD  | 64 Гб + 10 Гб (+ 10 Гб на каждую учетную запись) | 100 Гб + 10 Гб (+ 10 Гб на каждую учетную запись) |
| Монитор                 | 1280 x 720 | 1920 x 1080 или выше |

Системные требования для всех продуктов Primo RPA приведены [здесь](https://docs.primo-rpa.ru/primo-rpa/#sistemnye-trebovaniya).

### Рекомендации по организации дискового пространства на сервере  

**1. Разработка роботов в Primo Studio на сервере**
- Корневой раздел - необходимо 60 ГБ свободного пространства. 
- Необходимо также дополнительно зарезервировать по 10 Гб на каждого пользователя для создания проектов роботов. Пространство для проектов роботов может быть зарезервировано либо в разделе, где расположена папка `./home`, либо в отдельном разделе.


**2. Запуск роботов Primo на терминальном сервере**
- Корневой раздел - не менее 10 ГБ свободного пространства для логов и временных файлов.
- На каждого робота необходимо зарезервировать не менее 100МБ. Некоторые роботы создают много скриншотов (которые удаляются после работы робота), поэтому для таких роботов нужно до 200МБ.


 
