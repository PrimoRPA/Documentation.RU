# Экспортировать документ

![](../../../../resources/activities/basic/odf/text/cropped-exportdoc-fixed.png)

Компонент, производящий экспорт документа Word в другой формат. Доступный формат: PDF

## Свойства

1. **Путь к файлу** *[String]*: Путь к файлу (c:\folder\files.pdf).
2. **Формат** *[LTools.Office.Model.WordExportFormats]*: Тип формата.

## Только код
Пример использования элемента в процессе с типом Только код (Pure code):

C#:  
`Primo.Office.OdfOxml.WordApp app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName");`   
`app.Export(fileName, [format]);`
