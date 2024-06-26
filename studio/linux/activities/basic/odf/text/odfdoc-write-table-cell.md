---
description: Write table cell
---

# Записать в ячейку таблицы

![](../../../../resources/activities/basic/odf/text/odfdoc-write-table-cell.png)

Элемент записывает текст в ячейку таблицы. Элемент работает корректно только внутри контейнера  "Документ ODF".

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство     | Тип    | Описание                                  | Пример          |
| ------------ | ------ | ----------------------------------------- | --------------- |
| **Word** | | | |
| Индекс\* | Int32  | Порядковый номер таблицы (отсчет ведется с нуля) |`0`|
| Данные   | string | Данные ячейки            |`"строка"`|
| Строка   | Int32  | Индекс строки  (отсчет ведется с нуля) |`1`|
| Колонка  | Int32  | Индекс колонки  (отсчет ведется с нуля) |`2`|

## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
Primo.Office.OdfOxml.WordApp app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName");
app.WriteTableCell(idx, data, row, col);
```
{% endtab %}

{% tab title="Python" %}
```python
app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName")
app.WriteTableCell(idx, data, row, col)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app =  _lib.Primo.Office.OdfOxml.WordApp.Init(wf, "fileName");
app.WriteTableCell(idx, data, row, col);
```
{% endtab %}
{% endtabs %}
