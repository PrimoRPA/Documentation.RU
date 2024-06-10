# Выделение диапазона

![](../../../../resources/activities/basic/odf/table/cropped-selectrange-fixed.png)

Компонент выделяет диапазон ячеек Excel.<br>
Элемент работает только для файлов формата Microsoft Excel (файлы с расширением xsl, xlsx, xlsx, xlsm), поскольку все прочие форматы не поддерживают сохранение выделения диапазона.

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

1. **Диапазон\*** *[String]*: Диапазон считывания ячеек (A1:D12).
2. **Страница** *[String]*: Наименование страницы.
3. **Индекс страницы** *[Int32]*: Индекс страницы.

## Только код
Пример использования элемента в процессе с типом Только код (Pure code):  

**C#**  
`Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file]);`  
`app.SelectRange(range, [sheet], [sheetIdx]);`
