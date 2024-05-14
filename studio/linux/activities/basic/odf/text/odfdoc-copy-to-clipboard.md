---
description: Copy to clipboard
---

### Копировать в буфер обмена

Копирует текст в буфер обмена

Вставляем ссылку до картинки с визуальным обликом элемента, например:   

![](../../../../resources/activities/basic/odf/text/odfdoc-copy-to-clipboard.png)


Элемент работает корректно только внутри контейнера "Документ ODF"

### Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Текст**:

1. **Начало** *[Int32]* - Индекс символа начала текста для копирования в буфер обмена (отсчет с нуля, по умолчанию ноль). Пример: `12`.
2. **Длина** *[Int32]* - Длина текста(количество символов) для копирования в буфер обмена (по умолчанию до конца документа). Пример: `24`.

### Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
Primo.Office.OdfOxml.WordApp app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName");
app.CopyToClipboard( 12, 24);
```
{% endtab %}

{% tab title="Python" %}
```python
app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName")
app.CopyToClipboard( 12, 24)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let app =  _lib.Primo.Office.OdfOxml.WordApp.Init(wf, "fileName");
app.CopyToClipboard( 12, 24);
```
{% endtab %}
{% endtabs %}


/// Если для элемента не реализован чистый код, то сам раздел не убираем - просто пишем в нем, что на данный момент функция не реализована.
