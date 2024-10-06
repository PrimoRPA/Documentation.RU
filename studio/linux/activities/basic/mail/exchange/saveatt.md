---
description: Save attachment
---

# Сохранить вложение

Элемент позволяет сохранить вложение письма.

![](../../../../resources/activities/basic/mail/exchange/exchange-save-attachment-activity.png)

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство     | Тип                                                                     | Описание                           |
| ------------ | ----------------------------------------------------------------------- | ---------------------------------- |
| Путь к файлу | String                                                                  | Путь к файлу. Пример: `"C:\\folder\\files.ext"` |
| Вложение     | [LTools.Office.Model. OMailAttachment](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_mail/datatypes/omailattachment) | Название переменной, хранящей вложение письма. Например, фото, документ, а с версии 1.23.11 вложением может быть и другое письмо (в виде файла \*.eml) |

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

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

LTools.Office.Model.WFSaveAttachment attachment = null;
var pathToFile = "pathToFile";

app.SaveAttachment(attachment, pathToFile);
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

attachment = None;
pathToFile = "pathToFile";

app.SaveAttachment(attachment, pathToFile)
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

var attachment = Null;
var pathToFile = "pathToFile";

app.SaveAttachment(attachment, pathToFile);
```
{% endtab %}
{% endtabs %}
