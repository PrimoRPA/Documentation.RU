# Присутствие элемента

![](../../../resources/activities/basic/uiinteraction/image-571.png)

Компонент производит поиск элемента управления.

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство             | Тип                                         | Описание                                              |
| -------------------- | ------------------------------------------- | ----------------------------------------------------- |
| ***Процесс***           |  |  |
| Шаблон поиска\*      | String                                      | [Шаблон поиска](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/searchpatterns) элемента управления              |
| Область              | [System.Drawing.Rectangle](https://learn.microsoft.com/ru-ru/dotnet/api/system.drawing.rectangle?view=netcore-3.0)  | Область поиска компонента                             |
| Видимость            | Boolean                                     | Определяет, нужно ли проверять видимость элемента |
| Текущий пользователь | Boolean                                     | Определяет, нужно ли искать только среди процессов текущего пользователя. По умолчанию отключено   |
| Таймаут\*            | Int32                                       | Предельное время ожидания завершения процесса (мс). По умолчанию `10000`    |
| Строгий таймаут      | Boolean                                     | Определяет, нужно ли незамедлительно прерывать выполнение элемента по истечении указанного времени в свойстве **Таймаут**. По умолчанию выключено - Робот может продолжать выполнение еще какое-то время, сверх установленного лимита, для полного обхода дерева контролов. На данный момент свойство **введено в тестовом режиме**, поэтому рекомендуется использовать его аккуратно |
| ***Вывод***           |  |  |
| Элемент              | [LTools.UIInteraction.Model.UIControl](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_uiinteraction/tipy-dannykh/uicontrol) | Переменная для хранения ссылки на элемент управления  |
| Элементы             | List\<LTools.UIInteraction.Model.UIControl> | Переменная для хранения ссылок на элементы управления |
| Результат            | Boolean                                     | Переменная, хранящая результаты поиска                |
