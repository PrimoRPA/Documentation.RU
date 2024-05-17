---
description: Change cells
---
### Изменение ячейки

![](../../../../resources/activities/basic/odf/table/odftable-changecell.png)

Компонент изменяет формат ячеек таблицы.

### Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство     | Тип    | Описание                                  | Пример          |
| ------------ | ------ | ----------------------------------------- | --------------- |
| **Таблица:** | | | |
| Диапазон* | String | Диапазон ячеек | `"A1:D12"` |
| Страница | String | Название страницы (работает только когда не указан индекс страницы) | `"Лист 1"` |
| Индекс страницы | Int32 | Индекс страницы (отсчет ведется с нуля; значение по умолчанию - `0`, когда название страницы также не указано)| `1` |
| Цвет ячеек | Sуstem.Drawing.Color? | Цвет ячеек диапазона | `System.Drawing.Color.LightBlue` |
| Цвет бордюра | Sуstem.Drawing.Color? | Цвет бордюра ячеек диапазона | `System.Drawing.Color.Black` |
| Тип бордюра | Primo.Office.OdfOxml.Model.CellBorderTypes | Определяет бордюр ячеек для изменения | `Primo.Office.OdfOxml.Model.CellBorderTypes.Around` |
| Толщина бордюра | Primo.Office.OdfOxml.Model.CellBorderThickness | Толщина бордюра ячеек | `Primo.Office.OdfOxml.Model.CellBorderThickness.Medium`|
### Примечание
Свойство **Тип бордюра** может принимать следующие значения:<br>

- Keep: не изменять границы
- None: удалить все границы ячеек
- Around: внешняя граница диапазона
- Full: все границы ячеек
- Left: левая граница диапазона
- Right: правая граница диапазона
- Top: верхняя граница диапазона
- Bottom: нижняя граница диапазона
- Vertical: вертикальные границы ячеек       
- Horizontal: горизонтальные границы ячеек

Свойство **Толщина бордюра** может принимать следующие значения:<br>
- Thin: тонкий
- Medium: средний
- Thick: толстый

### Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file]);
app.SetCells("A1:D12",System.Drawing.Color.LightBlue, System.Drawing.Color.Black, Model.CellBorderThickness.Medium, Model.CellBorderTypes.Around, [sheet], [sheetIdx]);
```
{% endtab %}

{% tab title="Python" %}
```python
Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file])
app.SetCells("A1:D12",System.Drawing.Color.LightBlue, System.Drawing.Color.Black, Model.CellBorderThickness.Medium, Model.CellBorderTypes.Around, [sheet], [sheetIdx])
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file]);
app.SetCells("A1:D12",System.Drawing.Color.LightBlue, System.Drawing.Color.Black, Model.CellBorderThickness.Medium, Model.CellBorderTypes.Around, [sheet], [sheetIdx]);
```
{% endtab %}
{% endtabs %}
