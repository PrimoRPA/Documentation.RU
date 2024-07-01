# Выбрать элемент

![](../../../resources/activities/basic/desktop/checked-element.png)

Компонент, производящий изменение состояния выбранного элемента управления (для чек-боксов и радио-кнопок).

## Свойства
| Свойство        | Тип                             | Описание                                           |
| --------------- | ------------------------------- | -------------------------------------------------- |
| Шаблон поиска   | String                          | Шаблон поиска элемента управления                  |
| Элемент         | Tools.Desktop. Model.DUIControl | Ссылка на элемент управления                       |
| Новое состояние | Boolean?                        | Новое состояние элемента                           |
| Состояние       | Boolean?                        | Текущее состояние элемента                         |
| Таймаут\*       | Int32                           | Предельное время ожидания завершения процесса (мс) |

## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):
> Для работы с примером необходимо установить приложение **mate-calc**. Режим калькулятора `Расширенный`.

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Калькулятор", 10000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска
app.SetChecked("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":null,\"TextSearchMode\":0,\"Items\":[{\"Name\":\"subscript\",\"Role\":\"toggle button\",\"Items\":[]}]}", true);
//Ссылка на элемент
LTools.Desktop.Model.DUIControl el = app.FindElement("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":null,\"TextSearchMode\":0,\"Items\":[{\"Name\":\"subscript\",\"Role\":\"toggle button\",\"Items\":[]}]}");
app.SetChecked(el, true);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, null, "Калькулятор", 10000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
#Шаблон поиска
app.SetChecked("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":null,\"TextSearchMode\":0,\"Items\":[{\"Name\":\"subscript\",\"Role\":\"toggle button\",\"Items\":[]}]}", True)
#Ссылка на элемент
el = app.FindElement("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":null,\"TextSearchMode\":0,\"Items\":[{\"Name\":\"subscript\",\"Role\":\"toggle button\",\"Items\":[]}]}")
app.SetChecked(el, True)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Калькулятор", 10000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска
app.SetChecked("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":null,\"TextSearchMode\":0,\"Items\":[{\"Name\":\"subscript\",\"Role\":\"toggle button\",\"Items\":[]}]}", true);
//Ссылка на элемент
var el = app.FindElement("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":null,\"TextSearchMode\":0,\"Items\":[{\"Name\":\"subscript\",\"Role\":\"toggle button\",\"Items\":[]}]}");
app.SetChecked(el, true);
```
{% endtab %}
{% endtabs %}
