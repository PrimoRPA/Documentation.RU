# Ввод текста

![](../../../resources/activities/basic/uiinteraction/input-text-activity.png)

Компонент позволяет ввести текст в выбранный элемент управления. Инструмент ![](<../../../.gitbook/assets/image (794).png>), который расположен на компоненте, позволяет автоматически заполнить [шаблон поиска](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/searchpatterns) нужного элемента управления.

Если элемент управления относится к определенному приложению, сначала используйте контейнер [**Присоединиться к приложению**](https://docs.primo-rpa.ru/primo-rpa/g_elements/linuks/el-linux-basic/els-desktop/el-desktop-attach), а уже в него поместите **Ввод текста**.

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

***Процесс:***
1. **Текст** *[String]* - Текст, который нужно ввести. Пример: `"text"`.
1. **Защищенный текст** *[SecureString]* - Для вставки зашифрованного текста. Например, пароля пользователя, который не должен храниться в открытом виде.
1. **Режим** - Выберите режим ввода текста: *INVOKE* (по умолчанию) или *SIMULATE*. Режим *INVOKE* производит вставку текста, *SIMULATE* - эмулирует ввод текста с клавиатуры и предназначен для тех приложений, где ввод через *INVOKE* не поддерживается (например, в 1С).
1. **Шаблон поиска** *[String]* - Шаблон поиска элемента управления. Доступно заполнение вручную в формате JSON (через редактор), либо автоматически при помощи инструмента ![](<../../../.gitbook/assets/image (794).png>).
1. **Элемент** *[LTools.UIInteraction.Model.UIControl]* - Переменная со ссылкой на элемент управления, который был найден и сохранен ранее. Если заполнено это свойство, шаблон поиска указывать не нужно.
1. **Таймаут\*** *[Int32]* - Предельное время ожидания завершения процесса (мс).

***Эмуляция:***
1. **Пауза** *[Int32]* - Пауза между нажатиями в мс (**несовместимо с новым ядром**). Чем меньше пауза, тем быстрее будет введен текст.
1. **Очищать** *[Boolean]* - Определяет, нужно ли очистить область ввода перед вставкой текста. По умолчанию выключено - не очищается.
1. **Фокус** *[Boolean]* - Устанавливает фокус ввода в элементе управления. По умолчанию фокус включен.