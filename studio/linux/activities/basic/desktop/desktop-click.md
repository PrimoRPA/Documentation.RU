# Клик мышью

![](../../../resources/activities/basic/desktop/image-239.png)

Компонент, производящий клик мышью на выбранном элементе управления. Компонент корректно работает только внутри контейнера Присоединиться к приложению.

## Свойства
| Свойство          | Тип                                   | Описание                                           |
| ----------------- | ------------------------------------- | -------------------------------------------------- |
| Шаблон поиска     | String                                | Шаблон поиска элемента управления                  |
| Элемент           | LTools.Desktop.Model.DUIControl       | Ссылка на элемент управления                       |
| Координаты        | System.Drawing.Rectangle              | Координаты клика курсора                           |
| Кнопка клавиатуры | LTools.Desktop.Model.KeyboardKeys     | Кнопка клавиатуры                                  |
| Кнопка мыши       | LTools.Desktop.Model.MouseButtons     | Кнопка мыши                                        |
| Позиция           | LTools.Common.Model.ClickPositions    | Позиция курсора при клике                          |
| Таймаут\*         | Int32                                 | Предельное время ожидания завершения процесса (мс) |

## Только код  
Пример использования элемента в процессе с типом **Только код** (Pure code):
> Для работы с примером необходимо установить приложение **mate-calc**.

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Калькулятор", 20000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска + Кнопка мыши + Клавиатура
app.Click("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":\"mate-calc\",\"TextSearchMode\":0,\"Items\":[{\"Name\":\"5\",\"Role\":\"push button\",\"Items\":[]}]}",
		LTools.Desktop.Model.MouseButtons.BUTTON_LEFT, LTools.Desktop.Model.KeyboardKeys.CTRL, LTools.Common.Model.ClickPositions.Center, 20000);
//Элемент
LTools.Desktop.Model.DUIControl el = app.FindElement("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":\"mate-calc\",\"TextSearchMode\":0,\"Items\":[{\"Name\":\"5\",\"Role\":\"push button\",\"Items\":[]}]}");
app.Click(el);
//Координаты
app.Click(new System.Drawing.Point(100, 150));
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Калькулятор", 20000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
#Шаблон поиска + Кнопка мыши + Клавиатура
app.Click("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":\"mate-calc\",\"TextSearchMode\":0,\"Items\":[{\"Name\":\"5\",\"Role\":\"push button\",\"Items\":[]}]}",
		LTools.Desktop.Model.MouseButtons.BUTTON_LEFT, LTools.Desktop.Model.KeyboardKeys.CTRL, LTools.Common.Model.ClickPositions.Center, 20000)
#Элемент
el = app.FindElement("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":\"mate-calc\",\"TextSearchMode\":0,\"Items\":[{\"Name\":\"5\",\"Role\":\"push button\",\"Items\":[]}]}")
app.Click(el)
#Координаты
app.Click(System.Drawing.Point(100, 150))
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Калькулятор", 20000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска + Кнопка мыши + Клавиатура
app.Click("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":\"mate-calc\",\"TextSearchMode\":0,\"Items\":[{\"Name\":\"5\",\"Role\":\"push button\",\"Items\":[]}]}",
	_lib.LTools.Desktop.Model.MouseButtons.BUTTON_LEFT, _lib.LTools.Desktop.Model.KeyboardKeys.CTRL, _lib.LTools.Common.Model.ClickPositions.Center, 20000);
//Элемент
var el = app.FindElement("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":\"mate-calc\",\"TextSearchMode\":0,\"Items\":[{\"Name\":\"5\",\"Role\":\"push button\",\"Items\":[]}]}");
app.Click(el);
//Координаты
app.Click(new _lib.System.Drawing.Point(100, 150, 0, 0));
```
{% endtab %}
{% endtabs %}
