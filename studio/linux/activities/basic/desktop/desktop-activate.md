# Активировать окно

![](../../../resources/activities/basic/desktop/activate-window.png)

Компонент, выводящий окно процесса на передний план. Компонент корректно работает только внутри контейнера Присоединиться к приложению.

## Свойства
| Свойство          | Тип    | Описание                                           |
| ----------------- | -----  | -------------------------------------------------- |
| Заголовок         | String | Заголовок окна |
| Заголовок (RegEx) | String | Заголовок окна (регулярное выражение) |

## Только код  
Пример использования элемента в процессе с типом **Только код** (Pure code):
> Для работы с примером необходимо установить приложение **mate-calc**.

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Калькулятор", 10000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.ActivateWindow("Калькулятор");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Калькулятор*", 10000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
app.ActivateWindow("Калькулятор")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Калькулятор", 10000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.ActivateWindow("Калькулятор");
```
{% endtab %}
{% endtabs %}
