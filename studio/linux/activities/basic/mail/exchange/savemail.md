# Сохранить сообщение

![](../../../../resources/activities/basic/mail/exchange/exchange-save-message-activity.png)

Позволяет сохранить на диск письмо из электронной почты MS Exchange. Корректно работает только внутри контейнера [**Сервер MS Exchange**](https://docs.primo-rpa.ru/primo-rpa/g\_elements/el\_basic/els\_mail/els\_exchange/el\_connect).

> _Общие свойства элемента описаны в разделе_ [_**Работа с элементами**_](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)_._

| Свойство    | Тип                                                                        | Описание                               |
| ----------- | -------------------------------------------------------------------------- | -------------------------------------- |
| Путь\*      | String                                                                     | Путь сохранения файла в формате \*.eml |
| Сообщение\* | [LTools.Office.Model.OMailMessage](../els\_mail/datatypes/omailmessage.md) | Письмо для сохранения, переменная      |

{% tabs %}
{% tab title="C#" %}
```csharp
var version = Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2010;
var url = "url";
var login = "login";
var password = "password";
var domain = "domain";
var russianTimeZone = false;

LTools.Office.MSExchangeApp app = LTools.Office.MSExchangeApp.InitSvc(wf, version, url, login, password, domain, russianTimeZone);

LTools.Office.Model.OMailMessage message = null;
var pathToFile = "pathToFile";

app.SaveMessage(message, pathToFile);
```
{% endtab %}

{% tab title="Python" %}
```python
version = Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2010;
url = "url";
login = "login";
password = "password";
domain = "domain";
russianTimeZone = False;

app = LTools.Office.MSExchangeApp.InitSvc(wf, version, url, login, password, domain, russianTimeZone);

message = None;
pathToFile = "pathToFile";

app.SaveMessage(message, pathToFile)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var version = Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2010;
var url = "url";
var login = "login";
var password = "password";
var domain = "domain";
var russianTimeZone = false;

var app = _lib.LTools.Office.MSExchangeApp.InitSvc(wf, version, url, login, password, domain, russianTimeZone);

message = Null;
pathToFile = "pathToFile";

app.SaveMessage(message, pathToFile);
```
{% endtab %}
{% endtabs %}
