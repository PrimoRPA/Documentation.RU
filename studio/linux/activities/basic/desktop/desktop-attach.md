# Присоединиться к приложению

![](../../../resources/activities/basic/desktop/attach-activity.png)

Компонент осуществляет подключение к действующему процессу внешнего приложения.



Общие свойства элемента описаны в разделе [Работа с элементами](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements). Утилитарные свойства приведены в таблице ниже.

| Свойство               | Тип                               | Описание                                                                                                                                                                                                       |
| ---------------------- | --------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Заголовок              | String                            | Заголовок подключаемого приложения                                                                                                                                                                             |
| Имя процесса           | String                            | Название процесса запущенного приложения. Если указан заголовок приложения, имя процесса можно не указывать. Если заполнены оба свойства, при подключении будут учитываться оба значения                       |
| Таймаут\*              | Int32                             | Предельное время ожидания завершения процесса (мс)                                                                                                                                                             |

## Только код  
Пример использования элемента в процессе с типом **Только код** (Pure code):
> Для работы с примером необходимо установить приложение **mate-calc**.

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Калькулятор", 10000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Калькулятор", 10000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Калькулятор", 10000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
```
{% endtab %}
{% endtabs %}
