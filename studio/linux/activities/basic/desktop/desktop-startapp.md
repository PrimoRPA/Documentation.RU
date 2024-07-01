# Запустить приложение

![](../../../resources/activities/basic/desktop/start-process.png)

Компонент, запускающий новый процесс.

## Свойства
| Свойство          | Тип                               | Описание                                                                            |
| ----------------- | --------------------------------- | ----------------------------------------------------------------------------------- |
| Тип автоматизации | LTools.Desktop.Model.DesktopTypes | Тип используемой при взаимодействии с приложением автоматизации (UIAUTOMATION, RDP) |
| Приложение\*      | String                            | Имя запускаемого приложения                                                         |
| Аргументы         | String                            | Аргументы процесса. Возможно указать несколько аргументов через пробел: `"arg1 arg2"` |
| Рабочая папка     | String                            | Путь к рабочей папке процесса                                                       |
| Ожидать запуск    | Boolean                           | Ожидать запуск приложения                                                           |
| Переменная\*      | System.Diagnostics.Process        | Переменная для хранения созданного процесса                                         |

## Только код  
Пример использования элемента в процессе с типом **Только код** (Pure code):
> Для работы с примером необходимо установить приложение **mate-calc**.

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp.Start(wf, "mate-calc", null, null, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION, true);
LTools.Desktop.DesktopApp.Start(wf, "mate-calc", "--version");
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Desktop.DesktopApp.Start(wf, "mate-calc", None, None, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION, True)
LTools.Desktop.DesktopApp.Start(wf, "mate-calc", "--version")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Desktop.DesktopApp.Start(wf, "mate-calc", null, null, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION, true);
_lib.LTools.Desktop.DesktopApp.Start(wf, "mate-calc", "--version");
```
{% endtab %}
{% endtabs %}
