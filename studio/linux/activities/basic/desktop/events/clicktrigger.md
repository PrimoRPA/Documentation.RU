---
Description: Click trigger
---

# Клик элемента

![](../../../../resources/activities/basic/desktop/events/click-trigger-base.png)

Компонент, ожидающий событие нажатия мыши в окне приложения.

Для работы активности с типом [регистратора событий](/g_elements/el-linux/el-linux-basic/els-browser/els-events/event-recorder) уровня файла HID необходимо установить утилиту `Evtest` и дать права на чтения всех файлов по пути `/dev/input`.

### Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

1. **Шаблон поиска** *[String]* - Шаблон поиска элемента управления
1. **Заголовок** *[String]* - Заголовок подключаемого приложения
1. **Имя процесса** *[String]* - Имя процесса
1. **Основная кнопка** *[LTools.Common.Model. MouseButtons]* - Основная кнопка
1. **Модификатор** *[Avalonia.Input.KeyModifiers]* - Кнопка-модификатор (Ctrl, Shift...)
1. **Дополнительная кнопка** *[Avalonia.Input.KeyModifiers]* - Дополнительная кнопка
1. **Область** *[System.Drawing.Rectangle]* - Область клика мышью
1. **Тип регистратора событий** *[LTools.Common.Model.SystemEventsObservers.InputDeviceEventsObservers.Base.InputDeviceEventsObserverTypes]* - Тип [регистратора событий](/g_elements/el-linux/el-linux-basic/els-browser/els-events/event-recorder) в системе

