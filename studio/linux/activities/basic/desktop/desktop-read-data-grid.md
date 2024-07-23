# Чтение таблицы

![](../../../resources/activities/basic/desktop/desktop-read-data-grid.png)

Компонент, производящий чтение данных табличного элемента управления. Компонент корректно работает только внутри контейнера Присоединиться к приложению.

| Свойство             | Тип                                                          | Описание                                           |
| -------------------- | ------------------------------------------------------------ | -------------------------------------------------- |
| Шаблон поиска        | String                                                       | Шаблон поиска элемента управления                  |
| Элемент              | LTools.Desktop.Model.DUIControl                              | Ссылка на элемент управления                       |
| Переменная           | [LTools.Desktop.Model.UIDataTable](datatypes/uidatatable.md) | Переменная для хранения результатов чтения таблицы |
| Переменная (таблица) | System.Data.DataTable                                        | Переменная для хранения результатов чтения таблицы |
| Таймаут\*            | Int32                                                        | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
string processName = "fly-admin-device-manager";
string applicationTitle = null;
int timeOut = 20000;
bool isCurrentUser = true;

LTools.Desktop.DesktopApp application = LTools.Desktop.DesktopApp.Init(wf, processName, applicationTitle, timeOut, isCurrentUser, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);

string searchPattern = "{\"WinName\":\"Менеджер устройств\",\"WinPath\":\"/org/a11y/atspi/accessible/2147483675\",\"WinId\":-1,\"AppName\":\"fly-admin-device-manager\",\"Items\":[{\"Name\":\"\",\"Role\":\"tree\",\"Description\":\"\",\"Index\":1,\"Items\":[]}]}";

LTools.Desktop.Model.UIDataTable uiDataTable = application.ReadDataGrid(searchPattern);
```
{% endtab %}

{% tab title="Python" %}
```python
processName = "fly-admin-device-manager"
applicationTitle = None
timeOut = 20000
isCurrentUser = True

application = LTools.Desktop.DesktopApp.Init(wf, processName, applicationTitle, timeOut, isCurrentUser, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)

searchPattern = "{\"WinName\":\"Менеджер устройств\",\"WinPath\":\"/org/a11y/atspi/accessible/2147483675\",\"WinId\":-1,\"AppName\":\"fly-admin-device-manager\",\"Items\":[{\"Name\":\"\",\"Role\":\"tree\",\"Description\":\"\",\"Index\":1,\"Items\":[]}]}"

uiDataTable = application.ReadDataGrid(searchPattern)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var processName = "fly-admin-device-manager";
var applicationTitle = None;
var timeOut = 20000;
var isCurrentUser = True;

var application = _lib.LTools.Desktop.DesktopApp.Init(wf, processName, applicationTitle, timeOut, isCurrentUser, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);

var searchPattern = "{\"WinName\":\"Менеджер устройств\",\"WinPath\":\"/org/a11y/atspi/accessible/2147483675\",\"WinId\":-1,\"AppName\":\"fly-admin-device-manager\",\"Items\":[{\"Name\":\"\",\"Role\":\"tree\",\"Description\":\"\",\"Index\":1,\"Items\":[]}]}";

var uiDataTable = application.ReadDataGrid(searchPattern);
```
{% endtab %}
{% endtabs %}
