# Уничтожить процесс

![](../../resources/basic/desktop/image-(182).png)

Компонент, осуществляющий принудительное завершение внешнего приложения.

Данный компонент завершает все процессы, удовлетворяющие требованиям, указанным в свойствах. Если запущено 3 экземпляра одного процесса, то при указании его имени в свойстве **Имя процесса** будут закрыты все 3 экземпляра данного процесса.  

| Свойство             | Тип                               | Описание                                                                            |
| -------------------- | --------------------------------- | ----------------------------------------------------------------------------------- |
| Текущий пользователь | bool                              | Признак получения только процессов текущего пользователя                            |
| Тип автоматизации    | LTools.Desktop.Model.DesktopTypes | Тип используемой при взаимодействии с приложением автоматизации (UIAUTOMATION, RDP) |
| Заголовок            | String                            | Заголовок подключаемого приложения                                                  |
| Имя процесса         | String                            | Имя процесса                                                                        |
| Таймаут              | Int32                             | Предельное время ожидания завершения процесса (мс)                                  |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp.Kill(wf, null, "Test_*", 10000, true);
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Desktop.DesktopApp.Kill(wf, None, "Test_*", 10000, True)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Desktop.DesktopApp.Kill(wf, null, "Test_*", 10000, true);
```
{% endtab %}
{% endtabs %}