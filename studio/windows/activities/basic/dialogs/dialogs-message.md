# Окно сообщения

![](../../../resources/activities/basic/dialogs/image-387.png)

Компонент, производящий отображение окна с заданным сообщением.

Для корректной работы компонента необходимо в настройках Студии установить чекбокс "Наличие UI".

## Свойства

1. **Текст\*** *[String]* - Отображаемое сообщение

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Workflow.PrimoApp.MessageBox(wf, "text");
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Workflow.PrimoApp.MessageBox(wf, "text")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Workflow.PrimoApp.MessageBox(wf, "text");
```
{% endtab %}
{% endtabs %}
