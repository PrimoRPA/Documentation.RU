# Получить текст

![](../../../resources/activities/basic/uiinteraction/image-894.png)

Компонент позволяет получить текст из выбранного элемента управления.

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство             | Тип                                  | Описание                                            |
| -------------------- | ------------------------------------ | --------------------------------------------------- |
| ***Процесс:***        | | |
| Шаблон поиска        | String                               | [Шаблон поиска](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/searchpatterns) элемента управления |
| Элемент              | [LTools.UIInteraction.Model.UIControl](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/els_uiinteraction/tipy-dannykh/uicontrol) | Ссылка на элемент управления |
| Область              | [System.Drawing.Rectangle](https://learn.microsoft.com/ru-ru/dotnet/api/system.drawing.rectangle?view=netcore-3.0) | Область поиска компонента |
| Текущий пользователь | Boolean                              | Определяет, нужно ли выполнять поиск только среди процессов текущего пользователя. По умолчанию отключено |
| Режим                | -                                    | Режим чтения текста. Доступные значения: 1) `Default` - по умолчанию; 2) `Native`; 3) `Native_Full`. <p>Если возникает проблема с чтением текста в режиме по умолчанию, следует переключить режим на Native или Native_Full. **Важно**: в режиме Native необходимо, чтобы весь искомый текст был виден на экране. Экран не должен перекрываться другими окнами! </p> |
| Цель                 | -                                    | Цель для перехвата текста. Помогает лучше распознавать текст в ПО, не поддерживающих UI Automation (как правило, это более старые программы). Работает только с режимом Native или Native Full, для режима Default игнорируется. <p>По умолчанию для цели установлено значение `GDI`. Если библиотека GDI не помогает получить нужный результат, попробуйте изменить значение на `USP10`</p> |
| Таймаут\*            | Int32                                | Предельное время ожидания завершения процесса (мс). По умолчанию `10000` мс |
| Строгий таймаут      | Boolean                              | Определяет, нужно ли незамедлительно прерывать выполнение элемента по истечении указанного времени в свойстве **Таймаут**. По умолчанию выключено - Робот может продолжать выполнение еще какое-то время, сверх установленного лимита, для полного обхода дерева контролов. На данный момент свойство **введено в тестовом режиме**, поэтому рекомендуется использовать его аккуратно |
| ***Вывод:***          |  |  |
| Переменная           | String                               | Переменная вывода для сохранения полученного текста          |
| Блоки текста         | List\<[LTools.Desktop.Model.DesktopTextBlock](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_uiinteraction/datatypes/textblock)\> | Переменная сохраняет полученный текст в виде сгруппированных блоков. Это опциональное свойство, которое является альтернативой строковой переменной и работает только с режимом Native или Native Full (в режиме Default переменная будет пустой). Используется для извлечения текстовых данных из форм/таблиц десктопных приложений. <p>Позволяет продолжить работу с полученным текстом в дальнейшем: например, найти координаты нужного слова, чтобы выполнить клик мышью. Координаты будут доступны, только если выбрана цель `GDI`. </p> <p>Для корректной работы свойства требуется, чтобы искомый текст отображался на экране при выполнении элемента Роботом, не перекрывался другими экранами, не был спрятан и т.д.</p>  |


