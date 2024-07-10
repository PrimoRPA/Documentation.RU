# Исчезновение элемента

![](../../../resources/activities/basic/browser/image-100-1-1-1-1-1-1-1-2-68.png)

![](../../../resources/activities/basic/browser/element-vanish-activity.png)

Компонент, ожидающий исчезновение элемента управления.

## Свойства
| Свойство        | Тип    | Описание                                           |
| --------------- | ------ | -------------------------------------------------- |
| Шаблон поиска\* | String | Шаблон поиска элемента управления                  |
| Таймаут\*       | Int32  | Предельное время ожидания завершения процесса (мс) |


## Только код  
Пример использования элемента в процессе с типом **Только код** (Pure code):
>Для демонстрации исчезновения элемента в станице браузера, открытой при работе примера, необходимо ввести любой текст для поиска и нажать клавишу Enter.

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Open(wf, LTools.WebBrowser.Model.BrowserTypes.Yandex, "https://www.google.com/");
app.WaitElementVanish("{\"Tag\":\"TEXTAREA\",\"Text\":\"\",\"CSSSelector\":\"\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"gLFyf\"}]}", 20000);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.WebBrowser.BrowserApp.Open(wf, LTools.WebBrowser.Model.BrowserTypes.Yandex, "https://www.google.com/")
app.WaitElementVanish("{\"Tag\":\"TEXTAREA\",\"Text\":\"\",\"CSSSelector\":\"\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"gLFyf\"}]}", 20000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = LTools.WebBrowser.BrowserApp.Open(wf, LTools.WebBrowser.Model.BrowserTypes.Yandex, "https://www.google.com/");
app.WaitElementVanish("{\"Tag\":\"TEXTAREA\",\"Text\":\"\",\"CSSSelector\":\"\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"gLFyf\"}]}", 20000);
```
{% endtab %}
{% endtabs %}
  
