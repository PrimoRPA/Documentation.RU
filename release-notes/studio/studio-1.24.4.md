# Primo Studio 1.24.4

История изменений в Primo Studio для Windows за апрель 2024-го года.


## Обновления и улучшения (режим Pro)

1. Улучшена работа со множеством окон в SAP: обеспечена возможность выбора элементов и взаимодействия в нескольких окнах одновременно, что упрощает параллельную работу с разными транзакциями.
1. Добавлены [сниппеты](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/snippets) (snippets) — короткие, часто используемые фрагменты кода. Функциональность позволяет удобно интегрировать их в существующие проекты без создания новых процессов. Сниппеты переносятся в рабочую область в качестве элементов, упрощая процесс разработки.
1. Добавлена возможность просматривать структуру каждого процесса проекта. Показ структуры можно включать или выключать в [настройках](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings#obshie) Студии.
1. Добавлена функция **Пауза** в раздел **Отладка**, позволяющая успешно приостанавливать и возобновлять процесс отладки с того места, где была сделана пауза.
1. Расширены возможности работы с JSON. Стала поддерживаться автоматическая десериализация не только в тип Dictionary, но и в различные типы коллекций, включая `List<T>`.
1. Робот стал записывать свою версию в лог при запуске процесса. Улучшение призвано облегчить разбор инцидентов.
1. Название корневого контейнера **Последовательность** стало соответствовать имени процесса, указанному при создании. 
1. Улучшено взаимодействие шаблона поиска (селектора) с Java-элементами через плагин **Java_ext**. Теперь плагин обеспечивает точное формирование селекторов как с применением, так и без использования свойства **Text**.
1. Лучше стал определяться селектор на кнопках десктоп-приложений **TWR ITC**. Инструмент осуществляет надежный поиск элементов в иерархии, улучшено восстановление исходного форматирования текста.
1. Улучшен новый редактор шаблона поиска для десктопных приложений. В окне выбора свойств элемента управления появилась возможность отключать «Быстрый поиск», включенный по умолчанию.
1. Добавлен элемент [**Удаление писем**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_mail/imap_deletemail), предназначенный для удаления почтовых сообщений по протоколу **IMAP**.
1. Добавлена функциональность в элемент [**Ветвь**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_logic/el_logic_branch) (Pick branch), позволяющая задать действие по умолчанию для ситуаций, когда не срабатывает ни одна из условных ветвей.
1. В элементе [**Фильтр диапазона**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_filterrange) (Filter Range, Excel) добавлена возможность фильтрации по нескольким критериям одновременно, что улучшает гибкость работы с данными Excel.
1. Для элемента **Ссылка на процесс** добавлена функция подсветки изменений, внесенных в аргументы подпроцесса. Теперь, когда пользователь вносит изменения в аргументы подпроцесса, это будет подсвечено. Подсветка исчезает после того, как произведено редактирование и назначение переменных в мастере.
1. Улучшена функция поиска элементов в проекте (`Ctrl+F`). Теперь результаты поиска включают как русскоязычные наименования активностей, так и их технические обозначения — имена классов.
1. Для переменных, содержащих массив, добавлена поддержка валидации значения по умолчанию. При некорректном вводе значения система подсветит ошибку.
1. Добавлено окно с предупреждением при попытке закрыть Студию во время выполнения или отладки процесса.
1. Улучшена работа элементов типа **Событие** (OCR, Рабочий стол, Файлы). Внесенные изменения позволяют корректно выполнять автоматизацию.
1. Оптимизирована работа с диаграммами. В блоке `Decision` добавлена функциональность, которая требует наличия условий хотя бы в двух или более ветках диаграммы. Если условия отсутствуют, система выведет сообщение о необходимости их задать.
1. Улучшена работа [Импорта](https://docs.primo-rpa.ru/primo-rpa/primo-studio/tools/import#zapusk-importa), включая корректную миграцию элементов `Now`, условий в блоках `Switch` и `Flow Switch`, а также путей и переменных в `Excel Workbook`.
1. В процессах с типом **Последовательность** появилась возможность выделять сразу несколько последовательных элементов, используя `Shift` + клик мышью на первом и последнем элементе.



## Исправленные ошибки (режим Pro)

1. Устранена причина аварийного завершения работы Студии при повторных попытках открыть большие ltw-файлы проекта. 
1. Сокращено время открытия больших процессов проекта, а также объем занимаемой оперативной памяти.
1. Устранена утечка памяти при закрытии вкладок процессов.
1. Оптимизировано потребление оперативной памяти при бездействии Студии.
1. Устранены причины ошибки "Index was out of range", возникавшей во время работы с процессом или при попытке сохранить проект/процесс.
1. Исправлена ошибка, из-за которой при открытии Студии не отображалась история ранее открытых проектов. 
1. Восстановлен порядок открытия вкладок процессов после перезапуска Студии. Теперь вкладки с процессами открываются в том же порядке, в котором они были открыты до закрытия/перезапуска Студии.
1. Внедрены изменения в систему **undo-redo**, улучшающие обработку действий и целостность элементов в диаграммах. Ранее в диаграммах наблюдались проблемы с некорректной отменой действий и разрывами связей между элементами.
1. Решена проблема, когда при открытии диаграммы изменялся ltw-файл. 
1. Исправлена ошибка, из-за которой Студия зависала при добавлении новой активности в рабочую область и последующем запуске отладки. Теперь добавление новых элементов и их отладка проходят без сбоев.
1. Исправлена ошибка, при которой робот зависал в процессе отладки при переходе по шагам в подпроцесс с ошибкой и последующем возобновлении отладки. Теперь отладка корректно продолжается до конца, как при шаге в подпроцесс с ошибкой, так и при последующем возобновлении процесса отладки.
1. Исправлена ошибка, из-за которой не получалось изменить точку останова в процессе **Чистый код** во время отладки, если было выбрано ядро отладчика v2. 
1. Исправлены следующие ошибки в работе контекстного меню элементов:
   * при выборе команды **Раскомментировать элементы** из последовательности могла пропасть область для добавления элементов или возникнуть ошибка «Ссылка на объект не указывает на экземпляр объекта»;
   * при повторном выборе команды **Раскомментировать элементы** или отмене действия возникала ошибка «Адресат вызова создал исключение»;
   * для элементов отображалась недействительная команда **Извлечь элементы из try/catch**.
1. Исправлена ошибка, связанная с некорректным свойством ContainerID в шаблоне поиска у вложенного элемента. Ошибка возникала при перетаскивании элемента с шаблоном из одного контейнера в другой.
1. Исправлен сброс настроек в шаблоне поиска, если элемент с шаблоном был перемещен или скопирован в контейнер.
1. Улучшена работа нового редактора шаблона поиска. Ранее, если пользователь выбирал подпункт меню, используя `F5`, и нажимал кнопку «Строить путь до выбранного элемента от корневого элемента», то редактор шаблона закрывался, а селектор не был сформирован. Теперь при выборе «Строить путь до...» предпринимается попытка построить путь, а в случае, когда это невозможно, кнопка «Строить путь до..» переходит в неактивное состояние, что позволяет избежать закрытия редактора шаблона.
1. Решена проблема с элементами управления, которые переставали определяться после использования функции «Строить путь до выбранного элемента...» (Рабочий стол, тип автоматизации UIAUTOMATION). 
1. Исправлена ошибка долгой валидации после выбора десктопного элемента управления. Теперь дерево контролов строится только по запросу, ускоряя выбор элементов. Также устранено подвисание малой формы при переключении на вкладку **Структура**.
1. Исправлена ошибка в браузерном шаблоне поиска, когда вместо текущего тега выбирался неверный тег, вызывая сбои при клике.
1. Исправлена ошибка в браузерном шаблоне поиска. Теперь подстановочный знак `*` корректно работает в поле **Text**. В редакторе шаблонов улучшена работа текстовых полей.
1. Устранена ошибка в работе шаблона поиска у элемента **Ввод текста**. Ранее, когда в шаблоне поиска элемент управления определялся по индексу, то опция очистки поля после ввода текста работала некорректно.
1. Исправлена ошибка поиска элемента управления при некорректном значении индекса. Ранее при некорректном индексе для выбора элемента система ошибочно выполняла его поиск и валидацию, что могло привести к нарушению работы.
1. Решена проблема с превышением времени ожидания в элементе **Клик текста мышью**.
1. Исправлена работа элемента **Прочитать таблицу**, обеспечивающая точное считывание сложных HTML-таблиц и корректное считывание данных при работе с мастером.
1. Внесены изменения в элемент **Изменить статус элемента очереди**, из списка статусов убраны недействительные значения. 
1. Исправлена ошибка в элементе **Параллельные потоки** с вложенным элементом **Ссылка на процесс**. Вызов подпроцесса с типом **Чистый код** приводил к зависанию робота, причина устранена.
1. Исправлена ошибка сохранения проекта при использовании ссылок на процессы. Ранее в проектах, содержащих два или более процесса с активностями **Ссылка на процесс**, кнопка **Сохранить проект** работала некорректно.
1. Исправлена ошибка в работе элементов **Запись диапазона** и **Чтение диапазона** с драйвером Interop.   
1. Исправлена ошибка в работе элемента **Присоединиться к приложению** (Рабочий стол), которая возникала при выборе типов автоматизации. Ошибка воспроизводилась, если в контейнер был вложен элемент первого поколения.
1. Восстановлена логика работы с новыми элементами в процессе. Теперь, при добавлении элемента в рабочую область, он по умолчанию становится активным, открывается панель с его свойствами.
1. Исправлена ошибка, из-за которой  вставка элемента комбинацией `Ctrl+V` осуществлялась в некорректном месте последовательности. 
1. Оптимизировано количество пользовательских действий для отмены изменений, связанных с вырезанием, вставкой, перемещением элемента в другое место.
1. Решена проблема с потерей индикаторов предупреждения ⚠️ в панели «Переменные». Ранее, если пользователь отменял предыдущие действия (`CTRL+Z`), у переменных пропадал данный индикатор, хотя изменения их не затрагивали.




## Режим Citizen

1. Элемент **Эмуляция спецкнопки** стал более простым и понятным в использовании. Для этого на панель элемента были вынесены поля:
   * *Основная кнопка* — основная клавиша, которая будет эмулирована;
   * *Модификатор* — кнопка-модификатор, которая позволяет добавить к основной клавише дополнительные функции (Ctrl, Shift, Alt);
   * *Дополнительная кнопка* — вторая клавиша в комбинации, если требуется. 
1. Исправлена ошибка в работе элемента **Фильтр таблицы**, которая появлялась при смене условий фильтрации с `И` на `ИЛИ`. Теперь активность функционирует корректно, без прерывания работы.
1. Исправлена ошибка перетаскивания элемента. Теперь элементы последовательности при перетаскивании перемещаются по рабочему пространству синхронно с курсором мыши.
1. Поля элементов перестали расширяться до размеров указанных в них значений.


## Где найти
[Скачать дистрибутив Primo RPA Studio Enterprise](http://disk3.primo-rpa.ru/index.php/s/t9BHBjR6PP06Yax?path=%2FRelease%2FStudio%2FWindows).

[Скачать дистрибутив Primo RPA Robot](http://disk3.primo-rpa.ru/index.php/s/t9BHBjR6PP06Yax?path=%2FRelease%2FRobot%2FWindows):
* **Primo RPA Robot 1.24.4** — предназначен для установки на локальной рабочей станции. Выступает в роли цифрового ассистента пользователя. Дистрибутив поставляется в разрядности x64 и x86.
* **Primo RPA Robot Orchestrator 1.24.4** — предназначен для автоматической установки Оркестратором. Дистрибутив поставляется в разрядности x64 и x86.